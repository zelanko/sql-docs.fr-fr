---
title: Surveiller et résoudre des problèmes
titleSuffix: SQL Server big data clusters
description: Cet article fournit des commandes utiles pour la surveillance et la résolution des problèmes d’un cluster SQL Server 2019 Big Data (version préliminaire).
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 272249b7bd6c22895b7d10e7fbce4a20cb647a49
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419477"
---
# <a name="monitoring-and-troubleshoot-sql-server-big-data-clusters"></a>Surveillance et dépannage des clusters de SQL Server Big Data

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit plusieurs commandes Kubernetes utiles que vous pouvez utiliser pour analyser et dépanner un cluster SQL Server 2019 Big Data (version préliminaire). Il montre comment afficher des détails détaillés d’un pod ou d’autres artefacts Kubernetes situés dans le cluster Big Data. Cet article traite également des tâches courantes, telles que la copie de fichiers vers ou à partir d’un conteneur exécutant l’un des SQL Server Big Data les services de cluster.

> [!TIP]
> Exécutez les commandes **kubectl** suivantes sur un ordinateur client Windows (cmd ou PS) ou Linux (bash). Elles nécessitent une authentification antérieure dans le cluster et un contexte de cluster pour s’exécuter. Par exemple, pour un cluster AKS créé précédemment, vous pouvez `az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>` exécuter pour télécharger le fichier de configuration de cluster Kubernetes et définir le contexte de cluster.

## <a name="get-status-of-pods"></a>Obtient l’état des Pod

Vous pouvez utiliser la `kubectl get pods` commande pour obtenir l’état des Pod dans le cluster pour tous les espaces de noms ou pour l’espace de noms du cluster Big Data. Les sections suivantes présentent des exemples des deux.

### <a name="show-status-of-all-pods-in-the-kubernetes-cluster"></a>Afficher l’état de toutes les gousses dans le cluster Kubernetes

Exécutez la commande suivante pour récupérer tous les POD et leurs États, y compris les gousses qui font partie de l’espace de noms SQL Server Big Data les modules de cluster sont créés dans:

```bash
kubectl get pods --all-namespaces
```

### <a name="show-status-of-all-pods-in-the-sql-server-big-data-cluster"></a>Afficher l’état de toutes les Pod dans le SQL Server Big Data cluster

Utilisez le `-n` paramètre pour spécifier un espace de noms spécifique. Notez que SQL Server Big Data des modules de cluster sont créés dans un nouvel espace de noms créé au moment de l’amorçage du cluster en fonction du nom de cluster spécifié dans le fichier de configuration de déploiement. Le nom par défaut `mssql-cluster`,, est utilisé ici.

```bash
kubectl get pods -n mssql-cluster
```

La sortie doit ressembler à la liste suivante pour un cluster Big Data en cours d’exécution:

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
> Pendant le déploiement, les Pod dont l' **État** est **ContainerCreating** sont toujours en cours d’installation. Si le déploiement se bloque pour une raison quelconque, cela peut vous faire une idée de l’origine du problème. Examinez également la colonne **prêt** . Cela vous indique le nombre de conteneurs démarrés dans le POD. Notez que le déploiement peut prendre 30 minutes ou plus, selon votre configuration et votre réseau. La majeure partie de ce temps est consacrée au téléchargement des images conteneur pour différents composants.

## <a name="get-pod-details"></a>Afficher les détails du Pod

Exécutez la commande suivante pour obtenir une description détaillée d’un pod spécifique au format JSON. Il comprend des détails, tels que le nœud Kubernetes actuel sur lequel le Pod est placé, les conteneurs exécutés dans le POD et l’image utilisée pour démarrer les conteneurs. Il affiche également d’autres détails, tels que les étiquettes, l’État et les revendications de volumes persistants qui sont associés au pod.

```bash
kubectl describe pod  <pod_name> -n <namespace_name>
```

L’exemple suivant montre les détails de la `master-0` Pod dans un cluster Big Data nommé `mssql-cluster`:

```bash
kubectl describe pod  master-0 -n mssql-cluster
```

Si des erreurs se sont produites, vous pouvez parfois voir l’erreur dans les événements récents pour le POD.

## <a name="get-pod-logs"></a>Récupérer les journaux Pod

Vous pouvez récupérer les journaux des conteneurs qui s’exécutent dans une pod. La commande suivante récupère les journaux de tous les conteneurs s’exécutant dans le pod `master-0` nommé et les affiche dans un nom `master-0-pod-logs.txt`de fichier:

