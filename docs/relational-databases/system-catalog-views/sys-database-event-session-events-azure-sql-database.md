---
title: sys. database_event_session_events (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: f4c9eb0a-173c-4c66-8dd8-6f7176b2657f
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ce194b0cfadb4ec9fecb207848d1f784cede0259
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86003047"
---
# <a name="sysdatabase_event_session_events-azure-sql-database"></a>sys.database_event_session_events (Azure SQL Database)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Renvoie une ligne pour chaque événement d’une session d’événements.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 et à toutes les versions ultérieures.|  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|ID de la session d'événements. N'accepte pas la valeur NULL.|  
|event_id|**int**|ID de l'événement. Cet ID est unique au sein d'une session d'événements. N'accepte pas la valeur NULL.|  
|name|**sysname**|Nom de l’événement. N'accepte pas la valeur NULL.|  
|package|**sysname**|Nom du package d'événement qui contient l'événement. N'accepte pas la valeur NULL.|  
|module|**sysname**|Nom du module qui contient l'événement. N'accepte pas la valeur NULL.|  
|prédicat|**nvarchar (3000)**|Expression de prédicat qui est appliquée à l’événement. Autorise la valeur NULL.|  
|predicate_xml|**nvarchar (3000)**|Expression de prédicat XML qui est appliquée à l'événement. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation VIEW DATABASE STATE sur le serveur.  
  
## <a name="remarks"></a>Remarks  
 Cette vue a les cardinalités de relation suivantes.  
  
||||  
|-|-|-|  
|À partir|À|Relation|  
|sys. database_event_session_events. event_session_id|sys. database_event_sessions. event_session_id|Plusieurs-à-un|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)  
  
  
