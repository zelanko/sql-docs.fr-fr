---
title: Superviser et dépanner
titleSuffix: SQL Server big data clusters
description: Cet article fournit des commandes utiles pour surveiller et dépanner un cluster de données volumineuses de SQL Server 2019 (version préliminaire).
author: rothja
ms.author: jroth
manager: jroth
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 232c39e6a98f7f55fa3a653735f39c9607fbcbf4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800741"
---
# <a name="monitoring-and-troubleshoot-sql-server-big-data-clusters"></a>Surveillance et de résoudre les problèmes de clusters de données volumineuses de SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit plusieurs commandes Kubernetes utiles que vous pouvez utiliser pour surveiller et dépanner un cluster de données volumineuses de SQL Server 2019 (version préliminaire). Il montre comment afficher des informations détaillées d’un pod ou d’autres artefacts Kubernetes qui sont trouvent dans le cluster de données volumineux. Cet article couvre également les tâches courantes, telles que la copie des fichiers vers ou à partir d’un conteneur qui exécute un des services de cluster de données volumineuses de SQL Server.

> [!TIP]
> Exécutez la commande suivante **kubectl** commandes sur l’ordinateur de client Linux (bash) ou un Windows (cmd ou PS). Ils nécessitent d’authentification précédente dans le cluster et un contexte de cluster pour exécuter. Par exemple, pour un cluster ACS créé précédemment, vous pouvez exécuter `az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>` pour télécharger le fichier de configuration du cluster Kubernetes et de définir le contexte de cluster.

## <a name="get-status-of-pods"></a>Obtenir l’état de pods

Vous pouvez utiliser la `kubectl get pods` commande pour obtenir l’état de pods dans le cluster pour tous les espaces de noms ou de l’espace de noms de cluster de données volumineuses. Les sections suivantes montrent des exemples des deux.

### <a name="show-status-of-all-pods-in-the-kubernetes-cluster"></a>Afficher l’état de tous les pods dans le cluster Kubernetes

Exécutez la commande suivante pour obtenir tous les pods et leurs États, y compris les pods qui font partie de l’espace de noms que SQL Server pods du cluster big data sont créés dans :

```bash
kubectl get pods --all-namespaces
```

### <a name="show-status-of-all-pods-in-the-sql-server-big-data-cluster"></a>Afficher l’état de tous les pods dans le cluster de données volumineux de SQL Server

Utilisez le `-n` paramètre pour spécifier un espace de noms spécifique. Notez que les données volumineuses de SQL Server cluster pods sont créés dans un nouvel espace de noms créé au moment du démarrage cluster basé sur le nom de cluster spécifié dans le fichier de configuration de déploiement. Le nom par défaut, `mssql-cluster`, est utilisé ici.

```bash
kubectl get pods -n mssql-cluster
```

Vous devez voir une sortie similaire à la liste suivante pour un cluster de données volumineux en cours d’exécution :

```output
PS C:\> kubectl get pods -n mssql-cluster
NAME              READY   STATUS    RESTARTS   AGE
appproxy-f2qqt    2/2     Running   0          110m
compute-0-0       3/3     Running   0          110m
control-zlncl     4/4     Running   0          118m
data-0-0          3/3     Running   0          110m
data-0-1          3/3     Running   0          110m
gateway-0         2/2     Running   0          109m
logsdb-0          1/1     Running   0          112m
logsui-jtdnv      1/1     Running   0          112m
master-0          7/7     Running   0          110m
metricsdb-0       1/1     Running   0          112m
metricsdc-shv2f   1/1     Running   0          112m
metricsui-9bcj7   1/1     Running   0          112m
mgmtproxy-x6gcs   2/2     Running   0          112m
nmnode-0-0        1/1     Running   0          110m
storage-0-0       7/7     Running   0          110m
storage-0-1       7/7     Running   0          110m
```

> [!NOTE]
> Au cours du déploiement, pods avec un **état** de **ContainerCreating** sont toujours démarrent. Si le déploiement se bloque pour une raison quelconque, cela peut vous donner une idée où il est possible. Examinez également le **prêt** colonne. Cela indique le nombre de conteneurs ont démarré dans le pod. Notez que les déploiements peuvent prendre 30 minutes ou plus, selon votre configuration et votre réseau. Une grande partie de ce temps est consacré à télécharger les images de conteneur pour les différents composants.

## <a name="get-pod-details"></a>Obtenir les détails de pod

Exécutez la commande suivante pour obtenir une description détaillée d’un pod spécifique dans la sortie du format JSON. Il inclut des détails, tels que le nœud actuel Kubernetes qui le pod est placé sur, les conteneurs en cours d’exécution dans le pod et l’image utilisée pour démarrer les conteneurs. Il montre d’autres détails, tels que des étiquettes, état et persistante des revendications de volumes qui sont associées le pod.

```bash
kubectl describe pod  <pod_name> -n <namespace_name>
```

L’exemple suivant montre les détails de la `master-0` pod dans un cluster de données volumineuses nommé `mssql-cluster`:

