---
title: sys. server_trigger_events (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.server_trigger_events_TSQL
- server_trigger_events_TSQL
- sys.server_trigger_events
- server_trigger_events
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_trigger_events catalog view
ms.assetid: be7d8a59-3c00-4f1b-b4b0-3dcd5572e002
author: stevestein
ms.author: sstein
ms.openlocfilehash: c226b3c5daef98c9a34c7ac25934a94abc8baabc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68132999"
---
# <a name="sysserver_trigger_events-transact-sql"></a>sys.server_trigger_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque événement pour lequel s'exécute un déclencheur de niveau serveur (synchrone).  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**colonnes héritées**||Hérite de toutes les colonnes de [sys. server_events](../../relational-databases/system-catalog-views/sys-server-events-transact-sql.md).|  
|**is_first**|**bit**|Le déclencheur est marqué comme étant le premier à s'exécuter pour cet événement.|  
|**is_last**|**bit**|Le déclencheur est marqué comme étant le dernier à s'exécuter pour cet événement.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
