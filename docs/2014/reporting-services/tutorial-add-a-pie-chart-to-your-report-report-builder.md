---
title: 'Didacticiel : Ajouter un graphique à secteurs à votre rapport (Générateur de rapports) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: eaadf7bf-c312-428a-b214-0a1fbf959c3f
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 65a0db21f0334c6782c7888e7484f91058424cd1
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56290447"
---
# <a name="tutorial-add-a-pie-chart-to-your-report-report-builder"></a>Didacticiel : Ajouter un graphique à secteurs à votre rapport (Générateur de rapports)
  Les graphiques à secteurs et les graphiques en anneau affichent des données sous la forme d'une proportion de la totalité. Les graphiques en secteurs sont utilisés le plus souvent pour faire des comparaisons entre des groupes. Les graphique à secteurs et les graphiques en anneau, ainsi que les graphiques en pyramide et les graphiques en entonnoir, constituent un groupe de graphiques connus sous le nom de graphiques à base de formes. Les graphiques à base de formes n'ont pas d'axe. Lorsqu'un champ numérique est placé sur un graphique à base de formes, le graphique calcule le pourcentage de chaque valeur par rapport au total.  
  
 Lorsqu'un graphique à secteurs comporte trop de points de données, vos étiquettes de points de données peuvent devenir illisibles. Dans ce cas, envisagez d’utiliser un graphique en courbes. Pensez à utiliser des graphiques à secteurs uniquement lorsque vos données ont été agrégées en quelques points de données.  
  
 L'illustration suivante montre le graphique à secteurs que vous allez créer.  
  
 ![rs_TutorialPieChartConcave](../../2014/tutorials/media/rs-tutorialpiechartconcave.gif "rs_TutorialPieChartConcave")  
  
##  <a name="BackToTop"></a> Ce que vous allez apprendre  
 Dans ce didacticiel, vous apprendrez à :  
  
