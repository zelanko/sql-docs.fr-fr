---
title: Quelles sont les pools de calcul ?
titleSuffix: SQL Server 2019 big data clusters
description: Cet article décrit le pool de calcul dans un cluster de données volumineuses de SQL Server 2019 (version préliminaire).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 272f10cfed8f7cd1b07633b81642323a8c74b6d7
ms.sourcegitcommit: 56fb7b648adae2c7b81bd969de067af1a2b54180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57227131"
---
# <a name="what-are-compute-pools-in-a-sql-server-2019-big-data-cluster"></a>Quelles sont les pools de calcul dans un cluster de données volumineux de SQL Server 2019 ?

Cet article décrit le rôle de *pools de calcul de SQL Server* dans un cluster de données volumineuses preview SQL Server 2019. Les pools de calcul fournissent la montée en puissance des ressources de calcul pour un cluster de données volumineux. Les sections suivantes décrivent l’architecture et les fonctionnalités d’un pool de calcul.

## <a name="compute-pool-architecture"></a>Architecture de pool de calcul

Un pool de calcul est constitué d’un ou plusieurs pods en cours d’exécution dans Kubernetes de calcul. La création automatique et la gestion de ces blocs est coordonnée par le [instance principale de SQL Server](concept-master-instance.md). Chaque pod contient un ensemble de services de base et une instance du moteur de base de données SQL Server.

## <a name="scale-out-groups"></a>Groupes de scale-out

Un pool de calcul peut agir comme un groupe de scale-out PolyBase pour les requêtes distribuées sur différentes sources de données--comme HDFS, Oracle, MongoDB ou Terradata. À l’aide de calcul des pods dans Kubernetes, les clusters de données volumineuses peuvent automatiser la création et configuration pods de calcul pour les groupes de scale-out PolyBase.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters de données volumineuses de SQL Server, consultez la présentation suivante :

- [Quelles sont les clusters SQL Server 2019 big data ?](big-data-cluster-overview.md)
