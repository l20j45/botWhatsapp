# Despliegue

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


### Desplegar el contenedor con el nombre, el primer puerto cambiar se muestra template y ejemplo.
`docker run --name {nombre} --env-file {Archivo env} -d -p {puerto inicial}:3000 l20j45/whatsapp-bot`

`docker run --name tequila --env-file .envTequila -d -p 3001:3000 l20j45/whatsapp-bot`

### Iniciar sesion en el docker para iniciar la app.
`docker exec -it tequila /bin/bash`

### Crear el archivo .env con un echo
`echo -e "DEFAUL_MESSAGE=true \nSAVE_MEDIA=true\nPORT=3000\nDATABASE=mysql\nLANGUAGE=es\nSQL_HOST=$SQL_HOST\nSQL_PORT=$SQL_PORT\nSQL_USER=$SQL_USER\nSQL_PASS=$SQL_PASS\nSQL_DATABASE=$SQL_DATABASE\nKEEP_DIALOG_FLOW=false\nMULTI_DEVICE=true" > .env`

### Iniciar la app con pm2
`pm2 start app.js`

### Ver los logs del proyecto
`pm2 log`