1.  [Créer un graphique à secteurs à partir de l’Assistant graphique](#Chart)  
  
2.  [Choisissez le Type de graphique](#ChartType)  
  
3.  [Afficher des pourcentages dans chaque secteur](#Percentages)  
  
4.  [Combiner des petits secteurs en un secteur](#CombineSlices)  
  
5.  [Personnaliser l’effet de dessin](#DrawingEffect)  
  
6.  [Ajouter un titre de rapport](#Title)  
  
7.  [Enregistrer le rapport](#Save)  
  
> [!NOTE]  
>  Dans ce didacticiel, les étapes de l'Assistant sont consolidées en deux procédures. Pour obtenir des instructions détaillées sur l’accès à un serveur de rapports, ajouter une source de données et ajouter un jeu de données, consultez le premier didacticiel de cette série : [Didacticiel : Création d’un rapport de tableau de base &#40;Générateur de rapports&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Durée estimée pour effectuer ce didacticiel : 10 minutes  
  
## <a name="requirements"></a>Configuration requise  
 Pour plus d’informations sur les spécifications, consultez [Éléments requis pour les didacticiels &#40;Générateur de rapports&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="Chart"></a> 1. Créer un graphique à secteurs à partir de l'Assistant Graphique  
 Dans la boîte de dialogue Mise en route, utilisez l'Assistant Graphique pour créer un dataset incorporé, choisissez une source de données partagée et créez un graphique à secteurs.  
  
> [!NOTE]  
>  Dans ce didacticiel, la requête contient les valeurs de données, afin qu'il ne soit pas nécessaire de disposer d'une source de données externe. Cela rend la requête assez longue. Dans un environnement métier, une requête ne contient pas les données. Ceci est nécessaire à des fins de formation uniquement.  
  
#### <a name="to-create-a-new-chart-report"></a>Pour créer un rapport de graphique  
  
1.  Cliquez sur **Démarrer**, pointez sur **Programmes**, sur **Générateur de rapports Microsoft SQL Server 2012**, puis cliquez sur **Générateur de rapports version**.  
  
     La boîte de dialogue Mise en route s'affiche.  
  
    > [!NOTE]  
    >  Si la boîte de dialogue Mise en route ne s'affiche pas, à partir du bouton Générateur de rapports, cliquez sur **Nouveau**.  
  
2.  Dans le volet gauche, assurez-vous que **Nouveau rapport** est sélectionné.  
  
3.  Dans le volet droit, cliquez sur **Assistant Graphique**.  
  
4.  Dans la page **Choisir un dataset** , cliquez sur **Créer un dataset**, puis sur **Suivant**.  
  
5.  Dans la page **Choisir une connexion à une source de données** , sélectionnez une source de données existante ou naviguez jusqu’au serveur de rapports, sélectionnez une source de données, puis cliquez sur **Suivant**. Vous devrez peut-être entrer un nom d'utilisateur et un mot de passe.  
  
    > [!NOTE]  
    >  La source de données que vous choisissez n'a pas d'importance, tant que vous disposez des autorisations appropriées. Vous n'allez pas récupérer de données à partir de la source de données. Pour plus d’informations, consultez [Autres manières d’obtenir une connexion de données &#40;Générateur de rapports&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
6.  Dans la page **Créer une requête** , cliquez sur **Modifier en tant que texte**.  
  
7.  Collez la requête suivante dans le volet de requête :  
  
    ```  
    SELECT 'Advanced Digital Camera' AS Product, CAST(254995.21 AS money) AS Sales  
    UNION SELECT 'Slim Digital Camera' AS Product, CAST(164499.04 AS money) AS Sales  
    UNION SELECT 'SLR Digital Camera' AS Product, CAST(782176.79 AS money) AS Sales  
    UNION SELECT 'Lens Adapter' AS Product, CAST(36333.08 AS money) AS Sales  
    UNION SELECT 'Macro Zoom Lens' AS Product, CAST(40199.3 AS money) AS Sales  
    UNION SELECT 'USB Cable' AS Product, CAST(53245.5 AS money) AS Sales  
    UNION SELECT 'Independent Filmmaker Camcorder' AS Product, CAST(452288.0 AS money) AS Sales  
    UNION SELECT 'Full Frame Digital Camera' AS Product, CAST(247250.85 AS money) AS Sales  
    ```  
  
8.  (Facultatif) Cliquez sur le bouton Exécuter (**!**) pour voir les données sur lesquelles votre graphique sera basé.  
  
9. Cliquer sur **Suivant**.  
  
##  <a name="ChartType"></a> 2. Choisir le type de graphique  
 Vous avez le choix entre plusieurs types de graphiques prédéfinis.  
  
#### <a name="to-add-a-pie-chart"></a>Pour ajouter un graphique à secteurs  
  
1.  Sur le **choisir un type de graphique** , cliquez sur **à secteurs**, puis cliquez sur **suivant**. La page **Organiser les champs du graphique** s’affiche.  
  
     Dans la page **Organiser les champs du graphique** , faites glisser le champ Product vers le volet **Catégories** . Les catégories définissent le nombre de secteurs du graphique à secteurs. Dans cet exemple, il y a huit secteurs, un pour chaque produit.  
  
2.  Faites glisser le champ Sales vers le volet **Valeurs** . Le champ Sales représente le montant des ventes réalisées pour la sous-catégorie. Le volet **Valeurs** affiche `[Sum(Sales)]` , car le graphique affiche l’agrégat pour chaque produit.  
  
3.  Cliquer sur **Suivant**.  
  
4.  Sur le **choisir un style** page, dans le volet Styles, sélectionnez un style.  
  
     Un style spécifie un style de police, un jeu de couleurs et un style de bordure. Lorsque vous sélectionnez un style, le volet Aperçu affiche un aperçu du graphique avec ce style.  
  
5.  Cliquez sur **Terminer**.  
  
     Le graphique est ajouté à l'aire de conception.  
  
6.  Cliquez sur le graphique pour afficher ses poignées. Faites glisser l'angle inférieur droit du graphique pour augmenter sa taille. Notez que la taille de l'aire de conception du rapport augmente pour s'adapter à la taille du graphique.  
  
7.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Le rapport affiche le graphique à secteurs avec huit secteurs, un pour chaque produit. La taille de chaque secteur représente les ventes de ce produit. Trois des secteurs sont assez fins.  
  
##  <a name="Percentages"></a> 3. Afficher des pourcentages dans chaque secteur  
 Sur chaque secteur du graphique, vous pouvez afficher le pourcentage de ce secteur par rapport à l'ensemble.  
  
#### <a name="to-display-percentages-in-each-slice-of-the-pie-chart"></a>Pour afficher des pourcentages dans chaque secteur du graphique à secteurs  
  
1.  Basculez en mode création de rapport.  
  
2.  Cliquez avec le bouton droit sur le graphique à secteurs, puis cliquez sur **Afficher les étiquettes de données**. Les étiquettes de données s'affichent sur le graphique.  
  
3.  Cliquez sur une étiquette, puis cliquez sur **propriétés de l’étiquette série**.  
  
4.  Dans les données de l’étiquette, dans la zone de liste déroulante, sélectionnez **#PERCENT**.  
  
     Pour afficher les valeurs sous forme de pourcentages, la propriété UseValueAsLabel doit avoir la valeur false. Si vous êtes invité à définir cette valeur dans la boîte de dialogue **Confirmer l’action** , cliquez sur **Oui**.  
  
5.  (Facultatif) Pour spécifier l’étiquette affiche le nombre de décimales, tapez `#PERCENT{Pn}` où *n* est le nombre de décimales à afficher. Par exemple, pour ne pas afficher de décimale, tapez `#PERCENT{P0}`.  
  
    > [!NOTE]  
    >  L’option**Format de nombre** de la boîte de dialogue **Propriétés de l’étiquette de la série** n’a aucun effet quand vous mettez en forme des pourcentages. Elle met uniquement en forme les étiquettes sous forme de pourcentages, mais ne calcule pas le pourcentage représenté par chaque secteur du graphique à secteurs.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Le rapport affiche le pourcentage de chaque secteur par rapport à l'ensemble.  
  
##  <a name="CombineSlices"></a> 4. Combiner de petits secteurs en un secteur  
 Trois des secteurs du graphique à secteurs sont assez petits. Vous pouvez combiner plusieurs petits secteurs en un secteur plus grand qui représente l'ensemble de ces secteurs.  
  
#### <a name="to-combine-any-slices-on-the-pie-chart-smaller-than-5-percent-into-one-slice"></a>Pour regrouper dans un même secteur les secteurs du graphique représentant moins de 5 pour cent  
  
1.  Basculez en mode création de rapport.  
  
2.  Sur le **vue** sous l’onglet le **afficher/masquer** groupe, sélectionnez **propriétés**.  
  
3.  Dans l'aire de conception, cliquez sur un secteur du graphique. Les propriétés de la série sont affichées dans le volet Propriétés.  
  
4.  Dans la section **Général** , développez le nœud **CustomAttributes** .  
  
5.  Définissez la propriété **CollectedStyle** sur **SingleSlice**.  
  
6.  Vérifiez que la propriété **CollectedThreshold** a la valeur 5.  
  
7.  Vérifiez que la propriété **CollectedThresholdUsePercent** a la valeur **True**.  
  
8.  Dans le ruban, sur le **accueil** , cliquez sur **exécuter** pour afficher un aperçu du rapport.  
  
 Dans la légende, la catégorie « Autre » est désormais présente. Le nouveau secteur regroupe tous les secteurs de moins de 5 % dans un seul secteur qui représente 6 % de l'ensemble.  
  
##  <a name="DrawingEffect"></a> 5. Personnaliser l'effet de dessin  
 Dans l'Assistant Graphique, le style par défaut d'un graphique à secteurs est Océan, qui représente un effet de dessin concave. Vous pouvez le changer après avoir exécuté l'Assistant.  
  
#### <a name="to-add-a-drawing-effect-to-the-pie-chart"></a>Pour ajouter un effet de dessin au graphique à secteurs  
  
1.  Basculez en mode création de rapport.  
  
2.  Si le volet Propriétés n'est pas déjà ouvert, sous la **vue** onglet, sélectionnez **propriétés**.  
  
3.  Double-cliquez sur le graphique à secteurs lui-même. Les propriétés de série du graphique à secteurs sont affichées dans le volet Propriétés.  
  
4.  Dans le volet Propriétés, développez le nœud **CustomAttributes** .  
  
5.  Définir le **PieDrawingStyle** à **SoftEdge**.  
  
    > [!NOTE]  
    >  Les effets de dessin et les effets en trois dimensions sont des options exclusives. Si un graphique des effets en trois dimensions appliqués, **PieDrawingStyle** n’est pas disponible dans le volet Propriétés.  
  
6.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 L'illustration suivante montre le graphique à secteurs avec l'effet de contour adouci.  
  
 ![rs_TutorialPieChartSoftEdge](../../2014/tutorials/media/rs-tutorialpiechartsoftedge.gif "rs_TutorialPieChartSoftEdge")  
  
##  <a name="Title"></a> 6. Ajouter un titre de rapport  
  
#### <a name="to-add-a-report-title"></a>Pour ajouter un titre de rapport  
  
1.  Dans l'aire de conception, cliquez sur **Cliquez pour ajouter un titre**.  
  
2.  Tapez **Ventes d’appareils photo et de caméscopes**, appuyez sur Entrée, puis tapez **En pourcentage du total des ventes**, afin d’obtenir ce qui suit :  
  
     **Ventes d’appareils photo et de caméscopes**  
  
     **En pourcentage du total des ventes**  
  
3.  Sélectionnez **caméra ventes et caméscopes**et cliquez sur le **gras** bouton à partir de la **police** section de la **accueil** onglet du ruban.  
  
4.  Sélectionnez **en tant que pourcentage du Total des ventes**, puis, dans le **police** section sur la **accueil** onglet, définissez la taille de police sur **10**.  
  
5.  (Facultatif) Vous devrez peut-être agrandir la zone de texte Titre pour contenir les deux lignes de texte.  
  
     Ce titre s'affiche alors dans la partie supérieure du rapport. En l’absence d’en-tête de page défini, les éléments situés au-dessus du corps du rapport font office d’en-tête de rapport.  
  
6.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="Save"></a> 7. Enregistrer le rapport  
  
#### <a name="to-save-the-report"></a>Pour enregistrer le rapport  
  
1.  Basculez en mode création de rapport.  
  
2.  À partir du bouton Générateur de rapports, cliquez sur **Enregistrer sous**.  
  
3.  Dans **Nom**, tapez **Graphique à secteurs des ventes**.  
  
4.  Cliquez sur **Enregistrer**.  
  
 Votre rapport est enregistré sur le serveur de rapports.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez terminé le didacticiel d'ajout d'un graphique à secteurs à votre rapport. Pour en savoir plus sur les graphiques, consultez [Graphiques &#40;Générateur de rapports et SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) et [Graphiques sparkline et barres de données &#40;Générateur de rapports et SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels &#40;Générateur de rapports&#41;](report-builder-tutorials.md)   
 [Générateur de rapports dans SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
