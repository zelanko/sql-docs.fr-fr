---
title: Sys.dm_xe_database_session_targets (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: 7f353e2a-f8fc-4366-97e4-aa1c49eadaf4
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 2ce53be179bd25a71c92d2f0510036ef0d5c3f1e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704537"
---
# <a name="sysdmxedatabasesessiontargets-azure-sql-database"></a>sys.dm_xe_database_session_targets (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur les cibles de la session.  
  
||  
|-|  
|**S’applique aux**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 et toutes les futures versions.|  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Adresse mémoire de la session d'événements. A une relation plusieurs-à-un avec sys.dm_xe_database_sessions.address. N'accepte pas la valeur NULL.|  
|target_name|**nvarchar(60)**|Nom de la cible au sein d'une session. N'accepte pas la valeur NULL.|  
|target_package_guid|**uniqueidentifier**|GUID du package qui contient la cible. N'accepte pas la valeur NULL.|  
|execution_count|**bigint**|Nombre d'exécutions de la cible pour la session. N'accepte pas la valeur NULL.|  
|execution_duration_ms|**bigint**|Temps d'exécution total de la cible, en millisecondes. N'accepte pas la valeur NULL.|  
|target_data|**nvarchar(max)**|Données gérées par la cible, par exemple les informations sur l'agrégation d'événements. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’autorisation VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
|From|Pour|Relation|  
|----------|--------|------------------|  
|sys.dm_xe_database_session_targets.event_session_address|sys.dm_xe_database_sessions.address|Plusieurs-à-un|  
  
  
