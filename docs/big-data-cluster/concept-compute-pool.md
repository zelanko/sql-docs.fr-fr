---
title: Présentation des pools de calcul
titleSuffix: SQL Server big data clusters
description: Cet article décrit le pool de calcul dans un [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f6f2813dff5e965f61f15b947725d78bf327dde7
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532396"
---
# <a name="what-are-compute-pools-in-a-sql-server-big-data-cluster"></a>Présentation des pools de calcul dans un cluster Big Data SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit le rôle des *pools de calcul SQL Server* dans un cluster Big Data SQL Server. Les pools de calcul fournissent des ressources de calcul de scale-out pour les clusters Big Data. Les sections suivantes décrivent l’architecture et les fonctionnalités d’un pool de calcul.

## <a name="compute-pool-architecture"></a>Architecture d’un pool de calcul

Un pool de calcul est constitué d’un ou de plusieurs pods de calcul exécutés dans Kubernetes. La création et la gestion automatisées de ces pods sont coordonnées par l’[instance maître de SQL Server](concept-master-instance.md). Chaque pod contient un ensemble de services de base, ainsi qu’une instance du moteur de base de données SQL Server.

## <a name="scale-out-groups"></a>Groupes de scale-out

Un pool de calcul peut servir de groupe de scale-out PolyBase pour les requêtes distribuées sur différentes sources de données comme HDFS, Oracle, MongoDB ou Teradata. En utilisant des pods de calcul dans Kubernetes, les clusters Big Data peuvent automatiser la création et la configuration de pods de calcul pour les groupes de scale-out PolyBase.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], consultez les ressources suivantes :

- [Présentation des [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](big-data-cluster-overview.md)
- [Atelier : Architecture des [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Microsoft](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
