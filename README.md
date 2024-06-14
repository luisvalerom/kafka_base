# Proyecto base para lanzar un cluster de Kafka

Esto es solo con intención de aprendizaje, no recomendado para producción.

Desplegamos un cluster *Kafka* en modo combinado (*broker* y *controller* ejecutándose en el mismo nodo). Para proporcionar las configuraciones al cluster combinamos variables de entorno junto con un archivo de propiedades.

Cada *broker* del cluster expone un puerto para conexiones locales (29092, 39092, 49092) respectivamente.

Para garantizar que los *brokers* sean accesibles tanto para los clientes externos (*productores* y *consumidores*) como entre si, se exponen los siguientes puertos: kafka-1:19092, kafka-2:19092, kafka-3:19092

## Punto de inicio

- Crear la red de trabajo para el cluster en docker, nos apoyamos en la red ya creada en el [proyecto Hadoop Base](https://github.com/luisvalerom/hadoop-base)
  - `docker network create hadoop_network`
- Para iniciar el cluster utilizamos docker compose:
  - `docker compose -f docker-compose-combined.yml up`

## Configuración

Podemos encontrar el archivo de propiedades utilizado para configurar el cluster *Kafka* en `fixtures/combined/file-input/server.properties`

