## Desafío: clase 32: Loggers, Gzip y análisis de performance
#### Como ejecutar el programa en su computadora:

Ejecutar `npm install` para instalar las dependecias.

En archivo `.env` se define la conexion a MongoDB Atlas y se almacena como ejemplo
en la base de datos llamado `serverprocess` la info del sistema

Ejecutar `npm start` para iniciar el server.

#### Consignas del desafío y las respuestas

* Sobre la ruta `/info` del proyecto que venimos viendo se comparó la carga de la página con compresión gzip y sin ella

-- Sin compresión:
[![no-compress.jpg](https://i.postimg.cc/FzVxmD6C/no-compress.jpg)](https://postimg.cc/gLrhHqm3)

-- Con compresión:
[![yes-compress.jpg](https://i.postimg.cc/ydXRSWTk/yes-compress.jpg)](https://postimg.cc/XGqqRjmb)


* A continuación se utilizó la librería log4js

-- Se ingresó a las rutas existentes `/` , `/info` , `/api/randoms?cant=2000`
-- Se ingresó a path inexsistentes para mostrar los logs (se agregó página 404)

[![logs.jpg](https://i.postimg.cc/4x3NBxRH/logs.jpg)](https://postimg.cc/SJwhKqsm)


* Testeo de carga del servidor con Artillery

-- Para perfilamiento del servidor se realizó el siguiente comando:
```
node --prof app.js
```
-- Luego en otra terminal se realizó se generó un testeo de carga del servidor
```
artillery quick --count 50 -n 20 http://localhost:8080/info > result_fork.txt
```

