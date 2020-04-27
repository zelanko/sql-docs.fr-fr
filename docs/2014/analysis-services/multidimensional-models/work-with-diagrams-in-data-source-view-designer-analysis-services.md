---
title: Utiliser des diagrammes dans le concepteur de vue de source de données (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.diagramorganizerpane.f1
- sql12.asvs.dsvdesigner.findtable.f1
- sql12.asvs.dsvdesigner.diagrampane.f1
helpviewer_keywords:
- data source views [Analysis Services], diagrams
- diagrams [Analysis Services]
ms.assetid: 491fdd22-2326-4f27-a0dd-0a02faae3fd8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1aa03174d82c7319ce0c7b1cf455916e37a1b117
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66072381"
---
# <a name="work-with-diagrams-in-data-source-view-designer-analysis-services"></a>Utiliser des diagrammes dans un concepteur de vues de sources de données (Analysis Services)
  Un diagramme de vue de source de données (DSV) est une représentation visuelle des objets dans une vue DSV. Vous pouvez utiliser le diagramme en mode interactif pour ajouter, masquer, supprimer ou modifier des objets spécifiques. Vous pouvez également créer plusieurs diagramme sur la même vue DSV afin d'attirer l'attention sur un sous-ensemble des objets.  
  
 Pour modifier la zone du diagramme apparaissant dans le volet du diagramme, cliquez sur la flèche à quadruple pointes se trouvant dans le coin inférieur droit du volet et faites glisser la boîte correspondant à la sélection sur le diagramme miniature jusqu'à ce que vous sélectionniez la zone devant apparaître dans le volet du diagramme.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Ajouter un diagramme](#bkmk_add)  
  
 [Modifier ou supprimer un diagramme](#bkmk_edit)  
  
 [Rechercher des tables dans un diagramme](#bkmk_findtables)  
  
 [Organiser des objets dans un diagramme](#bkmk_arrangeobjects)  
  
 [Conserver la disposition des objets](#bkmk_preserve)  
  
##  <a name="add-a-diagram"></a><a name="bkmk_add"></a>Ajouter un diagramme  
 Les diagrammes de vue de source de données sont créés automatiquement lorsque vous créez la vue DSV. Une fois que la vue DSV existe, vous pouvez créer des diagrammes supplémentaires, les supprimer, ou masquer des objets spécifiques pour créer une représentation plus gérable de la vue DSV.  
  
 Pour créer un diagramme, cliquez avec le bouton droit n’importe où dans le volet **Bibliothèque de diagrammes** et cliquez sur **Nouveau diagramme**.  
  
 Lorsque vous définissez initialement une vue de source de données (DSV) dans un projet Analysis Services, toutes les tables et les vues ajoutées à la vue de source \<de données sont ajoutées au diagramme toutes les tables>. Ce diagramme s'affiche dans le volet Bibliothèque de diagrammes du Concepteur de vue de source de données. Les tables de ce diagramme (ainsi que leurs colonnes et relations) sont répertoriées dans le volet Tables et sont représentées graphiquement dans le volet des schémas. Toutefois, lorsque vous ajoutez des tables, des vues et des requêtes \<nommées au diagramme toutes les tables>, le nombre important d’objets dans ce diagramme rend difficile la visualisation des relations, en particulier lorsque plusieurs tables de faits sont ajoutées au diagramme, et les tables de dimension sont liées à plusieurs tables de faits.  
  
 Pour faciliter la compréhension lorsque vous souhaitez uniquement consulter un sous-ensemble de tables dans la vue de source de données, vous pouvez définir des sous-diagrammes (appelés diagrammes) composés des sous-ensembles de tables, de vues et de requêtes nommées sélectionnés dans la vue de source de données. Vous pouvez utiliser des diagrammes pour grouper des éléments de la vue de source de données en fonction des besoins de votre société ou de votre solution.  
  
 Vous pouvez grouper des tables associées et des requêtes nommées dans des diagrammes distincts à des fins professionnelles et pour faciliter la compréhension d'une vue de source de données contenant de nombreuses tables, vues et requêtes nommées. La même table ou requête nommée peut être incluse dans plusieurs diagrammes, à l' \<exception du diagramme toutes les tables>. Dans le \<diagramme toutes les tables>, tous les objets contenus dans la vue de source de données sont affichés une seule fois.  
  
##  <a name="edit-or-delete-a-diagram"></a><a name="bkmk_edit"></a>Modifier ou supprimer un diagramme  
 Lorsque vous travaillez avec un diagramme, prêtez la grande attention aux commandes utilisées pour ajouter et supprimer des objets. Par exemple, la suppression d'un objet dans un diagramme les supprime de la vue DSV. Si vous voulez le supprimer uniquement du diagramme, utilisez plutôt **Masquer la table** .  
  
 ![Capture d'écran du menu contextuel de l'espace de travail du diagramme](../media/ssas-olapdsv-diagram.gif "Capture d'écran du menu contextuel de l'espace de travail du diagramme")  
  
 Bien que vous puissiez masquer les objets individuellement, les réafficher à l'aide de la commande Afficher les tables associées retourne tous les objets associés au diagramme. Pour contrôler quels objets sont renvoyés à l'espace de travail, faites-les plutôt glisser depuis le volet Tables.  
  
##  <a name="find-tables-in-a-diagram"></a><a name="bkmk_findtables"></a>Rechercher des tables dans un diagramme  
 Si votre schéma est de grande taille, il peut être difficile de faire défiler le volet **Diagramme** jusqu’à une table particulière. Toutefois, les outils ci-dessous permettent de trouver facilement une table dans un diagramme.  
  
-   Faites défiler la liste des tables du volet **Tables** .  
  
     Pour inclure une table dans le diagramme actuellement affiché, faites-la glisser du volet **Tables** vers le volet de diagramme.  
  
     Pour centrer l’affichage d’une table déjà comprise dans le diagramme, sélectionnez-la dans le volet **Tables** .  
  
-   Localisateur de table dans le volet **schéma** : le localisateur de table est une icône en forme de flèche à quatre pointes située à l’intersection des barres de défilement verticale et horizontale dans le coin inférieur droit du volet **schéma** . Il ouvre une représentation en miniature du diagramme en cours dans le volet Diagramme. Vous pouvez utiliser cette miniature pour changer la vue dans le volet Diagramme en sélectionnant un emplacement de votre choix dans le diagramme.  
  
-   Utilisez la boîte de dialogue **Rechercher une table** , cliquez avec le bouton droit sur zone ouverte dans le volet Schéma, puis cliquez sur **Rechercher une table**. Sinon, cliquez sur la commande **Rechercher une table** dans la barre d’outils ou le menu **Vue de source de données** .  
  
     Vous pouvez taper des chaînes et des caractères génériques dans la zone Filtre pour afficher des sous-ensembles des tables du diagramme.  
  
##  <a name="arrange-objects-in-a-diagram"></a><a name="bkmk_arrangeobjects"></a>Organiser des objets dans un diagramme  
 Bien que le Concepteur de vue de source de données puisse définir plusieurs diagrammes pour rendre plus compréhensible une vue de source de données (DSV), la lecture de diagrammes contenant des dizaines de tables peut être difficile, et la réorganisation manuelle des dispositions des tables est un processus fastidieux. Le Concepteur de vue de source de données peut réorganiser automatiquement les tables dans le diagramme en cours en utilisant une présentation rectangulaire ou diagonale en fonction des relations entre les tables dans le diagramme en cours.  
  
-   Dans une présentation rectangulaire, les lignes des relations sont tracées entre des tables et non pas entre des colonnes. Les lignes des relations sont tracées horizontalement et verticalement entre les tables.  
  
-   Dans une présentation diagonale, les lignes des relations sont tracées aussi directement que possible entre les colonnes associées des tables. Une relation avec plusieurs colonnes relie la première colonne associée dans la table. Si les colonnes d'une table ne sont pas visibles, les lignes sont tracées jusqu'en haut de la table.  
  
##  <a name="preserve-object-arrangement"></a><a name="bkmk_preserve"></a>Conserver la disposition des objets  
 Après avoir réorganisé manuellement les tables comme vous le souhaitez, si vous ajoutez des tables supplémentaires au diagramme, celui-ci sera actualisé et les modifications récentes apportées à la mise en page des objets seront supprimées.  
  
 Ce comportement est probable lorsque vous ajoutez une table, ce qui provoque le déplacement d'autres tables dans la Bibliothèque de diagrammes pour pouvoir contenir la nouvelle. Il redessine ensuite le diagramme pour s'assurer que toutes les tables et les lignes de connexion sont représentées correctement. À ce stade, tous les réglages manuels de l'emplacement des objets peuvent être perdus.  
  
 Pour éviter ce problème, ajoutez toutes les tables avant d'effectuer les réglages finaux. Les objets doivent maintenant conserver leur position dans le diagramme lorsque vous le rouvrez.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de sources de données dans les modèles multidimensionnels](data-source-views-in-multidimensional-models.md)   
 [Concepteur de vue de source de données &#40;Analysis Services - Données multidimensionnelles&#41;](../data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
