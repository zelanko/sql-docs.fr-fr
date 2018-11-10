---
title: Qu’est un pool de calcul de clusters SQL données volumineuses ? | Microsoft Docs
description: Cet article décrit le pool de calcul dans un cluster de données volumineux de SQL Server 2019.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 6aa73c5881a4b6a17e190c26c15f97b3d8c79c14
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221795"
---
# <a name="what-is-a-sql-big-data-clusters-compute-pool"></a>Qu’est un pool de calcul de clusters SQL données volumineuses ?

Cet article décrit le rôle de *pools de calcul de SQL Server* dans un cluster de données volumineuses preview SQL Server 2019. Les pools de calcul fournissent la montée en puissance des ressources de calcul pour un cluster de données volumineux. Les sections suivantes décrivent l’architecture et les fonctionnalités d’un pool de calcul.

## <a name="compute-pool-architecture"></a>Architecture de pool de calcul

Un pool de calcul est constitué d’un ou plusieurs pods en cours d’exécution dans Kubernetes de calcul. La création automatique et la gestion de ces blocs est coordonnée par le [instance principale de SQL Server](concept-master-instance.md). Chaque pod contient un ensemble de services de base et une instance du moteur de base de données SQL Server.

> [!NOTE]
> CTP 2.1 prend uniquement en charge un pool de calcul unique par cluster.

## <a name="scale-out-groups"></a>Groupes de scale-out

Un pool de calcul peut agir comme un groupe de scale-out PolyBase pour les requêtes distribuées sur différentes sources de données--comme HDFS, Oracle, MongoDB ou Terradata. À l’aide de calcul des pods dans Kubernetes, les clusters de données volumineuses peuvent automatiser la création et configuration pods de calcul pour les groupes de scale-out PolyBase.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters de données volumineuses de SQL Server, consultez la présentation suivante :

- [Quelles sont les clusters SQL Server 2019 big data ?](big-data-cluster-overview.md)
