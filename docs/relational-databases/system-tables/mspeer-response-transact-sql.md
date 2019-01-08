---
title: MSpeer_response (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_response
- MSpeer_response_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_response system table
ms.assetid: 510e24cf-0292-47a9-b1d9-71a30fef030f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: adbddf6f26c28c5fba396b00892b97d828e60222
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52757991"
---
# <a name="mspeerresponse-transact-sql"></a>MSpeer_response (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSpeer_response** table est utilisée dans la réplication d’égal à égal pour stocker la réponse de chaque nœud à une demande d’état de publication. Cette table est stockée dans la base de données de publication.  
  
## <a name="definition"></a>Définition  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**request_id**|**Int**|Identifie une entrée de demande d’état dans le [MSpeer_request](../../relational-databases/system-tables/mspeer-request-transact-sql.md) table.|  
|**homologue**|**sysname**|Homologue qui a généré la réponse.|  
|**peer_db**|**sysname**|Base de données d'abonnement sur l'homologue qui a généré la réponse.|  
|**received_date**|**datetime**|Date et heure de réception de la demande de l'homologue.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
