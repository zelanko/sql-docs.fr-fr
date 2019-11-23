---
title: sp_help_category (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_category
- sp_help_category_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_category
ms.assetid: 8cad1dcc-b43e-43bd-bea0-cb0055c84169
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1b44f5962e8241afa95b9e68cf75d493dff01ad5
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72304807"
---
# <a name="sp_help_category-transact-sql"></a>sp_help_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fournit des informations sur les classes de travaux, d'alertes ou d'opérateurs spécifiées.  
   
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_category [ [ @class = ] 'class' ]   
     [ , [ @type = ] 'type' ]   
     [ , [ @name = ] 'name' ]   
     [ , [ @suffix = ] suffix ]   
```  
  
## <a name="arguments"></a>Arguments  
`[ @class = ] 'class'` la classe sur laquelle les informations sont demandées. la classe est de *type* **varchar (8)** , avec **Job**comme valeur par défaut. la *classe* peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**JOB**|Fournit des informations sur une catégorie de travaux.|  
|**NOTIFICATION**|Fournit des informations sur une catégorie d'alertes.|  
|**AND**|Fournit des informations sur une catégorie d'opérateurs.|  
  
`[ @type = ] 'type'` le type de catégorie pour lequel des informations sont demandées. le *type* est **varchar (12)** , avec NULL comme valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**LOCAL**|Catégorie de travaux locale.|  
|**MULTI-SERVEUR**|Catégorie de travaux multiserveur.|  
|**NONE**|Catégorie pour une classe autre que **Job**.|  
  
`[ @name = ] 'name'` le nom de la catégorie pour laquelle les informations sont demandées. *Name* est de **type sysname**, avec NULL comme valeur par défaut.  
  
`[ @suffix = ] suffix` spécifie si la colonne **category_type** dans le jeu de résultats est un ID ou un nom. le *suffixe* est de **bit**, avec **0**comme valeur par défaut. **1** affiche la **category_type** sous la forme d’un nom et **0** l’affiche comme ID.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Lorsque **\@suffixe** a la valeur **0**, **sp_help_category** retourne le jeu de résultats suivant :  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|ID de la catégorie|  
|**category_type**|**tinyint**|Type de catégorie :<br /><br /> **1** = local<br /><br /> **2** = multiserveur<br /><br /> **3** = aucun|  
|**nom**|**sysname**|Nom de la catégorie|  
  
 Lorsque **\@suffixe** a la valeur **1**, **sp_help_category** retourne le jeu de résultats suivant :  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|ID de la catégorie|  
|**category_type**|**sysname**|Type de catégorie : Un serveur **local**, **plusieurs serveurs**ou **aucun**|  
|**nom**|**sysname**|Nom de la catégorie|  
  
## <a name="remarks"></a>Notes  
 **sp_help_category** doit être exécuté à partir de la base de données **msdb** .  
  
 Si aucun paramètre n'est spécifié, le jeu de résultats fournit des informations sur toutes les catégories de travaux.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de SQL Server Agent](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-local-job-information"></a>A. Renvoi d'informations sur les travaux en local  
 L'exemple suivant renvoie des informations sur les travaux qui sont administrés localement.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_category  
    @type = N'LOCAL' ;  
GO  
```  
  
### <a name="b-returning-alert-information"></a>B. Renvoi d'informations sur les alertes  
 L'exemple suivant renvoie des informations sur la catégorie d'alerte de Replication.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_category  
    @class = N'ALERT',  
    @name = N'Replication' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md)   
 [sp_delete_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_update_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-category-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
