---
title: Qu’est un pool de données de clusters SQL données volumineuses ? | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 3a75f47148ff59d58d0d0d1397ba445b064c028f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796030"
---
# <a name="what-is-a-sql-big-data-clusters-data-pool"></a>Qu’est un pool de données de clusters SQL données volumineuses ?

Cet article décrit le rôle de *pools de données SQL Server* un 2019 de serveur SQL preview cluster Big Data. Les sections suivantes décrivent l’architecture et les fonctionnalités d’un pool de données SQL.

## <a name="data-pool-architecture"></a>Architecture de pool de données

Un pool de données se compose d’une ou plusieurs instances de pool de données SQL Server. Instances de pool de données SQL fournissent un stockage persistant de SQL Server pour le cluster. Un pool de données est utilisé pour recevoir les données à partir de requêtes SQL ou de travaux Spark. Pour offrir de meilleures performances sur grands jeux de données, les données dans un pool de données sont réparties dans les partitions entre les instances de pool de données membre SQL.

## <a name="scale-out-data-marts"></a>Montée en puissance datamarts

Les pools de données permettent la création de montée en puissance datamarts, où les données externes à partir de plusieurs sources sont ingérées dans le pool de données. Étant donné que les données sont réparties sur les instances de pool de données, les requêtes parallèles sur les données organisées sont plus efficaces.

![Montée en puissance Datamart](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters de données volumineuses de SQL Server, consultez la présentation suivante :

- [Qu’est SQL Server 2019 des clusters de données volumineuses ?](big-data-cluster-overview.md)
