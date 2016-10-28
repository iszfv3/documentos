## Manual de uso Sass

#### Como instalarlo

1) Sass se instala mediante la consola de Ruby, por lo tanto se debe descargar Ruby de aqui "http://rubyinstaller.org/"
2) Una vez instalado Ruby se abre la pantalla de comandos y se ejecuta el siguiente comando "gem install sass" y se verifica que este correctamente instalado con el comando **"sass -v".**

### Acomodando el entorno
Por experiencia propia es mas comodo trabajar Sass desde Sublime Text que en otro editor gracias a los plugins que hay para Sass en este.
Al utilizar Sublime Text se debe instalar el plugin "Syntax Highlighting for Sass" que permite llevar un mejor manejo del codigo.
Luego se debe fijar la syntax en Sass y estas listo para trabajar.

### Empezando a trabajar con Sass
Lo primero es crear el archivo .sass donde se va a trabajar, este archivo sera convertido a un css mediante el comando **"sass archivo.sass:archivo.css"**
Para que los cambios en el archivo Sass se agreguen en tiempo real al archivo css se debe de utilizar el siguiente comando **"sass --watch archivo.sass:archivo.css"**

### Utilizando Variables 
Es muy simple, solo se debe crear la variable con la siguiente syntax **"$nombredelavarible: valor"** estas son creadas mas que todo cuando van a ser utilizadas reiteradamente en el codigo.
la variable puede ser un color, tamaño, forma, etc.

#### Anidacion en Sass 
Si por ejemplo se tiene un header dentro del cual hay un elemento nav dentro del cual a su vez hay elementos a se puede dar estilos de la siguiente forma:
		
	header
	 //Estilos del header
	 nav
	   //Estilos del nav
	   a
	    //Estilos del a 

De esta forma se le da caracteristicas individuales y caracteristicas por anidacion a cada elemento. 

### Importando Archivos 
Aqui es donde ocurre la verdadera magia de Sass, supongamos se tiene una pagina html donde se le va a asignar estilos css a su navbar, a su footer, y a 3 secciones distintas de contenido.
Para ello se crea un solo documento css que puede ser llamado "main.css" que contiene todo el estilo de la pagina. Sass permite hacer esto de forma mucho mas facil, se puede crear un documento sass principal llamado main.sass 
y dentro de este se define todos los import que utiliza la hoja de estilo. Asi se obtiene un codigo mas facil de leer y mucho mas facil de editar mediante sass. 

El navbar, el footer y el contenido sera definido cada uno en un archivo sass y los 3 se juntaran en un mismo archivo css para que todo quede correctamente. Ejemplo:

	//Estilos del navbar en archivo _navbar.sass
	nav ul li{
		background: blue;
		font-size: 20px;
		border: 1px solid transparent;
			}

	//Estilos del footer en archivo _footer.sass
	footer{
		background: red;
		border: 1px solid transparent;
			}

	//Estilos del contenido en archivo _content.sass
	*{
		background: blue;
		font-size: 40px;
		padding-top: 10px;
			}
	div {
		display: inline-block;
			}

en el archivo **main.sass** todo quedaria: 

	@import _navbar
	@import _footer
	@import _content

obteniendo como resultado la siguiente hoja de css:

	nav ul li{
		background: blue;
		font-size: 20px;
		border: 1px solid transparent;
			}
	footer{
		background: red;
		border: 1px solid transparent;
			}
	*{
		background: blue;
		font-size: 40px;
		padding-top: 10px;
			}
	div {
		display: inline-block;
			}

>Nota: todos los archivos a importar deben ser creados con **_nombredelarchivo **para identificarlo como un import.

### Mixins 
**Mixins:** Ahorra la ladilla de los prefijos. 
ejemplo para definir prefijos del border-radius: 
	
	=border-radius($radio)
	-webkit-border-radius: $radio
	-moz-border-radius: $radio
	-ms-border-radius: $radio
	border-radius: $radio

para llamar al mixin la syntax es **+nombreMixin(valor)** el atributo va en parentesis **NO** despues de **':'**

Mayores dudas consultar en la documentacion oficial de Sass, pero en realidad esto es todo.