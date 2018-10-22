---
title: Utilisez kubectl pour surveiller un cluster de données volumineux de SQL Server | Microsoft Docs
description: Cet article fournit des commandes kubectl utile pour surveiller et dépanner un cluster de données volumineuses de SQL Server 2019 (version préliminaire).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/15/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: a47726e86bd1f10cda4db55bec6eac995344da38
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356593"
---
# <a name="kubectl-commands-for-monitoring-and-troubleshooting-sql-server-big-data-clusters"></a>Commandes Kubectl pour la surveillance et dépannage des clusters de données volumineuses de SQL Server

Cet article décrit plusieurs commandes Kubernetes utiles que vous pouvez utiliser pour surveiller et dépanner un cluster de données volumineuses de SQL Server 2019 (version préliminaire). Cet article traite des tâches courantes, telles que la copie des fichiers vers ou à partir d’un conteneur qui exécute un des services de cluster de données volumineuses de SQL Server. Il montre également comment afficher des informations détaillées d’un pod ou d’autres artefacts Kubernetes qui sont trouvent dans le cluster de données volumineux.

## <a name="kubectl-command-examples"></a>Exemples de commandes Kubectl

Exécutez la commande suivante **kubectl** commandes sur l’ordinateur de client Linux (bash) ou un Windows (cmd ou PS). Ils nécessitent d’authentification précédente dans le cluster et un contexte de cluster pour exécuter. Par exemple, pour un cluster ACS créé précédemment, vous pouvez exécuter `az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>` pour télécharger le fichier de configuration du cluster Kubernetes et de définir le contexte de cluster.

## <a name="get-status-of-pods"></a>Obtenir l’état de pods

Vous pouvez utiliser la `kubectl get pods` commande pour obtenir l’état de pods dans le cluster pour tous les espaces de noms ou de l’espace de noms de cluster de données volumineuses. Les sections suivantes montrent des exemples des deux.

### <a name="show-status-of-all-pods-in-the-kubernetes-cluster"></a>Afficher l’état de tous les pods dans le cluster Kubernetes

Exécutez la commande suivante pour obtenir tous les pods et leurs États, y compris les pods qui font partie de l’espace de noms que SQL Server pods du cluster big data sont créés dans :

```bash
kubectl get pods --all-namespaces
```

### <a name="show-status-of-all-pods-in-the-sql-server-big-data-cluster"></a>Afficher l’état de tous les pods dans le cluster de données volumineux de SQL Server

Utilisez le `-n` paramètre pour spécifier un espace de noms spécifique. Notez que SQL Server pods du cluster big data sont créés dans un nouvel espace de noms créé au moment du démarrage cluster basé sur le nom de cluster spécifié dans le `mssqlctl create cluster <cluster_name>` commande.

```bash
kubectl get pods -n <namespace_name>
```

Par exemple, la commande suivante affiche l’état de pods dans un cluster de données volumineuses nommé `big_data_cluster`:

```bash
kubectl get pods -n big_data_cluster
```

## <a name="get-pod-details"></a>Obtenir les détails de pod

Exécutez la commande suivante pour obtenir une description détaillée d’un pod spécifique dans la sortie du format json. Il inclut des détails, tels que le nœud actuel Kubernetes qui le pod est placé sur, les conteneurs en cours d’exécution dans le pod et l’image utilisée pour démarrer les conteneurs. Il montre d’autres détails, tels que des étiquettes, état et persistante des revendications de volumes qui sont associées le pod.

```bash
kubectl describe pod  <pod_name> -n <namespace_name>
```

L’exemple suivant montre les détails de la `mssql-data-pool-master-0` pod dans un cluster de données volumineuses nommé `big_data_cluster`:

```bash
kubectl describe pod  mssql-data-pool-master-0 -n big_data_cluster
```

## <a name="get-status-of-services"></a>Obtenir l’état des services

Exécutez la commande suivante pour obtenir des détails pour les services de cluster de données volumineuses. Ces détails incluent leur type et les adresses IP associées avec les ports et services respectifs. Notez que les services de cluster de données volumineuses de SQL Server sont créés dans un nouvel espace de noms créé au moment du démarrage cluster basé sur le nom de cluster spécifié dans le `mssqlctl create cluster <cluster_name>` commande.

```bash
kubectl get svc -n <namespace_name>
```

L’exemple suivant montre l’état des services dans un cluster de données volumineuses nommé `big_data_cluster`:

```bash
kubectl get svc -n big_data_cluster
```

## <a name="get-service-details"></a>Obtenir les détails du service

Exécutez cette commande pour obtenir une description détaillée d’un service dans la sortie du format json. Il inclura des détails tels que des étiquettes, sélecteur, adresse IP, adresse IP externe (si le service est de type de l’équilibreur de charge), port, etc.
```
kubectl describe pod  <pod_name> -n <namespace_name>
```

Exemple :
```
kubectl describe pod  mssql-data-pool-master-0 -n big_data_cluster
```

## <a name="run-commands-in-a-container"></a>Exécutez les commandes dans un conteneur

Si les outils existants ou l’infrastructure ne vous autorise pas à effectuer une tâche particulière sans être réellement dans le contexte du conteneur, vous pouvez vous connecter au conteneur en utilisant `kubectl exec` commande. Par exemple, vous devrez peut-être vérifier si un fichier spécifique existe, ou vous devrez peut-être redémarrer les services dans le conteneur. 

Pour utiliser le `kubectl exec` de commande, utilisez la syntaxe suivante :

```bash
kubectl exec -it <pod_name>  -c <container_name> -n <namespace_name> -- /bin/bash <command name> 
```