```bash
kubectl logs master-0 --all-containers=true -n mssql-cluser > master-0-pod-logs.txt
```

## <a id="services"></a>Obtient l’état des services

Exécutez la commande suivante pour obtenir des détails sur les services de cluster Big Data. Ces détails incluent leur type et les adresses IP associées aux services et ports respectifs. Notez que SQL Server Big Data les services de cluster sont créés dans un nouvel espace de noms créé au moment de l’amorçage du cluster en fonction du nom de cluster spécifié dans le fichier de configuration de déploiement.

```bash
kubectl get svc -n <namespace_name>
```

L’exemple suivant montre l’état des services dans un cluster Big Data nommé `mssql-cluster`:

```bash
kubectl get svc -n mssql-cluster
```

Les services suivants prennent en charge les connexions externes au cluster Big Data:

| de diffusion en continu | Description |
|---|---|
| **master-svc-external** | Fournit l’accès à l’instance principale.<br/>(**External-IP, 31433** et l’utilisateur **sa** ) |
| **controller-svc-external** | Prend en charge les outils et les clients qui gèrent le cluster. |
| **gateway-svc-external** | Permet d’accéder à la passerelle HDFS/Spark.<br/>(**External-IP** et l’utilisateur **racine** ) |
| **appproxy-svc-external** | Prendre en charge les scénarios de déploiement d’applications. |

