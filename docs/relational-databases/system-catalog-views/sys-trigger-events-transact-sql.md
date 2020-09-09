---
description: sys.trigger_events (Transact-SQL)
title: sys. trigger_events (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trigger_events_TSQL
- trigger_events
- sys.trigger_events
- sys.trigger_events_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trigger_events catalog view
ms.assetid: 92540447-131c-491c-b033-c064c7d950e1
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ead6f918e85c73d344924bfe1bc7c878bf4d44c6
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89537983"
---
# <a name="systrigger_events-transact-sql"></a>sys.trigger_events (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Contient une ligne par événement pour lequel un déclencheur est activé.  
  
> [!NOTE]  
>  **sys. trigger_events** ne s’applique pas aux notifications d’événements.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**\<Columns inherited from sys.events>**|Non applicable|Hérite de la **object_id**, du **type** **type_desc** des colonnes de [sys. Events](../../relational-databases/system-catalog-views/sys-events-transact-sql.md).|  
|**is_first**|**bit**|Le déclencheur est marqué comme étant le premier à s'exécuter pour cet événement.|  
|**is_last**|**bit**|Le déclencheur est marqué comme étant le dernier à s'exécuter pour cet événement.|  
|**event_group_type**|**int**|Groupe d'événements sur lequel le déclencheur est créé, ou Null si le déclencheur n'est pas créé sur un groupe d'événements.|  
|**event_group_type_desc**|**nvarchar(60)**|Description du groupe d'événements sur lequel le déclencheur est créé, ou Null si le déclencheur n'est pas créé sur un groupe d'événements.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
