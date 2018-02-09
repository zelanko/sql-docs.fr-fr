---
title: Sys.sysdepends (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysdepends_TSQL
- sysdepends
- sysdepends_TSQL
- sys.sysdepends
dev_langs:
- TSQL
helpviewer_keywords:
- sysdepends system table
- sys.sysdepends compatibility view
ms.assetid: f9c182cb-386f-4e72-859f-9f1115b389f9
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bc0f1360f5cff8d03dedce3e673c06c1104bf7bf
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="syssysdepends-transact-sql"></a>sys.sysdepends (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient des informations de dépendance entre les objets (vues, procédures et déclencheurs) de la base de données et les objets contenus dans leur définition (tables, vues et procédures).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID d'objet.|  
|**depid**|**int**|ID d'objet dépendant.|  
|**number**|**smallint**|Numéro de procédure.|  
|**depnumber**|**smallint**|Numéro de procédure dépendante.|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**deptype**|**tinyint**|Identifie le type d'objet dépendant :<br /><br /> 0 = Objet ou colonne (uniquement les références non liées au schéma)<br /><br /> 1 = Objet ou colonne (uniquement les références liées au schéma)|  
|**depdbid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**depsiteid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**selall**|**bit**|1 = L'objet est utilisé dans une instruction SELECT *.<br /><br /> 0 = Non.|  
|**resultobj**|**bit**|1 = L'objet est en cours de mise à jour.<br /><br /> 0 = Non.|  
|**readobj**|**bit**|1 = L'objet est en cours de lecture.<br /><br /> 0 = Non.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système pour les vues système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Vues de compatibilité &#40; Transact-SQL &#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [sp_depends &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-depends-transact-sql.md)   
 [sys.sql_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md)  
  
  
