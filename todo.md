TODO

Si el servicio REST hiciese uso de clases con lógica de negocio que a su vez hiciese uso de una capa de persistencia, habría que hacer tests de integración y test unitarios.
Para ello emplearía Junit y Mockito. El primero permite hacer aserciones entre un resultado esperado y el resultado obtenido. El segundo permite crear versiones 'mock' (creadas al efecto para devolver un cierto resultado para cierto conjunto de parámetros de entrada) para simular el comportamiento del resto de componentes implicados en la prueba. Por ejemplo, para probar un controller habría que utilizar una versión mock de la lógica de negocio que invoca para procesar una petición a ese REST.

También podría incluir i18n para que en función de la cabecera locale el saludo estuviese traducido al idioma que se espera recibir. Para esto hay varias soluciones, pero una sencilla es configurar el basename en application.properties y tener archivos de traducciones en la carpeta resources que sigan el convenio de nombre: basename_es.properties, basename_fr.properties... etc

Si fuese un poquito más sensible lo que devuelve el servicio, habilitaría seguridad con spring-security. Comenzaría con algo sencillo con auth básica de nombre y clave, pero también sabría hacerlo con Oauth y tokens.

Luego, si el proyecto tuviese que hacer uso de persistencia, en función del caso habría que buscar una solución con el mejor rendimiento, pues el uso de ORMs a veces no es lo más aconsejado cuando se busca la velocidad. Hay soluciones como el uso de tablas temporales en DB2 que pueden hacer más rápido un proceso, y se tiene mejor control mediante JDBC. Para cosas sencillas están bien los ORM como Hibernate.

Estas cosas son las que se me ocurren, pero seguro que si sigo pensando salen más :)