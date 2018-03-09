---
title: MSsub_identity_range (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSsub_identity_range_TSQL
- MSsub_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSsub_identity_range system table
ms.assetid: 26e20d28-14ed-44fc-af3b-4de386de4bb8
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06417c00191ad2a3002481c3b167e7305765acfd
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssubidentityrange-transact-sql"></a>MSsub_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSsub_identity_range** table fournit la prise en charge de gestion de plage identité pour les abonnements. Cette table est stockée dans la base de données d'abonnement.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**ID d’objet**|**int**|ID de la table dont la colonne d'identité est gérée par la réplication.|  
|**plage**|**bigint**|Contrôle la taille de la plage des valeurs d'identité consécutives qui seraient attribuées à l'abonné dans un ajustement.|  
|**last_seed**|**bigint**|Limite inférieure de la plage actuelle.|  
|**seuil**|**int**|Valeur de pourcentage qui contrôle le moment où l'Agent de distribution affecte une nouvelle plage d'identité. Lorsque le pourcentage de valeurs spécifié dans *seuil* est utilisé, l’Agent de Distribution crée une nouvelle plage d’identité.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
