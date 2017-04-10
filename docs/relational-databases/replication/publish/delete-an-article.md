---
title: "Supprimer un article | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "articles [SQL Server replication], dropping"
  - "sp_droparticle"
  - "sp_dropmergearticle"
  - "deleting articles"
  - "removing articles"
  - "abandon d'articles"
ms.assetid: 185b58fc-38c0-4abe-822e-6ec20066c863
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# Supprimer un article
  Cette rubrique explique comment supprimer un article dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou des objets RMO (Replication Management Objects). Pour plus d’informations sur les conditions dans les articles peuvent être supprimés et la suppression d’un article si requiert une nouvelle capture instantanée ou la réinitialisation des abonnements, consultez [Ajouter et supprimer des Articles de Publications existantes](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
 **Dans cette rubrique**  
  
-   **Pour supprimer un article à l'aide de :**  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Les articles peuvent être supprimés par programme en utilisant des procédures stockées de réplication. Les procédures stockées utilisées dépendent du type de publication auquel l'article appartient.  
  
#### Pour supprimer un article d'une publication transactionnelle ou d'instantané  
  
1.  Exécutez [sp_droparticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md) Pour supprimer un article spécifié par **@article**, à partir d’une publication spécifiée par **@publication**. Spécifiez la valeur **1** pour **@force_invalidate_snapshot**.  
  
2.  (Facultatif) Pour supprimer entièrement l'objet publié de la base de données, exécutez la commande `DROP <objectname>` au niveau du serveur de publication dans la base de données de publication.  
  
#### Pour supprimer un article d'une publication de fusion  
  
1.  Exécutez [sp_dropmergearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md) Pour supprimer un article spécifié par **@article**, à partir d’une publication spécifiée par **@publication**. Si nécessaire, spécifiez la valeur **1** pour **@force_invalidate_snapshot** et la valeur **1** pour **@force_reinit_subscription**.  
  
2.  (Facultatif) Pour supprimer entièrement l'objet publié de la base de données, exécutez la commande `DROP <objectname>` au niveau du serveur de publication dans la base de données de publication.  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 L'exemple suivant supprime un article d'une publication transactionnelle. Étant donné que cette modification invalide l’instantané existant, une valeur de **1** est spécifié pour le **@force_invalidate_snapshot** paramètre.  
  
```  
DECLARE @publication AS sysname;  
DECLARE @article AS sysname;  
SET @publication = N'AdvWorksProductTran';   
SET @article = N'Product';   
  
-- Drop the transactional article.  
USE [AdventureWorks]  
EXEC sp_droparticle   
  @publication = @publication,   
  @article = @article,  
  @force_invalidate_snapshot = 1;  
GO  
```  
  
 L'exemple suivant supprime deux articles d'une publication de fusion. Étant donné que ces modifications invalident l’instantané existant, la valeur de **1** est spécifié pour le **@force_invalidate_snapshot** paramètre.  
  
```  
DECLARE @publication AS sysname;  
DECLARE @article1 AS sysname;  
DECLARE @article2 AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge';  
SET @article1 = N'SalesOrderDetail';   
SET @article2 = N'SalesOrderHeader';   
  
-- Remove articles from a merge publication.  
USE [AdventureWorks]  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @article1,  
  @force_invalidate_snapshot = 1;  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @article2,  
  @force_invalidate_snapshot = 1;  
GO  
```  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Vous pouvez supprimer des articles par programme à l'aide des objets RMO (Replication Management Objects). Les classes RMO à utiliser pour supprimer un article dépendent du type de publication auquel l'article appartient.  
  
#### Pour supprimer un article qui appartient à une publication transactionnelle ou d'instantané.  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.TransArticle> classe.  
  
3.  Définir le <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, et <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> Propriétés.  
  
4.  Configuration de la connexion à l’étape 1 pour les <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété.  
  
5.  Vérifier la <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> propriété pour vérifier l’existence de l’article. Si la valeur de cette propriété est **false**, soit les propriétés de l’article ont été définies de manière incorrecte à l’étape 3, soit l’article n’existe pas.  
  
6.  Appelez le <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> méthode.  
  
7.  Fermez toutes les connexions.  
  
#### Pour supprimer un article qui appartient à une publication de fusion  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergeArticle> classe.  
  
3.  Définir le <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, et <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> Propriétés.  
  
4.  Configuration de la connexion à l’étape 1 pour les <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété.  
  
5.  Vérifier la <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> propriété pour vérifier l’existence de l’article. Si la valeur de cette propriété est **false**, soit les propriétés de l’article ont été définies de manière incorrecte à l’étape 3, soit l’article n’existe pas.  
  
6.  Appelez le <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> méthode.  
  
7.  Fermez toutes les connexions.  
  
## Voir aussi  
 [Ajouter et supprimer des articles de publications existantes](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Concepts liés aux procédures stockées système de réplication](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  