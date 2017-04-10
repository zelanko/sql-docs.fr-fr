---
title: "Sp&#233;cifier qu&#39;un article de table de fusion est en t&#233;l&#233;chargement seul | Microsoft Docs"
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
  - "merge replication [SQL Server replication], download-only articles"
  - "articles [SQL Server replication], download-only"
  - "articles disponibles uniquement par téléchargement"
ms.assetid: 14839cec-6dbf-49c2-aa27-56847b09b4db
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# Sp&#233;cifier qu&#39;un article de table de fusion est en t&#233;l&#233;chargement seul
  Cette rubrique explique comment définir un article de table de fusion en téléchargement seul dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Les articles en téléchargement uniquement sont conçus pour les applications dont les données ne sont pas mises à jour au niveau des Abonnés. Pour plus d’informations, consultez [optimiser les performances de réplication de fusion avec des Articles avec](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
-   **Pour spécifier qu'un article de table de fusion est en téléchargement seul à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Si vous spécifiez qu'un article est en téléchargement seul après l'initialisation des abonnements, tous les abonnements client qui ont reçu l'aticle doivent être réinitialisés. Les abonnements serveur n'ont pas besoin d'être réinitialisés. Pour plus d’informations sur les effets des modifications de propriétés, consultez [Publication de modification et les propriétés de l’Article](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Spécifier qu’un article est en téléchargement uniquement sur le **Articles** page de l’Assistant Nouvelle Publication ou **propriétés** onglet de le **Propriétés de l’Article - \< Article>** boîte de dialogue. Cette boîte de dialogue est disponible dans l’Assistant Nouvelle Publication et **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d’informations sur l’utilisation de l’Assistant et accéder à la boîte de dialogue, consultez [créer une Publication](../../../relational-databases/replication/publish/create-a-publication.md) et [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Pour spécifier qu'un article est en téléchargement seul dans la page Articles  
  
-   Sur le **Articles** page des nouvelles Assistant Publication, sélectionnez une table, puis activez la case à cocher **table sélectionnée est en téléchargement seul**.  
  
#### Pour spécifier qu’un article est en téléchargement uniquement sur l’onglet de propriétés propriétés de l’Article - \< Article> boîte de dialogue  
  
1.  Sur le **Articles** page de l’Assistant Nouvelle Publication ou le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez une table, puis cliquez sur **Propriétés de l’Article**.  
  
2.  Cliquez sur **Définir les propriétés de l'article de la table en surbrillance** ou **Définir les propriétés de tous les articles de la table**.  
  
3.  Dans la **objet de Destination** section de la **propriétés** onglet de le **Propriétés de l’Article - \< Article>** boîte de dialogue, spécifiez une des valeurs suivantes pour **la direction de synchronisation**:  
  
    -   **Téléchargement seul pour l'Abonné, interdire les modifications de l'Abonné**  
  
    -   **Téléchargement seul pour l'Abonné, autoriser les modifications de l'Abonné**  
  
4.  Si vous êtes dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour spécifier qu'une nouvelle table de fusion est en téléchargement uniquement  
  
1.  Exécutez [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), la valeur **1** ou **2** pour le paramètre **@subscriber_upload_options**. Ces chiffres correspondent aux comportements suivants :  
  
    -   **0** -aucune restriction (valeur par défaut). Les modifications sur l'abonné sont téléchargées par le serveur de publication.  
  
    -   **1** : les modifications sont autorisées sur l’abonné, mais ils ne sont pas téléchargées sur le serveur de publication.  
  
    -   **2** -modifications ne sont pas autorisées sur l’abonné.  
  
        > [!NOTE]  
        >  Si la table source d’un article est déjà publiée dans une autre publication, la valeur de **@subscriber_upload_options** doivent être identiques pour les deux articles.  
  
#### Pour modifier un article de table fusion existant en article en téléchargement uniquement  
  
1.  Pour déterminer si un article est en téléchargement uniquement, exécutez [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md). Notez la valeur de **upload_options** pour l’article dans le résultat défini.  
  
2.  Si la valeur retournée dans l’étape 1 est **0**, exécutez [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), la valeur de **subscriber_upload_options** pour **@property**, une valeur de **1** pour **@force_invalidate_snapshot** et **@force_reinit_subscription**, et la valeur **1** ou **2** pour **@value**, qui correspond au comportement suivant :  
  
    -   **1** : les modifications sont autorisées sur l’abonné, mais ils ne sont pas téléchargées sur le serveur de publication.  
  
    -   **2** -modifications ne sont pas autorisées sur l’abonné.  
  
        > [!NOTE]  
        >  Si la table source d'un article est déjà publiée dans une autre publication, les deux articles doivent être en téléchargement uniquement ou ne pas l'être.  
  
## Voir aussi  
 [Optimiser les performances de la réplication de fusion avec les articles en téléchargement seul](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)   
 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)   
 [Afficher et modifier les propriétés d'un article](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
  