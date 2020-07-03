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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 371ee711cbae4c97dc95e9d31d51739c29e85d14
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889634"
---
# <a name="mspeer_response-transact-sql"></a>MSpeer_response (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  La table **MSpeer_response** est utilisée dans la réplication d’égal à égal pour stocker la réponse de chaque nœud à une demande d’état de publication. Cette table est stockée dans la base de données de publication.  
  
## <a name="definition"></a>Définition  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**request_id**|**int**|Identifie une entrée de demande d’État dans la table [MSpeer_request](../../relational-databases/system-tables/mspeer-request-transact-sql.md) .|  
|**paires**|**sysname**|Homologue qui a généré la réponse.|  
|**peer_db**|**sysname**|Base de données d'abonnement sur l'homologue qui a généré la réponse.|  
|**received_date**|**datetime**|Date et heure de réception de la demande de l'homologue.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
