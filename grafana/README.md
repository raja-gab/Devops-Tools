# Grafana

## Introduction

[Grafana](https://grafana.com/) est un outil de tableau de bord léger et open-source. Il peut être intégré à de nombreuses sources de données comme Prometheus, AWS cloud watch, Stackdriver, etc.


### Déploiement manuel

La configuration de la source de données suivante est pour Prometheus. Si vous avez plus de sources de données, vous pouvez ajouter d'autres sources. Utilisez le script [config-map.yaml](https://github.com/raja-gab/Devops-Tools/blob/main/grafana/config-map.yaml) pour créer la configuration suivante:
```
$ kubectl apply -f config-map.yaml
```

Utilisez le script [grafana.yaml](https://github.com/raja-gab/Devops-Tools/blob/main/grafana/grafana.yaml) pour créer toutes les entités Kubernetes nécessaires.
Exécutez le script avec:
```
$ kubectl apply -f grafana.yaml
```


 
