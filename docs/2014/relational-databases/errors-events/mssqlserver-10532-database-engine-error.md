---
title: MSSQLSERVER_10532 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0c92e077135491a87687fbb765affc4642e064ea
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554144"
---
# <a name="mssqlserver_10532"></a>MSSQLSERVER_10532
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|10532|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_NO_ELIGIBLE_STMT|  
|Texte du message|Impossible de créer le repère de plan ’%.\*ls’, car le module ou lot spécifié par `@plan_handle` ne contient pas d’instruction éligible pour un repère de plan. Indiquez une autre valeur pour `@plan_handle`.|  
  
## <a name="explanation"></a>Explication  
 Le module ou lot spécifié par `@plan_handle` ne contient pas d'instruction éligible pour un repère de plan.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Indiquez une autre valeur pour `@plan_handle`.  
  
## <a name="see-also"></a>Voir aussi  
 [Repères de plan](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
