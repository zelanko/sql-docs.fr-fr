---
title: Présentation des pools de données
titleSuffix: SQL Server big data clusters
description: Cet article décrit le pool de données dans un cluster Big Data SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bfd4d9d6ca24599a2297799555f53a83c6601420
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652263"
---
# <a name="what-are-data-pools-in-a-sql-server-big-data-cluster"></a>Présentation des pools de données dans un cluster Big Data SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit le rôle des *pools de données SQL Server* dans un [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. Les sections suivantes décrivent l’architecture et les fonctionnalités d’un pool de données SQL.

## <a name="data-pool-architecture"></a>Architecture du pool de données

Un pool de données se compose d’une ou plusieurs instances de pool de données SQL Server. Les instances de pool de données SQL assurent un stockage SQL Server persistant pour le cluster. Un pool de données est utilisé pour l’ingestion des données à partir de requêtes SQL ou de travaux Spark. Pour améliorer les performances dans des jeux de données volumineux, les données d’un pool de données sont réparties en partitions sur les instances de pools de données SQL membres.

## <a name="scale-out-data-marts"></a>DataMart avec scale-out

Les pools de données permettent de créer des DataMarts avec scale-out où les données externes de plusieurs sources sont ingérées dans le pool de données. Les données étant réparties entre plusieurs instances du pool de données, les requêtes parallèles sur les données organisées sont plus efficaces.

![DataMart avec scale-out](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]le, consultez les ressources suivantes:

- [Que sont [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Atelier : Architecture [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Microsoft](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