Les deux sections suivantes fournissent deux exemples d’exécution d’une commande dans un conteneur spécifique.

### <a id="restartsql"></a> Connectez-vous à un conteneur spécifique et redémarrez le processus SQL Server

L’exemple suivant montre comment redémarrer le processus SQL Server dans le `mssql-server` conteneur dans le `mssql-master-pool-0` pod :

```bash
kubectl exec -it mssql-master-pool-0  -c mssql-server -n big_data_cluster -- /bin/bash 
supervisorctl restart mssql
```

### <a id="restartservices"></a> Ouvrez une session un conteneur spécifique et redémarrer les services dans un conteneur
 
L’exemple suivant montre comment redémarrer tous les services gérés par **supervisord**: 

```bash
kubectl exec -it mssql-master-pool-0  -c mssql-server -n big_data_cluster -- /bin/bash 
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
kubectl cp mssql-master-pool-0:/var/opt/mssql/log -c mssql-server -n big_data_cluster ~/tmp/sqlserverlogs
```

### <a id="copyinto"></a> Copier des fichiers dans le conteneur

L’exemple ci-après copie le **AdventureWorks2016CTP3.bak** fichier à partir de l’ordinateur local vers le conteneur d’instance principale de SQL Server (`mssql-server`) dans le `mssql-master-pool-0` pod. Le fichier est copié dans le `/tmp` répertoire dans le conteneur. 

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak mssql-master-pool-0:/tmp -c mssql-server -n big_data_cluster
```

## <a id="forcedelete"></a> Forcer la suppression un pod
 
Il n’est pas recommandé pour effectuer une suppression forcée un pod. Mais la disponibilité, la résilience et persistance des données de test, vous pouvez supprimer un pod pour simuler une défaillance de pod avec la `kubectl delete pods` commande.

```bash
kubectl delete pods <pod_name> -n <namespace_name> --grace-period=0 --force
```

L’exemple suivant supprime le pod de pool de stockage, `mssql-storage-pool-default-0`:

```bash
kubectl delete pods mssql-storage-pool-default-0 -n big_data_cluster --grace-period=0 --force
```

## <a id="getip"></a> Obtenir l’adresse IP du bloc
 
Pour résoudre ce problème, vous devrez peut-être obtenir l’adresse IP du nœud sur qu'un pod est en cours d’exécution. Pour obtenir l’adresse IP, utilisez le `kubectl get pods` commande avec la syntaxe suivante :

```bash
kubectl get pods <pod_name> -o yaml -n <namespace_name> | grep hostIP
```

L’exemple suivant obtient l’adresse IP du nœud qui le `mssql-master-pool-0` pod est en cours d’exécution :

```bash
kubectl get pods mssql-master-pool-0 -o yaml -n big_data_cluster | grep hostIP
```

## <a name="start-the-kubernetes-dashboard"></a>Démarrer le tableau de bord Kubernetes

Vous pouvez lancer le tableau de bord Kubernetes pour des informations supplémentaires sur le cluster. Les sections suivantes expliquent comment lancer le tableau de bord pour Kubernetes sur AKS et initialisé à l’aide de kubeadm de Kubernetes.
 
### <a name="start-dashboard-when-cluster-is-running-in-aks"></a>Démarrer le tableau de bord lorsque le cluster est en cours d’exécution dans ACS

Pour lancer le tableau de bord de Kubernetes :
 
```bash
az aks browse --resource-group <azure_resource_group> --name <aks_cluster_name>
```

> [!Note]
> Si vous obtenez l’erreur suivante : *Impossible d’écouter sur le port 8001 : Échec de tous les écouteurs de création avec les erreurs suivantes : Impossible de créer l’écouteur : erreur écouter tcp4 127.0.0.1:8001 : > lier : seule utilisation de chaque adresse de socket (protocole/réseau adresse/port) est normalement autorisé. Impossible de créer l’écouteur : erreur écouter tcp6 : adresse [[ :: 1]] : 8001 : manquant de port dans > résolution des problèmes : ne peut pas écouter les ports requis : [{8001 9090}]*, assurez-vous que vous n’avez pas démarré le tableau de bord déjà d’une autre fenêtre.

Lorsque vous lancez le tableau de bord sur votre navigateur, vous pouvez obtenir des avertissements d’autorisation en raison de RBAC étant activé par défaut dans les clusters AKS, et le compte de service utilisé par le tableau de bord n’a pas d’autorisations suffisantes pour accéder à toutes les ressources (par exemple,  *PODS est interdite : utilisateur « système : serviceaccount:kube-système : kubernetes-Need » ne peut pas répertorier les pods dans l’espace de noms « default »*). Exécutez la commande suivante pour accorder les autorisations nécessaires pour `kubernetes-dashboard`, puis redémarrez le tableau de bord :

```
kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

### <a name="start-dashboard-when-kubernetes-cluster-is-bootstrapped--using-kubeadm"></a>Démarrer le tableau de bord lorsque le cluster Kubernetes est initialisé à l’aide de kubeadm

Pour plus d’instructions déployer et configurer le tableau de bord dans votre cluster Kubernetes, consultez [la documentation de Kubernetes](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/). Pour lancer le tableau de bord Kubernetes, exécutez la commande suivante :

```
kubectl proxy
```

## <a name="next-steps"></a>Étapes suivantes

Pour surveiller et dépanner le c'est-à-dire spécifiques à SQL Server clusters de données volumineuses, consultez le [portail d’administration de cluster](cluster-admin-portal.md).