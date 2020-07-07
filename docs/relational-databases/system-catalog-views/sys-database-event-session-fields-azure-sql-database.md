---
title: sys. database_event_session_fields (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: 9b5c94d6-612c-4e0f-976d-ac6ba55da3ac
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 52fbdd5925d67592b10e5dc4d293e9523dcda758
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86003019"
---
# <a name="sysdatabase_event_session_fields-azure-sql-database"></a>sys.database_event_session_fields (Azure SQL Database)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Retourne une ligne pour chaque colonne personnalisable définie explicitement sur les événements et les cibles.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 et à toutes les versions ultérieures.|  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|ID de la session d'événements. N'accepte pas la valeur NULL.|  
|object_id|**int**|ID de l'objet auquel est associé ce champ. N'accepte pas la valeur NULL.|  
|name|**sysname**|Nom du champ. N'accepte pas la valeur NULL.|  
|value|**sql_variant**|Valeur du champ. N'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation VIEW DATABASE STATE sur le serveur.  
  
## <a name="remarks"></a>Remarks  
 Cette vue a les cardinalités de relation suivantes.  
  
||||  
|-|-|-|  
|À partir|À|Relation|  
|sys. database_event_session_actions. event_session_id|sys. database_event_sessions. event_session_id|Plusieurs-à-un|  
|sys. database_event_session_actions. event_id<br /><br /> sys. database_event_session_actions. object_id<br /><br /> sys. database_event_session_actions. event_session_id|sys. database_event_session_events. event_session_id<br /><br /> sys. database_event_session_events. event_id|Plusieurs-à-un|  
|sys. database_event_session_actions. event_session_id<br /><br /> sys. database_event_session_actions. object_id|sys. database_event_session_targets. event_session_id<br /><br /> sys. database_event_session_targets. target_id|Plusieurs-à-un|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)  
  
  
