---
title: sp_syspolicy_repair_policy_automation (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_repair_policy_automation
- sp_syspolicy_repair_policy_automation_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_repair_policy_automation
ms.assetid: d81682e3-2444-4d66-ad00-1cf628632e8b
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 40c4a84f16c455cbfe49093881202318bb3d2cf0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="spsyspolicyrepairpolicyautomation-transact-sql"></a>sp_syspolicy_repair_policy_automation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répare l'automatisation de stratégie dans la Gestion basée sur des stratégies. Par exemple, vous pouvez utiliser cette procédure stockée pour réparer des déclencheurs et des travaux associés à des stratégies qui sont configurées pour utiliser les modes d'évaluation « Selon la planification » ou « Sur modification ».  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_syspolicy_repair_policy_automation  
```  
  
## <a name="arguments"></a>Arguments  
 Cette procédure stockée n'a pas de paramètres.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Vous devez exécuter sp_syspolicy_repair_policy_automation dans le contexte de la base de données système msdb.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle de base de données fixe PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Élévation possible des informations d’identification : les utilisateurs du rôle PolicyAdministratorRole peuvent créer des déclencheurs de serveur et planifier des exécutions de stratégie qui peuvent affecter le fonctionnement de l’instance de la [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Par exemple, les utilisateurs du rôle PolicyAdministratorRole peuvent créer une stratégie qui peut empêcher la plupart des objets soient créés dans le [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Étant donné cette possible élévation des informations d’identification, le rôle PolicyAdministratorRole doit être accordé uniquement aux utilisateurs qui sont approuvés avec contrôle de la configuration de la [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant répare l'automatisation de stratégie.  
  
```  
EXEC msdb.dbo.sp_syspolicy_repair_policy_automation;  
  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion basée sur la stratégie stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)  
  
  
