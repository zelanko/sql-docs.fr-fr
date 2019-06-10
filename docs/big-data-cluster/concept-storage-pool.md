---
title: Qu’est le pool de stockage ?
titleSuffix: SQL Server big data clusters
description: Cet article décrit le pool de stockage dans un cluster de données volumineux de SQL Server 2019.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 7ff8b16ec5f1ea0d1df401cee9657eb8d564863a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66782988"
---
# <a name="what-is-the-storage-pool-sql-server-big-data-clusters"></a>Qu’est le pool de stockage (données volumineuses des clusters SQL Server) ?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit le rôle de la *pool de stockage de SQL Server* dans un cluster de données volumineuses de SQL Server 2019 (version préliminaire). Les sections suivantes décrivent l’architecture et les fonctionnalités d’un pool de stockage SQL.

## <a name="storage-pool-architecture"></a>Architecture du pool de stockage

Le pool de stockage se compose de stockage composés de nœuds de SQL Server sur Linux, Spark et HDFS. Tous les nœuds de stockage dans un cluster de données SQL sont membres d’un cluster HDFS.

![Architecture du pool de stockage](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Responsabilités

Nœuds de stockage sont responsables :

- Ingestion des données via Spark.
- Stockage des données dans HDFS (format Parquet). HDFS fournit également une persistance de données, comme les données HDFS sont réparties sur tous les nœuds de stockage dans le cluster de données SQL.
- Accès de données via les points de terminaison HDFS et SQL Server.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters de données volumineuses de SQL Server, consultez les ressources suivantes :

- [Quelles sont les clusters SQL Server 2019 big data ?](big-data-cluster-overview.md)
- [Atelier : Architecture de clusters de données volumineuses de Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
