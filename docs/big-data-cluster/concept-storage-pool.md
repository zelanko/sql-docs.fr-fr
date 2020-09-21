---
title: Qu’est-ce que le pool de stockage ?
titleSuffix: SQL Server big data clusters
description: Découvrez le rôle du pool de stockage SQL Server dans un cluster Big Data SQL Server 2019, ainsi que l’architecture et les fonctionnalités d’un pool de stockage SQL.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: fd7a38d555cbf6e2f64743f0907fbfbbdec4d41f
ms.sourcegitcommit: 6f49804b863fed44968ea5829e2c26edc5988468
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87806455"
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
