---
title: sp_marksubscriptionvalidation (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_marksubscriptionvalidation
- sp_marksubscriptionvalidation_TSQL
helpviewer_keywords:
- sp_marksubscriptionvalidation
ms.assetid: e68fe0b9-5993-4880-917a-b0f661f8459b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 22b25d1a6c33d52bac27ba2735cd439732b6e9c0
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53213558"
---
# <a name="spmarksubscriptionvalidation-transact-sql"></a>sp_marksubscriptionvalidation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Marque la transaction actuellement ouverte comme transaction de validation de niveau abonnement pour l'abonné spécifié. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_marksubscriptionvalidation [ @publication = ] 'publication'  
        , [ @subscriber = ] 'subscriber'  
        , [ @destination_db = ] 'destination_db'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@publication**=] **'***publication***'**  
 Nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
 [ **@subscriber**=] **'***abonné***'**  
 Nom de l'Abonné. *abonné* est de type sysname, sans valeur par défaut.  
  
 [  **@destination_db=**] **'***destination_db***'**  
 Nom de la base de données de destination. *destination_db* est **sysname**, sans valeur par défaut.  
  
 [  **@publisher=** ] **'***publisher***'**  
 Spécifie un non - [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  *serveur de publication* ne doit pas être utilisé pour une publication qui appartienne à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_marksubscriptionvalidation** est utilisé dans la réplication transactionnelle.  
  
 **sp_marksubscriptionvalidation** ne prend pas en charge non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonnés.  
  
 Pour les non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les serveurs de publication, vous ne pouvez pas exécuter **sp_marksubscriptionvalidation** à partir d’une transaction explicite. Cela est dû au fait que les transactions explicites ne sont pas prises en charge sur la connexion du serveur lié utilisée pour accéder au serveur de publication.  
  
 **sp_marksubscriptionvalidation** doit être utilisé conjointement avec [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md), en spécifiant la valeur de **1** pour  *subscription_level*et peut être utilisé avec d’autres appels à **sp_marksubscriptionvalidation** pour marquer la transaction actuellement ouverte pour d’autres abonnés.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_marksubscriptionvalidation**.  
  
## <a name="example"></a>Exemple  
 La requête suivante peut être appliquée à la base de données de publication pour publier des commandes de validation au niveau des abonnements. Ces commandes sont récupérées par les Agents de distribution des Abonnés spécifiés. Notez que la première transaction valide l’article '**art1**', tandis que la deuxième transaction valide'**art2**». Notez également que les appels à **sp_marksubscriptionvalidation** et [sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) ont été encapsulés dans une transaction. Nous ne recommandons qu’un seul appel à [sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) par transaction. Il s’agit, car [sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) détient un verrou de table partagé sur la table source pour la durée de la transaction. Les transactions courtes sont à privilégier pour maximiser l'accès simultané.  
  
```  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art1',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art2',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Valider des données répliquées](../../relational-databases/replication/validate-replicated-data.md)  
  
  
