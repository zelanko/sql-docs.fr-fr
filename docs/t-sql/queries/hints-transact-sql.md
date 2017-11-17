---
title: Indicateurs (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- query optimizer [SQL Server], hints
- hints [SQL Server], about hints
- SELECT statement [SQL Server], hints
- hints [SQL Server]
- INSERT statement [SQL Server], hints
- UPDATE statement [SQL Server], hints
- DELETE statement [SQL Server], hints
ms.assetid: 99412475-b0df-4264-9938-33a0b302b41a
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d2d8b50a38299162677b1f7d5bbff501fba9881
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="hints-transact-sql"></a>Indicateurs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Les indicateurs sont des options ou des stratégies appliquées par le processeur de requêtes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aux instructions SELECT, INSERT, UPDATE ou DELETE. Les indicateurs remplacent tout plan d'exécution pouvant être sélectionné par l'optimiseur de requête pour une requête.  
  
> [!CAUTION]  
>  Étant donné que la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] optimiseur de requête sélectionne généralement le meilleur plan d’exécution pour une requête, nous vous recommandons \<indicateurs join_hint >, \<query_hint >, et \<indicateur de table > être utilisé qu’en dernier recours par les développeurs expérimentés et aux administrateurs de base de données.
  
 Les indicateurs décrits dans cette section sont les suivants :  
  
-   [Indicateurs de jointure](../../t-sql/queries/hints-transact-sql-join.md)  
  
-   [Indicateurs de requête](../../t-sql/queries/hints-transact-sql-query.md)  
  
-   [Indicateur de table](../../t-sql/queries/hints-transact-sql-table.md)  
  
  

