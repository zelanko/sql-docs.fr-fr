---
title: Supprimer un article | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], dropping
- sp_droparticle
- sp_dropmergearticle
- deleting articles
- removing articles
- dropping articles
ms.assetid: 185b58fc-38c0-4abe-822e-6ec20066c863
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ce51b3fc6730b984c36aa44e87d3983233a3b006
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62960868"
---
# <a name="delete-an-article"></a>Supprimer un article
  Cette rubrique explique comment supprimer un article dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou des objets RMO (Replication Management Objects). Pour plus d’informations sur les conditions dans lesquelles un article peut être supprimé et pour savoir si la suppression d’un article requiert un nouvel instantané ou la réinitialisation des abonnements, consultez [Ajouter et supprimer des articles de publications existantes](add-articles-to-and-drop-articles-from-existing-publications.md).  
  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Les articles peuvent être supprimés par programme en utilisant des procédures stockées de réplication. Les procédures stockées utilisées dépendent du type de publication auquel l'article appartient.  
  
#### <a name="to-delete-an-article-from-a-snapshot-or-transactional-publication"></a>Pour supprimer un article d'une publication transactionnelle ou d'instantané  
  
1.  Exécutez [sp_droparticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droparticle-transact-sql) pour supprimer un article spécifié par **@article** d’une publication spécifiée par **@publication** . Affectez la valeur **1** à **@force_invalidate_snapshot** .  
  
2.  (Facultatif) Pour supprimer entièrement l'objet publié de la base de données, exécutez la commande `DROP <objectname>` au niveau du serveur de publication dans la base de données de publication.  
  
#### <a name="to-delete-an-article-from-a-merge-publication"></a>Pour supprimer un article d'une publication de fusion  
  
1.  Exécutez [sp_dropmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql) pour supprimer un article spécifié par **@article** d’une publication spécifiée par **@publication** . Si nécessaire, affectez la valeur **1** à **@force_invalidate_snapshot** et la valeur **1** à **@force_reinit_subscription** .  
  
2.  (Facultatif) Pour supprimer entièrement l'objet publié de la base de données, exécutez la commande `DROP <objectname>` au niveau du serveur de publication dans la base de données de publication.  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 L'exemple suivant supprime un article d'une publication transactionnelle. Dans la mesure où cette modification invalide l'instantané existant, la valeur **1** est affectée au paramètre **@force_invalidate_snapshot** .  
  
 [!code-sql[HowTo#sp_droparticle](../../../snippets/tsql/SQL15/replication/howto/tsql/droptranpub.sql#sp_droparticle)]  
  
 L'exemple suivant supprime deux articles d'une publication de fusion. Dans la mesure où ces modifications invalident l'instantané existant, la valeur **1** est affectée au paramètre **@force_invalidate_snapshot** .  
  
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepub.sql#sp_dropmergearticle)]
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergearticles.sql#sp_dropmergearticle)]  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Vous pouvez supprimer des articles par programme à l'aide des objets RMO (Replication Management Objects). Les classes RMO à utiliser pour supprimer un article dépendent du type de publication auquel l'article appartient.  
  
#### <a name="to-delete-an-article-that-belongs-to-a-snapshot-or-transactional-publication"></a>Pour supprimer un article qui appartient à une publication transactionnelle ou d'instantané.  
  
1.  Créez une connexion au serveur de publication en utilisant la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.TransArticle> .  
  
3.  Définissez les propriétés <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>et <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> .  
  
4.  Définissez la connexion créée à l'étape 1 pour la propriété <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Vérifiez la propriété <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> pour vérifier que l'article existe. Si la valeur de cette propriété est `false`, soit les propriétés de l'article ont été définies de manière incorrecte à l'étape 3, soit l'article n'existe pas.  
  
6.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> .  
  
7.  Fermez toutes les connexions.  
  
#### <a name="to-delete-an-article-that-belongs-to-a-merge-publication"></a>Pour supprimer un article qui appartient à une publication de fusion  
  
1.  Créez une connexion au serveur de publication en utilisant la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.MergeArticle> .  
  
3.  Définissez les propriétés <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>et <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> .  
  
4.  Définissez la connexion créée à l'étape 1 pour la propriété <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Vérifiez la propriété <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> pour vérifier que l'article existe. Si la valeur de cette propriété est `false`, soit les propriétés de l'article ont été définies de manière incorrecte à l'étape 3, soit l'article n'existe pas.  
  
6.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> .  
  
7.  Fermez toutes les connexions.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter et supprimer des articles de publications existantes](add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
