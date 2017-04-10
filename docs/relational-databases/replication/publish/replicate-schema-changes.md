---
title: "R&#233;pliquer les modifications de sch&#233;ma | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "replication [SQL Server], schema changes"
  - "schémas [réplication SQL Server], réplication des modifications"
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
caps.latest.revision: 43
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 43
---
# R&#233;pliquer les modifications de sch&#233;ma
  Cette rubrique explique comment répliquer les modification de schéma dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Si vous apportez les modifications de schéma suivantes dans un article publié, elles sont propagées, par défaut, à [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] abonnés :  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
-   **Pour répliquer les modifications de schéma à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   L’instruction ALTER TABLE… DROP COLUMN est toujours répliquée vers tous les Abonnés dont l’abonnement contient les colonnes à supprimer, même si vous désactivez la réplication des modifications de schéma.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Si vous ne souhaitez pas répliquer les modifications de schéma pour une publication, désactivez la réplication des modifications de schéma dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Pour désactiver la réplication des modifications de schéma  
  
1.  Sur le **Options d’abonnement** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue, définissez la valeur de la **répliquer les modifications de schéma** propriété **False**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Pour propager seulement des modifications de schéma spécifiques, définissez la propriété à **True** avant une modification de schéma, puis définissez-la à **False** après avoir effectué la modification. Inversement, pour propager la plupart des modifications de schéma mais pas une modification spécifique, définissez la propriété à **False** avant la modification de schéma, puis définissez-la à **True** après avoir effectué la modification.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Vous pouvez utiliser les procédures stockées de réplication pour spécifier si ces modifications de schéma sont répliquées. La procédure stockée que vous utilisez dépend du type de publication.  
  
#### Pour créer une publication transactionnelle ou d'instantané qui ne réplique pas les modifications du schéma  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addpublication & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), la valeur de **0** pour **@replicate_ddl**. Pour plus d'informations, voir [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Pour créer une publication de fusion qui ne réplique pas les modifications du schéma  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergepublication & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), la valeur de **0** pour **@replicate_ddl**. Pour plus d'informations, voir [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Pour désactiver temporairement la réplication des modifications du schéma pour une publication transactionnelle ou d'instantané  
  
1.  Pour une publication de réplication des modifications de schéma, exécutez [sp_changepublication & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), la valeur de **replicate_ddl** pour **@property** et la valeur **0** pour **@value**.  
  
2.  Exécutez la commande DDL sur l'objet publié.  
  
3.  (Facultatif) Réactiver la réplication des modifications de schéma en exécutant [sp_changepublication & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), la valeur de **replicate_ddl** pour **@property** et la valeur **1** pour **@value**.  
  
#### Pour désactiver temporairement la réplication des modifications du schéma pour une publication de fusion  
  
1.  Pour une publication de réplication des modifications de schéma, exécutez [sp_changemergepublication & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), la valeur de **replicate_ddl** pour **@property** et la valeur **0** pour **@value**.  
  
2.  Exécutez la commande DDL sur l'objet publié.  
  
3.  (Facultatif) Réactiver la réplication des modifications de schéma en exécutant [sp_changemergepublication & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), la valeur de **replicate_ddl** pour **@property** et la valeur **1** pour **@value**.  
  
## Voir aussi  
 [Modifier le schéma dans les bases de données de publication](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [Modifier le schéma dans les bases de données de publication](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  