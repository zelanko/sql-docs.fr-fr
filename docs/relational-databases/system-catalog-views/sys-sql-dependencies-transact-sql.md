---
title: Sys.sql_dependencies (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sql_dependencies
- sql_dependencies_TSQL
- sys.sql_dependencies_TSQL
- sys.sql_dependencies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_dependencies catalog view
ms.assetid: 1779aa87-a0b8-470a-a286-d7cc0b93ad2e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ae071c927ab60f5b93e69a43d7ad443d333aa856
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="syssqldependencies-transact-sql"></a>sys.sql_dependencies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque dépendance à une entité référencée telle qu'elle est référencée dans l'expression [!INCLUDE[tsql](../../includes/tsql-md.md)] ou les instructions qui définissent un autre objet de référence.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilisez [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) à la place.  

  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**classe**|**tinyint**|Identifie la classe de l'entité référencée :<br /><br /> 0 = objet ou colonne (références non liées au schéma uniquement)<br /><br /> 1 = Objet ou colonne (uniquement les références liées au schéma)<br /><br /> 2 = Types (uniquement les références liées au schéma)<br /><br /> 3 = Collections de schémas XML (uniquement les références liées au schéma)<br /><br /> 4 = Fonction de partition (uniquement les références liées au schéma)|  
|**class_desc**|**nvarchar (60)**|Description de la classe de l'entité référencée :<br /><br /> **OBJECT_OR_COLUMN_REFERENCE_NON_SCHEMA_BOUND**<br /><br /> **OBJECT_OR_COLUMN_REFERENCE_SCHEMA_BOUND**<br /><br /> **TYPE_REFERENCE**<br /><br /> **XML_SCHEMA_COLLECTION_REFERENCE**<br /><br /> **PARTITION_FUNCTION_REFERENCE**|  
|**object_id**|**int**|ID de l'objet de référence.|  
|**column_id**|**int**|Si l'ID de référence est une colonne, ID de la colonne de référence ; sinon, 0.|  
|**referenced_major_id**|**int**|ID de l'entité référencée, interprété par la valeur de la classe, en fonction de :<br /><br /> 0, 1 = ID d'objet de l'objet ou de la colonne.<br /><br /> 2 = ID de type.<br /><br /> 3 = ID de collection de schémas XML.|  
|**referenced_minor_id**|**int**|ID secondaire de l'entité référencée, interprété par la valeur de la classe, comme illustré ci-dessous :<br /><br /> Lorsque class =:<br /><br /> 0, **referenced_minor_id** est un ID de colonne ou si n’est pas une colonne, il est 0.<br /><br /> 1, **referenced_minor_id** est un ID de colonne ou si n’est pas une colonne, il est 0.<br /><br /> Dans le cas contraire, **referenced_minor_id** = 0.|  
|**is_selected**|**bit**|L'objet ou la colonne est sélectionné.|  
|**is_updated**|**bit**|L'objet ou la colonne est mis à jour.|  
|**is_select_all**|**bit**|L'objet est utilisé dans la clause SELECT *(au niveau de l'objet uniquement).|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** . Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue d’objets &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Questions fréquentes (FAQ) sur l’interrogation des catalogues système SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