> [!TIP]
> Il s’agit d’un moyen d’afficher les services avec **kubectl**, mais il est également possible `azdata bdc endpoint list` d’utiliser la commande pour afficher ces points de terminaison. Pour plus d’informations, consultez [obtenir Big Data points de terminaison de cluster](deployment-guidance.md#endpoints).

## <a name="get-service-details"></a>Afficher les détails du service

Exécutez cette commande pour obtenir une description détaillée d’un service au format JSON. Il inclut des détails tels que les étiquettes, le sélecteur, l’adresse IP, l’adresse IP externe (si le service est de type LoadBalancer), le port, etc.

```bash
kubectl describe service <service_name> -n <namespace_name>
```

L’exemple suivant récupère les détails du service **maître-SVC-External** :

```bash
kubectl describe service master-svc-external -n mssql-cluster
```

## <a name="run-commands-in-a-container"></a>Exécuter des commandes dans un conteneur

Si les outils existants ou l’infrastructure ne vous permettent pas d’effectuer une certaine tâche sans être réellement dans le contexte du conteneur, vous pouvez vous connecter au conteneur à l' `kubectl exec` aide de la commande. Par exemple, vous devrez peut-être vérifier s’il existe un fichier spécifique, ou vous devrez peut-être redémarrer les services dans le conteneur. 

Pour utiliser la `kubectl exec` commande, utilisez la syntaxe suivante:

```bash
kubectl exec -it <pod_name>  -c <container_name> -n <namespace_name> -- /bin/bash <command name> 
```

Les deux sections suivantes fournissent deux exemples d’exécution d’une commande dans un conteneur spécifique.

### <a id="restartsql"></a>Connectez-vous à un conteneur spécifique et redémarrez SQL Server processus

L’exemple suivant montre comment redémarrer le processus de SQL Server dans le `mssql-server` conteneur dans le `master-0` Pod:

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl restart mssql
```

### <a id="restartservices"></a>Connexion à un conteneur spécifique et redémarrage des services dans un conteneur
 
L’exemple suivant montre comment redémarrer tous les services gérés par le **superviseur**: 

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl -c /opt/supervisor/supervisord.conf reload
```

## <a id="copy"></a>Copier les fichiers

Si vous devez copier des fichiers à partir du conteneur sur votre ordinateur local, `kubectl cp` utilisez la commande avec la syntaxe suivante:

```bash
kubectl cp <pod_name>:<source_file_path> -c <container_name> -n <namespace_name> <target_local_file_path>
```

De même, vous pouvez utiliser `kubectl cp` pour copier des fichiers à partir de l’ordinateur local dans un conteneur spécifique.

```bash
kubectl cp <source_local_file_path> <pod_name>:<target_container_path> -c <container_name>  -n <namespace_name>
```

### <a id="copyfrom"></a>Copier des fichiers à partir d’un conteneur

L’exemple suivant copie les fichiers journaux SQL Server du conteneur vers le `~/temp/sqlserverlogs` chemin d’accès sur l’ordinateur local (dans cet exemple, l’ordinateur local est un client Linux):

```bash
kubectl cp master-0:/var/opt/mssql/log -c mssql-server -n mssql-cluster ~/tmp/sqlserverlogs
```

### <a id="copyinto"></a>Copier les fichiers dans le conteneur

L’exemple suivant copie le fichier **AdventureWorks2016CTP3. bak** de l’ordinateur local vers le conteneur d’instance maître SQL Server`mssql-server`() dans `master-0` le POD. Le fichier est copié dans le `/tmp` répertoire dans le conteneur. 

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak master-0:/tmp -c mssql-server -n mssql-cluster
```

## <a id="forcedelete"></a>Forcer la suppression d’un pod
 
Il n’est pas recommandé de forcer la suppression d’un pod. Toutefois, pour tester la disponibilité, la résilience ou la persistance des données, vous pouvez supprimer un pod pour simuler `kubectl delete pods` un échec Pod avec la commande.

```bash
kubectl delete pods <pod_name> -n <namespace_name> --grace-period=0 --force
```

L’exemple suivant supprime le pod de pool de `storage-0-0`stockage:

```bash
kubectl delete pods storage-0-0 -n mssql-cluster --grace-period=0 --force
```

## <a id="getip"></a>Accéder à l’adresse IP Pod
 
À des fins de dépannage, vous devrez peut-être obtenir l’adresse IP du nœud sur lequel un Pod est en cours d’exécution. Pour récupérer l’adresse IP, utilisez la `kubectl get pods` commande avec la syntaxe suivante:

```bash
kubectl get pods <pod_name> -o yaml -n <namespace_name> | grep hostIP
```

L’exemple suivant obtient l’adresse IP du nœud sur lequel le `master-0` Pod s’exécute:

```bash
kubectl get pods master-0 -o yaml -n mssql-cluster | grep hostIP
```

## <a name="kubernetes-dashboard"></a>Tableau de bord Kubernetes

Vous pouvez lancer le tableau de bord Kubernetes pour obtenir des informations supplémentaires sur le cluster. Les sections suivantes expliquent comment lancer le tableau de bord pour Kubernetes sur AKS et pour Kubernetes amorcé à l’aide de kubeadm.
 
### <a name="start-dashboard-when-cluster-is-running-in-aks"></a>Démarrer le tableau de bord lorsque le cluster est en cours d’exécution dans AKS

Pour lancer l’exécution du tableau de bord Kubernetes:

```bash
az aks browse --resource-group <azure_resource_group> --name <aks_cluster_name>
```

> [!Note]
> Si vous recevez l’erreur suivante: *Impossible d’écouter sur le port 8001: Échec de la création de tous les écouteurs avec les erreurs suivantes: Impossible de créer l’écouteur: Erreur d’écoute tcp4 127.0.0.1:8001: > la liaison: Une seule utilisation de chaque adresse de socket (protocole/adresse réseau/port) est normalement autorisée. Impossible de créer l’écouteur: Erreur Listen tcp6: adresse [[:: 1]]: 8001: port manquant dans > erreur d’adresse: Impossible d’écouter sur l’un des ports demandés: [{8001 9090}* ], assurez-vous que vous n’avez pas démarré le tableau de bord déjà à partir d’une autre fenêtre.

Lorsque vous lancez le tableau de bord sur votre navigateur, vous pouvez obtenir des avertissements d’autorisation en raison de l’activation par défaut de RBAC dans les clusters AKS et que le compte de service utilisé par le tableau de bord ne dispose pas  *des autorisations suffisantes pour accéder à toutes les ressources (par exemple, blocs interdits: L’utilisateur «System:, compte: Kube-System: kubernetes-Dashboard» ne peut pas répertorier les Pod dans*l’espace de noms «default»). Exécutez la commande suivante pour accorder les autorisations nécessaires à `kubernetes-dashboard`, puis redémarrez le tableau de bord:

```bash
kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

### <a name="start-dashboard-when-kubernetes-cluster-is-bootstrapped--using-kubeadm"></a>Démarrer le tableau de bord lorsque le cluster Kubernetes est amorcé à l’aide de kubeadm

Pour obtenir des instructions détaillées sur le déploiement et la configuration du tableau de bord dans votre cluster Kubernetes, consultez [la documentation de Kubernetes](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/). Pour lancer le tableau de bord Kubernetes, exécutez la commande suivante:

```bash
kubectl proxy
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [que sont les SQL Server Big Data les clusters](big-data-cluster-overview.md).
