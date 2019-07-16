---
title: sp_lookupcustomresolver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_lookupcustomresolver_TSQL
- sp_lookupcustomresolver
helpviewer_keywords:
- sp_lookupcustomresolver
ms.assetid: 356a7b8a-ae53-4fb5-86ee-fcfddbf23ddd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 274276a55a7b3e91ff85330a0810f01786a5a080
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937905"
---
# <a name="splookupcustomresolver-transact-sql"></a>sp_lookupcustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne les informations sur un gestionnaire de logique métier ou sur la valeur d'identificateur de classe (CLSID) d'un composant COM de résolveur personnalisé, qui est enregistré sur le serveur de distribution. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_lookupcustomresolver [ @article_resolver = ] 'article_resolver'   
    [, [ @resolver_clsid = ] 'resolver_clsid' OUTPUT ]  
    [ , [ @is_dotnet_assembly = ] is_dotnet_assembly OUTPUT ]  
    [ , [ @dotnet_assembly_name = ] 'dotnet_assembly_name' OUTPUT ]  
    [ , [ @dotnet_class_name = ] 'dotnet_class_name' OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @article_resolver = ] 'article_resolver'` Spécifie le nom de la logique métier personnalisée en cours de désinscription. *article_resolver* est **nvarchar (255)** , sans valeur par défaut. Si la logique d'entreprise en cours de suppression est un composant COM, ce paramètre est le nom convivial qui lui est octroyé. Si la logique d'entreprise est un assembly [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, ce paramètre est le nom de cet assembly.  
  
`[ @resolver_clsid = ] 'resolver_clsid' OUTPUT` Valeur CLSID de l’objet COM associé au nom de la logique métier personnalisée spécifiée dans le *article_resolver* paramètre. *resolver_clsid* est **nvarchar (50)** , avec NULL comme valeur par défaut.  
  
`[ @is_dotnet_assembly = ] 'is_dotnet_assembly' OUTPUT` Spécifie le type de logique métier personnalisée en cours d’inscription. *is_dotnet_assembly* est **bits**, avec 0 comme valeur par défaut. **1** indique que la logique métier personnalisée en cours d’inscription est un gestionnaire de logique métier Assembly ; **0** indique qu’il s’agit d’un composant COM.  
  
`[ @dotnet_assembly_name = ] 'dotnet_assembly_name' OUTPUT` Est le nom de l’assembly qui implémente le Gestionnaire de logique métier. *dotnet_assembly_name* est **nvarchar (255)** , avec NULL comme valeur par défaut.  
  
`[ @dotnet_class_name = ] 'dotnet_class_name' OUTPUT` Est le nom de la classe qui remplace <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> pour implémenter le Gestionnaire de logique métier. *dotnet_class_name* est **nvarchar (255)** , avec NULL comme valeur par défaut.  
  
`[ @publisher = ] 'publisher'` Est le nom du serveur de publication. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut. Utilisez ce paramètre lorsque la procédure stockée n'est pas appelée depuis le serveur de publication. Si le serveur local n'est pas spécifié, on suppose qu'il s'agit du serveur de publication.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_lookupcustomresolver** est utilisé dans la réplication de fusion.  
  
 **sp_lookupcustomresolver** retourne une valeur NULL pour *resolver_clsid* lorsque le composant n’est pas inscrit à la Distribution et la valeur « 00000000-0000-0000-0000-000000000000 » lorsque l’inscription appartient à un Assembly .NET framework enregistré comme un gestionnaire de logique métier.  
  
 **sp_lookupcustomresolver** est appelée par [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) et [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) pour valider le texte spécifié *article_resolver*.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **db_owner** rôle de base de données fixe sur la base de données de publication peut exécuter **sp_lookupcustomresolver**.  
  
## <a name="see-also"></a>Voir aussi  
 [Détection et résolution avancées des conflits de réplication de fusion](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Exécuter la logique métier lors de la synchronisation de fusion](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)   
 [Implémenter un gestionnaire de logique métier pour un article de fusion](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Spécifier un résolveur d’articles de fusion](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)   
 [sp_registercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
