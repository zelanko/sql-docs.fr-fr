---
title: Notes de publication
titleSuffix: SQL Server 2019 big data clusters
description: Cet article décrit les dernières mises à jour et les problèmes connus pour les clusters de données volumineuses de SQL Server 2019 (version préliminaire).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/07/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 4f16ee38b09198c036941085c9d7a5a1ee35f01b
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2019
ms.locfileid: "54242070"
---
# <a name="release-notes-for-sql-server-2019-big-data-clusters"></a>Notes de publication pour les clusters de données volumineuses de SQL Server 2019

Cet article fournit les dernières mises à jour et les problèmes connus de la dernière version des clusters de données volumineuses de SQL Server. Le tableau suivant renvoie à la section pour les versions couvert dans cet article.

| Version | Date |
|---|---|
| [CTP 2.2](#ctp22) | Décembre 2018 |
| [CTP 2.1](#ctp21) | Novembre 2018 |
| [CTP 2.0](#ctp20) | Octobre 2018 |

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

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
