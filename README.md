# Conteneurisation M2 TP08

## Les variables d'env dans les Dockerfile/Compose

Dans ce repository on peut trouver plusieurs choses : 
- 1 docker-compose [ici](docker-compose.yaml)
* 1 Dockerfile [ici](Dockerfile)
* 1 fichier stockant des variables d'environnement [ici](.env)

* generate a user for traefik [basicAuth](https://doc.traefik.io/traefik/middlewares/basicauth/) with docker
```bash
docker run -it --rm --name apache2-utils debian:10.4 /bin/bash -c "apt-get update -y && apt-get install apache2-utils && echo \$(htpasswd -nbB your_username 'your_user_password')"
```
* generate Portainer [admin user](https://documentation.portainer.io/v2.0/deploy/ceinstalldocker/) to avoid setting it manually
```bash
docker run -it --rm --name apache2-utils debian:10.4 /bin/bash -c "apt-get update -y && apt-get install apache2-utils && echo \$(htpasswd -nbB admin 'your_admin_password')"
sed -i "s/command: \"--admin-password='.*'\"/command: \"--admin-password='your_hashed_admin_password'\"/g" docker-compose.yaml
```

* run the project.
```bash
docker-compose up -d
curl -v docker.
```

* get Traefik rawdata
http://localhost:8080/api/rawdata

* proof-01 - Defaults values
![proof](commands.png)

* proof-02 - Overriding `MYSQL_ROOT_PASSWORD` with `--build-arg`
![proof](commands2.png)

* Traefik glossary
* [middleware](https://doc.traefik.io/traefik/middlewares/overview/)
```bash
There are several available middleware in Traefik, some can modify the request, the headers, some are in charge of redirections, some add authentication, and so on.
```
