---
title: sp_articlefilter (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_articlefilter_TSQL
- sp_articlefilter
helpviewer_keywords:
- sp_articlefilter
ms.assetid: 4c3fee32-a43f-4757-a029-30aef4696afb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 698a5941bc8e9920942e7ec7c962144b4ab24b62
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58492881"
---
# <a name="sparticlefilter-transact-sql"></a>sp_articlefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Filtre les données publiées en fonction d'un article de table. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_articlefilter [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @filter_name = ] 'filter_name' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication contenant l’article. *publication* est **sysname**, sans valeur par défaut.  
  
`[ @article = ] 'article'` Est le nom de l’article. *article* est **sysname**, sans valeur par défaut.  
  
`[ @filter_name = ] 'filter_name'` Est le nom de la procédure stockée de filtre doit être créé à partir de la *nom_de_filtre*. *nom_de_filtre* est **nvarchar (386)**, avec NULL comme valeur par défaut. Vous devez spécifier un nom unique pour le filtre d'article.  
  
`[ @filter_clause = ] 'filter_clause'` Est une restriction clause (WHERE) qui définit un filtre horizontal. Lorsque vous entrez la clause de restriction, omettez le mot clé où. *filter_clause* est **ntext**, avec NULL comme valeur par défaut.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Confirme que l’action entreprise par cette procédure stockée peut invalider un instantané existant. *àce_invalidate_snapshot* est un **bits**, avec une valeur par défaut **0**.  
  
 **0** Spécifie que les modifications de l’article n’invalident pas l’instantané n’est pas valide. Si la procédure stockée détecte que la modification requiert un nouvel instantané, une erreur se produit et aucune modification n'est effectuée.  
  
 **1** Spécifie que les modifications apportées à l’article peuvent invalider l’instantané n’est pas valide et il existe des abonnements qui nécessitent un nouvel instantané, autorise l’instantané existant soit marqué comme obsolète et de générer un nouvel instantané.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription` Confirme que l’action entreprise par cette procédure stockée peut nécessiter la réinitialisation des abonnements existants. *àce_reinit_subscription* est un **bits**, avec une valeur par défaut **0**.  
  
 **0** Spécifie que les modifications de l’article n’invalident pas besoin de la réinitialisation des abonnements. Si la procédure stockée détecte que la modification requiert la réinitialisation des abonnements, une erreur se produit et aucune modification n'est effectuée.  
  
 **1** indique que les modifications apportées à l’article entraînent la réinitialisation des abonnements existants et autorise la réinitialisation des abonnements se produise.  
  
`[ @publisher = ] 'publisher'` Spécifie un non - [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  *serveur de publication* ne doit pas être utilisé avec un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_articlefilter** est utilisé dans la réplication d’instantané ou transactionnelle.  
  
 L’exécution de **sp_articlefilter** pour un article avec des abonnements existants nécessite que les abonnements soient réinitialisés.  
  
 **sp_articlefilter** crée le filtre et insère l’ID de la procédure stockée de filtre dans le **filtre** colonne de la [sysarticles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md) table, puis Insère le texte de la clause de restriction dans la **filter_clause** colonne.  
  
 Pour créer un article avec un filtre horizontal, exécutez [sp_addarticle &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) sans aucune *filtre* paramètre. Exécutez **sp_articlefilter**, fournissant tous les paramètres y compris *filter_clause*, puis exécutez [sp_articleview &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md), en fournissant tous les paramètres y compris ce même *filter_clause*. Si le filtre existe déjà et si le **type** dans **sysarticles** est **1** (article basé sur journal), le filtre précédent est supprimé et un nouveau filtre est créé.  
  
 Si *nom_de_filtre* et *filter_clause* ne sont pas fournies, le filtre précédent est supprimé et l’ID du filtre est défini sur **0**.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articlefilter-transac_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_articlefilter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Définir et modifier un filtre de lignes statique](../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articleview &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
