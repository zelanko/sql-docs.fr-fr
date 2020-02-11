---
title: syspolicy_conditions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_conditions
- syspolicy_conditions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_conditions view
ms.assetid: af97d26c-4bd5-4b08-be51-8419e3b2832c
author: stevestein
ms.author: sstein
ms.openlocfilehash: ee0f269fcfda93733d36a0b7396fd72d16bc01d9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68121167"
---
# <a name="syspolicy_conditions-transact-sql"></a>syspolicy_conditions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche une ligne pour chaque condition de la gestion basée sur des stratégies dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]l’instance de. syspolicy_conditions appartient au schéma dbo dans la base de données msdb. Le tableau suivant décrit les colonnes dans la vue syspolicy_conditions.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|condition_id|**int**|Identificateur de cette condition. Chaque condition représente une collection d'une ou de plusieurs expressions de condition.|  
|name|**sysname**|Nom de la condition.|  
|date_created|**DATETIME**|Date et heure de création de la condition.|  
|description|**nvarchar(max)**|Description de la condition. La colonne de description est facultative et peut être NULL.|  
|created_by|**sysname**|Connexion qui a créé la condition.|  
|modified_by|**sysname**|Connexion qui a récemment modifié la condition. Est NULL si jamais modifiée.|  
|date_modified|**DATETIME**|Date et heure de création de la condition. Est NULL si jamais modifiée.|  
|is_name_condition|**smallint**|Spécifie si la condition est une condition d'affectation de noms.<br /><br /> 0 = l'expression de condition ne contient pas la variable @Name.<br /><br /> 1 = l'expression de condition contient la variable @Name.|  
|facette|**nvarchar(max)**|Nom de la facette sur laquelle est basée la condition.|  
|Expression|**nvarchar(max)**|Expression des états de la facette.|  
|obj_name|**sysname**|Nom d'objet affecté à @Name si l'expression de condition contient cette variable.|  
  
## <a name="remarks"></a>Notes  
 Lorsque vous dépannez la Gestion basée sur des stratégies, interrogez la vue syspolicy_conditions pour déterminer qui a créé ou modifié en dernier la condition.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Vues de la gestion basée sur des stratégies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
