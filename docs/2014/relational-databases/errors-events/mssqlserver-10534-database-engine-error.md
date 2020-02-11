---
title: MSSQLSERVER_10534 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10534 (Database Engine error)
ms.assetid: e65bb118-99d5-4fdb-b1d5-0ec70f0a677b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a9a20d1003e8b87179e2690fa35ad44b50894568
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62870578"
---
# <a name="mssqlserver_10534"></a>MSSQLSERVER_10534
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|10534|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_INVALID_PARAMS|  
|Texte du message|Impossible de créer le repère de plan '%.\*ls', car la valeur spécifiée pour `@params` n’est pas valide. Indiquez la valeur sous la forme *nom_paramètre type_paramètre* ou spécifiez Null.|  
  
## <a name="explanation"></a>Explication  
 La valeur spécifiée pour `@params` n'est pas valide.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Indiquez la valeur sous la forme *nom_paramètre type_paramètre* ou spécifiez Null.  
  
## <a name="see-also"></a>Voir aussi  
 [Repères de plan](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
