---
title: MSSQLSERVER_10531 | Microsoft Docs
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
- 10531 (Database Engine error)
ms.assetid: bb40e994-231c-44ce-933f-8d767fb2f450
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: accc628e1001adec68fa504f30d87c682e8d9121
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver10531"></a>MSSQLSERVER_10531
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10531|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_NO_ELIGIBLE_STMT|  
|Texte du message|Impossible de créer le repère de plan '%.*ls' à partir du cache, car l'utilisateur ne dispose pas des autorisations nécessaires. Accordez l'autorisation VIEW SERVER STATE à l'utilisateur qui crée le repère de plan.|  
  
## <a name="explanation"></a>Explication  
L'utilisateur ne dispose pas des autorisations adéquates pour créer le repère de plan spécifié à partir du cache du plan.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Accordez l’autorisation VIEW SERVER STATE à l’utilisateur qui crée le repère de plan.  
  
## <a name="see-also"></a>Voir aussi  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  

