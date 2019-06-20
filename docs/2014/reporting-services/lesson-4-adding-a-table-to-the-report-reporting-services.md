---
title: 'Leçon 4 : Ajouter une table au rapport (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ddf2914-bcdd-427d-8cba-0ccb8342f819
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3bb152b749041451cdb3a3294c24d8b172c49a99
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66108448"
---
# <a name="lesson-4-adding-a-table-to-the-report-reporting-services"></a>Leçon 4 : Ajouter une table au rapport (Reporting Services)
  Une fois le dataset défini, vous pouvez commencer à concevoir le rapport. Pour créer une mise en page de rapport, faites glisser les régions de données, les zones de texte, les images et autres éléments que vous souhaitez inclure dans un rapport vers l'aire de conception.  
  
 Les éléments qui contiennent des lignes de données répétées de datasets sous-jacents sont appelés *régions de données*. Un rapport de base possède une seule région de données, mais vous pouvez en ajouter davantage (pour ajouter un graphique à un rapport tabulaire, par exemple). Une fois que vous avez ajouté une région de données, vous pouvez y ajouter des champs.  
  
### <a name="to-add-a-table-data-region-and-fields-to-a-report-layout"></a>Pour ajouter une région de données de table et des champs à une mise en page de rapport  
  
1.  Dans la **Boîte à outils**, cliquez sur **Table**, puis sur l’aire de conception et faites glisser la souris. Le Concepteur de rapports trace une région de donnée de table composée de trois colonnes au centre de l'aire de conception.  
  
    > [!NOTE]  
    >  La **Boîte à outils** peut s’afficher sous la forme d’un onglet situé à gauche du volet **Données du rapport** . Pour ouvrir la **Boîte à outils**, positionnez le pointeur au-dessus de l’onglet **Boîte à outils** . Si la **Boîte à outils** n’est pas visible, cliquez sur **Boîte à outils** dans le menu **Affichage**.  
  
2.  Dans le **les données de rapport** volet, développez le **AdventureWorksDataset** jeu de données pour afficher les champs.  
  
3.  Faites glisser le champ de Date à partir de la **les données de rapport** volet vers la première colonne dans la table.  
  
     Lorsque vous déposez ce champ dans la première colonne, deux événements se produisent. En premier lieu, la cellule de données affiche le nom du champ, appelé *expression de champ*, entre crochets : `[Date]`. En second lieu, une valeur d'en-tête de colonne est automatiquement ajoutée à la ligne d'en-tête, immédiatement au-dessus de l'expression de champ. Par défaut, la colonne porte le nom du champ. Vous pouvez sélectionner le texte de la ligne d'en-tête et taper un nouveau nom.  
  
4.  Faites glisser le champ de commande à partir de la **les données de rapport** volet vers la deuxième colonne de la table.  
  
5.  Faites glisser le champ de produit à partir de la **les données de rapport** volet à la troisième colonne de la table.  
  
6.  Faites glisser le champ Qty vers le bord droit de la troisième colonne jusqu'à ce que vous obteniez un curseur vertical et que le pointeur de la souris prennent la forme d'un signe plus [+]. Lorsque vous relâchez le bouton de la souris, une quatrième colonne est créée pour `[Qty]`.  
  
7.  Ajoutez le champ LineTotal de la même façon, en créant une cinquième colonne.  
  
    > [!NOTE]  
    >  L'en-tête de colonne est Line Total. Le Concepteur de rapports crée automatiquement un nom convivial pour la colonne en fractionnant LineTotal en deux mots.  
  
     Le diagramme suivant représente une région de données de table remplie avec les champs suivants : Date, Order, Product, Qty et Ligne Total.  
  
     ![Conception, Table avec ligne d’en-tête et de ligne de détails](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "conception, Table avec ligne d’en-tête et de ligne de détails")  
  
## <a name="preview-your-report"></a>Affichage d'un aperçu d'un rapport  
 L'affichage d'un aperçu d'un rapport vous permet de visualiser le rapport rendu sans avoir à le publier au préalable sur un serveur de rapports. Vous souhaiterez probablement afficher fréquemment des aperçus du rapport pendant sa conception. Afficher un aperçu du rapport entraîne également l'exécution de la validation au niveau de la conception et des connexions de données pour vous permettre de corriger les erreurs et les problèmes avant la publication sur un serveur de rapports.  
  
#### <a name="to-preview-a-report"></a>Pour afficher l'aperçu d'un rapport  
  
-   Cliquez sur l'onglet **Aperçu** . Le Concepteur de rapports exécute le rapport et l'affiche en mode Aperçu.  
  
     Le diagramme suivant représente une partie du rapport en mode Aperçu.  
  
     ![Aperçu, lignes de détails d’une table comportant 5 colonnes](../../2014/tutorials/media/rs-basictabledetailspreview.gif "Aperçu, lignes de détails d’une table comportant 5 colonnes")  
  
     Remarquez que la devise (dans la colonne Line Total) possède six décimales après la virgule et que la date comporte un horodatage. Vous allez reprendre cette mise en forme dans la leçon suivante.  
  
> [!NOTE]  
>  Dans le menu **Fichier** , cliquez sur **Enregistrer tout** pour enregistrer le rapport.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez ajouté avec succès une région de données de table à votre rapport, ajouté des champs à la région de données et affiché un aperçu du rapport. Vous allez ensuite mettre en forme des en-têtes de colonnes et des valeurs de devise et de date. Voir [Leçon 5 : Mettre en forme un rapport &#40;Reporting Services&#41;](../reporting-services/lesson-5-formatting-a-report-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tables &#40;Générateur de rapports et SSRS&#41;](report-design/tables-report-builder-and-ssrs.md)   
 [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
  
  