```bash
kubectl describe pod  master-0 -n mssql-cluster
```

Si des erreurs se sont produites, vous pouvez parfois voir l’erreur dans les événements récents pour le pod.

## <a name="get-pod-logs"></a>Obtenir les journaux du pod

Vous pouvez récupérer les journaux de conteneurs en cours d’exécution dans un bloc. La commande suivante récupère les journaux de tous les conteneurs en cours d’exécution dans le bloc nommé `master-0` , puis les génère dans un fichier nommé `master-0-pod-logs.txt`:

```bash
kubectl logs master-0 --all-containers=true -n mssql-cluser > master-0-pod-logs.txt
```

## <a id="services"></a> Obtenir l’état des services

Exécutez la commande suivante pour obtenir des détails pour les services de cluster de données volumineuses. Ces détails incluent leur type et les adresses IP associées avec les ports et services respectifs. Notez que les services de cluster de données volumineuses de SQL Server sont créés dans un nouvel espace de noms créé au moment du démarrage cluster basé sur le nom de cluster spécifié dans le fichier de configuration de déploiement.

```bash
kubectl get svc -n <namespace_name>
```

L’exemple suivant montre l’état des services dans un cluster de données volumineuses nommé `mssql-cluster`:

```bash
kubectl get svc -n mssql-cluster
```

Les services suivants prennent en charge les connexions externes au cluster big data :

