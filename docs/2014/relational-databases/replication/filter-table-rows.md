---
title: Filtrer les lignes de la table | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.filtertablerows.f1
ms.assetid: 005f5c71-0401-490e-8823-adc54a2e9675
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dd8d9242b688592870b568db0df27b20f6040d63
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010602"
---
# <a name="filter-table-rows"></a>Filtrer les lignes de la table
  La page **Filtrer les lignes de la table** vous permet d'effectuer les opérations suivantes :  
  
-   Permet d'appliquer des filtres de lignes statiques à des articles de table dans des publications d'instantané, transactionnelles et de fusion.  
  
-   Permet d'appliquer des filtres de lignes paramétrés à des articles de table dans des publications de fusion.  
  
-   Utilisez les filtres de jointure afin d'étendre les filtres des articles de table de fusion aux articles de table associés.  
  
 Pour plus d’informations sur les options de filtrage, consultez [Filtrer des données publiées](publish/filter-published-data.md). Le filtrage peut être modifié dans la page **Filtrer les lignes** de la boîte de dialogue **Propriétés de la publication** .  
  
 Pour accroître au maximum les performances de votre application et réduire le stockage distant nécessaire, ou pour limiter la disponibilité de certaines données à des abonnés spécifiques, vous pouvez publier uniquement les données requises. Une publication peut comporter simultanément des tables filtrées et non filtrées. Par exemple, vous pouvez inclure l'intégralité de la table des produits de l'entreprise (non filtrée) et utiliser les filtres de lignes pour générer une table filtrée des clients d'une région particulière. En filtrant les données publiées, vous pouvez :  
  
-   Réduire la quantité de données envoyées via le réseau.  
  
-   Réduire la quantité d’espace de stockage requis sur l’abonné.  
  
-   Personnaliser les publications et les applications en fonction des exigences des abonnés individuels.  
  
-   Éviter ou réduire les conflits lorsque les abonnés mettent à jour les données car différentes partitions de données peuvent être envoyées vers différents abonnés (deux abonnés ne mettent pas à jour les mêmes valeurs de données).  
  
-   Éviter de transmettre des données sensibles. Vous pouvez utiliser les filtres de lignes et de colonne pour limiter l'accès d'un abonné aux données. Pour les réplications de fusion, vous devez tenir compte de certains points de sécurité si vous utilisez un filtre paramétré qui inclut HOST_NAME(). Pour plus d'informations, consultez la section « Filtrage avec HOST_NAME() » dans [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).  
  
 Aucun filtre ne doit inclure le `rowguidcol` utilisé par la réplication pour identifier les lignes. Par défaut, il s'agit de la colonne ajoutée lorsque vous avez configuré la réplication de fusion et qui a pour nom **rowguid**.  
  
## <a name="options"></a>Options  
 **Tables filtrées**  
 Ce volet est rempli avec des filtres à mesure que vous les ajoutez aux articles de table dans la publication. Les tables avec filtres de lignes sont affichées en tant que nœuds de niveau supérieur dans le volet. Pour les publications de fusion, les tables auxquelles les filtres ont été étendus par le biais d'un filtre de jointure sont affichées en tant que nœuds enfants.  
  
 **Ajouter**  
 Cliquez sur **Ajouter** pour lancer une boîte de dialogue qui vous permet de filtrer les articles de table. Si vous cliquez sur **Ajouter** pour une publication d'instantané ou transactionnelle, une boîte de dialogue s'ouvre immédiatement. Si vous cliquez sur **Ajouter** pour une publication de fusion, trois choix s'affichent : **Ajouter un filtre**; **Ajouter une jointure pour étendre le filtre sélectionné**; **Générer automatiquement des filtres**.  
  
-   Sélectionnez **Ajouter un filtre** pour ouvrir la boîte de dialogue du **même nom** . Elle vous permet d'appliquer des filtres de lignes à un article de table. Dans la boîte de dialogue **Ajouter un filtre** , vous pouvez, par exemple, indiquer qu'une table contenant des données client doit uniquement comporter des données relatives aux clients français lors de sa réplication vers des abonnés.  
  
