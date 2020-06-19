---
title: MSSQLSERVER_10537 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10537 (Database Engine error)
ms.assetid: 728469a4-6523-4a37-925f-a950d75420fa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b1baccad5236bd8c1a71024b7dd542cc9d11cbd7
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969779"
---
# <a name="mssqlserver_10537"></a>MSSQLSERVER_10537
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|10537|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_DUP_ENABLED|  
|Texte du message|Impossible d’activer le repère de plan '%.*ls', car le repère de plan activé '%.\*ls' contient les mêmes étendue et valeur de décalage de départ que l’instruction. Désactivez le repère de plan existant avant d'activer le repère de plan spécifié.|  
  
## <a name="explanation"></a>Explication  
 Un repère de plan existant contient les mêmes étendue et valeur de décalage de départ que l'instruction du repère de plan spécifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Désactivez le repère de plan existant avant d'activer le repère de plan spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Repères de plan](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
