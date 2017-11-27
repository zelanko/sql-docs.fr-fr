---
title: "dbo.slo_assignment_history (base de données de SQL Azure) | Documents Microsoft"
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 06/10/2016
ms.prod: 
ms.reviewer: 
ms.service: sql-database
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.slo_assignment_history
- slo_assignment_history
- slo_assignment_history_TSQL
- dbo.slo_assignment_history_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dbo.slo_assignment_history
- slo_assignment_history
ms.assetid: 048a6fb5-2fc2-4d12-a436-4c53ecd413f3
caps.latest.revision: "9"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 61bf1f0541df9085235dc00072624e1e91425cc5
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="dbosloassignmenthistory-azure-sql-database"></a>dbo.slo_assignment_history (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  **Cela s’applique uniquement aux [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11.**  
>   
>  Cette fonctionnalité est dans un état d'aperçu. N'établissez pas de dépendance sur l'implémentation spécifique de cette fonctionnalité, car elle est susceptible d'être modifiée ou supprimée dans une future version.  
  
 Retourne l'historique des affectations de SLO de la base de données sur le serveur, notamment :  
  
-   Historique des affectations de SLO de la base de données sur le serveur.  
  
-   Heure de début et de fin de chaque demande de modification de SLO de la base de données.  
  
-   Toutes les erreurs d'affectation de SLO qui sont enregistrées dans les colonnes error_code et error_desc.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|database_name|**sysname**|Nom de la base de données.|  
|database_id|**int**|ID de la base de données.|  
|create_date|**DateTimeOffset(7)**|Date de création de la base de données.|  
|service_objective_name|**sysname**|Nom de l'objectif de niveau de service (SLO).|  
|service_objective_id|**uniqueidentifier**|ID de l'objectif SLO.|  
|operation_id|**uniqueidentifier**|ID de l'opération.|  
|operation_start_time|**DateTimeOffset(7)**|Heure de début de la demande de modification de SLO de la base de données.|  
|operation_end_time|**DateTimeOffset(7)**|Heure de fin de la demande de modification de SLO de la base de données.|  
|error_code|**int**|Code d'erreur de la demande de modification de SLO de la base de données.|  
|error_desc|**nvarchar**|Description de l'erreur dans la demande de modification de SLO de la base de données.|  
  
## <a name="permissions"></a>Permissions  
 Cette vue est disponible pour tous les rôles d’utilisateur disposant des autorisations pour se connecter à virtuel **master** base de données.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne l'historique des affectations de SLO de la base de données pour une base de données spécifiée.  
  
```  
SELECT *  
FROM dbo.slo_assignment_history   
WHERE database_name = '<DB NAME>’   
ORDER BY operation_start_time DESC;  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des bases de données Premium](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
