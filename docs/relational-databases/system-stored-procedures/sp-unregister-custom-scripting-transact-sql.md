---
description: sp_unregister_custom_scripting (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1bb9545e4a74fdf6831317ee31f36488e781239d
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89547289"
---
# <a name="sp_unregister_custom_scripting-transact-sql"></a>sp_unregister_custom_scripting (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Cette procédure stockée supprime une procédure stockée personnalisée définie par l’utilisateur ou un [!INCLUDE[tsql](../../includes/tsql-md.md)] fichier de script qui a été enregistré en exécutant [sp_register_custom_scripting](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md). Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_unregister_custom_scripting [ @type  = ] 'type'  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @type = ] 'type'` Type de la procédure stockée ou du script personnalisé en cours de suppression. *type* **varchar (16)**, sans valeur par défaut, et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**insert**|Procédure stockée ou script personnalisé enregistré, exécuté lors de la réplication d'une instruction INSERT.|  
|**update**|Procédure stockée ou script personnalisé enregistré, exécuté lors de la réplication d'une instruction UPDATE.|  
|**delete**|Procédure stockée ou script personnalisé enregistré, exécuté lors de la réplication d'une instruction DELETE.|  
|**custom_script**|Procédure stockée ou script personnalisé enregistré, exécuté à la fin du déclencheur du langage de définition de données (DDL, Data Definition Language).|  
  
`[ @publication = ] 'publication'` Nom de la publication pour laquelle la procédure stockée ou le script personnalisé est en cours de suppression. *publication* est de **type sysname**, avec NULL comme valeur par défaut.  
  
`[ @article = ] 'article'` Nom de l’article pour lequel la procédure stockée ou le script personnalisé est en cours de suppression. *article* est de **type sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_unregister_custom_scripting** est utilisé dans la réplication transactionnelle et d’instantané.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** , du rôle de base de données fixe **db_owner** ou du rôle de base de données fixe **db_ddladmin** peuvent exécuter **sp_unregister_custom_scripting**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_register_custom_scripting &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md)  
  
  
