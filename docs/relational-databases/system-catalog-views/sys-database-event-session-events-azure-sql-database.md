---
title: Sys.database_event_session_events (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
ms.assetid: f4c9eb0a-173c-4c66-8dd8-6f7176b2657f
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: d49ac2e05868cfa4a9fd4a3bb1b9f799d4876687
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39549969"
---
# <a name="sysdatabaseeventsessionevents-azure-sql-database"></a>sys.database_event_session_events (Azure SQL Database)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque événement d'une session d'événements.  
  
||  
|-|  
|**S’applique aux**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 et les versions ultérieures.|  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**Int**|ID de la session d'événements. N'accepte pas la valeur NULL.|  
|event_id|**Int**|ID de l'événement. Cet ID est unique au sein d'une session d'événements. N'accepte pas la valeur NULL.|  
|NAME|**sysname**|Nom de l’événement. N'accepte pas la valeur NULL.|  
|package|**sysname**|Nom du package d'événement qui contient l'événement. N'accepte pas la valeur NULL.|  
|module|**sysname**|Nom du module qui contient l'événement. N'accepte pas la valeur NULL.|  
|prédicat|**nvarchar(3000)**|L’expression de prédicat est appliquée à l’événement. Autorise la valeur NULL.|  
|predicate_xml|**nvarchar(3000)**|Expression de prédicat XML qui est appliquée à l'événement. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation VIEW DATABASE STATE sur le serveur.  
  
## <a name="remarks"></a>Notes  
 Cette vue a les cardinalités de relation suivantes.  
  
||||  
|-|-|-|  
|From|Pour|Relation|  
|sys.database_event_session_events.event_session_id|sys.database_event_sessions.event_session_id|Plusieurs-à-un|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)  
  
  
