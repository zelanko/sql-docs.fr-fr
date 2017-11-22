---
title: MSSQLSERVER_10538 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 10538 (Database Engine error)
ms.assetid: 284d19b4-4979-4cbe-a9be-ac1104433c69
caps.latest.revision: "10"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c93dfdc81a37d06e6da2d1f1d2329ac378893090
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver10538"></a>MSSQLSERVER_10538
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10538|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_INVALID_PLANGUIDE_HANDLE|  
|Texte du message|Impossible de trouver le repère de plan, car l'ID du repère de plan spécifié a la valeur Null ou n'est pas valide, ou vous n'avez pas d'autorisation sur l'objet référencé par le repère de plan. Vérifiez que l’ID du repère de plan est valide, que la session active est définie en fonction du contexte de base de données approprié et que vous disposez de l’autorisation ALTER ou de l’autorisation ALTER DATABASE sur l’objet référencé par le repère de plan.|  
  
## <a name="explanation"></a>Explication  
L'ID du repère de plan spécifié est Null ou n'est pas valide, ou vous n'avez pas d'autorisation sur l'objet référencé par le repère de plan.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Vérifiez que l'ID du repère de plan est valide, que la session active est définie en fonction du contexte de base de données approprié et que vous disposez de l'autorisation ALTER ou de l'autorisation ALTER DATABASE sur l'objet référencé par le repère de plan.  
  
## <a name="see-also"></a>Voir aussi  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
