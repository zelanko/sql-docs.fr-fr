---
title: sp_unregister_custom_scripting (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_unregister_custom_scripting_TSQL
- sp_unregister_custom_scripting
helpviewer_keywords:
- sp_unregister_custom_scripting
ms.assetid: b6e9e0d2-9144-434d-88af-4874f2582399
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fce6b2d16e732b76519cb0fbf66a16ca5db6928f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spunregistercustomscripting-transact-sql"></a>sp_unregister_custom_scripting (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette procédure stockée supprime une procédure stockée personnalisée définie par l’utilisateur ou [!INCLUDE[tsql](../../includes/tsql-md.md)] fichier de script qui a été enregistré par l’exécution de [sp_register_custom_scripting](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md). Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_unregister_custom_scripting [ @type  = ] 'type'  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@type**  =] **'***type***'**  
 Type de la procédure stockée personnalisée ou du script personnalisé à supprimer. *type* est **varchar (16)**, sans valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Valeur| Description|  
|-----------|-----------------|  
|**INSERT**|Procédure stockée ou script personnalisé enregistré, exécuté lors de la réplication d'une instruction INSERT.|  
|**mise à jour**|Procédure stockée ou script personnalisé enregistré, exécuté lors de la réplication d'une instruction UPDATE.|  
|**supprimer**|Procédure stockée ou script personnalisé enregistré, exécuté lors de la réplication d'une instruction DELETE.|  
|**custom_script**|Procédure stockée ou script personnalisé enregistré, exécuté à la fin du déclencheur du langage de définition de données (DDL, Data Definition Language).|  
  
 [  **@publication**  =] **'***publication***'**  
 Nom de la publication pour laquelle il faut supprimer la procédure stockée personnalisée ou le script personnalisé. *publication* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@article**  =] **'***article***'**  
 Nom de l'article pour lequel il faut supprimer la procédure stockée personnalisée ou le script personnalisé. *article* est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_unregister_custom_scripting** est utilisé dans la réplication transactionnelle et d’instantané.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe le **db_owner** rôle de base de données fixe ou la **db_ddladmin** du rôle de base de données fixe peut exécuter **sp_unregister_custom_scripting**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_register_custom_scripting &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md)  
  
  
