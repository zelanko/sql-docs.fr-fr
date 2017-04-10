---
title: "Sp&#233;cifier des options de sch&#233;ma | Microsoft Docs"
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
  - "schémas [réplication SQL Server], options"
  - "articles [réplication SQL Server], options de réplication transactionnelle"
  - "articles [réplication SQL Server], options de réplication de fusion"
  - "articles [réplication SQL Server], options de schéma"
ms.assetid: 1f85a479-bd6e-4023-abf7-7435a7e5b567
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Sp&#233;cifier des options de sch&#233;ma
  Cette rubrique explique comment spécifier les options de schéma dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Lors de la publication d'une table ou d'une vue, vous pouvez contrôler les options de création d'objet qui sont répliquées pour l'objet publié. Vous pouvez définir ces options lorsque l'article est créé, et vous pouvez également les modifier ultérieurement. Si vous ne spécifiez pas explicitement ces options pour un article, un jeu d'options par défaut sera défini.  
  
> [!NOTE]  
>  Les options de schéma par défaut lors de l'utilisation de procédures stockées de réplication peuvent différer des options par défaut lorsque des articles sont ajoutés à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
-   **Pour spécifier des options de schéma à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Si vous modifiez des options de schéma après la création d'une publication, vous devez générer un nouvel instantané.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Pour obtenir la liste complète des options de schéma, consultez le **@schema_option** paramètre de [sp_addarticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) et [sp_addmergearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Spécifiez les options de schéma, telles que la copie des contraintes et des déclencheurs aux abonnés, sur le **propriétés** onglet de le **Propriétés de l’Article - \< Article>** boîte de dialogue. Cet onglet est disponible dans l’Assistant Nouvelle Publication et **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d’informations sur l’utilisation de l’Assistant et accéder à la boîte de dialogue, consultez [créer une Publication](../../../relational-databases/replication/publish/create-a-publication.md) et [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Pour spécifier des options de schéma  
  
1.  Sur le **Articles** Page de l’Assistant Nouvelle Publication ou **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez un article, puis cliquez sur **Propriétés de l’Article**.  
  
2.  Sélectionnez les articles auxquels les modifications de l'option de schéma doivent s'appliquer :  
  
    -   Cliquez sur **définir les propriétés de sélectionné \< ObjectType> Article** pour lancer le **Propriétés de l’Article - \< ObjectName>** boîte de dialogue ; la propriété modifications apportées dans cette boîte de dialogue sont appliquées uniquement à l’objet qui est mis en surbrillance dans le volet de l’objet sur le **Articles** page.  
  
    -   Cliquez sur **Propriétés de tous \< ObjectType> Articles** pour lancer le **pour toutes les propriétés de \< ObjectType> Articles** boîte de dialogue ; la propriété modifications apportées dans cette boîte de dialogue sont appliquées à tous les objets de ce type dans le volet de l’objet sur le **Articles** page, y compris celles non encore activée pour la publication.  
  
        > [!NOTE]  
        >  Apportées aux propriétés dans le **pour toutes les propriétés de \< ObjectType> Articles** boîte de dialogue remplacer celles effectuées précédemment dans le **Propriétés de l’Article - \< nomobjet>** boîte de dialogue. Ainsi, si vous voulez définir un certain nombre de valeurs par défaut applicables à tous les articles d'un type d'objet mais souhaitez également définir des propriétés pour des objets spécifiques, vous devez d'abord définir les valeurs par défaut pour tous les articles. Définissez ensuite les propriétés des objets individuels.  
  
3.  Dans la **Copier les objets et paramètres sur l’abonné** et **l’objet de Destination** sections de la **propriétés** onglet de le **Propriétés de l’Article - \< Article>** boîte de dialogue, spécifiez des valeurs pour les options.  
  
4.  Modifiez les propriétés si nécessaire, puis cliquez sur **OK**.  
  
