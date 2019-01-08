---
title: sp_ivindexhasnullcols (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_ivindexhasnullcols
- sp_ivindexhasnullcols_TSQL
helpviewer_keywords:
- sp_ivindexhasnullcols
ms.assetid: ed2cde63-37e1-43cf-b6ba-3b6114a0f797
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5e9ab98dc5beb4f2e07ac7fa62386f9fd44703ab
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52823326"
---
# <a name="spivindexhasnullcols-transact-sql"></a>sp_ivindexhasnullcols (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Valide le fait que l'index cluster de la vue indexée est unique et qu'il ne contient aucune colonne acceptant des valeurs NULL lorsque la vue indexée va servir à la création d'une publication transactionnelle. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_ivindexhasnullcols [ @viewname = ] 'view_name'  
        , [ @fhasnullcols= ] field_has_null_columns OUTPUT  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@viewname**=] **'***nom_vue***'**  
 Nom de la vue à vérifier. *view_name* est **sysname**, sans valeur par défaut.  
  
 [ **@fhasnullcols**=] *field_has_null_columns* sortie  
 Indicateur qui précise si l'index de la vue a des colonnes acceptant des valeurs NULL. *view_name* est **sysname**, sans valeur par défaut. Retourne une valeur de **1** si l’index de la vue a des colonnes acceptant des valeurs NULL. Retourne une valeur de **0** si la vue ne contient-elle pas les colonnes qui acceptent les valeurs NULL.  
  
> [!NOTE]  
>  Si la procédure stockée elle-même renvoie un code de retour **1**, ce qui signifie que l’exécution de la procédure stockée a connu une défaillance, cette valeur est **0** et doit être ignorée.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_ivindexhasnullcols** est utilisé par la réplication transactionnelle.  
  
 Par défaut, les articles de vue indexée d'une publication sont créés en tant que tables sur les Abonnés. Toutefois, lorsque la colonne indexée autorise les valeurs NULL, la vue indexée est créée en tant que vue indexée sur l'Abonné, au lieu de l'être en tant que table. L'exécution de cette procédure stockée indique à l'utilisateur si la vue indexée active est concernée par ce problème.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou le **db_owner** rôle de base de données fixe peuvent exécuter **sp_ivindexhasnullcols**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
