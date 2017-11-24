---
title: COLUMN_DOMAIN_USAGE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-information-schema-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLUMN_DOMAIN_USAGE_TSQL
- COLUMN_DOMAIN_USAGE
dev_langs: TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.COLUMN_DOMAIN_USAGE view
- COLUMN_DOMAIN_USAGE view
ms.assetid: deb20037-6a51-47ae-9f49-7601698fafaf
caps.latest.revision: "37"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 39fe828fd62ba367c607c2e7b84c6b37bb87cc65
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="columndomainusage-transact-sql"></a>COLUMN_DOMAIN_USAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Renvoie une ligne pour chaque colonne de la base actuelle ayant des données de type alias. Cette vue de schémas d'informations renvoie des informations sur les objets pour lesquels l'utilisateur actuel dispose d'autorisations.  
  
 Pour récupérer des informations à partir de ces vues, spécifiez le nom qualifié complet de **INFORMATION_SCHEMA.** *view_name*.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**DOMAIN_CATALOG**|**nvarchar (**128**)**|Base de données dans laquelle réside le type de données alias.|  
|**DOMAIN_SCHEMA**|**nvarchar (**128**)**|Nom du schéma qui contient le type de données alias.<br /><br /> **\*\*Important \* \***  n’utilisez pas les vues INFORMATION_SCHEMA pour déterminer le schéma d’un type de données. La seule méthode fiable pour rechercher le schéma d'un type est d'utiliser la fonction TYPEPROPERTY.|  
|**NOM_DOMAINE**|**sysname**|Type de données alias.|  
|**TABLE_CATALOG**|**nvarchar (**128**)**|Qualificateur de la table.|  
|**TABLE_SCHEMA**|**nvarchar (**128**)**|Propriétaire de la table.<br /><br /> **\*\*Important \* \***  n’utilisez pas les vues INFORMATION_SCHEMA pour déterminer le schéma d’un objet. La seule méthode fiable pour rechercher le schéma d’un objet est d’interroger l’affichage catalogue sys.objects.|  
|**NOM_TABLE**|**sysname**|Base de données où le type de données alias est utilisé.|  
|**NOM_COLONNE**|**sysname**|Colonne utilisant le type de données alias.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues système &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Vues de schémas d’informations &#40; Transact-SQL &#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [Sys.Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Sys.types &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)  
  
  
