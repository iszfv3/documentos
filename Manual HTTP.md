## Manual HTTP

El conjunto de metodos comunes para HTTP esta definido a continuación y puede ser expandido en base a los requerimientos. 
Los nombres de estos metodos son suceptibles a mayusculas y minisculas y deben ser escritos en mayuscula.

### Metodos y descripcion 

#### GET
El metodo GET es utilizado para recuperar informacion enviada del servidor utilizando un URI dado. 
Las solicitudes usando GET deben unicamente recuperar datos y no deben modificar los datos de ninguna forma. 
Este es el metodo principal a la hora de recuperar datos del servidor.

#### HEAD

Igual que GET, pero transfiere la linea de estatus y la seccion de header unicamente.   

#### POST 
Las peticiones de tipo POST son usadas para enviar los datos al servidor, por ejemplo, informacion del cliente, subir archivos, utilizando formularios HTML.

#### PUT 
Remplaza la informacion actual del servidor con el contenido enviado por el formulario.

#### DELETE 
Remueve la informacion del servidor destino asignado por un URI.

#### CONNECT 
Convierte la peticion de conexion en un tunel TCP/IP, usualmente se usa para facilitar la comunicacion encriptada SSL a traves de un proxy HTTP que no esta encriptado. 
Es usado por el cliente para establecer una conexion de red a un servidor web a traves de HTTP.

#### OPTIONS
Describe las opciones de comunicacion del servidor. Es usado por el cliente para averiguar cual metodo HTTP y otras opciones son soportadas por el servidor web.
El cliente puede especificar un URL para el metodo OPTIONS, o un asterisco (*) para referirse al servidor entero.

#### TRACE
Ejecuta un examen de revision interna en el servidor.
Es usado para imitar los contenidos de un peticion HTTP de regreso al que la solicita lo que puede ser usado para tareas elimar bugs en el tiempo de desarrollo. 

### Codigos de Estatus

Los codigos de status son elementos que envian los servidores, es un numero entero de 3 digitos donde el primer digito define la clase o peticion y los ultimos dos no tienen ningun rol en particular. Existen 5 valores para el primer digito:

1) 1xx -> Informativo: Significa que la peticion fue recibida y el proceso continua.
2) 2xx -> Exito: Significa que la accion fue recibida de forma exitosa, comprendida y aceptada. 
3) 3xx -> Redireccion: Significa que se deben tomar acciones adicionales para poder completar la peticion.
4) 4xx -> Error de cliente: Indica que la peticion tiene errores de tipeo o no puede ser cumplida.
5) 5xx -> Error de servidor: Indica que el servidor ha fallado en realizar la peticion, aparentemente, valida. 

#### Descripcion de cada estatus
**Tipo 1xx**

100 -> Continua: El servidor solo ha recibido una parte de la peticion, pero mientras no sea rechazada, la solicitud del cliente puede continuar. 
101 -> Cambiando protocolos: El servidor cambia de protocolo.

**Tipo 2xx**

200 -> OK: La solicitud fue procesada correctamente.
201 -> Creado: La solicitud fue completada y un nuevo recurso fue creado.
202 -> Aceptado: La peticion fue aceptada para ser procesada, pero el procesamiento no esta completo. 
203 -> Informacion no autorizada: La informacion perteneciente al header proviene de una copia local o de un tercero, no del servidor original.
204 -> Sin contenido: Se retorna un estatus y un header, pero no existe contenido en el body de la respuesta.
205 -> Contenido reiniciado: El navegador deberia limpiar el formulario usado en la operacion antes de agregar nueva informacion.
206 -> Contenido parcial: El servidor esta retornando solo una parte de la peticion enviada.  
 
**Tipo 3xx**

300 -> Opciones multiplies: Una lista de links. El usuario puede seleccionar un link e ir a esa direccion. Maximo cinco direcciones.
301 -> Mudado: La pagina solicitada fue mudada a una nueva URL.
302 -> Encontrado: La pagina solicitdad fue movida temporalmente a una nueva URL.
303 -> Ver otro: La pagina solicitada puede ser encontrada con otro URL diferente.
304 -> No modificado: Este es el codigo de respuesta a un header del tipo Modificado-desde, donde el URL no ha sido modificado desde dicha fecha.
305 -> Usar proxy: El URL solicitado debe ser accedido mediante el proxy mencionado en el Location del header,
307 -> Redireccionado temporalmente: La pagina solicitada ha sido movida temporalmente a una nueva URL.

**Tipo 4xx**

