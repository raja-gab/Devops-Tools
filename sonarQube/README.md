# SonarQube

## Introduction

[SonarQube](https://www.sonarqube.org/) est un outil de révision de code automatique permettant de détecter les bugs, les vulnérabilités et les anomalies dans votre code.

## Installation de SonarQube dans Kubernetes

Les étapes d'installation suivantes créeront SonarQube dans Kubernetes.

### Prérequis

* Base de données :
  * [PostgreSQL](https://hub.docker.com/_/postgres) : Version >= postgres:latest


### Déploiement manuel

Vous pouvez déployer SonarQube dans n'importe quel namespace, mais pour une meilleure isolation, il est recommandé de créer un namespace dédié.
```
$ kubectl create namespace sonarqube
```

#### Déploiement de la base de données

Utilisez le script [postgres.yaml](https://github.com/raja-gab/Devops-Tools/blob/main/sonarQube/postgres.yaml) pour créer toutes les entités Kubernetes nécessaires.
Exécutez le script avec:
```
$ kubectl apply -f postgres.yaml
```
En fonction de vos besoins, vous souhaiterez peut-être modifier:

  * taille du volume persistant (actuellement 5 Go)
  * image Docker (actuellement postgres:latest)
  * nombre de répliques égale 1


#### Déploiement de SonarQube

Utilisez le script [sonarqube.yaml](https://github.com/raja-gab/Devops-Tools/blob/main/sonarQube/sonarqube.yaml) pour créer toutes les entités Kubernetes nécessaires.
Exécutez le script avec:
```
$ kubectl apply -f sonarqube.yaml
```
En fonction de vos besoins, vous souhaiterez peut-être modifier:

  * taille du volume persistant (actuellement 10 Go)
  * image Docker (actuellement sonarqube)
  * nombre de répliques égale 1

 
