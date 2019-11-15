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
ms.openlocfilehash: 114296d0bad77c3bbbb088feed13bd6a4bd5a074
ms.sourcegitcommit: 594cee116fa4ee321e1f5e5206f4a94d408f1576
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "70009331"
---
# <a name="what-is-the-storage-pool-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Qu’est-ce que le pool de stockage ([!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]) ?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

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

- [Présentation des [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](big-data-cluster-overview.md)
- [Atelier : Architecture des [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Microsoft](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
