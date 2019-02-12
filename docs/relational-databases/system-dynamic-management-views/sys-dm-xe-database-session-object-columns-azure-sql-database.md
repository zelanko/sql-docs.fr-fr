---
title: Sys.dm_xe_database_session_object_columns (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 0e6adc54-4d97-4ef0-bf4f-b4538d69f136
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: a4a1807adb4d04c3e38332ffd9fe71e874c82233
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56035270"
---
# <a name="sysdmxedatabasesessionobjectcolumns-azure-sql-database"></a>sys.dm_xe_database_session_object_columns (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Indique les valeurs de configuration d'objets liés à une session.  
  
||  
|-|  
|**S’applique à** : [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 et les versions ultérieures.|  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Adresse mémoire de la session d'événements. A une relation plusieurs-à-un avec sys.dm_xe_database_sessions.address. N'accepte pas la valeur NULL.|  
|column_name|**nvarchar(60)**|Nom de la valeur de configuration. N'accepte pas la valeur NULL.|  
|column_id|**Int**|ID de la colonne. Unique dans l'objet. N'accepte pas la valeur NULL.|  
|column_value|**nvarchar(2048)**|Valeur configurée de la colonne. Autorise la valeur NULL.|  
|object_type|**nvarchar(60)**|Type de l’objet.  N’est pas nullable.object_type est une des :<br /><br /> événement<br /><br /> target|  
|object_name|**nvarchar(60)**|Nom de l'objet auquel appartient cette colonne. N'accepte pas la valeur NULL.|  
|object_package_guid|**uniqueidentifier**|GUID du package qui contient l'objet. N'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
|From|Pour|Relation|  
|----------|--------|------------------|  
|dm_xe_database_session_object_columns.object_name<br /><br /> dm_xe_database_session_object_columns.object_package_guid|sys.dm_xe_objects.package_guid<br /><br /> sys.dm_xe_objects.name|Plusieurs-à-un|  
|dm_xe_database_session_object_columns.column_name<br /><br /> dm_xe_database_session_object_columns.column_id|sys.dm_xe_object_columns.name<br /><br /> sys.dm_xe_object_columns.column_id|Plusieurs-à-un|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)  
  
  
