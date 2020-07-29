---
title: Qu’est-ce que le pool de stockage ?
titleSuffix: SQL Server big data clusters
description: Cet article décrit le pool de stockage dans un cluster Big Data SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d7a9d3e9e16eb923e0954154b46362cdc88c0bff
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730690"
---
# <a name="what-is-the-storage-pool-big-data-clusters-2019"></a>Qu’est-ce que le pool de stockage ([!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]) ?

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Cet article décrit le rôle du *pool de stockage SQL Server* dans un [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. Les sections suivantes décrivent l’architecture et les fonctionnalités d’un pool de stockage SQL.

## <a name="storage-pool-architecture"></a>Architecture du pool de stockage

Le pool de stockage est constitué de nœuds de stockage constitués de SQL Server sur Linux, Spark et HDFS. Tous les nœuds de stockage d’un cluster Big Data SQL sont membres d’un cluster HDFS.

![Architecture du pool de stockage](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Responsabilités

Les nœuds de stockage sont responsables des opérations suivantes :

- Ingestion des données par le biais de Spark.
- Stockage des données dans HDFS (format Parquet et texte délimité). HDFS assure également la persistance des données, car les données HDFS sont réparties sur tous les nœuds de stockage du cluster Big Data SQL.
- Accès aux données par le biais des points de terminaison HDFS et SQL Server.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], consultez les ressources suivantes :

- [Que sont les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] ?](big-data-cluster-overview.md)
- [Atelier : Architecture des [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Microsoft](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
