---
title: MSdistribution_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdistribution_status_TSQL
- MSdistribution_status
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistribution_status view
ms.assetid: 90d447de-3a4a-4f3e-aeab-e8fff6348361
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5942bf485673ad484a58edc43176da4ae5c95965
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52756722"
---
# <a name="msdistributionstatus-transact-sql"></a>MSdistribution_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSdistribution_status** vue expose des informations supplémentaires sur les commandes d’état dans la base de données de distribution. Cette vue est stockée dans la base de données de distribution.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**article_id**|**Int**|Identifie un article.|  
|**agent_id**|**Int**|Identifie un Agent de réplication.|  
|**UndelivCmdsInDistDB**|**Int**|Nombre de commandes en attente de remise aux Abonnés.|  
|**DelivCmdsInDistDB**|**Int**|Nombre de commandes remises aux Abonnés.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
