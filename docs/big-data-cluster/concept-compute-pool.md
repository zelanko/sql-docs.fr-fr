---
title: Qu’est un pool de calcul de clusters SQL données volumineuses ? | Microsoft Docs
description: Cet article décrit le pool de calcul dans un cluster de données volumineux de SQL Server 2019.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 67f13687bf55a9e267582a0749043c51d2e2b3bf
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050793"
---
# <a name="what-is-a-sql-big-data-clusters-compute-pool"></a>Qu’est un pool de calcul de clusters SQL données volumineuses ?

Cet article décrit le rôle de *pools de calcul de SQL Server* dans un cluster de données volumineuses preview SQL Server 2019. Les pools de calcul fournissent la montée en puissance des ressources de calcul pour un cluster de données volumineux. Les sections suivantes décrivent l’architecture et les fonctionnalités d’un pool de calcul.

## <a name="compute-pool-architecture"></a>Architecture de pool de calcul

Un pool de calcul est constitué d’un ou plusieurs pods en cours d’exécution dans Kubernetes de calcul. La création automatique et la gestion de ces blocs est coordonnée par le [instance principale de SQL Server](concept-master-instance.md). Chaque pod contient un ensemble de services de base et une instance du moteur de base de données SQL Server.

> [!NOTE]
> CTP 2.0 prend uniquement en charge un pool de calcul unique par cluster.

## <a name="scale-out-groups"></a>Groupes de scale-out

Un pool de calcul peut agir comme un groupe de scale-out PolyBase pour les requêtes distribuées sur différentes sources de données--comme HDFS, Oracle, MongoDB ou Terradata. À l’aide de calcul des pods dans Kubernetes, les clusters de données volumineuses peuvent automatiser la création et configuration pods de calcul pour les groupes de scale-out PolyBase.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters de données volumineuses de SQL Server, consultez la présentation suivante :

- [Quelles sont les clusters SQL Server 2019 big data ?](big-data-cluster-overview.md)
