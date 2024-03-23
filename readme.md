 Creacion de un Data pipeLine para la creación de KPIs usando las tecnologías Fluentbit, Kafka, Python y Postgres.

Una pipeline de datos es una construcción lógica que representa un proceso dividido en fases. 

En este caso, el proceso empezará con la ingesta de un fichero de logs real de Nginx que será publicado en una cola Kafka para ser consumido por un proceso programado en Python que guardará KPIs en una base de datos Postgres. Finalmente, utilizaremos una aplicación llamada CloudBeaver para consultar los datos y así cerrar el ciclo: Origen de datos, procesado, almacenado y uso de datos.

Infraestructura
La infraestructura necesaria para el ejemplo se compone de Zookeeper + Kafka para el envío de mensajes, Postgres como sistema de base de datos y CloudBeaver que es un cliente web para conectar con bases de datos.

Procesar datos del fichero de logs con fluentbit
Fluent bit es una utilidad que nos permite leer, procesar y guardar datos de distintas fuentes como ficheros de logs, bases de datos, etc. En este caso lo estamos usando para leer datos del fichero de logs nginx.log y enviarlo a una cola de kafa.


El script en python lee cada línea del fichero de logs que recibe desde el kafka y crea tres KPIs distintos: REQUEST_X_MINUTE, REQUEST_X_HOUR, REQUEST_X_DAY.
