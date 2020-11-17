---
title: Configurer le cluster
titleSuffix: Configure a SQL Server big data cluster
description: Présentation de la configuration d’un cluster Big Data SQL Server
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: rahul.ajmera
ms.date: 08/04/2020
ms.topic: overview
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b75f6946af9a13d6a8202c627d4c24a2225a51c1
ms.sourcegitcommit: 4545b502e3cae7136411fd9a7c15450315665f38
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94549986"
---
# <a name="configure-a-sql-server-big-data-cluster"></a>Configurer un cluster Big Data SQL Server

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Vous pouvez configurer les propriétés de l’instance maître SQL Server, Apache Spark et Apache Hadoop dans un cluster Big Data SQL Server Cluster 2019 au moment du déploiement.

Après le déploiement, les clusters Big Data ne prennent pas en charge la modification des propriétés de configuration.

## <a name="configuration-scopes"></a>Portée des configurations
La configuration Clusters Big Data offre deux portées possibles : `service` et `resource`. La hiérarchie des paramètres suit également cet ordre, de la plus élevée à la plus faible. Les composants Clusters Big Data prennent la valeur du paramètre défini avec la portée la plus faible. Un paramètre dont la portée n’est pas définie hérite de la valeur de la portée parente supérieure.

Supposons par exemple que vous définissiez le nombre de cœurs par défaut utilisé par le pilote Spark dans les `resources` du pool de stockage et de Sparkhead. Il existe deux méthodes pour le faire : 
- Spécifier une valeur de cœurs par défaut à la portée du service `Spark`  
- Spécifier une valeur de cœurs par défaut à la portée des ressources `storage-0` et `sparkhead`

Dans le premier scénario, toutes les ressources de portée inférieure du service Spark (pool de stockage et Sparkhead) *héritent* du nombre de cœurs par défaut de la valeur par défaut du service Spark.

Dans le second scénario, chaque ressource emploie la valeur définie comme sa propre portée.

Si le nombre de cœurs par défaut est configuré à la fois à la portée du service et à celle de la ressource, la valeur de portée ressource écrase celle de portée service, car il s’agit de la plus petite portée **configurée par l’utilisateur** pour le paramètre.

Pour obtenir des informations spécifiques sur la configuration, consultez les articles appropriés :

Procédure : 
- [Configurer l’instance maître de [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](configure-sql-server-master-instance.md)
- [Configurer Apache Spark et Apache Hadoop dans les clusters Big Data](configure-spark-hdfs.md)

Référence : 
- [Propriétés de configuration de l’instance maître SQL Server](reference-config-master-instance.md)
- [Propriétés de configuration d’Apache Spark et Apache Hadoop (HDFS)](reference-config-spark-hadoop.md)