-   Sélectionnez **Ajouter une jointure pour étendre le filtre sélectionné** afin de lancer la boîte de dialogue **Ajouter une jointure** . La boîte de dialogue **Ajouter une jointure** vous permet d'étendre un filtre de lignes de sorte à filtrer les données dans les tables associées à la table contenant le filtre de ligne. Par exemple, si une table de clients est filtrée de manière à ne contenir que les données relatives aux clients français et qu'une table de commandes client lui est associée, vous pouvez définir une jointure entre les deux tables afin que la table de commandes inclue uniquement les commandes émanant de clients français.  
  
    > [!NOTE]  
    >  Cette option est uniquement disponible si vous sélectionnez d'abord la table de base de la jointure dans le volet du filtre.  
  
-   Sélectionnez **Générer automatiquement des filtres** pour ouvrir la boîte de dialogue **Générer des filtres** . Cette boîte de dialogue vous permet de définir un filtre de lignes pour une table dans une publication de fusion afin que la réplication s'étende automatiquement aux autres tables associées par le biais de relations de clés étrangères. Par exemple, une publication peut inclure trois tables : une table de clients, une table de commandes (avec une clé étrangère pour la table de clients) et une table avec les détails des commandes (avec une clé étrangère pour la table de commandes). Définissez un filtre de lignes pour la table client afin que la réplication s'étende aux autres tables.  
  
    > [!NOTE]  
    >  Lorsque les filtres sont générés automatiquement par réplication, tous les filtres existants dans la publication sont supprimés. Pour inclure les filtres générés automatiquement et ceux définis manuellement, commencez par générer des filtres. Vous pouvez uniquement spécifier un jeu de filtres générés automatiquement pour chaque publication.  
  
 **Modifier**  
 Sélectionnez un filtre de lignes ou de jointure dans le volet des filtres et cliquez sur **Modifier** pour ouvrir la boîte de dialogue **Modifier le filtre** ou **Modifier une jointure** .  
  
 **Supprimer**  
 Sélectionnez un filtre de lignes ou de jointure dans le volet des filtres et cliquez sur **Supprimer** pour supprimer le filtre.  
  
 **Rechercher une table**  
 Fusionnez les publications uniquement avec des filtres de jointure. Cliquez sur **Rechercher une table** pour trouver une table dans une arborescence de filtres complexe. Dans une base de données comportant des relations complexes, une table peut être jointe à plusieurs tables et apparaître dès lors à plusieurs endroits dans l'arborescence des filtres.  
  
 La table réelle apparaît à un seul endroit dans l'arborescence. Aux autres endroits, elle est représentée par un raccourci. Ce raccourci n'est qu'une référence à la table ; il n'affiche pas les nœuds enfants de la table. Un nœud de raccourci est marqué par une flèche de raccourci et le développement de ce nœud affiche le texte **cliquez sur Rechercher une \<tablename> table pour afficher la table de **.  
  
 Choisissez un nœud de raccourci dans le volet et cliquez sur **Rechercher une table**. Ce volet est développé et la table est mise en surbrillance. Si vous cliquez sur **Rechercher une table** sans sélectionner un nœud de raccourci, une boîte de dialogue **Rechercher une table** s'ouvre.  
  
 **Filter**  
 Contient la définition [!INCLUDE[tsql](../../includes/tsql-md.md)] du filtre sélectionné dans le volet.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Publication](publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d’une publication](publish/view-and-modify-publication-properties.md)   
 [Filtrer des données publiées](publish/filter-published-data.md)   
 [Filtres de jointure](merge/join-filters.md)   
 [Filtres de lignes paramétrés](merge/parameterized-filters-parameterized-row-filters.md)   
 [Publier des données et des objets de base de données](publish/publish-data-and-database-objects.md)  
  
  
