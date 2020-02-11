---
title: sys. trigger_event_types (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trigger_event_types_TSQL
- sys.trigger_event_types_TSQL
- sys.trigger_event_types
- trigger_event_types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trigger_event_types catalog view
ms.assetid: 054aed54-7151-4760-934a-149fa434f1ae
author: stevestein
ms.author: sstein
ms.openlocfilehash: fb845732f3766e715df0e92d751a18b1aa8f2969
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091950"
---
# <a name="systrigger_event_types-transact-sql"></a>sys.trigger_event_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque événement ou groupe d'événements sur lequel un déclencheur peut être activé.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**entrer**|**int**|Type d'événement ou groupe d'événements qui active un déclencheur.|  
|**type_name**|**nvarchar (64)**|Nom d'un événement ou groupe d'événements. Cela peut être spécifié dans la clause FOR d’une instruction [CREATE TRIGGER](../../t-sql/statements/create-trigger-transact-sql.md) .|  
|**parent_type**|**int**|Type de groupe d'événements qui est le parent de l'événement ou du groupe d'événements.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
