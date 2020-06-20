---
title: Spécifier des options de schéma | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- schemas [SQL Server replication], options
- articles [SQL Server replication], transactional replication options
- articles [SQL Server replication], merge replication options
- articles [SQL Server replication], schema options
ms.assetid: 1f85a479-bd6e-4023-abf7-7435a7e5b567
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 52064cc189dc62152814436d2d11326a74c89ff6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85005235"
---
# <a name="specify-schema-options"></a>Spécifier des options de schéma
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
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   Si vous modifiez des options de schéma après la création d'une publication, vous devez générer un nouvel instantané.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recommandations  
  
-   Pour obtenir la liste complète des options de schéma, consultez le paramètre ** \@ schema_option** de [SP_ADDARTICLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) et [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Spécifiez les options de schéma, telles que la copie des contraintes et des déclencheurs vers les abonnés, sous l’onglet **Propriétés** de la boîte de dialogue Propriétés de l' **article- \<Article> ** . Cet onglet est disponible dans l’Assistant Nouvelle publication et dans la boîte de dialogue **Propriétés de la publication- \<Publication> ** . Pour plus d’informations sur l’utilisation de l’Assistant et sur l’accès à la boîte de dialogue, consultez [Créer une publication](create-a-publication.md) et [Afficher et modifier les propriétés d’une publication](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-schema-options"></a>Pour spécifier des options de schéma  
  
1.  Dans la page **Articles** de l’Assistant Nouvelle publication ou de la boîte de dialogue Propriétés de la **publication- \<Publication> ** , sélectionnez un article, puis cliquez sur Propriétés de **l’article**.  
  
2.  Sélectionnez les articles auxquels les modifications de l'option de schéma doivent s'appliquer :  
  
    -   Cliquez sur **définir les propriétés de \<ObjectType> l’article en surbrillance** pour ouvrir la boîte de dialogue Propriétés de **l’article- \<ObjectName> ** . les modifications de propriétés apportées dans cette boîte de dialogue sont appliquées uniquement à l’objet mis en surbrillance dans le volet objet de la page **Articles** .  
  
    -   Cliquez sur **définir les propriétés de tous les \<ObjectType> Articles** pour ouvrir la boîte **de dialogue Propriétés de tous les \<ObjectType> Articles** ; les modifications de propriétés apportées dans cette boîte de dialogue sont appliquées à tous les objets de ce type dans le volet objet de la page **Articles** , y compris ceux qui n’ont pas encore été sélectionnés pour la publication.  
  
        > [!NOTE]  
        >  Les modifications de propriétés apportées dans la boîte de dialogue **Propriétés de tous les \<ObjectType> Articles** remplacent celles effectuées précédemment dans la boîte de dialogue **Propriétés de l’article- \<ObjectName> ** . Ainsi, si vous voulez définir un certain nombre de valeurs par défaut applicables à tous les articles d'un type d'objet mais souhaitez également définir des propriétés pour des objets spécifiques, vous devez d'abord définir les valeurs par défaut pour tous les articles. Définissez ensuite les propriétés des objets individuels.  
  
3.  Dans les sections **copier les objets et les paramètres vers l’abonné** et objet de **destination** de l’onglet **Propriétés** de la boîte de dialogue Propriétés de l' **article- \<Article> ** , spécifiez des valeurs pour les options.  
  
4.  Modifiez les propriétés si nécessaire, puis cliquez sur **OK**.  
  
5.  Si vous êtes dans la boîte de dialogue Propriétés de la **publication- \<Publication> ** , cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Les options de schéma sont spécifiées sous la forme d'une valeur hexadécimale qui correspond au résultat [| (opération de bits OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) d'une ou de plusieurs options. Pour plus d'informations, consultez [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) et [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).  
  
> [!NOTE]  
>  Vous devez convertir les valeurs des options de schéma du format **binaire** au format **int** avant d'effectuer une opération au niveau du bit. Pour plus d’informations, consultez [CAST et CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-snapshot-or-transactional-publication"></a>Pour spécifier des options de schéma lors de la définition d'un article pour une publication transactionnelle ou d'instantané  
  
1.  Exécutez [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)sur la base de données de publication du serveur de publication. Spécifiez le nom de la publication à laquelle l’article appartient pour la ** \@ publication**, le nom de l' ** \@ article pour l’article, l'** objet de base de données qui est publié pour ** \@ source_object**, le type d’objet de base de données pour le ** \@ type**et le [| (Opérateur or au niveau du bit)](/sql/t-sql/language-elements/bitwise-or-transact-sql) résultat d’une ou de plusieurs options de schéma pour ** \@ schema_option**. Pour plus d’informations, consultez [définir un Article](define-an-article.md).  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-merge-publication"></a>Pour spécifier des options de schéma lors de la définition d'un article pour une publication de fusion  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Spécifiez le nom de la publication à laquelle l’article appartient pour la ** \@ publication**, le nom de l' ** \@ article pour l’article, l'** objet de base de données qui est publié pour ** \@ source_object**et le [| (Opérateur or au niveau du bit)](/sql/t-sql/language-elements/bitwise-or-transact-sql) résultat d’une ou de plusieurs options de schéma pour ** \@ schema_option**. Pour plus d’informations, consultez [définir un Article](define-an-article.md).  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-snapshot-or-transactional-publication"></a>Pour modifier des options de schéma pour un article existant dans une publication transactionnelle ou d'instantané  
  
1.  Exécutez [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)dans la base de données de publication du serveur de publication. Spécifiez le nom de la publication à laquelle l’article appartient pour la ** \@ publication** et le nom de l’article pour l' ** \@ article**. Notez la valeur de la colonne **schema_option** dans le jeu de résultats.  
  
2.  Exécutez une opération [& (Bitwise AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) en utilisant la valeur de l’étape 1 et la valeur de l’option de schéma de votre choix pour déterminer si cette option est définie.  
  
    -   Si le résultat est **0**, l'option n'est pas définie.  
  
    -   Si le résultat correspond à la valeur de l'option, l'option est déjà définie.  
  
3.  Si l'option n'est pas définie, exécutez une opération [| (opération de bits OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) en utilisant la valeur de l'étape 1 et la valeur de l'option de schéma de votre choix.  
  
4.  Exécutez [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)dans la base de données de publication du serveur de publication. Spécifiez le nom de la publication à laquelle l’article appartient pour la ** \@ publication**, le nom de l’article pour l' ** \@ article**, la valeur **schema_option** pour ** \@ propriété**et le résultat hexadécimal de l’étape 3 pour la ** \@ valeur**.  
  
5.  Exécutez l'Agent d'instantané afin de générer un nouvel instantané. Pour plus d’informations, voir [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-merge-publication"></a>Pour modifier des options de schéma pour un article existant dans une publication de fusion  
  
1.  Exécutez [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)dans la base de données de publication du serveur de publication. Spécifiez le nom de la publication à laquelle l’article appartient pour la ** \@ publication** et le nom de l’article pour l' ** \@ article**. Notez la valeur de la colonne **schema_option** dans le jeu de résultats.  
  
2.  Exécutez une opération [& (Bitwise AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) en utilisant la valeur de l’étape 1 et la valeur de l’option de schéma de votre choix pour déterminer si cette option est définie.  
  
    -   Si le résultat est **0**, l'option n'est pas définie.  
  
    -   Si le résultat correspond à la valeur de l'option, l'option est déjà définie.  
  
3.  Si l'option n'est pas définie, exécutez une opération [| (opération de bits OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) en utilisant la valeur de l'étape 1 et la valeur de l'option de schéma de votre choix.  
  
4.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql). Spécifiez le nom de la publication à laquelle l’article appartient pour la ** \@ publication**, le nom de l’article pour l' ** \@ article**, la valeur **schema_option** pour ** \@ propriété**et le résultat hexadécimal de l’étape 3 pour la ** \@ valeur**.  
  
5.  Exécutez l'Agent d'instantané afin de générer un nouvel instantané. Pour plus d’informations, voir [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Publier des données et des objets de base de données](publish-data-and-database-objects.md)   
 [Article Options for Transactional Replication](../transactional/article-options-for-transactional-replication.md)  
  
  