| Service | Description |
|---|---|
| **master-svc-external** | Fournit l’accès à l’instance principale.<br/>(**EXTERNAL-IP, 31433** et **SA** utilisateur) |
| **controller-svc-external** | Prend en charge des outils et les clients qui gèrent le cluster. |
| **mgmtproxy-svc-external** | Fournit l’accès à la [portail d’Administration de Cluster](cluster-admin-portal.md).<br/>(https://**EXTERNAL-IP**: 30777/portail) |
| **gateway-svc-external** | Fournit l’accès à la passerelle HDFS/Spark.<br/>(**EXTERNAL-IP** et **racine** utilisateur) |
| **appproxy-svc-external** | Prend en charge les scénarios de déploiement d’application. |

> [!TIP]
> Il s’agit d’une façon d’afficher les services avec **kubectl**, mais il est également possible d’utiliser `mssqlctl cluster endpoint list` commande pour afficher ces points de terminaison. Pour plus d’informations, consultez [obtenir les points de terminaison de cluster big data](deployment-guidance.md#endpoints).

## <a name="get-service-details"></a>Obtenir les détails du service

Exécutez cette commande pour obtenir une description détaillée d’un service dans la sortie du format JSON. Il inclura des détails tels que des étiquettes, sélecteur, adresse IP, adresse IP externe (si le service est de type de l’équilibreur de charge), port, etc.

```bash
kubectl describe service <service_name> -n <namespace_name>
```

L’exemple suivant récupère les détails pour le **master-svc-external** service :

```bash
kubectl describe service master-svc-external -n mssql-cluster
```

## <a name="run-commands-in-a-container"></a>Exécutez les commandes dans un conteneur

Si les outils existants ou l’infrastructure ne vous autorise pas à effectuer une tâche particulière sans être réellement dans le contexte du conteneur, vous pouvez vous connecter au conteneur en utilisant `kubectl exec` commande. Par exemple, vous devrez peut-être vérifier si un fichier spécifique existe, ou vous devrez peut-être redémarrer les services dans le conteneur. 

Pour utiliser le `kubectl exec` de commande, utilisez la syntaxe suivante :

```bash
kubectl exec -it <pod_name>  -c <container_name> -n <namespace_name> -- /bin/bash <command name> 
```

Les deux sections suivantes fournissent deux exemples d’exécution d’une commande dans un conteneur spécifique.

### <a id="restartsql"></a> Connectez-vous à un conteneur spécifique et redémarrez le processus SQL Server

L’exemple suivant montre comment redémarrer le processus SQL Server dans le `mssql-server` conteneur dans le `master-0` pod :

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl restart mssql
```

### <a id="restartservices"></a> Ouvrez une session un conteneur spécifique et redémarrer les services dans un conteneur
 
L’exemple suivant montre comment redémarrer tous les services gérés par **supervisord**: 

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl -c /opt/supervisor/supervisord.conf reload
```

## <a id="copy"></a> Copier des fichiers

Si vous devez copier les fichiers à partir du conteneur sur votre ordinateur local, utilisez `kubectl cp` commande avec la syntaxe suivante :

```bash
kubectl cp <pod_name>:<source_file_path> -c <container_name> -n <namespace_name> <target_local_file_path>
```

De même, vous pouvez utiliser `kubectl cp` pour copier des fichiers à partir de l’ordinateur local dans un conteneur spécifique.

```bash
kubectl cp <source_local_file_path> <pod_name>:<target_container_path> -c <container_name>  -n <namespace_name>
```

### <a id="copyfrom"></a> Copier des fichiers à partir d’un conteneur

L’exemple suivant copie les fichiers journaux SQL Server à partir du conteneur pour le `~/temp/sqlserverlogs` chemin d’accès sur l’ordinateur local (dans cet exemple, l’ordinateur local est un client Linux) :

```bash
kubectl cp master-0:/var/opt/mssql/log -c mssql-server -n mssql-cluster ~/tmp/sqlserverlogs
```

### <a id="copyinto"></a> Copier des fichiers dans le conteneur

L’exemple ci-après copie le **AdventureWorks2016CTP3.bak** fichier à partir de l’ordinateur local vers le conteneur d’instance principale de SQL Server (`mssql-server`) dans le `master-0` pod. Le fichier est copié dans le `/tmp` répertoire dans le conteneur. 

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak master-0:/tmp -c mssql-server -n mssql-cluster
```

## <a id="forcedelete"></a> Forcer la suppression un pod
 
Il n’est pas recommandé pour effectuer une suppression forcée un pod. Mais la disponibilité, la résilience et persistance des données de test, vous pouvez supprimer un pod pour simuler une défaillance de pod avec la `kubectl delete pods` commande.

```bash
kubectl delete pods <pod_name> -n <namespace_name> --grace-period=0 --force
```

L’exemple suivant supprime le pod de pool de stockage, `storage-0-0`:

```bash
kubectl delete pods storage-0-0 -n mssql-cluster --grace-period=0 --force
```

## <a id="getip"></a> Obtenir l’adresse IP du bloc
 
Pour résoudre ce problème, vous devrez peut-être obtenir l’adresse IP du nœud sur qu'un pod est en cours d’exécution. Pour obtenir l’adresse IP, utilisez le `kubectl get pods` commande avec la syntaxe suivante :

```bash
kubectl get pods <pod_name> -o yaml -n <namespace_name> | grep hostIP
```

L’exemple suivant obtient l’adresse IP du nœud qui le `master-0` pod est en cours d’exécution :

```bash
kubectl get pods master-0 -o yaml -n mssql-cluster | grep hostIP
```

## <a name="cluster-administration-portal"></a>Portail d’administration du cluster

Utilisez le [portail d’administration de cluster](cluster-admin-portal.md) pour surveiller l’état de votre cluster big data. Par exemple, au cours des déploiements, vous pouvez utiliser la **déploiement** onglet. Vous devez attendre la **mgmtproxy-svc-external** démarrage avant d’accéder à ce portail, donc il n’est pas disponible au début d’un déploiement du service.

## <a name="kubernetes-dashboard"></a>Tableau de bord Kubernetes

Vous pouvez lancer le tableau de bord Kubernetes pour des informations supplémentaires sur le cluster. Les sections suivantes expliquent comment lancer le tableau de bord pour Kubernetes sur AKS et initialisé à l’aide de kubeadm de Kubernetes.
 
### <a name="start-dashboard-when-cluster-is-running-in-aks"></a>Démarrer le tableau de bord lorsque le cluster est en cours d’exécution dans ACS

Pour lancer le tableau de bord de Kubernetes :

```bash
az aks browse --resource-group <azure_resource_group> --name <aks_cluster_name>
```

> [!Note]
> Si vous obtenez l’erreur suivante : *Impossible d’écouter sur le port 8001 : Échec de tous les écouteurs créer et les erreurs suivantes : Impossible de créer l’écouteur : Erreur écouter tcp4 127.0.0.1:8001 : > lier : Qu’une seule utilisation de chaque adresse de socket (adresse réseau/protocole/port) est normalement autorisée. Impossible de créer l’écouteur : Erreur écouter tcp6 : adresse [[ :: 1]] : 8001 : manquant de port dans > résolution des problèmes : Impossible d’écouter sur un des ports demandées : [{8001 9090}]* , assurez-vous que vous n’avez pas démarré le tableau de bord déjà d’une autre fenêtre.

Lorsque vous lancez le tableau de bord sur votre navigateur, vous pouvez obtenir des avertissements d’autorisation en raison de RBAC étant activé par défaut dans les clusters AKS, et le compte de service utilisé par le tableau de bord n’a pas d’autorisations suffisantes pour accéder à toutes les ressources (par exemple,  *PODS est interdite : Utilisateur « système : serviceaccount:kube-système : kubernetes-tableau de bord « Impossible de répertorier le nombre de pods dans l’espace de noms « default »* ). Exécutez la commande suivante pour accorder les autorisations nécessaires pour `kubernetes-dashboard`, puis redémarrez le tableau de bord :

```bash
kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

### <a name="start-dashboard-when-kubernetes-cluster-is-bootstrapped--using-kubeadm"></a>Démarrer le tableau de bord lorsque le cluster Kubernetes est initialisé à l’aide de kubeadm

Pour plus d’instructions déployer et configurer le tableau de bord dans votre cluster Kubernetes, consultez [la documentation de Kubernetes](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/). Pour lancer le tableau de bord Kubernetes, exécutez la commande suivante :

```bash
kubectl proxy
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses, consultez [que sont les clusters de données volumineuses de SQL Server](big-data-cluster-overview.md).
