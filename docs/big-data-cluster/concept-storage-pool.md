---
title: Qu’est le pool de stockage de clusters SQL Server données volumineuses ? | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 100ce09f7066a6df33d7b1daaf50db50bda4ed03
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796040"
---
# <a name="what-is-the-sql-server-big-data-clusters-storage-pool"></a>Qu’est le pool de stockage de clusters SQL Server données volumineuses ?

Cet article décrit le rôle de la *pool de stockage de SQL Server* un 2019 de serveur SQL preview cluster Big Data. Les sections suivantes décrivent l’architecture et les fonctionnalités d’un pool de stockage SQL.

## <a name="storage-pool-architecture"></a>Architecture du pool de stockage

Le pool de stockage se compose de stockage composés de nœuds de SQL Server sur Linux, Spark et HDFS. Tous les nœuds de stockage dans un cluster SQL Big Data sont membres d’un cluster HDFS.

![Architecture du pool de stockage](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Responsabilités

Nœuds de stockage sont responsables :

- Ingestion des données via Spark.
- Stockage des données dans HDFS (format Parquet). HDFS fournit également une persistance de données, comme les données HDFS sont réparties sur tous les nœuds de stockage dans le cluster SQL Big Data.
- Accès de données via les points de terminaison HDFS et SQL Server.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters de données volumineuses de SQL Server, consultez la présentation suivante :

- [Qu’est SQL Server 2019 des clusters de données volumineuses ?](big-data-cluster-overview.md)
