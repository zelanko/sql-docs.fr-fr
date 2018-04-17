---
title: sp_syspolicy_unsubscribe_from_policy_category (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_unsubscribe_from_policy_category_TSQL
- sp_syspolicy_unsubscribe_from_policy_category
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_unsubscribe_from_policy_category
ms.assetid: 47abab63-e605-40e8-a54e-2241e2e01afd
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e9d2749e6bfbd92553d2098abee790df17c37f90
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="spsyspolicyunsubscribefrompolicycategory-transact-sql"></a>sp_syspolicy_unsubscribe_from_policy_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un abonnement aux catégories de stratégies pour la base de données actuelle.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_syspolicy_unsubscribe_from_policy_category [ @policy_category = ] 'policy_category'  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@policy_category=** ] **'***policy_category***'**  
 Nom de l'abonnement aux catégories de stratégies à supprimer. *policy_category* est **sysname**et est requis.  
  
 Pour obtenir les valeurs de *policy_category*, interrogez la vue système msdb.dbo.syspolicy_policy_categories.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Vous devez exécuter sp_syspolicy_unsubscribe_from_policy_category dans le contexte de la base de données de laquelle vous voulez supprimer un abonnement aux catégories de stratégies.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle de base de données fixe db_owner.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime un abonnement à la catégorie de stratégie « Finance » pour la base de données spécifiée.  
  
```  
USE <database_name>;  
  
EXEC sys.sp_syspolicy_unsubscribe_from_policy_category @policy_category = N'Finance';  
  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de gestion basée sur la stratégie &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_subscribe_to_policy_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-subscribe-to-policy-category-transact-sql.md)  
  
  
