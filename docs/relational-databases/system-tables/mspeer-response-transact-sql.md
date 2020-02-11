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
ms.openlocfilehash: c930a5eeae8bfdb7d952610fadc0b7d779033435
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68026673"
---
# <a name="mspeer_response-transact-sql"></a>MSpeer_response (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table **MSpeer_response** est utilisée dans la réplication d’égal à égal pour stocker la réponse de chaque nœud à une demande d’état de publication. Cette table est stockée dans la base de données de publication.  
  
## <a name="definition"></a>Définition  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**request_id**|**int**|Identifie une entrée de demande d’État dans la table [MSpeer_request](../../relational-databases/system-tables/mspeer-request-transact-sql.md) .|  
|**paires**|**sysname**|Homologue qui a généré la réponse.|  
|**peer_db**|**sysname**|Base de données d'abonnement sur l'homologue qui a généré la réponse.|  
|**received_date**|**DATETIME**|Date et heure de réception de la demande de l'homologue.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
