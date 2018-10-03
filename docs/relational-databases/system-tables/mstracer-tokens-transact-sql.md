---
title: MStracer_tokens (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MStracer_tokens_TSQL
- MStracer_tokens
dev_langs:
- TSQL
helpviewer_keywords:
- MStracer_tokens system table
ms.assetid: b273aa48-8188-4213-8e2c-311543c3236f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 55140e134876870179c0a13208e85ee55414ca8f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628933"
---
# <a name="mstracertokens-transact-sql"></a>MStracer_tokens (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MStracer_tokens** table conserve un enregistrement des enregistrements de jeton de suivi insérés dans une publication. Cette table est stockée dans la base de données de distribution et sert au moment de la réplication à l'analyse des performances.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**tracer_id**|**Int**|Identifie un enregistrement de jeton de suivi.|  
|**publication_id**|**Int**|Identifie la publication dans laquelle l'enregistrement du jeton de suivi a été inséré.|  
|**publisher_commit**|**datetime**|Date et heure du moment où l'enregistrement du jeton de suivi a été validé sur le serveur de publication.|  
|**distributor_commit**|**datetime**|Date et heure du moment où l'enregistrement du jeton de suivi a été validé sur le serveur de distribution.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
