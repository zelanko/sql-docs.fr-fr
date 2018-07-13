---
title: MSSQLSERVER_10532 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: be808412900aed583450824dca873deea4697f40
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409477"
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
  
  
