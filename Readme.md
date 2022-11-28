# Curso de DevOps

## Instalación Docker

- https://learn.microsoft.com/es-es/windows/wsl/install
- https://docs.docker.com/desktop/install/windows-install/

## Kata

- https://github.com/emilybache/GildedRose-Refactoring-Kata/blob/main/GildedRoseRequirements_es.md

## Repositorios

- https://github.com/jmagit/demos-devops
- https://github.com/jmagit/demos-frontend-angular
- https://github.com/jmagit/MOCKWebServer

## Comandos

- docker run --rm -it --name maven -v %cd%:/local -v maven-repository:/root/.m2 maven:3.8.6-eclipse-temurin-8 sh

## Entorno CI/CD

### Montar imagen

- Descagar Dockerfile
- docker build -t jenkins-maven-docker .

### Desplegar contenedores

- docker run -d --name mailhog -p 1025:1025 -p 8025:8025 mailhog/mailhog
- docker run -d --name sonarQube --publish 9000:9000 --network jenkins sonarqube:latest
- docker run -d --name jenkins-docker --detach --privileged --network jenkins --network-alias docker --env DOCKER_TLS_CERTDIR=/certs --volume jenkins-docker-certs:/certs/client --volume jenkins-data:/var/jenkins_home --publish 2376:2376 docker:dind --storage-driver overlay2
- docker run --name jenkins --network jenkins --env DOCKER_HOST=tcp://docker:2376 --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1 --publish 50080:8080 --publish 50000:50000 --volume %cd%/jenkins_home:/home --volume jenkins-data:/var/jenkins_home --volume jenkins-docker-certs:/certs/client:ro --env JAVA_OPTS="-Dhudson.plugins.git.GitSCM.ALLOW_LOCAL_CHECKOUT=true" jenkins-maven-docker
