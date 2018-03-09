---
title: MSSQLSERVER_10507 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 10507 (Database Engine error)
ms.assetid: cd83fa81-ac37-4eda-a3c3-17610b051de2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3bad7ac89e53fb1de9c814cc64618f966e328b66
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver10507"></a>MSSQLSERVER_10507
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10507|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_STMT_DOES_NOT_MATCH|  
|Texte du message|Impossible de créer le repère de plan '%.\*ls', car l’instruction spécifiée par **@stmt** et **@module_or_batch** ou par **@plan_handle** et **@statement_start_offset** ne correspond à aucune instruction dans le module ou lot spécifié. Modifiez les valeurs pour qu'elles correspondent à une instruction dans le module ou le lot.|  
  
## <a name="explanation"></a>Explication  
Une instruction dans le module ou le lot spécifié n'a pas pu être mise en correspondance avec l'instruction ou la valeur de décalage de l'instruction spécifiée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Modifiez les valeurs de paramètre spécifiées pour qu'elles correspondent à une instruction dans le module ou le lot.  
  
## <a name="see-also"></a>Voir aussi  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
