## Manual de uso JSON
El JSON es la estructura de envio de datos por excelencia actualmente y es la que sera empleada constatemente en el diseño de cada app. 
El media type con el que se trabaja el JSON es "applicantion/json" y su extension es .json.

### Casos de uso de JSON

1) Es usado cuando se escriben aplicaciones en JavaScript que incluyen extensiones del navegador y de sitios.
2) El formato JSON es usado para enviar datos estructuradas a traves de conexiones de red.
3) Su uso principal es para transmitir datos entre servidor y la aplicacion web.
4) Los Web services y las APIs utilizan JSON para proveer los datos.
5) Puede ser usado con los lenguajes de programacion mas modernos. 

### Caracteristicas del JSON 
- Es facil de leer y escribir.
- Su formato basado en texto es ligero y de facil intercambio. 
- El JSON es independiente del lenguaje en que se este programando.

{
   "book": [
    
      {
         "id":"01",
         "language": "Java",
         "edition": "third",
         "author": "Herbert Schildt"
      },
    
      {
         "id":"07",
         "language": "C++",
         "edition": "second",
         "author": "E.Balagurusamy"
      }
   ]
}

### Syntax de un JSON 
La sintaxis de JSON es basicamente un subconjunto de la sintaxis de JavaScript e incluye lo siguiente:

- Los datos son representados en pares de nombre/valor
- Las llaves contienen los objetos y cada nombre le sigue ':', los pares de nombre/valor estan separados por comas ','
- Los corchetes contienen arreglos y valores separados por coma ','.

JSON soporta dos tipos de estructura de datos.
- Una coleccion de pares de nombre/valor que es el tipo de estructura soportada por la mayoria de lenguajes.
- Lista ordenada de valores que incluye arreglos, listas, vectores o secuencias, etc.

El formato JSON soporta todos los tipos de datos tradicionales: numeros (decimales o enteros), string, boolean, arreglos, valores, objetos.

### Tipos de datos que aceptada JSON

El formato JSON soporta los siguientes tipos de datos.

Tipo | Descripcion
----|----
Numeros | Enteros - decimales
String | De tipo unicode
Boolean | True o false
Array | Una forma ordenada de valores
Value | Puede ser un numero, string, true o flase, null, etc.
Objeto | Una coleccion que no esta ordenada de valores en pares nombre:valor
null | Vacios

### Crear un objeto JSON simple
Los objetos de tipo JSON pueden ser creados con JavaScript. 
ejm:

    var JSONObj = {}; //Creando el objeto vacio
    var JSONObj = new Object (); //Creando un nuevo objeto de tipo JSON.
    var JSONObj = {"bookname" : "Divina Comedia","precio":"200"}; //Asignandole valores al objeto JSON.

  
### Esquema de JSON
El JSON Schema es una especificacion para el JSON donde se definira la estructura que tendran los datos de este.
- Describe el formato existente de datos.
- Es una documentacion facil de leer tanto para la maquina como para el humano.
- Validacion estructural completa muy util para el testeo automatizado.
- Validacion estructural completa que permite validar los datos suministrados por el cliente.

Los librerias de validacion mas utilizadas son: 
- PHP: php-json-schema; json-schema
- JavaScript: Orderly; JSV; json-schema; Matic; Dojo; schema.js; Persevere.

{
   "$schema": "http://json-schema.org/draft-04/schema#",
   "title": "Product",
   "description": "A product from Acme's catalog",
   "type": "object",
    
   "properties": {
    
      "id": {
         "description": "The unique identifier for a product",
         "type": "integer"
      },
        
      "name": {
         "description": "Name of the product",
         "type": "string"
      },
        
      "price": {
         "type": "number",
         "minimum": 0,
         "exclusiveMinimum": true
      }
      },
    
      "required": ["id", "name", "price"]
      }

### Usando JSON en PHP 

Desde PHP 5.2.0 la extension JSON esta compilada por defecto.

Funciones JSON:
- json_encode: Retona la representacion JSON de un valor.
- json_decode: Decodifica el JSON en un string.
- json_last_error: Retorna el ultimo error ocurrido.








