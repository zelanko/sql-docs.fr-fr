---
title: Notes de publication des clusters Big Data SQL Server
titleSuffix: SQL Server big data clusters
description: Cet article décrit les dernières mises à jour et les problèmes connus relatifs aux clusters Big Data SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bc5928a7e3015545d36900b52ef01a42d9694cc0
ms.sourcegitcommit: b4ad3182aa99f9cbfd15f4c3f910317d6128a2e5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73706173"
---
# <a name="sql-server-big-data-clusters-release-notes"></a>Notes de publication des clusters Big Data SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Obtenez des insights en quasi temps réel à partir de toutes vos données avec des [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. Ceux-ci fournissent un environnement complet permettant d’utiliser des jeux de données volumineux, notamment des fonctionnalités de machine learning et d’IA.

Cet article dresse la liste des mises à jour et des problèmes connus pour les versions les plus récentes des [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] (clusters BDC).

## <a id="rtm"></a> SQL Server 2019

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] introduit les clusters Big Data SQL Server.

Utilisez les clusters Big Data SQL Server pour :

- [Déployer des clusters scalables](../big-data-cluster/deploy-get-started.md) de conteneurs SQL Server, Spark et HDFS exécutés sur Kubernetes. 
- Lire, écrire et traiter les données du Big Data à partir de Transact-SQL ou de Spark.
- Combiner et analyser facilement des données relationnelles à valeur élevée et un volume important de données du Big Data.
- Interroger des sources de données externes.
- Stocker les données du Big Data dans un système HDFS géré par SQL Server.
- Interroger les données de plusieurs sources de données externes via le cluster.
- Utiliser les données pour l’IA, le machine learning et d’autres tâches d’analyse.
- [Déployer et exécuter des applications](../big-data-cluster/concept-application-deployment.md) dans des [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)].
- Virtualiser les données avec [Polybase](../relational-databases/polybase/polybase-guide.md). Interrogez des données à partir de sources de données SQL Server, Oracle, Teradata, MongoDB et ODBC externes avec des tables externes.
- Fournir la haute disponibilité pour l’instance principale SQL Server et toutes les bases de données à l’aide de la technologie des groupes de disponibilité Always On.

## <a name="sql-server-version"></a>Version de SQL Server

La version actuelle de SQL Server est `15.0.2070.34`.

## <a name="image-tags"></a>Étiquettes d’image

L’étiquette d’image de cette version est `2019-GDR1-ubuntu-16.04`.

[!INCLUDE [sql-server-servicing-updates-version-15](../includes/sql-server-servicing-updates-version-15.md)]

## <a name="supportability"></a>Prise en charge

Cette section explique les plateformes qui sont prises en charge avec les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] (clusters BDC).

### <a name="kubernetes-platforms"></a>Plateformes Kubernetes

