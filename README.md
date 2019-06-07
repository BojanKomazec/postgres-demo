# postgres-demo
Scratchpad project for PostgreSQL DB. Postgres DB and pgAdmin run as two services in separate containers, orchestrated by docker-compose.yml.

To run containers execute:
```
$ docker-compose up
```

To stop containers, use:
```
$ docker-compose down --rmi all --volumes --remove-orphans
```

For DB and DB UI Client services Docker creates a network named `postgres-demo-net` - as specified in .yml file.
This can be verified via:
```
$ docker network ls
NETWORK ID          NAME                             DRIVER              SCOPE
ab1cb65db6fb        postgres-demo-net                bridge              local
```

To access pgAdmin, go to local browser and type in the address bar: http://localhost:5052.
To log in, use email & pass as set in docker-compose.yml.

When adding DB server, use IP address as specified in ipv4_address property of pg_db service in yml file. In the same way use, port number, DB username and password.
