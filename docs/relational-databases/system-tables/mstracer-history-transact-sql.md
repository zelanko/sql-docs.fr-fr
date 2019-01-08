---
title: MStracer_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MStracer_history
- MStracer_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MStracer_history system table
ms.assetid: 97237a0c-d574-4b17-8a94-1a8730b31d98
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b1ba25e4f55debbe73a66de23986743a83d1feb5
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52765261"
---
# <a name="mstracerhistory-transact-sql"></a>MStracer_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MStracer_history** table conserve un enregistrement de tous les jetons de suivi qui ont été reçus sur l’abonné. Cette table est stockée dans la base de données de distribution et sert au moment de la réplication à l'analyse des performances.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**parent_tracer_id**|**Int**|Identifie de manière unique un jeton de suivi.|  
|**agent_id**|**Int**|Identifie l'Agent qui a géré l'enregistrement du jeton de suivi.|  
|**subscriber_commit**|**datetime**|Date et heure auxquelles l'enregistrement du jeton de suivi a été validé sur l'Abonné.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
