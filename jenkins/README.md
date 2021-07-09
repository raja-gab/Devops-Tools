# Jenkins

## Introduction
 
[Jenkins](https://www.jenkins.io/) est un outil logiciel open source d’intégration continue développé en Java.Il permet de tester et de signaler en temps réel des modifications isolées dans un code de grande ampleur. Ce logiciel permet aux développeurs de rechercher et de résoudre rapidement les anomalies, ainsi que d'automatiser les tests de leurs builds.

## Installation de Jenkins dans Kubernetes

Les étapes d'installation suivantes créeront un serveur Jenkins fonctionnel dans Kubernetes.

### Déploiement manuel

#### Déploiement de Jenkins
Vous pouvez déployer jenkins dans n'importe quel namespace, mais pour une meilleure isolation, il est recommandé de créer un namespace dédié.
```
$ kubectl create namespace jenkins
```

Utilisez le script [jenkins.yaml](https://github.com/raja-gab/Devops-Tools/blob/main/jenkins/jenkins.yaml) pour créer toutes les entités Kubernetes nécessaires. Exécutez le script avec:
```
$ kubectl apply -f jenkins.yaml
```
#### Ajouter un Kubernetes Service Account et un rôle pour Jenkins
Jenkins doit accéder à l'API Kubernetes, vous devez donc configurer correctement un Kubernetes Service Account et un rôle afin de représenter l'accès Jenkins pour l'API Kubernetes.
* Créez un service account:
  * ``` $ kubectl create serviceaccount jenkins-master -n jenkins ```
* Utilisez le script [role.yaml](https://github.com/raja-gab/Devops-Tools/blob/main/jenkins/role.yaml) pour créer le Role et le RoleBinding pour jenkins-master. Exécutez le script avec:
  * ``` $ kubectl apply -f role.yaml ```
 
