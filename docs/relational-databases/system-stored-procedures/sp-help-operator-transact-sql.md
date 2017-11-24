---
title: sp_help_operator (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_operator
- sp_help_operator_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_operator
ms.assetid: caedc43d-44b8-415a-897e-92923f6de3b8
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 392586d2f3ea34b6914cb7bf34757d0481e890a9
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
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
|**id**|**int**|Numéro d'identification de l'opérateur.|  
|**nom**|**sysname**|Nom de l’opérateur.|  
|**activé**|**tinyint**|L'opérateur est disponible pour recevoir des notifications :<br /><br /> **1** = Oui<br /><br /> **0** = non|  
|**email_address**|**nvarchar (100)**|Adresse de messagerie de l'opérateur.|  
|**last_email_date**|**int**|Date de la dernière notification envoyée par courrier électronique à l'opérateur.|  
|**last_email_time**|**int**|Heure de la dernière notification envoyée par courrier électronique à l'opérateur.|  
|**adresse_radiomessagerie**|**nvarchar (100)**|Adresse de radiomessagerie de l'opérateur.|  
|**last_pager_date**|**int**|Date de la dernière notification envoyée par radiomessagerie à l'opérateur.|  
|**last_pager_time**|**int**|Heure de la dernière notification envoyée par radiomessagerie à l'opérateur.|  
|**weekday_pager_start_time**|**int**|Début de la période pendant laquelle l'opérateur peut recevoir des notifications par radiomessagerie pendant la semaine.|  
|**au vendredi**|**int**|Fin de la période pendant laquelle l'opérateur peut recevoir des notifications par radiomessagerie pendant la semaine.|  
|**heure_début_radiomessagerie_samedi**|**int**|Début de la période pendant laquelle l'opérateur peut recevoir des notifications par radiomessagerie le samedi.|  
|**heure_fin_radiomessagerie_samedi**|**int**|Fin de la période pendant laquelle l'opérateur peut recevoir des notifications par radiomessagerie le samedi.|  
|**heure_début_radiomessagerie_dimanche**|**int**|Début de la période pendant laquelle l'opérateur peut recevoir des notifications par radiomessagerie le dimanche.|  
|**sunday_pager_end_time**|**int**|Fin de la période pendant laquelle l'opérateur peut recevoir des notifications par radiomessagerie le dimanche.|  
|**jours_radiomessagerie**|**tinyint**|Un masque de bits (**1** = dimanche, **64** = samedi) de jours de la semaine indiquant à quel moment l’opérateur peut recevoir des notifications par radiomessagerie.|  
|**netsend_address**|**nvarchar (100)**|Adresse de l'opérateur pour les notifications envoyées par le réseau|  
|**last_netsend_date**|**int**|Date de la dernière notification envoyée à l'opérateur via le réseau.|  
|**last_netsend_time**|**int**|Heure de la dernière notification envoyée à l'opérateur via le réseau.|  
|**category_name**|**sysname**|Nom de la catégorie à laquelle appartient cet opérateur.|  
  
## <a name="remarks"></a>Notes  
 **sp_help_operator** doit être exécuté à partir de la **msdb** base de données.  
  
## <a name="permissions"></a>Permissions  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
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
 [sp_add_operator &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_delete_operator &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [sp_update_operator &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
