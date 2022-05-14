## Variables de Entorno Linux - MacOS


> Son variables globales del sistema operativo y las podemos utilizar con cualquier aplicación que se use desde el terminal (ejemplo: rails s)

> Quedan almacenadas en el equipo.

> En nuestro proyecto solo llamamos una referencia a esa variable.


> ¿Cómo se define una variable de entorno?

export  NOMBRE_VARIABLE=VALOR_VARIABLE

> Otras opciones:

Ejemplos:

1.- .env (debemos crear un archivo llamado .env, y este pasarlo a .gitignore para que al momento de subir el proyecto a un repositorio, ignore ese archivo y lo que contiene dentro).

2.- .gitignore

```shell
#Ignore bundler config.
/ .bundle

#Ignore the default SWLite database.
/db/*.sqlite3
```


> Mostrar los archivos ocultos: $ ls -a 
O listar los archivos ocultos con $ ls -la

Archivos ocultos que podemos utilizar (se cargan junto con la terminal al ser utilizada, ya que utiliza ciertas dependencias del sistema):

***Linux:***

.bashrc
.profile

***Mac:***

.bash_profile (recomendada)
.bashrc

***¿Cómo abrir un archivo oculto?***

Linux:

```shell
$ nano .profile
$ code .profile
```

1.- Crear la variable de entorno en uno de los archivos ocultos ya mencionados.

2.- Cargar las variables en la terminal.
 - Primero cerrar esa terminal, para que se carguen en una nueva sesión. Y abrir un nuevo terminal para que estén disponibles.

 - Comprobar si se encuentra disponible: 
 
 `$ printenv PASSWORD_KEY`

- Esto debiera retornar el valor de la variable
- Otra manera de hacerlo, es recargar el archivo `.profile` con `$ source .profile`

Cada vez que abramos un terminal es una sesión diferente.

Quedan guardadas en los archivos disponibles del terminal (o levantar un servidor).

> En mi código debo llamar a esa variable:

En Rails se llama con la palabra reservada ENV[], que viene del archivo environments .

***Ejemplo:*** tengo un usuario y su password:

```rb
Config.omniauth :facebook, ENV[‘USER_CLIENT’], ENV[‘PASSWORD_KEY’]
```


> Cuando se levante nuevamente el servidor, va a ir a buscar en el entorno donde se está ejecutando el servidor.


### Para que nuestras credenciales funcionen en entorno de Producción y no solo en entorno de Desarrollo, podemos setear esas credenciales y pasarelas a Heroku.


> A Heroku le podemos preguntar por una variable y obtener su valor con:

```shell
$ heroku config:get NOMBRE_DE_LA_VARIABLE
```

O sestear una variable con:

```shell
$ heroku config:set CLIENT_KEY=cbcbudssjsisnxn6447bysyx
```


***Ver las variables en Heroku***

1.- Heroku

2.- Settings

3.- Config Vars | Reveal Config Vars

4.- También se pueden sestear desde Heroku, pero es mejor hacerlo en la terminal.


********************************************

Linux:

```shell
nano .profile
source .profile
printenv CLIENT
```


Llamar a todas las variables de entorno que comiencen con un nombre en particular:
 
Primero cargar el archivo con `source .profile`
Y luego `$ printenv | grep CLIENT`

********************************************

MacOS:

```shell
$ nano .bash_profile
$ source .bash_profile
$ printenv CLIENT_KEY
```


Llamar a todas las variables de entorno que comiencen con un nombre en particular:
 
Primero cargar el archivo con `source .bash_profile`
Y luego `$ printenv | grep CLIENT`



