# Despliegue

con esto terminamos de instalar docker
esta herramienta es de ellos

`curl -sSL https://get.docker.com/ | sh`

Creamos usuario para que use docker sin sudo

`sudo usermod -aG docker ${USER}`

`su - ${USER}`

`id -nG`


### Crear contenedor docker con la aplicacion.

`docker pull l20j45/whatsapp-bot`

### Crear archivo env.
archivo .env

DEFAULT_MESSAGE=true
SAVE_MEDIA=true
PORT=3000
DATABASE=mysql
LANGUAGE=es
SQL_HOST=$SQL_HOST
SQL_PORT=$SQL_PORT
SQL_USER=$SQL_USER
SQL_PASS=$SQL_PASS
SQL_DATABASE=$SQL_DATABASE
KEEP_DIALOG_FLOW=false
MULTI_DEVICE=true


### Crear el archivo .env con un echo
```
echo -e "DEFAUL_MESSAGE=true
SAVE_MEDIA=true
PORT=3000
DATABASE=mysql
LANGUAGE=es
SQL_HOST=$SQL_HOST
SQL_PORT=$SQL_PORT
SQL_USER=$SQL_USER
SQL_PASS=$SQL_PASS
SQL_DATABASE=$SQL_DATABASE
KEEP_DIALOG_FLOW=false
MULTI_DEVICE=true" > .env
```

### Desplegar el contenedor con el nombre, el primer puerto cambiar se muestra template y ejemplo.
`docker run --name {nombre} --env-file {Archivo env} -d -p {puerto inicial}:3000 l20j45/whatsapp-bot`

`docker run --name tequila --env-file .envTequila -d -p 3001:3000 l20j45/whatsapp-bot`

### Iniciar sesion en el docker para iniciar la app.
`docker exec -it tequila /bin/bash`

## Dentro del contenedor

### primero debemos de actualizar los paquetes con

`npm update`

### Iniciar la app con pm2
`pm2 start app.js`

### Ver los logs del proyecto
`pm2 log`
