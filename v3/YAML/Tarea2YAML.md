### Segundo Ejercicio: Automatización con Ansible y YAML en Terraformadores de Venus

En **Terraformadores de Venus**, buscamos constantemente optimizar y automatizar nuestras infraestructuras para garantizar la seguridad, eficiencia y escalabilidad de nuestros servicios. En esta segunda misión sobre **YAML**, vamos a adentrarnos en el uso de **Ansible**, una herramienta fundamental para la administración automatizada de sistemas.

#### ¿Qué es Ansible y por qué es tan importante?

**Ansible** es una herramienta de automatización que nos permite gestionar la configuración y despliegue de aplicaciones en nuestra infraestructura sin necesidad de interacción manual. A través de **playbooks**, que son archivos escritos en **YAML**, podemos definir de forma clara y estructurada las tareas que deben ejecutarse automáticamente en nuestros servidores. Gracias a Ansible, podemos llevar a cabo configuraciones complejas en minutos, lo que resulta especialmente útil para escalar nuestros servicios en la nube privada **NimbusNet** y en los entornos híbridos que gestionamos.

La importancia de Ansible en la administración de sistemas radica en su simplicidad y capacidad de automatización, permitiéndonos realizar desde configuraciones sencillas hasta despliegues a gran escala, con tareas repetibles y fáciles de mantener.

### Ejercicio: Configuración de Ansible y Análisis de Playbooks

Ya habéis demostrado vuestro dominio del lenguaje de programación **Python** en misiones de otros visionario, por lo que esta actividad os servirá para profundizar aún más en su uso en contextos de administración de sistemas. En esta misión, vais a aplicar vuestros conocimientos de Python para analizar un playbook de Ansible. En caso de no haber tocado nunca Python no os preocupeis ya que se trata de una práctica muy fácil, que podréis realizar sin problemas si os basais en el ejemplo que has trabajado en clase [enlace](./ejemplosLibros.md)

El archivo [`ansible.yaml`](./ansible.yaml) es un playbook que tiene como objetivo la instalación automática de **MySQL** en uno de nuestros servidores. Vuestra tarea será crear diferentes instrucciones en Python para procesar y extraer información del playbook, demostrando así vuestro manejo de **YAML** y **Python**.

#### Tareas a realizar:
Crear un programa en Python que devuelva lo siguiente
1. **Contar el número de tareas en el playbook:**
   - Se debe devolver cuántas tareas se ejecutan en el playbook [`ansible.yaml`](./ansible.yaml).

2. **Obtener los nombres de las tareas:**
   - Se debe devolver una lista con los nombres de las distintas tareas definidas en el playbook.

3. **Instalación de paquetes:**
   - La primera tarea del playbook realiza la instalación de paquetes en el servidor. Muestra el nombre de los paquetes que se instalan.

4. **Contraseña de MySQL para el usuario root:**
   - Dentro del playbook, se asigna una contraseña al usuario root de **MySQL**. El programa debe mostrar dicha contraseña.


### ¿Qué debes entregar?

1. **Fichero Python:** Un archivo con las funciones en Python que realicen las tareas descritas. 

   Añade comentarios al código `#` y insturcciones `print` para que la salida del programa sea clara y se pueda apreciar cada parte del ejercicio de forma separada.
   
2. **Fichero Markdown:** Un documento Markdown con una **breve** explicación del proceso que seguiste para analizar el playbook. Incluye capturas de pantalla de los resultados de la ejecución del programa, demostrando que tu código funciona correctamente.

Con este ejercicio completarás tu inmersión en el uso práctico de **YAML** dentro de **Terraformadores de Venus**, aplicando el conocimiento tanto en la configuración de sistemas como en la automatización de tareas críticas para la infraestructura. Al mismo tiempo, demostrarás tu dominio de Python.


### Codigo Ansible.yaml
```yaml
---
hosts: servidor_mysql
sudo: yes
vars:
  mysql_root_db_pass: 'asdasd'
tasks:
  - name: install mysql
    apt: name={{ item }} state=latest
    with_items:
      - mysql-server
      - python-mysqldb 

  - name: Ensure mysql binds to internal interface
    template: >
      src=templates/my.cnf 
      dest=/etc/mysql/my.cnf 
      owner=root 
      group=root 
      mode=0644
    notify: restart mysql
  
  - name: update mysql root password for locahost accounts
    mysql_user: >
      name=root
      host=localhost
      password={{ mysql_root_db_pass }}
  - name: copy .my.cnf file with root password credentials
    template: src=templates/.my.cnf.j2 dest=~/.my.cnf owner=root mode=0600


  - name: update mysql root password for all root accounts
    mysql_user: name=root host={{ item }} password={{ mysql_root_db_pass }}
    with_items:
      - "{{ ansible_hostname }}"
      - localhost


handlers:
  - name: restart mysql
    service: name=mysql state=restarted
```