---
title: sp_help_operator (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_operator
- sp_help_operator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_operator
ms.assetid: caedc43d-44b8-415a-897e-92923f6de3b8
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2e95006d991f9a3c8380c2144c5744e2e798c34c
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394897"
---
# <a name="sphelpoperator-transact-sql"></a>sp_help_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fournit des informations sur les opérateurs définis pour le serveur.  
  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_operator  
     { [ @operator_name = ] 'operator_name'   
     | [ @operator_id = ] operator_id }  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@operator_name=** ] **'***nom_opérateur***'**  
 Le nom de l’opérateur. *nom_opérateur* est **sysname**. Si *nom_opérateur* est ne pas spécifié, les informations sur tous les opérateurs sont renvoyées.  
  
 [  **@operator_id=** ] *operator_id*  
 Numéro d'identification de l'opérateur dont il faut obtenir des informations. *operator_id*est **int**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Soit *operator_id* ou *nom_opérateur* doit être spécifié, mais ne peut pas être spécifiés.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**Int**|Numéro d'identification de l'opérateur.|  
|**nom**|**sysname**|Nom de l’opérateur.|  
|**enabled**|**tinyint**|L'opérateur est disponible pour recevoir des notifications :<br /><br /> **1** = Oui<br /><br /> **0** = Non|  
|**email_address**|**nvarchar(100)**|Adresse de messagerie de l'opérateur.|  
|**last_email_date**|**Int**|Date de la dernière notification envoyée par courrier électronique à l'opérateur.|  
|**last_email_time**|**Int**|Heure de la dernière notification envoyée par courrier électronique à l'opérateur.|  
|**pager_address**|**nvarchar(100)**|Adresse de radiomessagerie de l'opérateur.|  
|**last_pager_date**|**Int**|Date de la dernière notification envoyée par radiomessagerie à l'opérateur.|  
|**last_pager_time**|**Int**|Heure de la dernière notification envoyée par radiomessagerie à l'opérateur.|  
|**weekday_pager_start_time**|**Int**|Début de la période pendant laquelle l'opérateur peut recevoir des notifications par radiomessagerie pendant la semaine.|  
|**weekday_pager_end_time**|**Int**|Fin de la période pendant laquelle l'opérateur peut recevoir des notifications par radiomessagerie pendant la semaine.|  
|**saturday_pager_start_time**|**Int**|Début de la période pendant laquelle l'opérateur peut recevoir des notifications par radiomessagerie le samedi.|  
|**saturday_pager_end_time**|**Int**|Fin de la période pendant laquelle l'opérateur peut recevoir des notifications par radiomessagerie le samedi.|  
|**sunday_pager_start_time**|**Int**|Début de la période pendant laquelle l'opérateur peut recevoir des notifications par radiomessagerie le dimanche.|  
|**sunday_pager_end_time**|**Int**|Fin de la période pendant laquelle l'opérateur peut recevoir des notifications par radiomessagerie le dimanche.|  
|**jours_radiomessagerie**|**tinyint**|Un masque de bits (**1** = dimanche, **64** = samedi) de jours de la semaine qui indique quand l’opérateur est disponible pour recevoir des notifications par radiomessagerie.|  
|**netsend_address**|**nvarchar(100)**|Adresse de l'opérateur pour les notifications envoyées par le réseau|  
|**last_netsend_date**|**Int**|Date de la dernière notification envoyée à l'opérateur via le réseau.|  
|**last_netsend_time**|**Int**|Heure de la dernière notification envoyée à l'opérateur via le réseau.|  
|**category_name**|**sysname**|Nom de la catégorie à laquelle appartient cet opérateur.|  
  
## <a name="remarks"></a>Notes  
 **sp_help_operator** doit être exécuté à partir de la **msdb** base de données.  
  
## <a name="permissions"></a>Permissions  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Exemples  
 Cet exemple vous renseigne sur l'opérateur `François Ajenstat`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_operator  
    @operator_name = N'François Ajenstat' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_delete_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [sp_update_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
