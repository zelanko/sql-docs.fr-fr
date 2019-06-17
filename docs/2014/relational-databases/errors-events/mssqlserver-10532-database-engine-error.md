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
manager: craigg
ms.openlocfilehash: cda3117df524ba90f322bbb99d6db98ee989ab71
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62870628"
---
# <a name="mssqlserver10532"></a>MSSQLSERVER_10532
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10532|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_NO_ELIGIBLE_STMT|  
|Texte du message|Impossible de créer le repère de plan ' %. \*%.*ls, car le module ou lot spécifié par `@plan_handle` ne contient pas d’instruction éligible pour un repère de plan. Indiquez une autre valeur pour `@plan_handle`.|  
  
## <a name="explanation"></a>Explication  
 Le module ou lot spécifié par `@plan_handle` ne contient pas d'instruction éligible pour un repère de plan.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Indiquez une autre valeur pour `@plan_handle`.  
  
## <a name="see-also"></a>Voir aussi  
 [Repères de plan](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