|Plateforme|Versions prises en charge|
|---------|---------|
|Kubernetes|Le cluster BDC requiert la version minimale Kubernetes 1.13. Consultez [Version de Kubernetes et stratégie de prise en charge des décalages de version](https://kubernetes.io/docs/setup/release/version-skew-policy/) pour découvrir la stratégie de prise en charge des versions de Kubernetes.|
|Azure Kubernetes Service (AKS)|Le cluster BDC requiert la version minimale AKS 1.13.<br/>Consultez [Versions Kubernetes prises en charge dans AKS](/azure/aks/supported-kubernetes-versions) pour découvrir la stratégie de prise en charge des versions.|

### <a name="host-os-for-kubernetes"></a>Système d’exploitation hôte pour Kubernetes

|Plateforme|Versions prises en charge|
|---------|---------|
|Red Hat Enterprise Linux|7.3, 7.4, 7.5, 7.6|
|Ubuntu|16.04|

### <a name="tools"></a>Outils

|Plateforme|Versions prises en charge|
|---------|---------|
|`azdata`|La même version mineure que le serveur doit être utilisée (identique à l’instance principale SQL Server).<br/>Exécutez `azdata –-version` pour valider la version. Actuellement, cette version est `15.0.2070`.|
|Azure Data Studio|Procurez-vous la dernière version d’[Azure Data Studio](https://aka.ms/getazuredatastudio).|

### <a name="sql-server-editions"></a>Éditions de SQL Server

|Édition|Remarques|
|---------|---------|
|Enterprise<br/>Standard<br/>Développeur| L’édition du cluster Big Data est déterminée par l’édition de l’instance principale SQL Server. Au moment du déploiement, l’édition Développeur est déployée par défaut. Vous pouvez changer l’édition après le déploiement. Consultez [Configurer l’instance principale SQL Server](../big-data-cluster/configure-sql-server-master-instance.md). |

## <a name="known-issues"></a>Problèmes connus

### <a name="livy-job-submission-from-azure-data-studio-ads-or-curl-fail-with-500-error"></a>Échec de l’envoi de tâches Livy à partir d’Azure Data Studio (ADS) ou de curl avec l’erreur 500

**Problème et impact sur le client** : Dans une configuration à haute disponibilité, les ressources partagées Spark (sparkhead) sont configurées avec plusieurs réplicas. Dans ce cas, vous pouvez rencontrer des échecs lors de l’envoi de tâches Livy à partir d’Azure Data Studio (ADS) ou de `curl`. Pour vérifier, une opération `curl` vers n’importe quel pod sparkhead entraîne un refus de connexion. Par exemple, `curl https://sparkhead-0:8998/` ou `curl https://sparkhead-1:8998` retourne l’erreur 500.

Ceci est le cas dans les scénarios suivants :

- Les pods ou les processus Zookeeper pour chaque instance Zookeeper sont redémarrés plusieurs fois.
- Lorsque la connectivité réseau n’est pas fiable entre le pod Sparkhead et les pods Zookeeper.

**Solution de contournement**: Redémarrage des deux serveurs Livy.

```bash
kubectl -n <clustername> exec sparkhead-0 -c hadoop-livy-sparkhistory supervisorctl restart livy
```

```bash
kubectl -n <clustername> exec sparkhead-1 -c hadoop-livy-sparkhistory supervisorctl restart livy
```

### <a name="create-memory-optimized-table-when-master-instance-in-an-availability-group"></a>Créer une table à mémoire optimisée lorsque l’instance principale est dans un groupe de disponibilité

- **Problème et impact sur le client** : Vous ne pouvez pas utiliser le point de terminaison principal exposé pour la connexion aux bases de données du groupe de disponibilité (écouteur) pour créer des tables à mémoire optimisée.

- **Solution de contournement**: Pour créer des tables à mémoire optimisée lorsque l’instance principale SQL Server est une configuration de groupe de disponibilité, [connectez-vous à l’instance SQL Server](deployment-high-availability.md#instance-connect), exposez un point de terminaison, connectez-vous à la base de données SQL Server et créez les tables optimisées en mémoire dans le session créée avec la nouvelle connexion.

### <a name="insert-to-external-tables-active-directory-authentication-mode"></a>Insérer dans des tables externes en mode d’authentification Active Directory

- **Problème et impact sur le client** : Lorsque l’instance principale SQL Server est en mode d’authentification Active Directory, une requête qui sélectionne uniquement à partir de tables externes où au moins l’une des tables externes figure dans un pool de stockage, et insère dans une autre table externe, retourne :

   ```
   Msg 7320, Level 16, State 102, Line 1
   Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "SQLNCLI11". Only domain logins can be used to query Kerberized storage pool.
   ```

- **Solution de contournement**: Modifiez la requête de l’une des manières suivantes. Joignez d’abord la table de pool de stockage à une table locale, ou insérez dans la table locale, puis lisez la table locale pour l’insérer dans le pool de données.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] ?](big-data-cluster-overview.md)
