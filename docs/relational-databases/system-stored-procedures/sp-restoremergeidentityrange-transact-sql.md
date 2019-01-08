---
title: sp_restoremergeidentityrange (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_restoremergeidentityrange_TSQL
- sp_restoremergeidentityrange
helpviewer_keywords:
- sp_restoremergeidentityrange
ms.assetid: 7923e422-2748-40c0-b5a8-6410c48d5b70
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 88cf393ac488f6e6f4c078b9bd346a3e6cb53204
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52823053"
---
# <a name="sprestoremergeidentityrange-transact-sql"></a>sp_restoremergeidentityrange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette procédure stockée permet de mettre à jour les affectations de plage d'identité. Elle garantit le bon fonctionnement de la gestion automatique des plages d'identité lorsqu'un serveur de publication a été restauré à partir d'une sauvegarde. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_restoremergeidentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@publication** =] **'***publication***'**  
 Nom de la publication. *publication* est **sysname**, avec la valeur par défaut de **tous les**. Lorsque cet argument est spécifié, seules les plages d'identité de la publication correspondante sont restaurées.  
  
 [ **@article** =] **'***article***'**  
 Nom de l'article. *article* est **sysname**, avec une valeur par défaut **tous les**. Lorsque cet argument est spécifié, seules les plages d'identité de l'article correspondant sont restaurées.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_restoremergeidentityrange** est utilisé avec la réplication de fusion.  
  
 **sp_restoremergeidentityrange** Obtient des informations d’allocation de plage maximale d’identité du serveur de distribution et met à jour les valeurs dans le **max_used** colonne de [MSmerge_identity_range_allocations &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-identity-range-allocations-transact-sql.md) pour les articles qui utilisent la gestion de plage d’identité automatique.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_restoremergeidentityrange**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [Répliquer des colonnes d’identité](../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  
