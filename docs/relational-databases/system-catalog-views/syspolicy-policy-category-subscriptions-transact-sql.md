---
title: syspolicy_policy_category_subscriptions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_category_subscriptions_TSQL
- syspolicy_policy_category_subscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_group_subscriptions view
ms.assetid: b3b3a7d7-0b78-46c0-9755-045f7a5692b9
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 304e904ab95e4be58ba2a373bd6ed9c11131049f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68094894"
---
# <a name="syspolicy_policy_category_subscriptions-transact-sql"></a>syspolicy_policy_category_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche une ligne pour chaque abonnement de la Gestion basée sur des stratégies dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Chaque ligne décrit une cible et une paire de catégorie de stratégies. Le tableau suivant décrit les colonnes dans la vue syspolicy_policy_group_subscriptions.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|policy_category_subscription_id|**int**|Identificateur de cet enregistrement.|  
|target_type|**sysname**|Type d'objet de base de données qui est la cible de cet abonnement.|  
|target_object|**sysname**|Nom de l'objet cible.|  
|policy_category_id|**int**|ID de la catégorie de stratégies qui s'applique à la cible.|  
  
## <a name="remarks"></a>Notes  
 Cette vue affiche les cibles abonnées aux catégories de stratégies.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l’aide de la gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Vues de la Gestion basée sur des stratégies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
