---
title: Comparer et analyser des plans d’exécution | Microsoft Docs
ms.custom: ''
ms.date: 11/21/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan results
- execution plans [SQL Server]
- queries [SQL Server], tuning
- execution plans [SQL Server], how-to topics
- SQL Server Management Studio [SQL Server], execution plans
- tuning queries [SQL Server]
ms.assetid: bcd6f094-c613-4835-ae19-4caaadb4bb17
author: pmasl
ms.author: pelopes
manager: amitban
ms.openlocfilehash: 0b7a932f58fe791b6609b999f4495a42af88422d
ms.sourcegitcommit: ba7fb4b9b4f0dbfe77a7c6906a1fde574e5a8e1e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52303422"
---
# <a name="compare-and-analyze-execution-plans"></a>Comparer et analyser des plans d’exécution
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Cette section explique comment comparer et analyser des plans d’exécution à l’aide de Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
Les plans d’exécution affichent graphiquement les méthodes de récupération des données choisies par l’Optimiseur de requête de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les plans d’exécution représentent le coût d’exécution de requêtes et d’instructions spécifiques dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par des icônes plutôt que par la représentation tabulaire résultant des instructions [SET SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md) ou [SET SHOWPLAN_TEXT](../../t-sql/statements/set-showplan-text-transact-sql.md). Cette approche graphique s'avère très utile pour la compréhension des caractéristiques de performances d'une requête. 

[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] inclut une fonctionnalité qui permet aux utilisateurs de comparer deux plans d’exécution, par exemple des plans perçus comme bons et mauvais pour la même requête, et d’effectuer une analyse de la cause racine. Il comprend également une fonctionnalité pour effectuer une analyse de plan de requête unique, ce qui permet d’obtenir des insights concernant les scénarios susceptibles d’affecter les performances d’une requête grâce à l’analyse de son plan d’exécution.

Pour plus d’informations sur les plans d’exécution de requête, consultez [plan d’exécution estimé](../../relational-databases/performance/display-the-estimated-execution-plan.md), [plan d’exécution réel](../../relational-databases/performance/display-an-actual-execution-plan.md) et le [Guide d’architecture de traitement des requêtes](../../relational-databases/query-processing-architecture-guide.md).
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comparer des plans d’exécution](../../relational-databases/performance/display-the-estimated-execution-plan.md)  
  
-   [Analyser un plan d’exécution réel](../../relational-databases/performance/display-an-actual-execution-plan.md)  
  
  
