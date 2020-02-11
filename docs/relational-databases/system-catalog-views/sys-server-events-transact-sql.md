---
title: sys. server_events (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_events_TSQL
- sys.server_events_TSQL
- server_events
- sys.server_events
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_events catalog view
ms.assetid: 996f6c9b-6426-4847-95d9-6b77541422be
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3613c3da1138a6ec17394a5b6615d78d0a941e56
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68133151"
---
# <a name="sysserver_events-transact-sql"></a>sys.server_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne par événement pour lequel est activé un déclencheur DDL de niveau serveur ou une notification d'événement de niveau serveur. Les colonnes **object_id** et **type** identifient de manière unique l’événement de serveur.  

  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID de la notification d'événements de niveau serveur ou du déclencheur DDL de niveau serveur à activer.|  
|**entrer**|**int**|Type de l'événement à l'origine de l'activation de la notification d'événement ou du déclencheur DDL.|  
|**type_desc**|**nvarchar (60)**|Description de l'événement à l'origine de l'activation du déclencheur DDL ou de la notification d'événement.|  
|**event_group_type**|**int**|Groupe d'événements sur lequel le déclencheur ou la notification d'événements est créé(e), ou null si le déclencheur n'est pas créé sur un groupe d'événements.|  
|**event_group_type_desc**|**nvarchar (60)**|Description du groupe d’événements sur lequel le déclencheur ou la notification d’événements est créé, ou null s’il n’est pas créé sur un groupe d’événements|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
