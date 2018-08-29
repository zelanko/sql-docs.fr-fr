---
title: syspolicy_policy_category_subscriptions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
manager: craigg
ms.openlocfilehash: e0d08a739b2fe0d56a263cf2cd77890232592148
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43026346"
---
# <a name="syspolicypolicycategorysubscriptions-transact-sql"></a>syspolicy_policy_category_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche une ligne pour chaque abonnement de la Gestion basée sur des stratégies dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Chaque ligne décrit une paire de catégorie cible et la stratégie. Le tableau suivant décrit les colonnes dans la vue syspolicy_policy_group_subscriptions.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|policy_category_subscription_id|**Int**|Identificateur de cet enregistrement.|  
|target_type|**sysname**|Type d'objet de base de données qui est la cible de cet abonnement.|  
|target_object|**sysname**|Nom de l'objet cible.|  
|policy_category_id|**Int**|ID de la catégorie de stratégies qui s'applique à la cible.|  
  
## <a name="remarks"></a>Notes  
 Cette vue affiche les cibles abonnées aux catégories de stratégies.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Vues de la Gestion basée sur des stratégies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
