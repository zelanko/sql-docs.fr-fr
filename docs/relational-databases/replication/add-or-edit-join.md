---
title: "Ajouter ou modifier une jointure | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.addeditjoin.f1"
ms.assetid: 3b546560-720f-48b8-9d63-cf159290e9d4
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Ajouter ou modifier une jointure
  Le **Ajouter une jointure** et **Modifier une jointure** boîtes de dialogue vous permettent d’ajouter et modifier des filtres de jointure pour les publications de fusion.  
  
> [!NOTE]  
>  Pour pouvoir modifier un filtre dans une publication existante, vous devez procéder au préalable à un nouvel instantané de la publication. Si cette dernière dispose d'abonnements, ces abonnements doivent alors être réinitialisés. Pour plus d’informations sur les modifications de propriété, consultez [Publication de modification et les propriétés de l’Article](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
 Un filtre de jointure permet de filtrer une table en fonction du filtrage d'une table associée dans la publication. En règle générale, une table parente est filtrée en utilisant un filtre de lignes paramétrable. Ensuite, un ou plusieurs filtres de jointure sont définis en suivant pratiquement la même procédure que celle utilisée pour définir une jointure entre des tables. Les filtres de jointure étendent le filtre de lignes pour que les données des tables associées soient répliquées uniquement si elles correspondent à la clause de filtrage de jointure.  
  
 En règle générale, les filtres de jointure suivent les relations clé primaire/clé étrangère définies pour les tables auxquelles ils sont appliqués, mais ils ne sont pas strictement limités à ces relations. Le filtre de jointure peut être basé sur n'importe quelle logique qui compare des données associées dans deux tables d'articles.  
  
> [!IMPORTANT]  
>  Les filtres de jointure peuvent impliquer un nombre illimité de tables, mais les filtres avec un grand nombre de tables peuvent affecter les performances au cours du traitement de la fusion. Si vous générez des filtres de jointure pour au moins cinq tables, envisagez d'autres solutions : ne filtrez pas les petites tables, les tables qui ne changent pas ou les tables de recherche principales. Utilisez des filtres de jointure uniquement entre les tables qui doivent être partitionnées entre les abonnés.  
  
## Options  
 Cette boîte de dialogue implique un traitement en trois étapes pour créer un filtre de jointure entre deux tables. La création de plusieurs filtres de jointure implique que plusieurs filtres passent par la boîte de dialogue.  
  
1.  **Vérifiez la table filtrée et sélectionnez la table jointe.**  
  
    -   Si vous ajoutez une nouvelle jointure, vérifiez que la table dans le **table filtrée** zone de texte est correcte (si elle n’est pas correcte, cliquez sur **Annuler**, sélectionnez la table appropriée sur le **filtrer les lignes de Table** page, puis cliquez sur **Ajouter une jointure** pour revenir à cette boîte de dialogue). Sélectionnez ensuite une table à partir de la **table jointe** zone de liste déroulante.  
  
    -   Si vous ajoutez une jointure existante, les noms des tables sont déjà définis et ne peuvent pas être modifiés. Pour modifier les tables impliquées dans la jointure, vous devez supprimer le filtre de jointure existante sur le **filtrer les lignes de Table** page et créez une nouvelle jointure entre les différentes tables.  
  
2.  **Créez l'instruction de jointure.**  
  
    -   Si vous ajoutez une nouvelle jointure, sélectionnez **utiliser le générateur pour créer l’instruction** ou **créer manuellement l’instruction de jointure**. Si vous créez une jointure manuellement, vous pouvez utiliser le générateur.  
  
         Si vous choisissez d’utiliser le générateur, utilisez les colonnes de la grille (**association**, **colonne de table filtrée**, **opérateur**, et **colonne de table jointe**) pour créer une instruction de jointure. Chaque colonne de la grille contient une zone de liste déroulante, qui vous permet de sélectionner deux colonnes et un opérateur (**=**, **<>**, **<=**, **\<**, **>=**, **>**, **comme**). Les résultats s'affichent dans la zone de texte **Aperçu** . Si la jointure implique plusieurs paires de colonnes, sélectionnez une conjonction (**et** ou **ou**) à partir de la **association** colonne, puis entrez deux colonnes supplémentaires et un autre opérateur.  
  
         Si vous créez l'instruction manuellement, écrivez l'instruction de jointure dans la zone de texte **Instruction de jointure** . Utilisez le **filtrer les colonnes de la table** zone de liste et **joint des colonnes de la table** zone de liste pour faire glisser et déposer des colonnes dans la **instruction de jointure** zone de texte.  
  
    -   Si vous modifiez une jointure existante, vous devez effectuer les modifications manuellement.  
  
3.  **Spécifiez les options de jointure.**  
  
    -   Si la colonne sur laquelle vous la jointure de la table filtrée est unique, sélectionnez **clé Unique**. Le processus de fusion possède des fonctionnalités d'optimisation de performances spéciales disponibles si la colonne est unique.  
  
        > [!CAUTION]  
        >  La sélection de cette option indique que la relation entre les tables enfant et parent dans un filtre de jointure correspond à une relation Un à un ou Un à plusieurs. Sélectionnez uniquement cette option s'il existe une contrainte sur la colonne de jointure dans la table parent qui garantit l'unicité. Si vous ne définissez pas correctement l'option, des erreurs de non-convergence de données peuvent se produire.  
  
    -   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures uniquement. Par défaut, la réplication de fusion traite les modifications ligne par ligne lors de la synchronisation. Pour les modifications traitées comme une unité associées, sélectionnez **enregistrement logique**. Cette option est disponible uniquement si les conditions d'article et de publication d'utilisation d'enregistrements logiques sont satisfaites. Pour plus d’informations, consultez la section « Considérations pour l’utilisation enregistrements logiques » dans [modifications du groupe de lignes associées avec les enregistrements logiques](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Après avoir ajouté ou modifié un filtre, cliquez sur **OK** pour enregistrer les modifications et fermer ainsi la boîte de dialogue. Le filtre que vous spécifiez est ensuite analysé et exécuté sur la table indiquée dans la clause SELECT. Si l'instruction de filtrage contient des erreurs de syntaxe ou d'autres erreurs, vous recevrez un message et pourrez modifier l'instruction de filtrage.  
  
## Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d'une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Filtrer des données publiées](../../relational-databases/replication/publish/filter-published-data.md)   
 [Filtres de jointure](../../relational-databases/replication/merge/join-filters.md)   
 [Filtres de lignes paramétrés](../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  