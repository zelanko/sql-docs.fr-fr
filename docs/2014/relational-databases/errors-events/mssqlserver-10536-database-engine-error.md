---
title: MSSQLSERVER_10536 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 00ca6874fc2b46c1b01495c5c7a0808265b0dd77
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428948"
---
# <a name="mssqlserver10536"></a>MSSQLSERVER_10536
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10536|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_TOO_MANY_STMTS|  
|Texte du message|Impossible de créer le repère de plan ' %. \*%.*ls, car le lot ou module correspondant spécifié `@plan_handle` contient plus de 1000 instructions éligibles. Créez un repère de plan pour chaque instruction du lot ou module en indiquant une valeur `statement_start_offset` pour chacune.|  
  
## <a name="explanation"></a>Explication  
 Le lot ou module correspondant au `@plan_handle` spécifié contient plus de 1 000 instructions éligibles.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Créez un repère de plan pour chaque instruction du lot ou module en indiquant une valeur `statement_start_offset` pour chacune.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Repères de plan](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
