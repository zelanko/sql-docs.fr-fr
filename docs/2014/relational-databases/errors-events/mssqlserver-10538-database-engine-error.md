---
title: MSSQLSERVER_10538 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10538 (Database Engine error)
ms.assetid: 284d19b4-4979-4cbe-a9be-ac1104433c69
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aa6bce659e20fb80f013539049cc1b99e3e0b4c1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62870644"
---
# <a name="mssqlserver_10538"></a>MSSQLSERVER_10538
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|10538|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_INVALID_PLANGUIDE_HANDLE|  
|Texte du message|Impossible de trouver le repère de plan, car l'ID du repère de plan spécifié a la valeur Null ou n'est pas valide, ou vous n'avez pas d'autorisation sur l'objet référencé par le repère de plan. Vérifiez que l’ID du repère de plan est valide, que la session active est définie en fonction du contexte de base de données approprié et que vous disposez de l’autorisation ALTER ou de l’autorisation ALTER DATABASE sur l’objet référencé par le repère de plan.|  
  
## <a name="explanation"></a>Explication  
 L'ID du repère de plan spécifié est Null ou n'est pas valide, ou vous n'avez pas d'autorisation sur l'objet référencé par le repère de plan.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez que l'ID du repère de plan est valide, que la session active est définie en fonction du contexte de base de données approprié et que vous disposez de l'autorisation ALTER ou de l'autorisation ALTER DATABASE sur l'objet référencé par le repère de plan.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Repères de plan](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
