---
title: "D&#233;finir la m&#233;thode de propagation des modifications de donn&#233;es des articles transactionnels | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "transactional replication, propagation methods"
  - "Propager les modifications de données [réplication SQL Server]"
ms.assetid: 0a291582-f034-42da-a1a3-29535b607b74
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# D&#233;finir la m&#233;thode de propagation des modifications de donn&#233;es des articles transactionnels
  Cette rubrique explique comment définir la méthode de propagation pour les modifications de données d'articles transactionnels dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Par défaut, la réplication transactionnelle propage les modifications vers les Abonnés à l'aide d'un ensemble de procédures stockées pour chaque article. Vous pouvez remplacer ces procédures par des procédures personnalisées. Pour plus d’informations, consultez [spécifier comment les modifications sont propagées des Articles transactionnels](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
-   **Pour définir la méthode de propagation des modifications de données d'articles transactionnels à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
## Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   La modification des fichiers d'instantanés générés par la réplication nécessite la plus grande prudence. Vous devez tester et prendre en charge la logique personnalisée dans les procédures stockées personnalisées. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] n'assure pas la prise en charge de la logique personnalisée.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Spécifier la méthode de propagation sur le **propriétés** onglet de la **Propriétés de l’Article - \< Article>** boîte de dialogue, qui est disponible dans l’Assistant Nouvelle Publication et le **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d’informations sur l’utilisation de l’Assistant et accéder à la boîte de dialogue, consultez [créer une Publication](../../../relational-databases/replication/publish/create-a-publication.md) et [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Pour spécifier la méthode de propagation  
  
1.  Sur le **Articles** page de l’Assistant Nouvelle Publication ou le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez une table, puis cliquez sur **Propriétés de l’Article**.  
  
2.  Cliquez sur **Définir les propriétés de l'article de Table en surbrillance**.  
  
3.  Sur le **propriétés** onglet de le **Propriétés de l’Article - \< Article>** boîte de dialogue le **remise d’instruction** spécifiez la méthode de propagation pour chaque opération à l’aide la **format de remise INSERT**, **format de remise mise à jour**, et **format de remise DELETE** menus.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Si vous êtes dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
#### Pour générer et utiliser des procédures stockées personnalisées  
  
1.  Sur le **Articles** page de l’Assistant Nouvelle Publication ou le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez une table, puis cliquez sur **Propriétés de l’Article**.  
  
