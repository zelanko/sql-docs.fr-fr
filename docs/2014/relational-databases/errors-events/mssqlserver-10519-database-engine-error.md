---
title: MSSQLSERVER_10519 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0ec584649842f787b1de9d2ea6d161aea6970250
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84947769"
---
# <a name="mssqlserver_10519"></a>MSSQLSERVER_10519
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|10519|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_INCOMPATIBLE_STMT_AND_HINTS|  
|Texte du message|Impossible de créer le repère de plan '%.\*ls', car les indicateurs spécifiés dans `@hints` ne peuvent pas être appliqués à l’instruction spécifiée par `@stmt` ou `@statement_start_offset`. Vérifiez que les indicateurs peuvent être appliqués à l'instruction.|  
  
## <a name="explanation"></a>Explication  
 Les indicateurs spécifiés dans `@hints` ne peuvent pas être appliqués à l'instruction spécifiée par `@stmt` ou `@statement_start_offset`.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Spécifiez des indicateurs qui peuvent être appliqués à l'instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Repères de plan](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
