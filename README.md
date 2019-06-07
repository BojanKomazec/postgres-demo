# postgres-demo
Scratchpad project for PostgreSQL DB. Postgres DB and pgAdmin run as two services in separate containers, orchestrated by docker-compose.yml.

To run containers execute:
```
$ docker-compose up
```

To stop containers, use:
```
$ docker-compose down
```
After stopping DB container DB data will be preserved in directory which has been mapped onto a volume `/var/lib/postgresql/data`. Next time DB is started, it will pick up the state of the DB saved in this volume.
Similarly, after stopping DB UI Client container pgAdmin data (e.g. saved DB servers, usernames etc...) will be preserved in directory which has been mapped onto a volume `/var/lib/pgadmin`. Next time pgAdmin is started, it will show all DB servers saved on this volume.
```
To stop containers and remove all images and volumes used by them:
```
$ docker-compose down --rmi all --volumes --remove-orphans
$ sudo rm -rf ./database_data/
$ sudo rm -rf pgadmin
```
After this no DB and no pgAdmin data will be preserved for future container sessions.

For DB and DB UI Client services Docker creates a network named `postgres-demo-net` - as specified in .yml file.
This can be verified via:
```
$ docker network ls
NETWORK ID          NAME                             DRIVER              SCOPE
ab1cb65db6fb        postgres-demo-net                bridge              local
```

To access pgAdmin, go to local browser and type in the address bar: http://localhost:5052.
To log in, use email & pass as set in docker-compose.yml.

When adding DB server, use IP address as specified in `ipv4_address` property of `pg_db` service in yml file. In the same way use, port number, DB username and password.

Directories specified in `volumes` section in yml file don't have to be created manually - `docker-compose up` will create them.
