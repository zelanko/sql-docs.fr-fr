---
title: MSpeer_topologyrequest (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSpeer_topologyrequest_TSQL
- MSpeer_topologyrequest
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_topologyrequest
ms.assetid: c644814b-4e40-44d7-b6b4-5954b0d4db7c
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a78d3067be186cd56953035c8e05a37e8c654169
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="mspeertopologyrequest-transact-sql"></a>MSpeer_topologyrequest (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Permet de suivre les requêtes de statut de topologie pour une publication dans le cadre d'une réplication d'égal à égal. Cette table est stockée dans la base de données de publication.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|id|**int**|Identifie une demande de statut de topologie. La colonne request_id dans [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) utilise cette valeur.|  
|publication|**sysname**|Nom de la publication d'où provient la demande de statut de topologie.|  
|sent_date|**datetime**|Date et heure d'émission de la demande de statut de topologie.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
