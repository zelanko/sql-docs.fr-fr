---
title: Notes de publication
titleSuffix: SQL Server 2019 big data clusters
description: Cet article décrit les dernières mises à jour et les problèmes connus pour les clusters de données volumineuses de SQL Server 2019 (version préliminaire).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: dced44806927f7b41957c2eb8374688e8be88f1f
ms.sourcegitcommit: 670082cb47f7d3d82e987b549b6f8e3a8968b5db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57334746"
---
# <a name="release-notes-for-sql-server-2019-big-data-clusters"></a>Notes de publication pour les clusters de données volumineuses de SQL Server 2019

Cet article fournit les dernières mises à jour et les problèmes connus de la dernière version des clusters de données volumineuses de SQL Server. Le tableau suivant renvoie à la section pour les versions couvert dans cet article.

| Version | Date |
|---|---|
| [CTP 2.3](#ctp23) | Février 2019 |
| [CTP 2.2](#ctp22) | Décembre 2018 |
| [CTP 2.1](#ctp21) | Novembre 2018 |
| [CTP 2.0](#ctp20) | Octobre 2018 |

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="ctp23"></a> CTP 2.3 (février 2019)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters de données volumineuses dans SQL Server 2019 CTP 2.3.

### <a name="whats-in-the-ctp-23-release"></a>Nouveautés dans la version CTP 2.3

- [Envoyer des travaux Spark sur les Clusters Big Data SQL Server dans IntelliJ](spark-submit-job-intellij-tool-plugin.md).
- [CLI courantes pour la gestion de cluster et de déploiement des applications](big-data-cluster-create-apps.md).
- [Extension de Code Visual Studio pour déployer des applications pour les clusters de données volumineuses de SQL Server](app-deployment-extension.md).
- [Modifications apportées à la **mssqlctl** outil utilisation de la commande](#mssqlctlctp23).
- [Utiliser Sparklyr dans un cluster de données SQL Server 2019 Big](sparklyr-from-RStudio.md).
- Monter un stockage compatible HDFS externe dans le cluster de données volumineux avec [HDFS la hiérarchisation](hdfs-tiering.md).
- Nouvelle expérience de connexion unifiée pour la [instance principale de SQL Server et de la passerelle HDFS/Spark](connect-to-big-data-cluster.md).
- Suppression d’un cluster avec **mssqlctl cluster delete** maintenant supprime uniquement les objets dans l’espace de noms qui faisaient partie du cluster de données volumineuses, mais laisse de l’espace de noms. Cette commande supprimé auparavant, l’espace de noms entier.
- Les noms de point de terminaison ont été modifiés et consolidés dans cette version :

   | Points de terminaison précédents | Nouveau point de terminaison |
   |---|---|
   | **service-security-lb**<br/>**service-security-nodeport** | **endpoint-security** |
   | **service-proxy-lb**<br/>**service-proxy-nodeport** | **endpoint-service-proxy** |
   | **service-mssql-controller-lb**<br/>**service-mssql-controller-nodeport** | **endpoint-controller** |

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes fournissent des problèmes connus pour les clusters de données volumineuses de SQL Server dans les CTP 2.3.

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

### <a name="whats-in-the-ctp-22-release"></a>Nouveautés dans la version CTP 2.2

- Portail d’administration de cluster accessible avec `/portal` (**https://\<ip-address\>: 30777/portail**).
- Nom du service maître pool a été remplacée par `service-master-pool-lb` et `service-master-pool-nodeport` à `endpoint-master-pool`.
- Nouvelle version de **mssqlctl** et mis à jour des images.
- Divers correctifs de bogues et améliorations.

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes fournissent des problèmes connus pour les clusters de données volumineuses de SQL Server dans les CTP 2.2.

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

### <a name="whats-in-the-ctp-21-release"></a>Nouveautés dans la version CTP 2.1

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

### <a name="whats-in-the-ctp-20-release"></a>Nouveautés dans la version CTP 2.0

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
