---
title: "dbo.slo_service_objectives (de base de données SQL Azure) | Documents Microsoft"
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 03/04/2017
ms.prod: 
ms.reviewer: 
ms.service: sql-database
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: Azure SQL Database
f1_keywords:
- dbo.slo_service_objectives
- dbo.slo_service_objectives_TSQL
- slo_service_objectives
- slo_service_objectives_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dbo.slo_service_objectives
- slo_service_objectives
ms.assetid: d5dd7ed9-440a-4432-ad45-644e4e72318f
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5330bc8977c0e043f27cb5f035510c5da007e0c4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="dbosloserviceobjectives-azure-sql-database"></a>dbo.slo_service_objectives (de base de données SQL Azure)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  Cette fonctionnalité est dans un état d’aperçu et a été déconseillée dans [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12. N'établissez pas de dépendance sur l'implémentation spécifique de cette fonctionnalité, car elle est susceptible d'être modifiée ou supprimée dans une future version.  
  
 Retourne des informations d'objectif de niveau de service (SLO) sur le serveur actuel.  
  
||  
|-|  
|**S’applique aux**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V11.|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|objective_id|**uniqueidentifier**|ID de l'objectif de niveau de service.|  
|name|**sysname**|Nom de l'objectif de niveau de service.|  
|description|**nvarchar**|Description de l'objectif de niveau de service.|  
|create_date|**DateTimeOffset(7)**|Date de création de l'objet de niveau de service sur le serveur.|  
|is_system|**bit**|1 = Objectif de niveau de service système|  
|is_default|**bit**|1 = L'objectif de niveau de service est le SLO par défaut.|  
|state|**tinyint**|1 = L'objectif de niveau de service est activé.<br /><br /> 2 = L'objectif de niveau de service est désactivé.|  
|state_desc|**nvarchar**|Description de l'objectif de niveau de service.|  
|metadata_version|**decimal**|Version de l'objectif de niveau de service.|  
  
## <a name="permissions"></a>Permissions  
 Cette vue est disponible pour tous les rôles d’utilisateur disposant des autorisations pour se connecter à virtuel **master** base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des bases de données Premium](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
