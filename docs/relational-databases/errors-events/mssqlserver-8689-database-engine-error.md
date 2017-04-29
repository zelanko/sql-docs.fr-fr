---
title: MSSQLSERVER_8689 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e6de76f8ef1fe370e8dc1361631b6776440ea172
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver8689"></a>MSSQLSERVER_8689
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|8689|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|USEPLAN_ERR_NO_DB|  
|Texte du message|La base de données '%.*ls' spécifiée dans l'indicateur USE PLAN n'existe pas. Indiquez une base de données existante.|  
  
## <a name="explanation"></a>Explication  
Une base de données spécifiée dans l'indicateur USE PLAN n'existe pas.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Veillez à ce que toutes les bases de données spécifiées dans l'indicateur USE PLAN existent.  
  
## <a name="see-also"></a>Voir aussi  
[Indicateurs de requête &#40;Transact-SQL&#41;](~/t-sql/queries/hints-transact-sql-query.md)  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
  

