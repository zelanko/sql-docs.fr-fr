---
title: Présentation des pools de calcul
titleSuffix: SQL Server big data clusters
description: Cet article décrit le pool de calcul dans un [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 420c4705d86eb55b6b99a6cf432cb95f3b9a6694
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798235"
---
# <a name="what-are-compute-pools-in-a-sql-server-big-data-cluster"></a>Présentation des pools de calcul dans un cluster Big Data SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit le rôle des *pools de calcul SQL Server* dans un cluster Big Data SQL Server 2019 (préversion). Les pools de calcul fournissent des ressources de calcul de scale-out pour les clusters Big Data. Les sections suivantes décrivent l’architecture et les fonctionnalités d’un pool de calcul.

## <a name="compute-pool-architecture"></a>Architecture d’un pool de calcul

Un pool de calcul est constitué d’un ou de plusieurs pods de calcul exécutés dans Kubernetes. La création et la gestion automatisées de ces pods sont coordonnées par l’[instance maître de SQL Server](concept-master-instance.md). Chaque pod contient un ensemble de services de base, ainsi qu’une instance du moteur de base de données SQL Server.

## <a name="scale-out-groups"></a>Groupes de scale-out

Un pool de calcul peut agir en tant que groupe de montée en puissance parallèle Polybase pour les requêtes distribuées sur différentes sources de données, telles que HDFS, Oracle, MongoDB ou Teradata. En utilisant des pods de calcul dans Kubernetes, les clusters Big Data peuvent automatiser la création et la configuration de pods de calcul pour les groupes de scale-out PolyBase.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur le [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], consultez les ressources suivantes :

- [Qu’est-ce que [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Atelier : architecture de Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
