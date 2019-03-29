---
title: Notes de publication
titleSuffix: SQL Server 2019 big data clusters
description: Cet article décrit les dernières mises à jour et les problèmes connus pour les clusters de données volumineuses de SQL Server 2019 (version préliminaire).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/28/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: c7c80b69ac7120f2cd88500d3c276a313ef34390
ms.sourcegitcommit: 0c049c539ae86264617672936b31d89456d63bb0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58618306"
---
# <a name="release-notes-for-big-data-clusters-on-sql-server"></a>Notes de publication pour les clusters de données volumineuses sur SQL Server

Cet article répertorie les mises à jour et connaître les problèmes pour les versions les plus récentes des clusters de données volumineuses de SQL Server.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="ctp24"></a> CTP 2.4 (mars)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters de données volumineuses dans SQL Server 2019 CTP 2.4.

### <a name="whats-new"></a>What's New

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
| Obtenir des conseils sur le GPU prend en charge pour l’exécution de deep learning avec TensorFlow dans Spark. | [Déployer un cluster de données volumineuses avec prise en charge GPU et exécuter TensorFlow](spark-gpu-tensorflow.md). |
| **SqlDataPool** et **SqlStoragePool** des sources de données ne sont plus créés par défaut. | Créer manuellement en fonction des besoins. Consultez le [problèmes connus](#externaltablesctp24). |
| `INSERT INTO SELECT` prise en charge pour le pool de données. | Pour obtenir un exemple, consultez [didacticiel : Recevoir des données dans un pool de données SQL Server avec Transact-SQL](tutorial-data-pool-ingest-sql.md). |
| `FORCE SCALEOUTEXECUTION` et `DISABLE SCALEOUTEXECUTION` option. | Force ou désactive l’utilisation du pool de calcul pour les requêtes sur les tables externes. Par exemple, `SELECT TOP(100) * FROM web_clickstreams_hdfs_book_clicks OPTION(FORCE SCALEOUTEXECUTION)`. |
| Mise à jour des recommandations de déploiement AKS. | Lorsque vous évaluez les clusters de données volumineuses sur AKS, nous recommandons à présent à l’aide d’un seul nœud de taille **Standard_L8s**. |
| Exécution de Spark mise à niveau à Spark 2.4. | |

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus et les limitations de cette version.

#### <a name="deployment"></a>Déploiement

- La mise à niveau d’un cluster de données volumineuses de données à partir d’une version précédente n’est pas pris en charge.

   > [!IMPORTANT]
   > Vous devez sauvegarder vos données, puis supprimez votre cluster big data existant (à l’aide de la version précédente de **mssqlctl**) avant de déployer la dernière version. Pour plus d’informations, consultez [mise à niveau vers une nouvelle version](deployment-guidance.md#upgrade).

- Après avoir déployé sur AKS, vous pouvez voir les deux événements d’avertissement suivants du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déploiement du cluster de données volumineuses sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’un déploiement de cluster de données volumineuses, l’espace de noms associé n’est pas supprimé. Cela peut entraîner un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer l’espace de noms manuellement avant de déployer un cluster avec le même nom.

#### <a name="kubeadm-deployments"></a>déploiements kubeadm

Si vous utilisez kubeadm déploiement Kubernetes sur plusieurs ordinateurs, le portail d’administration de cluster n’affiche pas correctement les points de terminaison nécessaires pour se connecter au cluster big data. Si vous rencontrez ce problème, utilisez la solution de contournement suivante pour découvrir les adresses IP de point de terminaison de service :

- Si vous vous connectez à partir d’au sein du cluster, interrogez Kubernetes pour l’adresse IP de service pour le point de terminaison que vous souhaitez vous connecter. Par exemple, ce qui suit **kubectl** commande affiche l’adresse IP de l’instance principale de SQL Server :

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Si vous vous connectez à partir de l’extérieur du cluster, procédez comme suit pour vous connecter :

   1. Obtenir l’adresse IP du nœud qui exécute l’instance principale de SQL Server : `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`.

   1. Se connecter à l’instance principale de SQL Server à l’aide de cette adresse IP.

   1. Requête la **cluster_endpoint_table** dans la base de données master pour les autres points de terminaison externes.

      En cas d’échec avec un délai de connexion, il est possible du que nœud correspondant est protégé par un pare-feu. Dans ce cas, vous devez contacter votre administrateur de cluster Kubernetes et demander pour l’adresse IP de nœud qui est exposé en externe. Cela peut être n’importe quel nœud. Vous pouvez ensuite utiliser cette adresse IP et le port correspondant pour se connecter à différents services en cours d’exécution dans le cluster. Par exemple, l’administrateur peut trouver cette adresse IP en exécutant :

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a name="delete-cluster-fails"></a>Supprimer le cluster tombe en panne

Lorsque vous tentez de supprimer un cluster avec **mssqlctl**, elle échoue avec l’erreur suivante :

```
2019-03-26 20:38:11.0614 UTC | INFO | Deleting cluster ...
Error processing command: "TypeError"
delete_namespaced_service() takes 3 positional arguments but 4 were given
Makefile:61: recipe for target 'delete-cluster' failed
make[2]: *** [delete-cluster] Error 1
Makefile:223: recipe for target 'deploy-clean' failed
make[1]: *** [deploy-clean] Error 2
Makefile:203: recipe for target 'deploy-clean' failed
make: *** [deploy-clean] Error 2
```

Un nouveau client Kubernetes de Python (version 9.0.0) modifié delete espaces de noms API, ce qui interrompt actuellement **mssqlctl**. Cela se produit uniquement si vous avez un client plus récent de python Kubernetes installé. Vous pouvez contourner ce problème en supprimant directement le cluster à l’aide **kubectl** (`kubectl delete ns <ClusterName>`), ou vous pouvez installer la version antérieure à l’aide `sudo pip install kubernetes==8.0.1`.

#### <a id="externaltablesctp24"></a> Tables externes

- Déploiement de cluster de données volumineuses ne crée plus la **SqlDataPool** et **SqlStoragePool** sources de données externes. Vous pouvez créer ces sources de données manuellement pour prendre en charge de la virtualisation des données pour le pool de données et le pool de stockage.

   ```sql
   -- Create the SqlDataPool data source:
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
     CREATE EXTERNAL DATA SOURCE SqlDataPool
     WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');

   -- Create the SqlStoragePool data source:
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
   BEGIN
     IF SERVERPROPERTY('ProductLevel') = 'CTP2.3'
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://service-mssql-controller:8080');
     ELSE IF SERVERPROPERTY('ProductLevel') = 'CTP2.4'
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://service-master-pool:50070');
   END
   ```

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit :

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Si vous créez une table externe à Oracle qui utilisent des types de données caractères, l’Assistant de virtualisation d’Azure Data Studio interprète ces colonnes comme VARCHAR dans la définition de table externe. Cela entraîne un échec dans la table externe DDL. Modifiez le schéma Oracle pour utiliser le type NVARCHAR2, ou créer manuellement les instructions de la TABLE externe et spécifiez NVARCHAR au lieu d’utiliser l’Assistant.

#### <a name="application-deployment"></a>Déploiement d’applications

- Lors de l’appel d’une application de R, Python ou MLeap à partir de l’API RESTful, l’appel expire dans 5 minutes.

#### <a name="spark-and-notebooks"></a>Spark et notebooks

- Adresses IP de POD peuvent changer dans l’environnement de Kubernetes en tant que les redémarrages de PODs. Dans le scénario où le pod de master redémarre, la session Spark peut échouer avec `NoRoteToHostException`. Cela est provoqué par les caches JVM n’est-il actualisés avec la nouvelle adresse IP adresses.

- Si vous avez Jupyter est déjà installé et distinct Python sur Windows, les blocs-notes Spark risque d’échouer. Pour contourner ce problème, vous devez mettre à niveau Jupyter vers la dernière version.

- Dans un bloc-notes, si vous cliquez sur le **ajouter le texte** commande, la cellule de texte est ajoutée dans le mode Aperçu, et non en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et de modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez sur un fichier dans HDFS pour en afficher un aperçu, vous pouvez voir l’erreur suivante :

   `Error previewing file: File exceeds max size of 30MB`

   Il n’existe actuellement aucun moyen pour afficher un aperçu des fichiers supérieurs à 30 Mo dans Azure Data Studio.

- Modifications de configuration HDFS qui impliquent des modifications apportées à hdfs-site.XML ne sont pas pris en charge.

#### <a name="security"></a>Sécurité

- Le SA_PASSWORD fait partie de l’environnement et détectable (par exemple dans un fichier de vidage cordon). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Cela n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [modifier le mot de passe SA](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS journaux peuvent contenir le mot de passe SA pour les déploiements de cluster big data.

## <a id="ctp23"></a> CTP 2.3 (février)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters de données volumineuses dans SQL Server 2019 CTP 2.3.

### <a name="whats-new"></a>What's New

| Nouvelle fonctionnalité ou mise à jour | Détails |
| :---------- | :------ |
| Envoyez des travaux Spark sur des clusters de données volumineuses dans IntelliJ. | [Envoyer des travaux Spark sur des clusters de données volumineuses de SQL Server dans IntelliJ](spark-submit-job-intellij-tool-plugin.md) |
| CLI courantes pour la gestion de cluster et de déploiement des applications. | [Comment déployer une application sur un cluster de données volumineux de SQL Server 2019 (version préliminaire)](big-data-cluster-create-apps.md) |
| Extension de Code Visual Studio pour déployer des applications sur un cluster de données volumineux. | [Comment utiliser VS Code pour déployer des applications sur les clusters de données volumineuses de SQL Server](app-deployment-extension.md) |
| Modifications apportées à la **mssqlctl** outil utilisation de la commande. | Pour plus d’informations, consultez le [problèmes connus dans mssqlctl](#mssqlctlctp23). |
| Utiliser Sparklyr dans un cluster de données volumineux | [Utiliser Sparklyr dans un cluster de données volumineux de SQL Server 2019](sparklyr-from-RStudio.md) |
| Monter un stockage compatible HDFS externe dans le cluster de données volumineux avec **HDFS la hiérarchisation**. | Consultez [HDFS la hiérarchisation](hdfs-tiering.md). |
| Nouvelle expérience de connexion unifiée pour l’instance principale de SQL Server et de la passerelle HDFS/Spark. | Consultez [instance principale de SQL Server et de la passerelle HDFS/Spark](connect-to-big-data-cluster.md). |
| Suppression d’un cluster avec **mssqlctl cluster delete** maintenant supprime uniquement les objets dans l’espace de noms qui faisaient partie du cluster de données volumineuses. | L’espace de noms n’est pas supprimé. Toutefois, dans les versions antérieures, cette commande n’a supprimé l’espace de noms entier. |
| _Sécurité_ les noms de point de terminaison ont été modifiés et consolidés. | **service-sécurité-lb** et **service-sécurité-nodeport** ont été consolidées dans la **-security du point de terminaison** point de terminaison. |
| _Proxy_ les noms de point de terminaison ont été modifiés et consolidés. | **proxy-service-lb** et **proxy-service-nodeport** ont été consolidées dans la **proxy de service de point de terminaison** point de terminaison. |
| _Contrôleur_ les noms de point de terminaison ont été modifiés et consolidés. | **service-mssql-contrôleur-lb** et **service-mssql-contrôleur-nodeport** ont été consolidées dans la **contrôleur de point de terminaison** point de terminaison. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus et les limitations de cette version.

#### <a name="deployment"></a>Déploiement

- La mise à niveau d’un cluster de données volumineuses de données à partir d’une version précédente n’est pas pris en charge.

   > [!IMPORTANT]
   > Vous devez sauvegarder vos données, puis supprimez votre cluster big data existant (à l’aide de la version précédente de **mssqlctl**) avant de déployer la dernière version. Pour plus d’informations, consultez [mise à niveau vers une nouvelle version](deployment-guidance.md#upgrade).

- Le **ACCEPT_EULA** variable d’environnement doit être « yes » ou « Oui » pour accepter le CLUF. Les versions précédentes autorisés « y » et « Y » mais ils ne sont plus acceptés et entraînent l’échec du déploiement.

- Le **CLUSTER_PLATFORM** variables d’environnement n’a pas de valeur par défaut comme elle le faisait dans les versions précédentes.

- Après avoir déployé sur AKS, vous pouvez voir les deux événements d’avertissement suivants du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déploiement du cluster de données volumineuses sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’un déploiement de cluster de données volumineuses, l’espace de noms associé n’est pas supprimé. Cela peut entraîner un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer l’espace de noms manuellement avant de déployer un cluster avec le même nom.

#### <a name="kubeadm-deployments"></a>déploiements kubeadm

Si vous utilisez kubeadm déploiement Kubernetes sur plusieurs ordinateurs, le portail d’administration de cluster n’affiche pas correctement les points de terminaison nécessaires pour se connecter au cluster big data. Si vous rencontrez ce problème, utilisez la solution de contournement suivante pour découvrir les adresses IP de point de terminaison de service :

- Si vous vous connectez à partir d’au sein du cluster, interrogez Kubernetes pour l’adresse IP de service pour le point de terminaison que vous souhaitez vous connecter. Par exemple, ce qui suit **kubectl** commande affiche l’adresse IP de l’instance principale de SQL Server :

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Si vous vous connectez à partir de l’extérieur du cluster, procédez comme suit pour vous connecter :

   1. Obtenir l’adresse IP du nœud qui exécute l’instance principale de SQL Server : `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`.

   1. Se connecter à l’instance principale de SQL Server à l’aide de cette adresse IP.

   1. Requête la **cluster_endpoint_table** dans la base de données master pour les autres points de terminaison externes.

      En cas d’échec avec un délai de connexion, il est possible du que nœud correspondant est protégé par un pare-feu. Dans ce cas, vous devez contacter votre administrateur de cluster Kubernetes et demander pour l’adresse IP de nœud qui est exposé en externe. Cela peut être n’importe quel nœud. Vous pouvez ensuite utiliser cette adresse IP et le port correspondant pour se connecter à différents services en cours d’exécution dans le cluster. Par exemple, l’administrateur peut trouver cette adresse IP en exécutant :

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a id="mssqlctlctp23"></a> mssqlctl

- Le **mssqlctl** outil a été remplacée par une commande de type verbe-substantif classement selon un ordre de verbe-substantif. Par exemple, `mssqlctl create cluster` est désormais `mssqlctl cluster create`.

- Le `--name` paramètre est désormais requis lors de la création d’un cluster avec `mssqlctl cluster create`.

   ```bash
   mssqlctl cluster create --name <cluster_name>
   ```

- Pour plus d’informations sur la mise à niveau vers la dernière version des clusters de données volumineuses et **mssqlctl**, consultez [mise à niveau vers une nouvelle version](deployment-guidance.md#upgrade).

#### <a name="external-tables"></a>Tables externes

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit :

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Si vous créez une table externe à Oracle qui utilisent des types de données caractères, l’Assistant de virtualisation d’Azure Data Studio interprète ces colonnes comme VARCHAR dans la définition de table externe. Cela entraîne un échec dans la table externe DDL. Modifiez le schéma Oracle pour utiliser le type NVARCHAR2, ou créer manuellement les instructions de la TABLE externe et spécifiez NVARCHAR au lieu d’utiliser l’Assistant.

#### <a name="application-deployment"></a>Déploiement d’applications

- Lors de l’appel d’une application de R, Python ou MLeap à partir de l’API RESTful, l’appel expire dans 5 minutes.

#### <a name="spark-and-notebooks"></a>Spark et notebooks

- Adresses IP de POD peuvent changer dans l’environnement de Kubernetes en tant que les redémarrages de PODs. Dans le scénario où le pod de master redémarre, la session Spark peut échouer avec `NoRoteToHostException`. Cela est provoqué par les caches JVM n’est-il actualisés avec la nouvelle adresse IP adresses.

- Si vous avez Jupyter est déjà installé et distinct Python sur Windows, les blocs-notes Spark risque d’échouer. Pour contourner ce problème, vous devez mettre à niveau Jupyter vers la dernière version.

- Dans un bloc-notes, si vous cliquez sur le **ajouter le texte** commande, la cellule de texte est ajoutée dans le mode Aperçu, et non en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et de modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez sur un fichier dans HDFS pour en afficher un aperçu, vous pouvez voir l’erreur suivante :

   `Error previewing file: File exceeds max size of 30MB`

   Il n’existe actuellement aucun moyen pour afficher un aperçu des fichiers supérieurs à 30 Mo dans Azure Data Studio.

- Modifications de configuration HDFS qui impliquent des modifications apportées à hdfs-site.XML ne sont pas pris en charge.

#### <a name="security"></a>Sécurité

- Le SA_PASSWORD fait partie de l’environnement et détectable (par exemple dans un fichier de vidage cordon). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Cela n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [modifier le mot de passe SA](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS journaux peuvent contenir le mot de passe SA pour les déploiements de cluster big data.

## <a id="ctp22"></a> CTP 2.2 (décembre 2018)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters de données volumineuses dans SQL Server 2019 CTP 2.2.

### <a name="new-features"></a>Nouvelles fonctionnalités

- Portail d’administration de cluster accessible avec `/portal` (**https://\<ip-address\>: 30777/portail**).
- Nom du service maître pool a été remplacée par `service-master-pool-lb` et `service-master-pool-nodeport` à `endpoint-master-pool`.
- Nouvelle version de **mssqlctl** et mis à jour des images.
- Divers correctifs de bogues et améliorations.

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus et les limitations de cette version.

#### <a name="deployment"></a>Déploiement

- La mise à niveau d’un cluster de données volumineuses de données à partir d’une version précédente n’est pas pris en charge. Vous devez sauvegarder et supprimer tous les clusters de données volumineuses existant avant de déployer la dernière version. Pour plus d’informations, consultez [mise à niveau vers une nouvelle version](deployment-guidance.md#upgrade).

- Après avoir déployé sur AKS, vous pouvez voir les deux événements d’avertissement suivants du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déploiement du cluster de données volumineuses sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’un déploiement de cluster de données volumineuses, l’espace de noms associé n’est pas supprimé. Cela peut entraîner un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer l’espace de noms manuellement avant de déployer un cluster avec le même nom.

#### <a name="cluster-administration-portal"></a>Portail d’administration du cluster

Le portail d’administration de cluster n’affiche pas le point de terminaison pour l’instance principale de SQL Server. Pour trouver l’adresse IP et le port de l’instance principale, utilisez la commande suivante **kubectl** commande :

```
kubectl get svc endpoint-master-pool -n <your-cluster-name>
```

#### <a name="external-tables"></a>Tables externes

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit :

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark et notebooks

- Adresses IP de POD peuvent changer dans l’environnement de Kubernetes en tant que les redémarrages de PODs. Dans le scénario où le pod de master redémarre, la session Spark peut échouer avec `NoRoteToHostException`. Cela est provoqué par les caches JVM n’est-il actualisés avec la nouvelle adresse IP adresses.

- Si vous avez Jupyter est déjà installé et distinct Python sur Windows, les blocs-notes Spark risque d’échouer. Pour contourner ce problème, vous devez mettre à niveau Jupyter vers la dernière version.

- Dans un bloc-notes, si vous cliquez sur le **ajouter le texte** commande, la cellule de texte est ajoutée dans le mode Aperçu, et non en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et de modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez sur un fichier dans HDFS pour en afficher un aperçu, vous pouvez voir l’erreur suivante :

   `Error previewing file: File exceeds max size of 30MB`

   Il n’existe actuellement aucun moyen pour afficher un aperçu des fichiers supérieurs à 30 Mo dans Azure Data Studio.

- Modifications de configuration HDFS qui impliquent des modifications apportées à hdfs-site.XML ne sont pas pris en charge.

#### <a name="security"></a>Sécurité

- Le SA_PASSWORD fait partie de l’environnement et détectable (par exemple dans un fichier de vidage cordon). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Cela n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [modifier le mot de passe SA](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS journaux peuvent contenir le mot de passe SA pour les déploiements de cluster big data.

## <a id="ctp21"></a> CTP 2.1 (novembre 2018)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters de données volumineuses dans SQL Server 2019 CTP 2.1.

### <a name="new-features"></a>Nouvelles fonctionnalités

- [Déployer des applications Python et R](big-data-cluster-create-apps.md) dans un cluster de données volumineux.
- Nouvelle version de **mssqlctl** et mis à jour des images. 
- Divers correctifs de bogues et améliorations.

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes fournissent des problèmes connus pour les clusters de données volumineuses de SQL Server dans les CTP 2.1.

#### <a name="deployment"></a>Déploiement

- La mise à niveau d’un cluster de données volumineuses de données à partir d’une version précédente n’est pas pris en charge. Vous devez sauvegarder et supprimer tous les clusters de données volumineuses existant avant de déployer la dernière version. Pour plus d’informations, consultez [mise à niveau vers une nouvelle version](deployment-guidance.md#upgrade).

- Après avoir déployé sur AKS, vous pouvez voir les deux événements d’avertissement suivants du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déploiement du cluster de données volumineuses sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’un déploiement de cluster de données volumineuses, l’espace de noms associé n’est pas supprimé. Cela peut entraîner un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer l’espace de noms manuellement avant de déployer un cluster avec le même nom.

#### <a name="admin-portal"></a>Portail d’administration

- Lorsque vous [créer une application à l’aide de la commande de la version ctp msqlctl](big-data-cluster-create-apps.md) et déployez-le sur un cluster de données volumineux, le portail d’administration de Cluster montre les pods où l’application a été déployée comme « Inconnue » dans la section de contrôleur de la partie de l’administrateur de SQL Server.

#### <a name="external-tables"></a>Tables externes

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit :

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark et notebooks

- Adresses IP de POD peuvent changer dans l’environnement de Kubernetes en tant que les redémarrages de PODs. Dans le scénario où le pod de master redémarre, la session Spark peut échouer avec `NoRoteToHostException`. Cela est provoqué par les caches JVM n’est-il actualisés avec la nouvelle adresse IP adresses.

- Si vous avez Jupyter est déjà installé et distinct Python sur Windows, les blocs-notes Spark risque d’échouer. Pour contourner ce problème, vous devez mettre à niveau Jupyter vers la dernière version.

- Dans un bloc-notes, si vous cliquez sur le **ajouter le texte** commande, la cellule de texte est ajoutée dans le mode Aperçu, et non en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et de modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez sur un fichier dans HDFS pour en afficher un aperçu, vous pouvez voir l’erreur suivante :

   `Error previewing file: File exceeds max size of 30MB`

   Il n’existe actuellement aucun moyen pour afficher un aperçu des fichiers supérieurs à 30 Mo dans Azure Data Studio.

- Modifications de configuration HDFS qui impliquent des modifications apportées à hdfs-site.XML ne sont pas pris en charge.

#### <a name="security"></a>Sécurité

- Le SA_PASSWORD fait partie de l’environnement et détectable (par exemple dans un fichier de vidage cordon). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Cela n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [modifier le mot de passe SA](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS journaux peuvent contenir le mot de passe SA pour les déploiements de cluster big data.

## <a id="ctp20"></a> CTP 2.0 (octobre 2018)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters de données volumineuses dans SQL Server 2019 CTP 2.0.

### <a name="new-features"></a>Nouvelles fonctionnalités

- Expérience de déploiement simple à l’aide d’outil de gestion mssqlctl
- Expérience de bloc-notes native dans Azure Data Studio
- Fichiers de HDFS de requête via une Instance de stockage de SQL Server
- Virtualisation des données par le biais de master à SQL Server, Oracle, MongoDB et HDFS
- Assistant de virtualisation des données pour SQL Server et Oracle dans Azure Data Studio
- Services ML sur master
- Portail d’administration de cluster que vous pouvez utiliser pour la surveillance et dépannage
- Envoi de travail Spark dans Azure Data Studio 
- Interface utilisateur Spark dans le portail d’administration de cluster
- Volume de montage pour les classes de stockage
- Les requêtes portant sur les pools de données à partir de master
- Afficher le plan pour les requêtes distribuées dans SSMS
- Package PIP mssqlctl outil de gestion
- Moteur de déploiement intégrées via le service de contrôleur

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes fournissent des problèmes connus pour les clusters de données volumineuses de SQL Server dans CTP 2.0.

#### <a name="deployment"></a>Déploiement

- Si vous utilisez Azure Kubernetes Service (AKS), la version recommandée de Kubernetes est 1.10. *, qui ne prend pas en charge la redimensionnement de disque. Vous devez vous assurer que vous dimensionnez le stockage en conséquence au moment du déploiement. Pour plus d’informations sur la façon d’ajuster les tailles de stockage, consultez le [persistance des données](concept-data-persistence.md) article. Pour Kubernetes déployé sur les machines virtuelles, la version recommandée est 1.11.

- Après avoir déployé sur AKS, vous pouvez voir les deux événements d’avertissement suivants du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déploiement du cluster de données volumineuses sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’un déploiement de cluster de données volumineuses, l’espace de noms associé n’est pas supprimé. Cela peut entraîner un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer l’espace de noms manuellement avant de déployer un cluster avec le même nom.

#### <a name="external-tables"></a>Tables externes

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit :

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark et notebooks

- Adresses IP de POD peuvent changer dans l’environnement de Kubernetes en tant que les redémarrages de PODs. Dans le scénario où le pod de master redémarre, la session Spark peut échouer avec `NoRoteToHostException`. Cela est provoqué par les caches JVM n’est-il actualisés avec la nouvelle adresse IP adresses.

- Si vous avez Jupyter est déjà installé et distinct Python sur Windows, les blocs-notes Spark risque d’échouer. Pour contourner ce problème, vous devez mettre à niveau Jupyter vers la dernière version.

- Dans un bloc-notes, si vous cliquez sur le **ajouter le texte** commande, la cellule de texte est ajoutée dans le mode Aperçu, et non en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et de modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez sur un fichier dans HDFS pour en afficher un aperçu, vous pouvez voir l’erreur suivante :

   `Error previewing file: File exceeds max size of 30MB`

   Il n’existe actuellement aucun moyen pour afficher un aperçu des fichiers supérieurs à 30 Mo dans Azure Data Studio.

- Modifications de configuration HDFS qui impliquent des modifications apportées à hdfs-site.XML ne sont pas pris en charge.

#### <a name="security"></a>Sécurité

- Le SA_PASSWORD fait partie de l’environnement et détectable (par exemple dans un fichier de vidage cordon). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Cela n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [modifier le mot de passe SA](../linux/quickstart-install-connect-docker.md#sapassword).

- AKS journaux peuvent contenir le mot de passe SA pour les déploiements de cluster big data.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses de SQL Server, consultez [que sont les clusters de données volumineuses de SQL Server 2019 ?](big-data-cluster-overview.md).
