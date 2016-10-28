##Lista de comandos principales en git
### Configuracion Inicial

    git config --global user.name "tu_nombre"
    git config --global user.email "tu_email"

### Crear nuevo repositorio
Creando uno nuevo

    cd "ubicacion donde quieres crear la nueva carpeta" 
    mkdir "nombre de la nueva carpeta"
    cd "nombre de la nueva carpeta creada" //Asi se crea y nos ubicamos en la nueva carpeta
    git init //Para iniciar el nuevo repositorio (Crear la carpeta .git dentro de la nueva carpeta)

Trabajando con uno ya creado que este en bitbucket por ejemplo

    git clone "direccion del repositorio en bitbucket" //Esperar clone todo el directorio de trabajo
    cd "carpeta donde esta el repositorio clonado"

### Trabajando en el repositorio (Directorio de trabajo)

Suponiendo se tiene un archivo creado llamado "index.html" y "style.css" y se quieren agregar al repositorio se hace lo siguiente

**Agregando index.html**

    git add index.html
    git commit -m "Descripcion del cambio"
    git push origin master //Se suben los cambios a nuestro repositorio en bitbucket

**Agregando ambos archivos**

    git add . //Con el punto se envia todas las modificaciones que tenga en el repositorio
    git commit -m "Descripcion de esos cambios"
    git push origin master

**NOTA IMPORTANTE SOBRE COMMIT:** Cualquier commit a realizar responde estas preguntas: 
1) Por que se hizo?
2) Que fue lo que se cambio? 
3) Que se espera cambie en el sistema? //Opcional con las primeras dos es suficiente si es un cambio corto
Cada pregunta se responde lo mas breve posible separando cada respuesta con un punto.

Ejemplo: Suponiendo que a un archivo llamado "style.css" se le cambio dos atributos con respecto  al tamaño y color de las letras del body

**MAL COMMIT:** git commit -m "Grande y verde"
**BUEN COMMIT:** git commit -m "Mejor visualizacion. Tamaño y color de letras en body. Mejor estilo en el body"

>NOTA DE LA NOTA: si solo ejecutan git commit se les abre la ventana de commit, de ser necesario expliquense todo lo que sea necesario aca si se un cambio muy grande.

Ese mensaje debe ser Primera linea: Resumen del cambio  
				      Segunda linea: va en blanco  
				      Tercera linea: Empieza la descripcion detallada del mensaje.

### Eliminar archivos en el repositorio

Suponiendo se quiere eliminar index.html del repositorio 

    git rm index.html
    git status //Para consultar que su estado sea "deleted"
    git commit -m "Commit de por que se borro el archivo"

Suponiendo que quiero eliminar el repositorio completo:
Me ubico en la carpeta donde esta el repositorio
ejecutar este comando: rd /s .git Presionar Y para confirmar.

### Moviendo archivos
Supongan quieren mover el archivo index.html del repositorio a otra carpeta, para ello utilizan funciones de consola de windows
Mover uno o más archivos: 

    MOVE [/Y | /-Y] [unidad:][ruta]nombrearchivo1[,...] destino 

### Deshacer cambios
Se quiere descartar el index.html del HEAD
    
    git reset HEAD index.html
    git checkout --index.html //Para deshacer todos los cambios

### Examinar todos los cambios hechos

    git log //Muestra todos los commits que estan en el repositorio.
    git log --oneline //Codigo corto de cada commit, resumen de una linea del commit

### Creando y borrando Ramas

    git branch nombrequeselequieradaralarama
    git branch //Para saber las ramas en el repositorio
    git branch -d nombre_que_se_le_dio_a_la_rama

### Fusionar Ramas

    git checkout master //Para ubicarnos en la rama donde queremos se fusione todo
    git merge rama_a_fusionar

**NOTA IMPORTANTE:** NO EDITAR LA MISMA REGION DE CODIGO EN AMBAS RAMAS AL FUSIONAR, git no tiene idea de con que modificacion se queda y da conflicto.
>**NOTA DE LA NOTA:** ESTO SE EVITA CON COMUNICACION DOS PERSONAS NO PUEDEN EDITAR LA MISMA REGION DE CODIGO SIN SABER.

### Revisar commits pasados

    git log --oneline //Para que despliegue lista de commits
    git checkout codigo_del_commit 

De ese punto se puede crear una nueva rama o un tag

### Creando Tags
Le crea un apodo al commit, asi se puede asociar mas rapidamente que fue la modificacion.
    
    git log --oneline 
    git tag tag_que_se_le_quiera_dar //Asi se le crea a todos los cambios
    git tag tag_que_se_le_quiera_dar codigo_del_commit //Asi se le crea tag a uno en concreto

Se le puede hacer un checkout al tag directamente asi se ahorra tener que buscar por codigo de commit

### Actualizando los repositorios remotos con pull

    git pull origin master //Para descargar todos los cambios nuevos realizados en el repositorio remoto
    git pull --rebase //Para proteguer los cambios que no se quieren perder al hacer pull 





