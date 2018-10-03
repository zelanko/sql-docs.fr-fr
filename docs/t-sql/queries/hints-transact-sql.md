---
title: Indicateurs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 68d93d1ab8e0c1b9f3592642763123491f9d90d1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47689627"
---
# <a name="hints-transact-sql"></a>Indicateurs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Les indicateurs sont des options ou des stratégies appliquées par le processeur de requêtes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aux instructions SELECT, INSERT, UPDATE ou DELETE. Les indicateurs remplacent tout plan d'exécution pouvant être sélectionné par l'optimiseur de requête pour une requête.  
  
> [!CAUTION]  
>  Étant donné que l’optimiseur de requête [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sélectionne généralement le meilleur plan d’exécution pour une requête, nous vous recommandons d’utiliser les indicateurs \<join_hint>, \<query_hint> et \<table_hint> uniquement en dernier recours et si vous êtes un administrateur de base de données ou un développeur expérimenté.
  
 Les indicateurs décrits dans cette section sont les suivants :  
  
-   [Indicateurs de jointure](../../t-sql/queries/hints-transact-sql-join.md)  
  
-   [Indicateurs de requête](../../t-sql/queries/hints-transact-sql-query.md)  
  
-   [Indicateur de table](../../t-sql/queries/hints-transact-sql-table.md)  
  
  
