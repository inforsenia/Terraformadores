# Ejemplo utilización PyYAML

## Instalación
Una vez instalado Python:

- En debian/Ubuntu instalamos el gestor de paquetes python pip:

	    apt-get install python3-pip

    E instalamos el páquete:

	    pip install PyYAML

- En Windows
    ```powershell
    py -m ensurepip --upgrade
    py get-pip.py
    pip install pyyaml
    ```

## Leer un fichero YAML

Si tenemos el fichero books.yaml:

```yaml
bookstore:
  book: 
  - title: 
        lang: "en"
        text: "Everyday Italian"
        author: "Giada De Laurentiis"
        year: "2005"
        price: "30.00"
        category: "COOKING"
    
  - title: 
        lang: "en"
        text: "Harry Potter"
        author: "J K. Rowling"
        year: "2005"
        price: "29.99"
        category: "CHILDREN"
    
  - title: 
        lang: "en"
        text: "XQuery Kick Start"
        author: 
            - "James McGovern"
            - "Per Bothner"
            - "Kurt Cagle"
            - "James Linn"
            - "Vaidyanathan Nagarajan"
        year: "2003"
        price: "49.99"
        category: "WEB"
    
  - title: 
        lang: "en"
        text: "Learning XML"
        author: "Erik T. Ray"
        year: "2003"
        price: "39.95"
        category: "WEB"
```

Podríamos hacer un programa como este para ver como representa internamente la información de yaml después de abrir el fichero y como se accede a la información básica utilizando la libreria pyyaml:

```python
import yaml   
with open("books.yaml") as fichero:
    doc=yaml.safe_load(fichero)
```

## Obteniendo información
```python
print(doc)
```

### Cantidad de libros
```python
numLibros=(len(doc["bookstore"]["book"]))
print("Número de libros en la biblioteca: ",numLibros)
```
### Títulos de los libros
```python
for libro in doc["bookstore"]["book"]:
    print(libro["title"]["text"]) 
```
### Autores de los libros
```python
for libro in doc["bookstore"]["book"]:
    if isinstance(libro["author"],list):
        for autor in libro["author"]:
            print(autor)
    else:
        print(libro["author"])
```