---
title: MSSQLSERVER_10519 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3bb5075ef33ced9cac22a6c92d9068907ca2ec01
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47790927"
---
# <a name="mssqlserver10519"></a>MSSQLSERVER_10519
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10519|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_INCOMPATIBLE_STMT_AND_HINTS|  
|Texte du message|Impossible de créer le repère de plan '%.\*ls', car les indicateurs spécifiés dans **@hints** ne peuvent pas être appliqués à l’instruction spécifiée par **@stmt** ou **@statement_start_offset**. Vérifiez que les indicateurs peuvent être appliqués à l'instruction.|  
  
## <a name="explanation"></a>Explication  
Les indicateurs spécifiés dans **@hints** ne peuvent pas être appliqués à l’instruction spécifiée par **@stmt** ou **@statement_start_offset**.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Spécifiez des indicateurs qui peuvent être appliqués à l'instruction.  
  
## <a name="see-also"></a> Voir aussi  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
