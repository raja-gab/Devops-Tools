# Gogs

## Introduction

[Gogs](https://gogs.io/) est une solution Git auto-hébergée garantie sans prise de tête et écrite en Go.

## Installation de gogs dans Kubernetes

Les étapes d'installation suivantes créeront un serveur Git fonctionnel dans Kubernetes.

### Prérequis

* Base de données :
  * [MySQL](https://hub.docker.com/_/mysql) : Version >= 5.7
* Git (bash) :
  * Version >= 1.7.1 pour le serveur et le client

### Déploiement manuel

Vous pouvez déployer gogs dans n'importe quel namespace, mais pour une meilleure isolation, il est recommandé de créer un namespace dédié.
```
$ kubectl create namespace gogs
```

#### Déploiement de la base de données

Utilisez le script [mysql.yaml](http://10.112.42.85/rajagabsi/Gogs/src/master/mysql.yaml) pour créer toutes les entités Kubernetes nécessaires.
Exécutez le script avec:
```
$ kubectl apply -f mysql.yaml
```
En fonction de vos besoins, vous souhaiterez peut-être modifier:

  * taille du volume persistant (actuellement 9 Go)
  * image Docker (actuellement mysql:5.7)
  * nombre de répliques égale 1


#### Déploiement de gogs

Utilisez le script [gogs.yaml](http://10.112.42.85/rajagabsi/Gogs/src/master/gogs.yaml) pour créer toutes les entités Kubernetes nécessaires.
Exécutez le script avec:
```
$ kubectl apply -f gogs.yaml
```
En fonction de vos besoins, vous souhaiterez peut-être modifier:

  * taille du volume persistant (actuellement 9 Go)
  * image Docker (actuellement gogs/gogs:0.11.91)
  * nombre de répliques égale 1



