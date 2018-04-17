---
title: Sys.service_contract_message_usages (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- service_contract_message_usages_TSQL
- sys.service_contract_message_usages
- sys.service_contract_message_usages_TSQL
- service_contract_message_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_contract_message_usages catalog view
ms.assetid: f783e662-126c-4595-8e22-f9d05191f5d0
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d83783a6ad2bdaf28e4da16d0759303920bac770
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sysservicecontractmessageusages-transact-sql"></a>sys.service_contract_message_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cet affichage catalogue contient une ligne par paire contrat/type de message.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**service_contract_id**|**int**|ID du contrat qui utilise le type de message. Cette colonne n'accepte pas la valeur NULL.|  
|**message_type_id**|**int**|ID du type de message utilisé par le contrat. Cette colonne n'accepte pas la valeur NULL.|  
|**is_sent_by_initiator**|**bit**|Le type de message peut être envoyé par l'initiateur de la conversation. Cette colonne n'accepte pas la valeur NULL.|  
|**is_sent_by_target**|**bit**|Le type de message peut être envoyé par la cible de la conversation. Cette colonne n'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