5.  Si vous êtes dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Options de schéma sont spécifiées en tant que valeur hexadécimale qui est le [| (OR au niveau du bit)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) résultat d’une ou plusieurs options. Pour plus d’informations, consultez [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) et [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).  
  
> [!NOTE]  
>  Vous devez convertir les valeurs des options de schéma du format **binaire** au format **int** avant d'effectuer une opération au niveau du bit. Pour plus d’informations, consultez [CAST et CONVERT & #40 ; Transact-SQL & #41 ;](../../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
#### Pour spécifier des options de schéma lors de la définition d'un article pour une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Spécifiez le nom de la publication à laquelle l’article appartient pour **@publication**, un nom de l’article pour **@article**, l’objet de base de données qui est publiée pour **@source_object**, le type d’objet de base de données pour **@type**, et le [| (OR au niveau du bit)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) résultat d’une ou plusieurs options de schéma pour **@schema_option**. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
#### Pour spécifier des options de schéma lors de la définition d'un article pour une publication de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Spécifiez le nom de la publication à laquelle l’article appartient pour **@publication**, un nom de l’article pour **@article**, l’objet de base de données qui est publiée pour **@source_object**, et le [| (OR au niveau du bit)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) résultat d’une ou plusieurs options de schéma pour **@schema_option**. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
#### Pour modifier des options de schéma pour un article existant dans une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md). Spécifiez le nom de la publication à laquelle l'article appartient pour **@publication** et le nom de l'article pour **@article**. Notez la valeur de la **schema_option** colonne du jeu de résultats.  
  
2.  Exécuter un [& (opérateur de bits et)](../../../t-sql/language-elements/bitwise-and-transact-sql.md) valeur pour déterminer si l’option a la valeur de l’option opération à l’aide de la valeur à l’étape 1 et le schéma de votre choix.  
  
    -   Si le résultat est **0**, l'option n'est pas définie.  
  
    -   Si le résultat correspond à la valeur de l'option, l'option est déjà définie.  
  
3.  Si l’option n’est pas définie, exécutez une [| (OR au niveau du bit)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) opération à l’aide de la valeur de l’étape 1 et la valeur d’option de schéma de votre choix.  
  
4.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md). Spécifiez le nom de la publication à laquelle l’article appartient pour **@publication**, le nom de l’article pour **@article**, une valeur de **schema_option** pour **@property**, et le résultat de l’étape 3 pour hexadécimal **@value**.  
  
5.  Exécutez l'Agent d'instantané afin de générer un nouvel instantané. Pour plus d'informations, voir [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
#### Pour modifier des options de schéma pour un article existant dans une publication de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md). Spécifiez le nom de la publication à laquelle l'article appartient pour **@publication** et le nom de l'article pour **@article**. Notez la valeur de la **schema_option** colonne du jeu de résultats.  
  
2.  Exécuter un [& (opérateur de bits et)](../../../t-sql/language-elements/bitwise-and-transact-sql.md) valeur pour déterminer si l’option a la valeur de l’option opération à l’aide de la valeur à l’étape 1 et le schéma de votre choix.  
  
    -   Si le résultat est **0**, l'option n'est pas définie.  
  
    -   Si le résultat correspond à la valeur de l'option, l'option est déjà définie.  
  
3.  Si l’option n’est pas définie, exécutez une [| (OR au niveau du bit)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) opération à l’aide de la valeur de l’étape 1 et la valeur d’option de schéma de votre choix.  
  
4.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Spécifiez le nom de la publication à laquelle l’article appartient pour **@publication**, le nom de l’article pour **@article**, une valeur de **schema_option** pour **@property**, et le résultat de l’étape 3 pour hexadécimal **@value**.  
  
5.  Exécutez l'Agent d'instantané afin de générer un nouvel instantané. Pour plus d'informations, voir [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
## Voir aussi  
 [Publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Options d'articles pour la réplication transactionnelle](../../../relational-databases/replication/transactional/article-options-for-transactional-replication.md)  
  
  