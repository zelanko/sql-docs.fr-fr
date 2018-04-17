---
title: Sys.service_message_types (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 06/10/2016
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
- sys.service_message_types
- service_message_types
- sys.service_message_types_TSQL
- service_message_types_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_message_types catalog view
ms.assetid: 6a38709a-60fe-46f6-89da-718f74f15600
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 15482ba9ddf58f4b037cb19ee376df224308516d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sysservicemessagetypes-transact-sql"></a>sys.service_message_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cet affichage catalogue contient une ligne par type de message inscrit dans Service Broker.
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom du type de message, unique dans la base de données. Cette colonne n'accepte pas la valeur NULL.|  
|**message_type_id**|**int**|Identificateur du type de message, unique dans la base de données. Cette colonne n'accepte pas la valeur NULL.|  
|**principal_id**|**int**|Identificateur du principal de base de données propriétaire de ce type de message. Accepte la valeur NULL.|  
|**validation**|**char(2)**|Validation effectuée par Service Broker avant l'envoi de messages de ce type. Cette colonne n'accepte pas la valeur NULL. Une des valeurs suivantes :<br /><br /> N = aucun<br /><br /> X = XML<br /><br /> E = vide|  
|**validation_desc**|**nvarchar(60)**|Description de la validation effectuée par Service Broker avant l'envoi de messages de ce type. Accepte la valeur NULL. Une des valeurs suivantes :<br /><br /> Aucune<br /><br /> XML<br /><br /> EMPTY|  
|**xml_collection_id**|**int**|Pour une validation qui utilise un schéma XML, l'identificateur de la collection de schéma utilisée.<br /><br /> Sinon, NULL.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
