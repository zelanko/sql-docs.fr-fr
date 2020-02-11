---
title: sp_syspolicy_rename_policy (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_rename_policy_TSQL
- sp_syspolicy_rename_policy
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_rename_policy
ms.assetid: ce2b07f5-23b1-4f49-8e7b-c18cf3f3d45b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: baf0ebbea6eb78d8a125b5ea786039880addf032
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67997306"
---
# <a name="sp_syspolicy_rename_policy-transact-sql"></a>sp_syspolicy_rename_policy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renomme une stratégie existante dans la Gestion basée sur des stratégies.  
  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_syspolicy_rename_policy { [ @name = ] 'name' | [ @policy_id = ] policy_id }  
    , [ @new_name = ] 'new_name'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @name = ] 'name'`Nom de la stratégie que vous souhaitez renommer. *Name* est de **type sysname**et doit être spécifié si *policy_id* a la valeur null.  
  
`[ @policy_id = ] policy_id`Est l’identificateur de la stratégie que vous souhaitez renommer. *policy_id* est de **type int**et doit être spécifié si *Name* a la valeur null.  
  
`[ @new_name = ] 'new_name'`Nouveau nom de la stratégie. *new_name* est de **type sysname**et est obligatoire. Ne peut pas avoir la valeur NULL ou être une chaîne vide.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Vous devez exécuter sp_syspolicy_rename_policy dans le contexte de la base de données système msdb.  
  
 Vous devez spécifier une valeur pour *Name* ou *policy_id*. Les deux ne peuvent pas être NULL. Pour obtenir ces valeurs, interrogez la vue système msdb.dbo.syspolicy_policies.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle de base de données fixe PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Élévation possible des informations d’identification : les utilisateurs du rôle PolicyAdministratorRole peuvent créer des déclencheurs de serveur et planifier des exécutions de stratégie qui peuvent affecter le fonctionnement [!INCLUDE[ssDE](../../includes/ssde-md.md)]de l’instance du. Par exemple, les utilisateurs du rôle PolicyAdministratorRole peuvent créer une stratégie qui peut empêcher la création de la plupart des objets [!INCLUDE[ssDE](../../includes/ssde-md.md)]dans le. En raison de cette élévation possible des informations d’identification, le rôle PolicyAdministratorRole doit être accordé uniquement aux utilisateurs approuvés par le contrôle de la configuration [!INCLUDE[ssDE](../../includes/ssde-md.md)]du.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant renomme une stratégie nommée « Test Policy 1 » en « Test Policy 2 ».  
  
```  
EXEC msdb.dbo.sp_syspolicy_rename_policy @name = N'Test Policy 1'  
, @new_name = N'Test Policy 2';  
  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de gestion basée sur des stratégies &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)  
  
  