400 -> Solicitud erronea: El servidor no entiende la peticion.
401 -> Sin permiso: La pagina solicitada requiere un usuario y contraseña.
403 -> Prohibido: El acceso a la pagina solicitada esta prohibido.
404 -> No encontrado: El servidor no puede encontrar la pagina solicitada.
405 -> Metodo no permitido: El metodo especificado en la peticion no esta permitido.
406 -> No es aceptable: El servidor puede generar unicamente una respuesta que no es aceptada por el cliente.
407 -> Requiere autenticacion de proxy: Debes autenticar con un servidor de proxy antes de poder atender la peticion. 
408 -> Paso el tiempo de peticion: La peticion tomo mas tiempo del que el servidor esta preparado para esperar.
409 -> Conflicto: La peticion no fue completada debido a un conflicto.
410 -> Desaparecida: La pagina solicitada no se encuentra mas disponible.
411 -> Longitud requerida: El "Content-Length" no esta definido. El servidor no aceptara una peticion sin ella.
413 -> Peticion muy larga: El servidor no aceptara la peticion porque la entidad es muy larga.
414 -> URL solicitado es muy largo: El servidor no aceptara la peticion porque el url es muy largo. Ocurre cuando conviertes una peticion "post" a un "get" con mayor informacion de busqueda.
415 -> Media type no soportado: El servidor no acepta la peticion porque el mediatype no es soportado.

**Tipo 5xx**

500 -> Error interno en el servidor: La solicitud no fue completada. El servidor encontro una condicion inesperada.
501 -> No implementado: La solicitud no fue completada. El servidor no soporta la funcionalidad requerida.
502 -> Gateway erroneo: El servidor recibio una respuesta invalida de un servidor TRADUCIR UPSTREAM
503 -> Servicio indisponible: El servidor esta temporalmente sobrecargado o caido.
504 -> Tiempo de Gateway: El tiempo del gateway ha caducado.
505 -> Version de HTTP no soportada: El servidor no puede soportar el protocolo http enviado en esta version.
 
### Seguridad en HTTP 

HTTP es usado para las comunicaciones en el internet, asi que los desarrolladores de aplicaciones, los proveedores de informacion, y usuarios deben ser conscientes de las limitaciones de seguridad en HTTP/1.1. 
Aqui se plantean algunas recomendaciones para reducir los riesgos de seguridad.

#### Informacion personal filtrada

Los clientes HTTP usualmente proveen de una gran cantidad de informacion personal como sus nombres, direcciones, correos electronicos, contraseñas, etc. 
Asi que debes ser cuidadoso con prevenir filtrados inintencionales de esta informacion via el protocolo HTTP hacia otras fuentes.
Recomendaciones en este caso: 
	* Toda la informacion personal debe ser alojada en el servidor de forma encriptada.
	* Revelar la version especifica de software del servidor puede que lo vuelva mas vulnerable contra ataques en contra del software si se conoce los problemas de seguridad.
	* Proxys que sirven como portal a traves un firewall de la red de tomar especiales precauciones en relacion a la transferencia de informacion en el header que identifica el host detras del firewall.
	* La informacion enviada en el campo "From" puede generar conflictos con el interes de privacidad del cliente o la politica de seguridad del sitio, y por lo tanto, no debe ser enviado sin que el usuario esa capaz de desactivarlo, activarlo, y modificar en contenido de los campos.
	* Los clientes no pueden referir el campo del header en una peticion HTTP no segura, si la pagina fue transferida con un protocolo seguro.
	* Desarrolladores que usen el protocolo HTTP no deben usar el metodo GET para el envio de datos de formularios, porque ocasionara que los datos sean codificados en la URI solicitada.

#### Ataques basados en los nombres de archivos y de direccion

El documento debe estar restringido a los documentos que fueron destinados por los administradores del servidor en cada peticion HTTP.

Por ejemplo, UNIX, Windows, y otros sistemas operativos usan '..' como complemento de ruta para indicar un directorio que esta un nivel debajo del directorio actual. 
En tales sistemas, un servidor HTTP DEBE prohibir este tipo de complemento en la URI solicitidad, de no hacerlo puede permitir acceso a recursos que no estaba planeado fueran accesibles en el servidor HTTP.

#### DNS engañoso 

Los clientes confian fuertemente en el servicio de DNS, es por eso que son propensos a ataques de seguridad basados en la mala interpretacion de la direccion IP y del nombre de DNS.
Asi que los clientes necesitan ser cuidadosos en asumir validaciones continuas de un numero IP/nombre de DNS.

El cliente HTTP pasa al cache el resultado de el nombre del host para poder mejorar el rendimiento, deben por lo tanto observar la informacion de TTL (Tiempo de vida) reportada por el DNS. 
Si el cliente HTTP no cumple con esta regla puede ser burlado cuando una direccion de servidor IP que ha sido previamente usada cambia. 






