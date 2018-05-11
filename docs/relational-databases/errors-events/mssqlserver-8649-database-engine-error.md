---
title: MSSQLSERVER_8649 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e87c496b60ce000ec148b79e7556a5cd15edfcdf
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver8649"></a>MSSQLSERVER_8649
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|8649|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|COST_TOO_HIGH|  
|Texte du message|La requête a été annulée parce que son coût estimé (%d) est supérieur au seuil configuré, %d. Contactez l'administrateur système.|  
  
## <a name="explanation"></a>Explication  
La requête a été annulée parce que son coût estimé est supérieur au seuil configuré pour QUERY_GOVERNOR_COST_LIMIT.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Spécifiez une valeur supérieure pour l'option QUERY_GOVERNOR_COST_LIMIT.  
  
## <a name="see-also"></a> Voir aussi  
[SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](~/t-sql/statements/set-query-governor-cost-limit-transact-sql.md)  
  
