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
manager: craigg
ms.openlocfilehash: 05e5ef298e9365b63b4e66b93c0f2aa637be8312
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706997"
---
# <a name="sphelpcategory-transact-sql"></a>sp_help_category (Transact-SQL)
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
 [  **@class=**] **'***classe***'**  
 Classe faisant l'objet d'une demande d'informations. *classe* est **varchar(8)**, avec une valeur par défaut **travail**. *classe* peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**JOB**|Fournit des informations sur une catégorie de travaux.|  
|**ALERTE**|Fournit des informations sur une catégorie d'alertes.|  
|**OPÉRATEUR**|Fournit des informations sur une catégorie d'opérateurs.|  
  
 [  **@type=** ] **'***type***'**  
 Type de catégorie faisant l'objet d'une demande d'informations. *type* est **varchar(12)**, avec NULL comme valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**LOCAL**|Catégorie de travaux locale.|  
|**MULTI-SERVEUR**|Catégorie de travaux multiserveur.|  
|**NONE**|Catégorie d’une classe autre que **travail**.|  
  
 [  **@name=** ] **'***nom***'**  
 Nom de la catégorie faisant l'objet d'une demande d'informations. *nom* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@suffix=** ] *suffixe*  
 Spécifie si le **category_type** colonne du jeu de résultats est un ID ou un nom. *suffixe* est **bits**, avec une valeur par défaut **0**. **1** montre le **category_type** en tant que nom, et **0** indique qu’il a un ID.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Lorsque **@suffix** est **0**, **sp_help_category** retourne le jeu de résultats suivant :  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**category_id**|**Int**|ID de la catégorie|  
|**category_type**|**tinyint**|Type de catégorie :<br /><br /> **1** = local<br /><br /> **2** = multiserveur<br /><br /> **3** = none|  
|**nom**|**sysname**|Nom de la catégorie|  
  
 Lorsque **@suffix** est **1**, **sp_help_category** retourne le jeu de résultats suivant :  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**category_id**|**Int**|ID de la catégorie|  
|**category_type**|**sysname**|Type de catégorie : Un des **LOCAL**, **multiserveur**, ou **NONE**|  
|**nom**|**sysname**|Nom de la catégorie|  
  
## <a name="remarks"></a>Notes  
 **sp_help_category** doit être exécuté à partir de la **msdb** base de données.  
  
 Si aucun paramètre n'est spécifié, le jeu de résultats fournit des informations sur toutes les catégories de travaux.  
  
## <a name="permissions"></a>Permissions  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
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
  
  
