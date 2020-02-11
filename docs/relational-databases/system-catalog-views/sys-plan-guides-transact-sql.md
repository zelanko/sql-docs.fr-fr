---
title: sys. plan_guides (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.planguides_TSQL
- plan_guides
- sys.planguides
- plan_guides_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.plan_guides catalog view
ms.assetid: 3dde0397-ef6f-4b3f-8250-3f25584eb62b
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 19b78ff53b5640d74b49d2e5956c39aa1df2e230
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68068070"
---
# <a name="sysplan_guides-transact-sql"></a>sys.plan_guides (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Contient une ligne pour chaque repère de plan dans la base de données.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**plan_guide_id**|**int**|Identificateur unique du repère de plan dans la base de données.|  
|**nomme**|**sysname**|Nom du repère de plan.|  
|**create_date**|**DATETIME**|Date et heure de création du repère de plan.|  
|**modify_date**|**Date/heure**|Date de la dernière modification du repère de plan.|  
|**is_disabled**|**bit**|1 = Repère de plan désactivé.<br /><br /> 0 = Repère de plan activé.|  
|**query_text**|**nvarchar(max)**|Texte de la requête utilisé pour créer le repère de plan.|  
|**scope_type**|**tinyint**|Identifie l'étendue du repère de plan.<br /><br /> 1 = OBJECT<br /><br /> 2 = SQL<br /><br /> 3 = TEMPLATE|  
|**scope_type_desc**|**nvarchar (60)**|Description de l'étendue du repère de plan.<br /><br /> OBJECT<br /><br /> SQL<br /><br /> TEMPLATE|  
|**scope_object_id**|**Tiers**|object_id de l'objet définissant l'étendue du repère de plan, si celle-ci est OBJECT.<br /><br /> NULL si le repère de plan ne s'étend pas à OBJECT.|  
|**scope_batch**|**nvarchar(max)**|Texte du lot, si **scope_type** est SQL.<br /><br /> NULL si le type du traitement n'est pas SQL.<br /><br /> Si NULL et **scope_type** est SQL, la valeur de **query_text** s’applique.|  
|**paramètres**|**nvarchar(max)**|Chaîne définissant la liste des paramètres associés au repère de plan.<br /><br /> NULL = Aucune liste de paramètres n'est associée au repère de plan.|  
|**indicateurs**|**nvarchar(max)**|Indicateurs de la clause OPTION associés au repère de plan.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
  
