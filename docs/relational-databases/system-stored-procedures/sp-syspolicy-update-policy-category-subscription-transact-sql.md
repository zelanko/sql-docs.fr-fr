---
title: sp_syspolicy_update_policy_category_subscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_update_policy_category_subscription_TSQL
- sp_syspolicy_update_policy_category_subscription
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_update_policy_category_subscription
ms.assetid: d0769566-8f5c-4c8a-84d3-ee17ea6e0cb4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: f3833d16d0cf4e791064dc369d460fe9cf5cc3e2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68035366"
---
# <a name="spsyspolicyupdatepolicycategorysubscription-transact-sql"></a>sp_syspolicy_update_policy_category_subscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Met à jour un abonnement aux catégories de stratégies pour une base de données spécifiée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_syspolicy_update_policy_category_subscription [ @policy_category_subscription_id = ] policy_category_subscription_id  
    [ , [ @target_type = ] 'target_type' ]  
    [ , [ @target_object = ] 'target_object' ]  
    , [ @policy_category = ] 'policy_category'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @policy_category_subscription_id = ] policy_category_subscription_id` Est l’identificateur pour l’abonnement aux catégories de stratégie que vous souhaitez mettre à jour. *policy_category_subscription_id* est **int**et est requis.  
  
`[ @target_type = ] 'target_type'` Est le type de cible de l’abonnement aux catégories. *target_type* est **sysname**, avec NULL comme valeur par défaut.  
  
 Si vous spécifiez *target_type*, la valeur doit être définie à 'DATABASE'.  
  
`[ @target_object = ] 'target_object'` Est le nom de la base de données qui peuvent s’abonner à la catégorie de stratégie. *target_object* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @policy_category = ] 'policy_category'` Est le nom de catégorie de stratégie que vous souhaitez vous abonner à la base de données. *policy_category* est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Vous devez exécuter sp_syspolicy_update_policy_category_subscription dans le contexte de la base de données système msdb.  
  
 Pour obtenir les valeurs de *policy_category_subscription_id* et pour *policy_category*, vous pouvez utiliser la requête suivante :  
  
```  
SELECT a.policy_category_subscription_id, a.target_type, a.target_object  
    , b.name AS policy_category  
FROM msdb.dbo.syspolicy_policy_category_subscriptions AS a  
INNER JOIN msdb.dbo.syspolicy_policy_categories AS b  
ON a.policy_category_id = b.policy_category_id;  
```  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle de base de données fixe PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Élévation possible des informations d’identification : Les utilisateurs du rôle PolicyAdministratorRole peuvent créer des déclencheurs de serveur et planifier des exécutions de stratégie qui peuvent affecter le fonctionnement de l’instance de la [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Par exemple, les utilisateurs du rôle PolicyAdministratorRole peuvent créer une stratégie qui peut empêcher la plupart des objets d’être créées dans le [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Étant donné cette possible élévation des informations d’identification, le rôle PolicyAdministratorRole doit être accordé uniquement aux utilisateurs qui sont approuvés avec contrôle de la configuration de la [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant met à jour un abonnement aux catégories de stratégies existant de sorte que la base de données AdventureWorks2012 s'abonne à la catégorie de stratégie « Finance ».  
  
```  
EXEC msdb.dbo.sp_syspolicy_update_policy_category_subscription @policy_category_subscription_id = 1  
, @target_object = 'AdventureWorks2012'  
, @policy_category = 'Finance';  
  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de gestion basée sur des stratégies &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_add_policy_category_subscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql.md)   
 [sp_syspolicy_delete_policy_category_subscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-delete-policy-category-subscription-transact-sql.md)  
  
  
