---
title: sp_register_custom_scripting (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_register_custom_scripting
- sp_register_custom_scripting_TSQL
helpviewer_keywords:
- sp_register_custom_scripting
ms.assetid: a8159282-de3b-4b9e-bdc9-3d3fce485c7f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 85f9104d9a9bb634dd10dfb588cf07e01d1c1fb1
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535916"
---
# <a name="spregistercustomscripting-transact-sql"></a>sp_register_custom_scripting (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La réplication permet aux procédures stockées personnalisées définies par l'utilisateur de remplacer une ou plusieurs procédures par défaut utilisées dans la réplication transactionnelle. Lorsqu'une modification de schéma est apportée à une table répliquée, ces procédures stockées sont recréées. **sp_register_custom_scripting** inscrit une procédure stockée ou [!INCLUDE[tsql](../../includes/tsql-md.md)] fichier de script qui est exécuté lorsqu’une modification de schéma se produit au script de la définition d’une nouvelle défini par l’utilisateur procédure stockée personnalisée. Cette nouvelle procédure stockée personnalisée définie par l'utilisateur doit refléter le nouveau schéma de la table. **sp_register_custom_scripting** est exécutée sur le serveur de publication sur la base de données de publication, et le fichier de script enregistré ou d’une procédure stockée est exécutée sur l’abonné lorsqu’une modification de schéma se produit.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_register_custom_scripting [ @type  = ] 'type'  
    [ @value = ] 'value'   
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @type = ] 'type'` Le type de procédure stockée personnalisée ou du script en cours d’inscription. *type* est **varchar (16)**, sans valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**insert**|La procédure stockée personnalisée inscrite est exécutée lorsqu'une instruction INSERT est répliquée.|  
|**update**|La procédure stockée personnalisée inscrite est exécutée lorsqu'une instruction UPDATE est répliquée.|  
|**delete**|La procédure stockée personnalisée inscrite est exécutée lorsqu'une instruction DELETE est répliquée.|  
|**custom_script**|Le script est exécuté à la fin du déclencheur DDL (Data Definition Language).|  
  
`[ @value = ] 'value'` Nom d’une procédure stockée ou le nom et le chemin complet vers le [!INCLUDE[tsql](../../includes/tsql-md.md)] fichier de script qui est en cours d’inscription. *valeur* est **nvarchar (1024)**, sans valeur par défaut.  
  
> [!NOTE]  
>  En spécifiant NULL pour *valeur*paramètre annule un script précédemment enregistré, ce qui est le même que l’exécution [sp_unregister_custom_scripting](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md).  
  
 Lorsque la valeur de *type* est **custom_script**, le nom et le chemin d’accès complet d’un [!INCLUDE[tsql](../../includes/tsql-md.md)] fichier de script est attendu. Sinon, *valeur* doit être le nom d’une procédure stockée inscrit.  
  
`[ @publication = ] 'publication'` Nom de la publication pour laquelle la procédure stockée personnalisée ou un script est en cours d’inscription. *publication* est **sysname**, avec une valeur par défaut **NULL**.  
  
`[ @article = ] 'article'` Nom de l’article pour lequel la procédure stockée personnalisée ou un script est enregistré. *article* est **sysname**, avec une valeur par défaut **NULL**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_register_custom_scripting** est utilisé dans la réplication transactionnelle et d’instantané.  
  
 Vous devez exécuter cette procédure stockée avant d'apporter une modification de schéma à une table répliquée. Pour plus d’informations sur l’utilisation de cette procédure stockée, consultez [régénérer des procédures transactionnelles personnalisées pour refléter les modifications de schéma](../../relational-databases/replication/transactional/transactional-articles-regenerate-to-reflect-schema-changes.md).  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe le **db_owner** rôle de base de données fixe ou le **db_ddladmin** rôle de base de données fixe peuvent exécuter **sp_ register_custom_scripting**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_unregister_custom_scripting &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md)  
  
  
