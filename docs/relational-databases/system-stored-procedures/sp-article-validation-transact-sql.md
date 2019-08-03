---
title: sp_article_validation (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_article_validation_TSQL
- sp_article_validation
helpviewer_keywords:
- sp_article_validation
ms.assetid: 44e7abcd-778c-4728-a03e-7e7e78d3ce22
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6f5ee076163ff3cf0f69daab7ceff115bf5876a6
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769021"
---
# <a name="sparticlevalidation-transact-sql"></a>sp_article_validation (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Lance une demande de validation de données pour l'article spécifié. Cette procédure stockée est exécutée sur la base de données de publication du serveur de publication et sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_article_validation [ @publication = ] 'publication'  
    [ , [ @article = ] 'article' ]  
    [ , [ @rowcount_only = ] type_of_check_requested ]  
    [ , [ @full_or_fast = ] full_or_fast ]  
    [ , [ @shutdown_agent = ] shutdown_agent ]  
    [ , [ @subscription_level = ] subscription_level ]  
    [ , [ @reserved = ] reserved ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication dans laquelle l’article existe. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @article = ] 'article'`Nom de l’article à valider. *article* est de **type sysname**et n’a pas de valeur par défaut.  
  
`[ @rowcount_only = ] type_of_check_requested`Spécifie si seul le RowCount de la table est retourné. *type_of_check_requested* est de type **smallint**, avec **1**comme valeur par défaut.  
  
 Si la **valeur est 0**, effectuez un [!INCLUDE[msCoName](../../includes/msconame-md.md)] comptage de lignes et une somme de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contrôle compatible 7,0.  
  
 Si **1**, effectuez une vérification du ROWCOUNT uniquement.  
  
 Si la condition est **2**, effectuez un comptage de lignes et une somme de contrôle binaire.  
  
`[ @full_or_fast = ] full_or_fast`Méthode utilisée pour calculer le RowCount. *full_or_fast* est de **type tinyint**et peut prendre l’une des valeurs suivantes.  
  
|**Valeur**|**Description**|  
|---------------|---------------------|  
|**0**|Effectue un comptage total à l’aide de COUNT (*).|  
|**1**|Effectue un comptage rapide à partir de **sysindexes. Rows**. Le comptage des lignes dans **sysindexes** est plus rapide que le comptage des lignes dans la table réelle. Toutefois, **sysindexes** est mis à jour tardivement et le ROWCOUNT peut ne pas être précis.|  
|**2** (par défaut)|Exécute un comptage rapide conditionnel en essayant d'abord la méthode rapide. Si la méthode rapide affiche des différences, revient à la méthode totale. Si *expected_rowcount* a la valeur NULL et la procédure stockée est en cours d’utilisation pour obtenir la valeur, un Count (\*) complète est toujours utilisée.|  
  
`[ @shutdown_agent = ] shutdown_agent`Spécifie si l’agent de distribution doit se fermer immédiatement à la fin de la validation. *shutdown_agent* est de valeur de **bit**, avec **0**comme valeur par défaut. Si la **valeur est 0**, le agent de distribution ne s’arrête pas. Si la taille est **1**, le agent de distribution s’arrête après la validation de l’article.  
  
`[ @subscription_level = ] subscription_level`Spécifie si la validation est récupérée par un ensemble d’abonnés. *subscription_level* est de valeur de **bit**, avec **0**comme valeur par défaut. Si la **valeur est 0**, la validation est appliquée à tous les abonnés. Si la valeur est **1**, la validation est appliquée uniquement à un sous-ensemble des abonnés spécifiés par les appels à **sp_marksubscriptionvalidation** dans la transaction ouverte actuelle.  
  
`[ @reserved = ] reserved` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @publisher = ] 'publisher'`Spécifie un serveur [!INCLUDE[msCoName](../../includes/msconame-md.md)] de publication non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . *Publisher* est de **type sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  l' *éditeur* ne doit pas être utilisé lors de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] demande de validation sur un serveur de publication.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_article_validation** est utilisé dans la réplication transactionnelle.  
  
 **sp_article_validation** provoque la collecte des informations de validation sur l’article spécifié et publie une demande de validation dans le journal des transactions. Lorsque l'Agent de distribution reçoit la requête, il compare les informations de validation de la requête à la table des Abonnés. Les résultats de la validation sont affichés dans les messages d'alerte du gestionnaire de réplication et de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="permissions"></a>Autorisations  
 Seuls les utilisateurs disposant d’autorisations SELECT ALL sur la table source pour l’article en cours de validation peuvent exécuter **sp_article_validation**.  
  
## <a name="see-also"></a>Voir aussi  
 [Valider les données répliquées](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [sp_marksubscriptionvalidation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-marksubscriptionvalidation-transact-sql.md)   
 [sp_publication_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md)   
 [sp_table_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-validation-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
