# TallerFinalDockerMitocode
Taller final curso docker mitocode Tienda

Se crearon 3 servicios:

- 1.postgres11: es una bd de datos postgres v11 llamada tienda que tiene 3 tablas producto, cliente y compras.
- 2.wsproductos: Es un servicio spring boot que retorna la información de productos y compras que ha hecho un cliente.
- 3.wscliente: Es un servicio spring boot que retorna la información de clientes y se conecta a wsproductos para cosumir el servicio de compras que ha realizado un cliente.

## Comandos
- docker stack deploy -c docker-compose.yml tallerfinal
- docker stack ps tallerfinal
- docker service ls
- docker service ps tallerfinal_wsproductos
- docker service logs -f tallerfinal_wsproductos

## Comentarios
Despues de que se levantes los servicios se puede acceder a las siguientes url que tienen la documentación de los servicio. La ip del host cambia según el manager de docker swarm.

- wsproductos --> http://192.168.99.103:8081/swagger-ui.html.
- wscliente   --> http://192.168.99.103:8082/swagger-ui.html.

### wsproductos
http://host:8081/swagger-ui.html

Este servicio esta expuexto por el puerto 8081 tiene dos metodos:

- GET http://host:8081/productos/ --> retorna todos los productos.
- GET http://host:8081/productos/idcliente --> retorna los productos comprados por un cliente hay tres clientes (1, 2, 3).

### wscliente
http://host:8082/swagger-ui.html

Este servicio esta expuexto por el puerto 8082 tiene dos metodos:

- GET http://host:8082/clientes/ --> retorna todos los clientes
- GET http://host:8082/clientes/1 --> Se conecta a wsproductos mediante la libreria JAX-RS retorna los productos comprados por un cliente hay tres clientes (1, 2, 3)
