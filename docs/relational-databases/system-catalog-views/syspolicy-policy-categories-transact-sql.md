---
title: syspolicy_policy_categories (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_categories
- syspolicy_policy_categories_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_groups view
ms.assetid: 65f080c7-771f-4cf6-a7a0-88882c637f8d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: adf4fd9f815297fc31611f46c1c9a7c86e893f46
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85664027"
---
# <a name="syspolicy_policy_categories-transact-sql"></a>syspolicy_policy_categories (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Affiche une ligne pour chaque catégorie de la stratégie de la Gestion basée sur des stratégies dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les catégories de stratégies vous aident à organiser des stratégies lorsque celles-ci sont nombreuses. Le tableau suivant décrit les colonnes dans la vue syspolicy_policy_groups.  
 
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|policy_category_id|**int**|Identificateur de la catégorie de stratégie.|  
|name|**sysname**|Nom de la catégorie de stratégie.|  
|mandate_database_subscriptions|**bit**|Indique si la catégorie de stratégie s'applique à toutes les bases de données dans une instance sans un abonnement explicite (1) ou si la catégorie de stratégie doit être appliquée à une base de données en utilisant un abonnement explicite (0).|  
  
## <a name="remarks"></a>Remarques  
 Affiche une liste des groupes de stratégie de la Gestion basée sur des stratégies.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l’aide de la gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Vues de la Gestion basée sur des stratégies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
