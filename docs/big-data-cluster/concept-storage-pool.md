---
title: Qu’est-ce que le pool de stockage ?
titleSuffix: SQL Server big data clusters
description: Cet article décrit le pool de stockage dans un cluster Big Data SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 58e6f16a088d6dc6c1fc6bd32297e7bd698acbbf
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958659"
---
# <a name="what-is-the-storage-pool-sql-server-big-data-clusters"></a>Qu’est-ce que le pool de stockage (clusters Big Data SQL Server) ?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit le rôle du *pool de stockage SQL Server* dans un cluster Big Data SQL Server 2019 (préversion). Les sections suivantes décrivent l’architecture et les fonctionnalités d’un pool de stockage SQL.

## <a name="storage-pool-architecture"></a>Architecture du pool de stockage

Le pool de stockage est constitué de nœuds de stockage constitués de SQL Server sur Linux, Spark et HDFS. Tous les nœuds de stockage d’un cluster Big Data SQL sont membres d’un cluster HDFS.

![Architecture du pool de stockage](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Responsabilités

Les nœuds de stockage sont responsables des opérations suivantes :

- Ingestion des données par le biais de Spark.
- Stockage des données dans HDFS (format Parquet). HDFS assure également la persistance des données, car les données HDFS sont réparties sur tous les nœuds de stockage du cluster Big Data SQL.
- Accès aux données par le biais des points de terminaison HDFS et SQL Server.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters Big Data SQL Server, consultez les ressources suivantes :

- [Présentation des clusters Big Data SQL Server 2019](big-data-cluster-overview.md)
- [Atelier : Architecture des clusters Big Data Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
