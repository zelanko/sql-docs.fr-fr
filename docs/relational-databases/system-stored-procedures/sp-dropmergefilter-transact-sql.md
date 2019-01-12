---
title: sp_dropmergefilter (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergefilter_TSQL
- sp_dropmergefilter
helpviewer_keywords:
- sp_dropmergefilter
ms.assetid: 798586d7-05f3-4a5e-bea8-a34b7b52d0fd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7de6c03b133746156f414687fd661f70b40e842e
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54128116"
---
# <a name="spdropmergefilter-transact-sql"></a>sp_dropmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un filtre de fusion. **sp_dropmergefilter** supprime toutes les colonnes de filtre de fusion définies dans le filtre de fusion à supprimer. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dropmergefilter [ @publication= ] 'publication', [ @article= ] 'article'     , [ @filtername= ] 'filtername'  
    [ , [ @force_invalidate_snapshot= ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publication=**] **'**_publication_**'**  
 Nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
 [  **@article=**] **'**_article_**'**  
 Nom de l'article. *article* est **sysname**, sans valeur par défaut.  
  
 [  **@filtername=**] **'**_filtername_**'**  
 Nom du filtre à supprimer. *FilterName* est **sysname**, sans valeur par défaut.  
  
 [  **@force_invalidate_snapshot=** ] *àce_invalidate_snapshot*  
 Active ou désactive la possibilité d'invalider un instantané. *àce_invalidate_snapshot* est un **bits**, avec une valeur par défaut **0**.  
  
 **0** Spécifie que les modifications apportées à l’article de fusion n’invalident pas l’instantané n’est pas valide.  
  
 **1** signifie que les modifications apportées à l’article de fusion peuvent invalider l’instantané n’est pas valide. Si qui est le cas, la valeur **1** autorise le nouvel instantané de se produire.  
  
 [ **@force_reinit_subscription**=] *àce_reinit_subscription*  
 Active ou désactive la possibilité de marquer un abonnement comme non valide. *àce_reinit_subscription* est un **bits**, avec une valeur par défaut **0**.  
  
 **0** Spécifie que les modifications apportées au filtre d’article de fusion n’invalident pas les abonnements n’est pas valide.  
  
 **1** signifie que les modifications apportées au filtre d’article de fusion invalident les abonnements n’est pas valide.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_dropmergefilter** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou le **db_owner** rôle de base de données fixe peuvent exécuter **sp_dropmergefilter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Changer les propriétés des publications et des articles](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_changemergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
