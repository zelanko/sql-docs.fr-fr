---
title: "Specify the Conflict Tracking and Resolution Level for Merge Articles | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "merge replication conflict resolution [SQL Server replication], levels"
  - "articles [SQL Server replication], conflict resolution"
  - "résolution des conflits [réplication SQL Server], réplication de fusion"
ms.assetid: 81e9ecb6-1d31-4a78-b32a-96f7f4d67077
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Specify the Conflict Tracking and Resolution Level for Merge Articles
  Cette rubrique explique comment spécifier le niveau de suivi et de résolution des conflits pour les articles de fusion dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Lorsqu'un abonnement à une publication de fusion est synchronisé, la réplication vérifie la présence de conflits faisant suite à de la modification des mêmes données au niveau du serveur de publication et de l'Abonné. Vous pouvez spécifier si les conflits sont détectés au niveau de la ligne, auquel cas toute modification apportée à la ligne est considérée comme un conflit, ou au niveau de la colonne, auquel cas seules les modifications apportées aux mêmes ligne et colonne sont considérées comme un conflit. La résolution des conflits pour les articles est réalisée au niveau de la ligne. Pour plus d'informations sur la détection et la résolution des conflits avec des enregistrements logiques, consultez [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
-   **Pour spécifier le niveau de suivi et de résolution des conflits pour les article de fusion à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Si vous modifiez le niveau de suivi une fois les abonnements initialisés, ces derniers doivent être réinitialisés. Pour plus d’informations sur les effets des modifications de propriétés, consultez [Publication de modification et les propriétés de l’Article](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
-   Avec le suivi au niveau des lignes et des colonnes, la résolution des conflits est toujours effectuée au niveau des lignes : la ligne gagnante remplace la ligne perdante. La réplication de fusion vous permet également de spécifier que les conflits sont suivis et résolus au niveau des enregistrements logiques, mais ces options ne sont pas disponibles à partir de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]. Pour plus d'informations sur la définition de ces options à partir des procédures stockées de réplication, consultez [Define a Logical Record Relationship Between Merge Table Articles](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Spécifier ou colonne-suivi de niveau ligne pour les articles de fusion sur le **propriétés** onglet de le **Propriétés de l’Article** boîte de dialogue, qui est disponible dans l’Assistant Nouvelle Publication et la **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d’informations sur l’utilisation de l’Assistant et accéder à la boîte de dialogue, consultez [créer une Publication](../../../relational-databases/replication/publish/create-a-publication.md) et [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Pour spécifier le suivi au niveau des lignes ou des colonnes  
  
1.  Sur le **Articles** page de l’Assistant Nouvelle Publication ou le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez une table.  
  
2.  Cliquez sur **Propriétés de l'article**, puis cliquez sur **Définir les propriétés de l'article de Table en surbrillance** ou sur **Définir les propriétés de tous les articles de table**.  
  
3.  Sur le **propriétés** onglet de le **Propriétés de l’Article \< Article>** boîte de dialogue, sélectionnez une de ces valeurs pour le **niveau de suivi** propriété : **suivi de niveau ligne** ou **suivi au niveau colonne**.  
  
4.  Si vous êtes dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour spécifier les options de suivi des conflits pour un nouvel article de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) et spécifiez une des valeurs suivantes pour **@column_tracking**:  
  
    -   **true** -utiliser le suivi au niveau colonne pour l’article.  
  
    -   **false** -suivi de niveau ligne utilisation, qui est la valeur par défaut.  
  
#### Pour modifier les options de suivi des conflits pour un article de fusion  
  
1.  Pour déterminer le conflit d’options de suivi pour un article de fusion, exécutez [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md). Notez la valeur de la **column_tracking** option dans le jeu de résultats pour l’article. Valeur **1** signifie que le suivi au niveau colonne est utilisé et la valeur **0** signifie que le suivi de niveau ligne est utilisé.  
  
2.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Spécifiez la valeur **column_tracking** pour **@property** et une de ces valeurs pour **@value**:  
  
    -   **true** -utiliser le suivi au niveau colonne pour l’article.  
  
    -   **false** -suivi de niveau ligne utilisation, qui est la valeur par défaut.  
  
     Spécifiez la valeur **1** pour les deux **@force_invalidate_snapshot** et **@force_reinit_subscription**.  
  
## Voir aussi  
 [Détection et résolution avancées des conflits de réplication de fusion](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Détection et résolution des conflits dans les enregistrements logiques](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md)   
 [Définir une relation d'enregistrement logique entre des articles de table de fusion](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md)   
 [Détecter et résoudre de conflits de réplication de fusion](../../../relational-databases/replication/merge/detect-and-resolve-merge-replication-conflicts.md)  
  
  