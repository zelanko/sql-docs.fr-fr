---
title: TABLES (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-information-schema-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TABLES_TSQL
- TABLES
dev_langs: TSQL
helpviewer_keywords:
- TABLES view
- INFORMATION_SCHEMA.TABLES view
ms.assetid: 723a9e63-8f6e-4d6e-b570-468cfaf03201
caps.latest.revision: "39"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d9b2aa91d604bc38a24d4704614f4eb2b47960e4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="tables-transact-sql"></a>TABLES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie une ligne pour chaque table de la base de données active pour laquelle l'utilisateur actuel dispose d'autorisations.  
  
 Pour récupérer des informations à partir de ces vues, spécifiez le nom qualifié complet de **INFORMATION_SCHEMA.** *view_name*.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar (**128**)**|Qualificateur de la table.|  
|**TABLE_SCHEMA**|**nvarchar (**128**)**|Nom du schéma qui contient la table.<br /><br /> **\*\*Important \* \***  n’utilisez pas les vues INFORMATION_SCHEMA pour déterminer le schéma d’un objet. La seule méthode fiable pour rechercher le schéma d'un objet est d'interroger l'affichage catalogue sys.objects. Les vues INFORMATION_SCHEMA peuvent être incomplètes dans la mesure où elles ne sont pas mises à jour pour toutes les nouvelles fonctionnalités.|  
|**NOM_TABLE**|**sysname**|Nom de la table.|  
|**TABLE_TYPE**|**varchar (**10**)**|Type de table. Peut être VIEW ou BASE TABLE.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues système &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Vues de schémas d’informations &#40; Transact-SQL &#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [Sys.Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)  
  
  