2.  Cliquez sur **Définir les propriétés de l'article de Table en surbrillance**.  
  
     Sur le **propriétés** onglet de le **Propriétés de l’Article - \< Article>** boîte de dialogue le **remise d’instruction** sélectionnez la syntaxe d’appel dans le menu format de remise appropriée (**format de remise INSERT**, **format de remise mise à jour**, ou **format de remise DELETE**), puis tapez le nom de la procédure à utiliser dans **procédure stockée INSERT**, **Supprimer une procédure stockée**, ou **procédure stockée de mise à jour**. Pour plus d’informations sur la syntaxe d’appel, consultez la section « Syntaxe d’appel des procédures stockées » dans [spécifier comment les modifications sont propagées des Articles transactionnels](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
4.  Si vous êtes dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
5.  Lorsque l'instantané de la publication est généré, il inclut la procédure spécifiée à l'étape précédente. Les procédures utilisent la syntaxe CALL spécifiée, mais incluent également la logique par défaut utilisée par la réplication.  
  
     Une fois l'instantané généré, accédez au dossier d'instantanés de la publication à laquelle cet article appartient, puis recherchez le fichier **.sch** dont le nom est identique à celui de l'article. Ouvrez ce fichier à l'aide du Bloc-notes ou d'un autre éditeur de texte, recherchez la commande CREATE PROCEDURE pour les procédures stockées INSERT, UPDATE ou DELETE, puis modifiez la définition de la procédure pour fournir une logique personnalisée de propagation des modifications de données. Si l'instantané est régénéré, vous devez recréer la procédure personnalisée.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 La réplication transactionnelle vous permet de contrôler comment les modifications sont propagées du serveur de publication aux Abonnés et cette méthode de propagation peut être définie par programme lorsqu'un article est créé et modifié ultérieurement à l'aide de procédures stockées de réplication.  
  
> [!NOTE]  
>  Vous pouvez spécifier une méthode de propagation différente pour chaque type d'opération DML (Data Manipulation Language) (insertion, mise à jour ou suppression) effectué sur une ligne de données publiées.  
  
 Pour plus d’informations, consultez [spécifier comment les modifications sont propagées des Articles transactionnels](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
#### Pour créer un article qui utilise des commandes Transact-SQL pour propager des modifications de données  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Spécifiez le nom de la publication à laquelle l’article appartient pour **@publication**, un nom de l’article pour **@article**, l’objet de base de données qui est publiée pour **@source_object**, et la valeur **SQL** pour au moins un des paramètres suivants :  
  
    -   **@ins_cmd** -contrôle la réplication des [Insérer](../../../t-sql/statements/insert-transact-sql.md) commandes.  
  
    -   **@upd_cmd** -contrôle la réplication des [mise à jour](../../../t-sql/queries/update-transact-sql.md) commandes.  
  
    -   **@del_cmd** -contrôle la réplication des [Supprimer](../../../t-sql/statements/delete-transact-sql.md) commandes.  
  
    > [!NOTE]  
    >  Lorsque vous spécifiez une valeur de **SQL** pour les paramètres ci-dessus, les commandes de ce type seront répliquées vers l’abonné comme approprié [!INCLUDE[tsql](../../../includes/tsql-md.md)] commande.  
  
     Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
#### Pour créer un article qui ne propage pas les modifications de données  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Spécifiez le nom de la publication à laquelle l’article appartient pour **@publication**, un nom de l’article pour **@article**, l’objet de base de données qui est publiée pour **@source_object**, et la valeur **NONE** pour au moins un des paramètres suivants :  
  
    -   **@ins_cmd** -contrôle la réplication des [Insérer](../../../t-sql/statements/insert-transact-sql.md) commandes.  
  
    -   **@upd_cmd** -contrôle la réplication des [mise à jour](../../../t-sql/queries/update-transact-sql.md) commandes.  
  
    -   **@del_cmd** -contrôle la réplication des [Supprimer](../../../t-sql/statements/delete-transact-sql.md) commandes.  
  
    > [!NOTE]  
    >  Lorsque vous spécifiez une valeur de **NONE** pour les paramètres ci-dessus, les commandes de ce type ne seront pas répliquées vers l’abonné.  
  
     Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
#### Pour créer un article avec des procédures stockées personnalisées modifiées par utilisateur  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Spécifiez le nom de la publication à laquelle l’article appartient pour **@publication**, un nom de l’article pour **@article**, l’objet de base de données qui est publiée pour **@source_object**, une valeur pour le **@schema_option** masque de bits qui contient la valeur **0 x 02** (permet la génération automatique de procédures stockées personnalisées) et au moins un des paramètres suivants :  
  
    -   **@ins_cmd** -spécifier la valeur **appel sp_MSins_*nom_article***, où ***nom_article*** est la valeur spécifiée pour **@article**.  
  
    -   **@del_cmd** -spécifier la valeur **appel sp_MSdel_*nom_article*** ou **XCALL sp_MSdel_*nom_article***, où ***nom_article*** est la valeur spécifiée pour **@article**.  
  
    -   **@upd_cmd** -spécifier la valeur **SCALL sp_MSupd_*nom_article***, **appel sp_MSupd_*nom_article***, **XCALL sp_MSupd_*nom_article***, ou **MCALL sp_MSupd_*nom_article***, où ***nom_article*** est la valeur spécifiée pour **@article**.  
  
    > [!NOTE]  
    >  Pour chacun des paramètres de commande ci-dessus, vous pouvez spécifier votre propre nom pour les procédures stockées que la réplication génère.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la syntaxe d’appel, SCALL, XCALL et MCALL, consultez [spécifier comment les modifications sont propagées des Articles transactionnels](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
     Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Une fois l'instantané généré, accédez au dossier d'instantanés de la publication à laquelle cet article appartient, puis recherchez le fichier **.sch** dont le nom est identique à celui de l'article. Ouvrez ce fichier à l'aide de Notepad.exe, recherchez la commande CREATE PROCEDURE pour les procédures stockées INSERT, UPDATE ou DELETE, puis modifiez la définition de la procédure pour fournir une logique personnalisée de propagation des modifications de données. Pour plus d’informations, consultez [spécifier comment les modifications sont propagées des Articles transactionnels](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
#### Pour créer un article avec des scripts personnalisés dans les procédures stockées personnalisées pour propager les modifications de données  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Spécifiez le nom de la publication à laquelle l’article appartient pour **@publication**, un nom de l’article pour **@article**, l’objet de base de données qui est publiée pour **@source_object**, une valeur pour le **@schema_option** masque de bits qui contient la valeur **0 x 02** (permet la génération automatique de procédures stockées personnalisées) et au moins un des paramètres suivants :  
  
    -   **@ins_cmd** -spécifier la valeur **appel sp_MSins_*nom_article***, où ***nom_article*** est la valeur spécifiée pour **@article**.  
  
    -   **@del_cmd** -spécifier la valeur **appel sp_MSdel_*nom_article*** ou **XCALL sp_MSdel_*nom_article***, où ***nom_article*** est la valeur spécifiée pour **@article**.  
  
    -   **@upd_cmd** -spécifier la valeur **SCALL sp_MSupd_*nom_article***, **appel sp_MSupd_*nom_article***, **XCALL sp_MSupd_*nom_article***, **MCALL sp_MSupd_*nom_article***, où ***nom_article*** est la valeur spécifiée pour **@article**.  
  
    > [!NOTE]  
    >  Pour chacun des paramètres de commande ci-dessus, vous pouvez spécifier votre propre nom pour les procédures stockées que la réplication génère.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la syntaxe d’appel, SCALL, XCALL et MCALL, consultez [spécifier comment les modifications sont propagées des Articles transactionnels](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
     Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Sur la base de données de publication de l’éditeur, utilisez le [ALTER PROCEDURE](../../../t-sql/statements/alter-procedure-transact-sql.md) instruction pour modifier [sp_scriptpublicationcustomprocs](../../../relational-databases/system-stored-procedures/sp-scriptpublicationcustomprocs-transact-sql.md) afin qu’il retourne un [CREATE PROCEDURE](../../../t-sql/statements/create-procedure-transact-sql.md) script d’insertion, mise à jour et procédures stockées de suppression personnalisées. Pour plus d’informations, consultez [spécifier comment les modifications sont propagées des Articles transactionnels](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
#### Pour modifier la méthode de propagation des modifications pour un article existant  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md). Spécifiez **@publication**, **@article**, une valeur de **ins_cmd**, **upd_cmd**, ou **del_cmd** pour **@property**, et la méthode de propagation appropriée pour **@value**.  
  
2.  Répétez l'étape 1 pour chaque méthode de propagation à modifier.  
  
## Voir aussi  
 [Spécifier le mode de propagation des modifications des articles transactionnels](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md)   
 [Créer, modifier et supprimer des Publications et Articles & #40 ; Réplication & #41 ;](../../../relational-databases/replication/publish/create-modify-and-delete-publications-and-articles-replication.md)  
  
  