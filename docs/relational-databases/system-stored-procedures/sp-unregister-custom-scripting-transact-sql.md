---
title: sp_unregister_custom_scripting (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_unregister_custom_scripting_TSQL
- sp_unregister_custom_scripting
helpviewer_keywords:
- sp_unregister_custom_scripting
ms.assetid: b6e9e0d2-9144-434d-88af-4874f2582399
author: stevestein
ms.author: sstein
ms.openlocfilehash: fe6bfe4c93ccabfaaec27739f7a1fd0e09348526
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68017900"
---
# <a name="spunregistercustomscripting-transact-sql"></a>sp_unregister_custom_scripting (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette procédure stockée supprime une procédure stockée personnalisée définie par l’utilisateur ou [!INCLUDE[tsql](../../includes/tsql-md.md)] fichier de script qui a été enregistrée en exécutant [sp_register_custom_scripting](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md). Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_unregister_custom_scripting [ @type  = ] 'type'  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @type = ] 'type'` Est le type de procédure stockée personnalisée ou du script en cours de suppression. *type* est **varchar (16)** , sans valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**insert**|Procédure stockée ou script personnalisé enregistré, exécuté lors de la réplication d'une instruction INSERT.|  
|**update**|Procédure stockée ou script personnalisé enregistré, exécuté lors de la réplication d'une instruction UPDATE.|  
|**delete**|Procédure stockée ou script personnalisé enregistré, exécuté lors de la réplication d'une instruction DELETE.|  
|**custom_script**|Procédure stockée ou script personnalisé enregistré, exécuté à la fin du déclencheur du langage de définition de données (DDL, Data Definition Language).|  
  
`[ @publication = ] 'publication'` Nom de la publication pour laquelle la procédure stockée personnalisée ou un script est en cours de suppression. *publication* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @article = ] 'article'` Nom de l’article pour lequel la procédure stockée personnalisée ou un script est en cours de suppression. *article* est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_unregister_custom_scripting** est utilisé dans la réplication transactionnelle et d’instantané.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe le **db_owner** rôle de base de données fixe ou le **db_ddladmin** rôle de base de données fixe peuvent exécuter **sp_ unregister_custom_scripting**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_register_custom_scripting &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md)  
  
  
