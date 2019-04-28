---
title: sp_syspolicy_rename_condition (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_rename_condition
- sp_syspolicy_rename_condition_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_rename_condition
ms.assetid: d9f3f9b1-701b-4fce-9b42-c282656caf84
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 0305e7bc2daa087483fce0472d32df0887271ba3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000649"
---
# <a name="spsyspolicyrenamecondition-transact-sql"></a>sp_syspolicy_rename_condition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renomme une condition existante dans la Gestion basée sur des stratégies.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_syspolicy_rename_condition { [ @name = ] 'name' | [ @condition_id = ] condition_id }  
    , [ @new_name = ] 'new_name'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @name = ] 'name'` Est le nom de la condition que vous souhaitez renommer. *nom* est **sysname**et doit être spécifié si *condition_id* a la valeur NULL.  
  
`[ @condition_id = ] condition_id` Est l’identificateur pour la condition que vous souhaitez renommer. *condition_id* est **int**et doit être spécifié si *nom* est NULL.  
  
`[ @new_name = ] 'new_name'` Est le nouveau nom de la condition. *new_name* est **sysname**et est requis. Ne peut pas avoir la valeur NULL ou être une chaîne vide.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Vous devez exécuter sp_syspolicy_rename_condition dans le contexte de la base de données système msdb.  
  
 Vous devez spécifier une valeur pour *nom* ou *condition_id*. Les deux ne peuvent pas être NULL. Pour obtenir ces valeurs, interrogez la vue msdb.dbo.syspolicy_conditions.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle de base de données fixe PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Élévation possible des informations d’identification : Les utilisateurs du rôle PolicyAdministratorRole peuvent créer des déclencheurs de serveur et planifier des exécutions de stratégie qui peuvent affecter le fonctionnement de l’instance de la [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Par exemple, les utilisateurs du rôle PolicyAdministratorRole peuvent créer une stratégie qui peut empêcher la plupart des objets d’être créées dans le [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Étant donné cette possible élévation des informations d’identification, le rôle PolicyAdministratorRole doit être accordé uniquement aux utilisateurs qui sont approuvés avec contrôle de la configuration de la [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant renomme une condition nommée « Change Tracking Enabled ».  
  
```  
EXEC msdb.dbo.sp_syspolicy_rename_condition @name = N'Change Tracking Enabled'  
, @new_name = N'Verify Change Tracking Enabled';  
  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de gestion basée sur des stratégies &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)  
  
  
