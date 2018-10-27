---
title: Qu’est le pool de stockage de clusters SQL Server données volumineuses ? | Microsoft Docs
description: Cet article décrit le pool de stockage dans un cluster de données volumineux de SQL Server 2019.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: cbf9ff14ece1b33e1c271786bc96f0ac590b807e
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050751"
---
# <a name="what-is-the-sql-server-big-data-clusters-storage-pool"></a>Qu’est le pool de stockage de clusters SQL Server données volumineuses ?

Cet article décrit le rôle de la *pool de stockage de SQL Server* dans un cluster de données volumineuses preview SQL Server 2019. Les sections suivantes décrivent l’architecture et les fonctionnalités d’un pool de stockage SQL.

## <a name="storage-pool-architecture"></a>Architecture du pool de stockage

Le pool de stockage se compose de stockage composés de nœuds de SQL Server sur Linux, Spark et HDFS. Tous les nœuds de stockage dans un cluster de données SQL sont membres d’un cluster HDFS.

![Architecture du pool de stockage](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Responsabilités

Nœuds de stockage sont responsables :

- Ingestion des données via Spark.
- Stockage des données dans HDFS (format Parquet). HDFS fournit également une persistance de données, comme les données HDFS sont réparties sur tous les nœuds de stockage dans le cluster de données SQL.
- Accès de données via les points de terminaison HDFS et SQL Server.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters de données volumineuses de SQL Server, consultez la présentation suivante :

- [Quelles sont les clusters SQL Server 2019 big data ?](big-data-cluster-overview.md)
