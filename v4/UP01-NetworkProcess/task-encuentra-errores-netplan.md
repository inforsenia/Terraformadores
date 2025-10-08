# Tarea : [ NetPlan ] Errores en el Script.

El Agente Amarillo de la fundación SCP ha desaparecido, su última conexión fué hace más de 48 horas y 
no sabemos donde se encuentra.

No hay duda de que alguna cosa le ha ocurrido y de que necesitamos contactar con él. 

El equipo de *Respuesta Rápida Martillo de Terciopelo* ha llegado a la DMZ y ha encontrado 
este **Script** que estaba completando Amarillo. Sin embargo, cuando han ido a ejecutarlo, 
el Agente Warren ha detectado algo...**errores**, que si se ejecutaban en producción
podrían producir fallos en la red. 

Preparad un *Ubuntu Server* en una MV y arreglad el script: se han detectado *10 fallos*. 


```shell
#!/bin/bash

RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
NC='\033[0m'

error() {
    echo -e "${RED}[ERROR]${NC} $1"
    exit 1
}

info() {
    echo -e "${GREEN}[INFO]${NC} $1"
}

warning() {
    echo -e "${YELLOW}[WARNING]${NC} $1"
}

if [ "$(id -u)" -ne 0 ]; then
    error "Este script debe ejecutarse como root o con sudo."
fi

if ! command -v netplan &> /dev/null; then
    error "Netplan no está instalado. Instálalo con: apt install netplan.io"
fi

NETPLAN_DIR="/etc/netplan"
if [ ! -d "$NETPLAN_DIR" ]; then
    error "Directorio de Netplan no encontrado: $NETPLAN_DIR"
fi

detectar_tipo_red() {
    info "Detectando tipo de red..."
    if ip a | grep -q "inet " && ip route | grep -q "default via"; then
        if ip route | grep -q "192.168\|10.\|172.16"; then
            echo "NAT"
        else
            echo "RED_PUBLICA"
        fi
    elif ip a | grep -q "inet " && ! ip route | grep -q "default via"; then
        echo "ADAPTADOR_PUENTE"
    else
        echo "DESCONOCIDO"
    fi
}

pregunta() {
    local pregunta=$1
    local opciones=$2
    local respuesta
    echo -e "\n${YELLOW}$pregunta${NC}"
    echo "Opciones: $opciones"
    read -p "Selecciona una opción: " respuesta
    echo "$respuesta"
}

generar_netplan() {
    local nombre_archivo=$1
    local interfaz=$2
    local tipo_red=$3
    local ip=$4
    local gateway=$5
    local dns=$6

    local config="# Configuración de Netplan generada automáticamente\n"
    config+="network:\n"
    config+="  version: 2\n"
    config+="  renderer: networkd\n"
    config+="  ethernets:\n"
    config+="    $interfaz:\n"

    if [ "$tipo_red" = "NAT" ]; then
        config+="      dhcp4: true\n"
    elif [ "$tipo_red" = "RED_PUBLICA" ]; then
        config+="      addresses: [$ip]\n"
        config+="      routes:\n"
        config+="        - to: default\n"
        config+="          via: $gateway\n"
        config+="      nameservers:\n"
        config+="        addresses: [$dns]\n"
    elif [ "$tipo_red" = "ADAPTADOR_PUENTE" ]; then
        config+="      dhcp4: false\n"
        config+="      addresses: [$ip]\n"
    fi

    echo "$config" > "$nombre_archivo"
    info "Archivo de configuración generado: $nombre_archivo"
}

aplicar_netplan() {
    local archivo=$1
    info "Aplicando configuración de Netplan..."
    netplan apply
    if [ $? -eq 0 ]; then
        info "Configuración aplicada correctamente."
    else
        error "Error al aplicar la configuración de Netplan."
    fi
}

clear
info "Script de configuración de Netplan para Ubuntu Server"

interfaces=$(ip -o link show | awk -F': ' '{print $2}')
if [ -z "$interfaces" ]; then
    error "No se encontraron interfaces de red."
fi

interfaz=$(pregunta "Selecciona la interfaz de red a configurar:" "$interfaces")

tipo_red=$(detectar_tipo_red)
info "Tipo de red detectado: $tipo_red"

if [ "$tipo_red" = "NAT" ]; then
    info "Configuración automática (DHCP) para NAT."
    ip="dhcp"
    gateway="auto"
    dns="auto"
elif [ "$tipo_red" = "RED_PUBLICA" ]; then
    ip=$(pregunta "Introduce la IP estática (ej: 192.168.1.100/24):" "")
    gateway=$(pregunta "Introduce el gateway (ej: 192.168.1.1):" "")
    dns=$(pregunta "Introduce los DNS (ej: 8.8.8.8,8.8.4.4):" "")
elif [ "$tipo_red" = "ADAPTADOR_PUENTE" ]; then
    ip=$(pregunta "Introduce la IP estática (ej: 192.168.1.100/24):" "")
    gateway="none"
    dns="none"
else
    error "No se pudo detectar el tipo de red."
fi

nombre_archivo="/home/$(logname)/netplan_$interfaz.yaml"
generar_netplan "$nombre_archivo" "$interfaz" "$tipo_red" "$ip" "$gateway" "$dns"

info "Copiando configuración a $NETPLAN_DIR..."
cp "$nombre_archivo" "$NETPLAN_DIR/"
aplicar_netplan "$nombre_archivo"

info "Resumen de la configuración:"
echo "----------------------------------------"
cat "$nombre_archivo"
echo "----------------------------------------"
info "Configuración completada. El archivo también está en tu HOME: $nombre_archivo"

```

