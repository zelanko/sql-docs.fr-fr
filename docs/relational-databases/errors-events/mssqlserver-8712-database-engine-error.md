---
title: MSSQLSERVER_8712 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
caps.latest.revision: "12"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: c8d97513694a8f1b0559dbd029a6f9f3bed91cf5
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver8712"></a>MSSQLSERVER_8712
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|8712|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|USEPLAN_ERR_NO_INDEX|  
|Texte du message|L'index '%.*ls' spécifié dans l'indicateur USE PLAN n'existe pas. Indiquez un index existant ou créez-en un avec le nom spécifié.|  
  
## <a name="explanation"></a>Explication  
Un index spécifié dans l'indicateur USE PLAN n'existe pas.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Veillez à ce que tous les index spécifiés dans l'indicateur USE PLAN existent.  
  
## <a name="see-also"></a>Voir aussi  
[Indicateurs de requête &#40;Transact-SQL&#41;](~/t-sql/queries/hints-transact-sql-query.md)  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
  
