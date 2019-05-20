---
title: 'Leçon 4 : ajout d’une table au rapport (Reporting Services) | Microsoft Docs'
ms.date: 04/29/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 5ddf2914-bcdd-427d-8cba-0ccb8342f819
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e925dec5eb14365a6c313349599a77ffe1d7ab13
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65106006"
---
# <a name="lesson-4-adding-a-table-to-the-report-reporting-services"></a>Leçon 4 : Ajout d'une table au rapport (Reporting Services)

Une fois le dataset défini, vous pouvez commencer à concevoir le rapport. Vous créez une disposition de rapport en faisant glisser et en déposant des *objets de rapport* du volet **Boîte à outils** vers l’**Aire de conception**. Voici quelques-uns des types d’objets de rapport existants :

- Table de charge de travail
- Zone de texte
- image
- Ligne
- Rectangle
- Graphique
- Carte

Les éléments qui contiennent des lignes de données répétées de datasets sous-jacents sont appelés *régions de données*. Une fois que vous avez ajouté une région de données, vous pouvez y ajouter des champs. Un rapport de base n’aura qu’une seule région de données. Vous pouvez en ajouter de nouvelles pour afficher des informations supplémentaires, par exemple un graphique.

## <a name="add-a-table-data-region-and-fields-to-a-report-layout"></a>Ajouter une région de données de table et des champs à une mise en page de rapport

1. Sélectionnez l’onglet **Boîte à outils** dans le volet gauche du Concepteur de rapports. Avec la souris, sélectionnez l’objet **Table** et faites-le glisser vers l’aire de conception du rapport. Le Concepteur de rapports trace une région de donnée de table composée de trois colonnes au centre de l'aire de conception. Si vous ne voyez pas l’objet **Boîte à outils**, sélectionnez le menu **Affichage** > **Boîte à outils**.

    ![ssrs_ssdt_addtable](media/ssrs-ssdt-addtable.png)

    Vous pouvez également ajouter une table au rapport à partir de l’aire de conception. Cliquez avec le bouton droit sur l’aire de conception, puis sélectionnez **Insérer** > **Table**.

2. Dans le volet **Données du rapport**, développez AdventureWorksDataset pour en afficher les champs.

3. Faites glisser le champ `[Date]` du volet **Données du rapport** vers la première colonne de la table.

    > [!IMPORTANT]
    > Lorsque vous déposez ce champ dans la première colonne, deux événements se produisent. En premier lieu, le Concepteur de rapports affiche le nom du champ, appelé *expression de champ*, entre crochets : `[Date]` dans la cellule de données. En second lieu, il ajoute une étiquette de colonne à la ligne d’en-tête, juste au-dessus de l’expression de champ. Par défaut, l’étiquette de colonne porte le nom du champ. Vous pouvez sélectionner l’étiquette de colonne et taper une nouvelle valeur si vous souhaitez la modifier.

4. Faites glisser le champ `[Order]` du volet **Données du rapport** vers la deuxième colonne de la table.

5. Faites glisser le champ `[Product]` du volet **Données du rapport** vers la troisième colonne de la table.

6. Faites glisser le champ `[Qty]` vers le bord droit de la troisième colonne jusqu’à ce que vous obteniez un curseur vertical et que le pointeur de la souris prenne la forme d’un signe plus [+]. Quand vous relâchez le bouton de la souris, une quatrième colonne est créée pour l’expression de champ `[Qty]`.

    ![ssrs_tutorial_addcolumn](media/ssrs-tutorial-addcolumn.png)

7. Ajoutez le champ `[LineTotal]` de la même façon, en créant une cinquième colonne. L’étiquette de colonne « Line Total » est ajoutée. Le Concepteur de rapports crée automatiquement un nom convivial pour la colonne en fractionnant « LineTotal » en deux mots.

Le diagramme suivant représente une région de données de table qui a été remplie avec les champs suivants : Date, Order, Product, Qty et Line Total.
![rs_BasicTableDetailsDesign](media/rs-basictabledetailsdesign.png)

## <a name="preview-your-report"></a>Afficher un aperçu de votre rapport

L'affichage d'un aperçu d'un rapport vous permet de visualiser le rapport rendu sans avoir à le publier au préalable sur un serveur de rapports. Affichez un aperçu de votre rapport fréquemment lors de sa création. Ainsi, vous validerez la conception et les connexions de données, ce qui vous permettra de corriger les erreurs et les problèmes éventuels au fur et à mesure.

### <a name="to-preview-a-report"></a>Pour afficher l'aperçu d'un rapport

- Sélectionnez l’onglet **Aperçu**. Le Concepteur de rapports exécute le rapport et l’affiche en mode **Aperçu**.

    ![ssrs_ssdt_preview](media/ssrs-ssdt-preview.png)

Le diagramme suivant représente une partie du rapport en mode **Aperçu**.

   ![Aperçu, lignes de détails d’une table comportant cinq colonnes](media/rs-basictabledetailspreview.png "Aperçu, lignes de détails d’une table comportant cinq colonnes")

Examinez les valeurs de Date et Line Total. Dans la leçon suivante, vous allez apprendre à les mettre en forme pour qu’elles soient plus lisibles.

> [!NOTE]
> Dans le menu **Fichier**, sélectionnez **Enregistrer tout** pour enregistrer le rapport.

## <a name="next-steps"></a>Étapes suivantes

Vous avez ajouté une région de données de table à votre rapport, ajouté des champs à la région de données et affiché un aperçu du rapport. Dans la leçon suivante, vous allez apprendre à mettre en forme les en-têtes de colonnes et les expressions de champs. Maintenant, passez à la [Leçon 5 : Mise en forme d’un rapport &#40;Reporting Services&#41;](lesson-5-formatting-a-report-reporting-services.md).
  
## <a name="see-also"></a>Voir aussi

[Tables &#40;Générateur de rapports et SSRS&#41;](report-design/tables-report-builder-and-ssrs.md)  
[Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
