---
title: 'Didacticiel : Ajouter un histogramme à votre rapport (Générateur de rapports) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 63480059-b7b9-44b5-9d7f-91780db708b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 24c8e48ef26d3db2bc7662a36d40725c84b1bbc7
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56026768"
---
# <a name="tutorial-add-a-column-chart-to-your-report-report-builder"></a>Didacticiel : Ajouter un histogramme à votre rapport (Générateur de rapports)
  Un histogramme affiche une série sous la forme d'un ensemble de barres verticales regroupées par catégorie. Un histogramme s'avère utile pour :  
  
-   montrer l'évolution des données sur une période ;  
  
-   comparer la valeur relative de plusieurs séries.  
  
-   afficher une moyenne mobile pour montrer les tendances.  
  
 L'illustration suivante montre l'histogramme que vous allez créer, avec une moyenne mobile.  
  
 ![rs_TutorialColChartFinished](../../2014/tutorials/media/rs-tutorialcolchartfinished.gif "rs_TutorialColChartFinished")  
  
##  <a name="BackToTop"></a> Ce que vous allez apprendre  
 Dans ce didacticiel, vous apprendrez à effectuer les tâches suivantes :  
  
1.  [Créer un graphique à partir de l’Assistant graphique](#Chart)  
  
2.  [Choisissez le Type de graphique](#ChartType)  
  
3.  [Mettre en forme et étiqueter l’axe Horizontal](#Horizontal)  
  
4.  [Déplacer la légende](#Legend)  
  
5.  [Titre du graphique](#ChartTitle)  
  
6.  [Mettre en forme et étiqueter l’axe Vertical](#Vertical)  
  
7.  [Ajouter une moyenne mobile](#Average)  
  
8.  [Ajouter un titre de rapport](#Title)  
  
9. [Enregistrer le rapport](#Save)  
  
> [!NOTE]  
>  Dans ce didacticiel, les étapes de l'Assistant sont consolidées en une seule procédure. Pour obtenir des instructions détaillées sur l’accès à un serveur de rapports, choisissez une source de données et créer un jeu de données, consultez le premier didacticiel de cette série : [Didacticiel : Création d’un rapport de tableau de base &#40;Générateur de rapports&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Durée estimée pour effectuer ce didacticiel : 15 minutes.  
  
## <a name="requirements"></a>Configuration requise  
 Pour plus d’informations sur les spécifications, consultez [Éléments requis pour les didacticiels &#40;Générateur de rapports&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="Chart"></a> 1. Créer un rapport de graphique à partir de l'Assistant Graphique  
 À partir de la **mise en route** boîte de dialogue, utilisez l’Assistant graphique pour créer un dataset incorporé, choisir une source de données partagée et créez un histogramme.  
  
> [!NOTE]  
>  Dans ce didacticiel, la requête contient les valeurs de données, afin qu'il ne soit pas nécessaire de disposer d'une source de données externe. Cela rend la requête assez longue. Dans un environnement métier, une requête ne contient pas les données. Ceci est nécessaire à des fins de formation uniquement.  
  
#### <a name="to-create-a-new-chart-report"></a>Pour créer un rapport de graphique  
  
1.  Cliquez sur **Démarrer**, pointez sur **Programmes**, sur **Générateur de rapports Microsoft SQL Server 2012**, puis cliquez sur **Générateur de rapports version**.  
  
     La boîte de dialogue **Mise en route** s'affiche.  
  
    > [!NOTE]  
    >  Si le **mise en route** boîte de dialogue n’apparaît pas, à partir de la **le Générateur de rapports** bouton, cliquez sur **New**.  
  
2.  Dans le volet gauche, assurez-vous que **Nouveau rapport** est sélectionné.  
  
3.  Dans le volet droit, cliquez sur **Assistant Graphique**.  
  
4.  Dans la page **Choisir un dataset**, cliquez sur **Créer un dataset**, puis sur **Suivant**.  
  
5.  Dans la page **Choisir une connexion à une source de données** , sélectionnez une source de données existante ou naviguez jusqu’au serveur de rapports, sélectionnez une source de données, puis cliquez sur **Suivant**. Vous devrez peut-être entrer un nom d'utilisateur et un mot de passe.  
  
    > [!NOTE]  
    >  La source de données que vous choisissez n'a pas d'importance, tant que vous disposez des autorisations appropriées. Vous n'allez pas récupérer de données à partir de la source de données. Pour plus d’informations, consultez [Autres manières d’obtenir une connexion de données &#40;Générateur de rapports&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
6.  Dans la page **Créer une requête** , cliquez sur **Modifier en tant que texte**.  
  
7.  Collez la requête suivante dans le volet de requête :  
  
    ```  
    SELECT CAST('2009-01-01' AS date) AS SalesDate, CAST(54995.21 AS money) AS Sales  
    UNION SELECT CAST('2009-01-05' AS date) AS SalesDate, CAST(64499.04 AS money) AS Sales  
    UNION SELECT CAST('2009-02-11' AS date) AS SalesDate, CAST(37821.79 AS money) AS Sales  
    UNION SELECT CAST('2009-03-18' AS date) AS SalesDate, CAST(53633.08 AS money) AS Sales  
    UNION SELECT CAST('2009-04-23' AS date) AS SalesDate, CAST(24019.3 AS money) AS Sales  
    UNION SELECT CAST('2009-05-01' AS date) AS SalesDate, CAST(93245.5 AS money) AS Sales  
    UNION SELECT CAST('2009-06-06' AS date) AS SalesDate, CAST(55288.0 AS money) AS Sales  
    UNION SELECT CAST('2009-06-16' AS date) AS SalesDate, CAST(68733.5 AS money) AS Sales  
    UNION SELECT CAST('2009-07-16' AS date) AS SalesDate, CAST(24750.85 AS money) AS Sales  
    UNION SELECT CAST('2009-08-23' AS date) AS SalesDate, CAST(43452.3 AS money) AS Sales  
    UNION SELECT CAST('2009-09-24' AS date) AS SalesDate, CAST(58656. AS money) AS Sales  
    UNION SELECT CAST('2009-10-15' AS date) AS SalesDate, CAST(44583. AS money) AS Sales  
    UNION SELECT CAST('2009-11-21' AS date) AS SalesDate, CAST(81568. AS money) AS Sales  
    UNION SELECT CAST('2009-12-15' AS date) AS SalesDate, CAST(45973. AS money) AS Sales  
    UNION SELECT CAST('2009-12-26' AS date) AS SalesDate, CAST(96357. AS money) AS Sales  
    UNION SELECT CAST('2009-12-31' AS date) AS SalesDate, CAST(81946. AS money) AS Sales  
    ```  
  
8.  (Facultatif) Cliquez sur le bouton Exécuter (**!**) pour voir les données sur lesquelles votre graphique sera basé.  
  
9. Cliquer sur **Suivant**.  
  
##  <a name="ChartType"></a> 2. Choisir le type de graphique  
 Vous avez le choix entre plusieurs types de graphiques prédéfinis.  
  
#### <a name="to-add-a-column-chart"></a>Pour ajouter un histogramme  
  
1.  Dans la page **Choisir un type de graphique** , l’histogramme est le type de graphique par défaut. Cliquer sur **Suivant**.  
  
2.  Dans la page **Organiser les champs du graphique** , faites glisser le champ SalesDate vers **Catégories**. Les catégories s'affichent sur l'axe horizontal.  
  
3.  Faites glisser le champ Sales vers **Valeurs**. La zone **Valeurs** affiche Sum(Sales), car la somme de la valeur totale des ventes est agrégée pour chaque date. Les valeurs s'affichent sur l'axe vertical.  
  
4.  Cliquer sur **Suivant**.  
  
5.  Sur le **choisir un Style** page, dans la zone Styles, sélectionnez un style.  
  
     Un style spécifie un style de police, un jeu de couleurs et un style de bordure. Lorsque vous sélectionnez un style, le volet Aperçu affiche un aperçu du graphique avec ce style.  
  
6.  Cliquez sur **Terminer**.  
  
     Le graphique est ajouté à l'aire de conception.  
  
7.  Cliquez sur le graphique pour afficher ses poignées. Faites glisser l'angle inférieur droit du graphique pour augmenter sa taille. Notez que la taille de l'aire de conception du rapport augmente pour s'adapter à la taille du graphique.  
  
8.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="Horizontal"></a> 3. Mettre en forme et étiqueter l'axe horizontal  
 Par défaut, l'axe horizontal affiche les valeurs dans un format général qui est mis à l'échelle automatiquement pour s'ajuster à la taille du graphique.  
  
#### <a name="to-format-a-date-on-the-horizontal-axis"></a>Pour mettre en forme une date sur l'axe horizontal  
  
1.  Basculez en mode création de rapport.  
  
2.  Cliquez sur l’axe horizontal, puis cliquez sur **propriétés de l’axe Horizontal**.  
  
3.  Cliquez sur **Nombre**.  
  
4.  Dans **catégorie**, sélectionnez **Date**.  
  
5.  Dans la zone **Type** , sélectionnez **31 Jan 2000**.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Sous l’onglet Accueil, cliquez sur **Exécuter** pour afficher l’aperçu du rapport.  
  
 La date s'affiche dans le format de date que vous avez sélectionné. Notez que le graphique ne répertorie pas chaque catégorie sur l'axe horizontal. Par défaut, seules sont incluses les étiquettes qui n'empiètent pas sur l'axe.  
  
 Vous pouvez personnaliser l'affichage des étiquettes en les faisant pivoter et en spécifiant l'intervalle.  
  
#### <a name="to-rotate-the-axis-labels-and-change-the-display-interval-along-the-horizontal-axis"></a>Pour faire pivoter les étiquettes sur l'axe horizontal et modifier l'intervalle qui les sépare  
  
1.  Basculez en mode création de rapport.  
  
2.  Cliquez sur le titre de l’axe horizontal, puis cliquez sur **afficher le titre de l’axe** pour supprimer le titre. Étant donné que l'axe horizontal indique les dates, le titre n'est pas nécessaire.  
  
3.  Cliquez sur l’axe horizontal, puis sur **propriétés de l’axe Horizontal**.  
  
4.  Dans le **Options de l’axe** page sous **plage de l’axe et intervalle**, type **3** pour **intervalle**. Le graphique affiche les dates selon un intervalle de trois.  
  
5.  Cliquez sur **Étiquettes**.  
  
6.  Dans **modifier les options ajustement automatique des étiquettes d’axe**, sélectionnez **désactiver l’ajustement automatique**.  
  
7.  Dans **Angle de rotation des étiquettes**, sélectionnez **-90**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     L'exemple de texte de l'axe horizontal pivote de 90 degrés.  
  
9. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Sur le graphique, les étiquettes pivotent et sont affichées à raison d'une date sur trois.  
  
##  <a name="Legend"></a> 4. Déplacer la légende  
 La légende est créée automatiquement à partir des données de catégories et de séries.  
  
#### <a name="to-move-the-legend-below-the-chart-area-of-a-column-chart"></a>Pour déplacer la légende sous la zone de graphique d'un histogramme  
  
1.  Basculez en mode création de rapport.  
  
2.  Avec le bouton droit sur la légende du graphique, puis cliquez sur **propriétés de la légende**.  
  
3.  Pour **mise en page et Position**, sélectionnez une autre position. Par exemple, choisissez de positionner le graphique en bas au centre.  
  
     Lorsque la légende est placée en haut ou en bas d'un graphique, la disposition de la légende change de vertical à horizontal. Vous pouvez sélectionner une autre disposition dans la liste déroulante **Disposition** .  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  (Facultatif) Étant donné que ce didacticiel ne comprend qu'une seule catégorie, la légende n'est pas nécessaire. Pour supprimer la légende, avec le bouton droit de la légende, puis cliquez sur **supprimer la légende**.  
  
6.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="ChartTitle"></a> 5. Intituler le graphique  
  
#### <a name="to-change-the-chart-title-above-the-chart-area"></a>Pour modifier le titre d'un graphique au-dessus de la zone de graphique  
  
1.  Basculez en mode création de rapport.  
  
2.  Sélectionnez les mots **titre du graphique** en haut du graphique, puis tapez le texte suivant : **Total des commandes de Store**.  
  
3.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="Vertical"></a> 6. Mettre en forme et étiqueter l'axe vertical  
 Par défaut, l'axe vertical affiche les valeurs dans un format général qui est mis à l'échelle automatiquement pour s'ajuster à la taille du graphique.  
  
#### <a name="to-format-as-currency-the-numbers-on-the-vertical-axis"></a>Pour appliquer le format monétaire aux chiffres figurant sur l'axe vertical  
  
1.  Basculez en mode création de rapport.  
  
2.  Double-cliquez sur les étiquettes sur l’axe vertical le long du côté du graphique pour les sélectionner.  
  
3.  Dans le ruban, sur le **accueil** sous l’onglet le **nombre** de groupe, cliquez sur le **devise** bouton. Les étiquettes de l'axe changent pour afficher le format monétaire.  
  
4.  Dans le ruban, sur le **accueil** sous l’onglet le **nombre** de groupe, cliquez sur le **réduire les décimales** bouton deux fois, pour afficher le nombre arrondi au dollar plus proche.  
  
5.  Cliquez sur l’axe vertical, sur **propriétés de l’axe Vertical**.  
  
6.  Cliquez sur **Nombre**. Notez que **devise** est déjà sélectionné dans le **catégorie** zone, et **décimales** est déjà **0** (zéro).  
  
7.  Dans le **afficher les valeurs en** , cliquez sur **milliers**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. Cliquez sur le titre de l’axe vertical le long du côté du graphique, sur **propriétés du titre axe**.  
  
10. Remplacez le texte dans le **texte du titre** champ avec le texte suivant : **Total des ventes (en milliers)**. Vous pouvez également spécifier diverses options de mise en forme du titre.  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="Average"></a> 7. Ajouter une moyenne mobile  
  
#### <a name="to-add-a-moving-average"></a>Pour ajouter une moyenne mobile  
  
1.  Basculez en mode création de rapport.  
  
2.  Double-cliquez sur le graphique pour afficher le volet **Données du graphique** .  
  
3.  Avec le bouton droit le **[SUM (Sales)]** champ qui se trouve dans le **valeurs** zone, puis cliquez sur **ajouter une série calculée**.  
  
4.  Dans **Formule**, vérifiez que **Moyenne mobile** est sélectionné.  
  
5.  Dans **Définir les paramètres de la formule**, pour **Période**, sélectionnez **4**.  
  
6.  Cliquez sur **bordure**.  
  
7.  Dans **largeur de ligne**, sélectionnez **3pt**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Le graphique présente une ligne qui indique la moyenne mobile pour le total des ventes par date. La moyenne est ici calculée toutes les quatre dates.  
  
##  <a name="Title"></a> 8. Ajouter un titre de rapport  
  
#### <a name="to-add-a-report-title"></a>Pour ajouter un titre de rapport  
  
1.  Basculez en mode création de rapport.  
  
2.  Dans l'aire de conception, cliquez sur **Cliquez pour ajouter un titre**.  
  
3.  Type **graphique des ventes**, appuyez sur entrée, puis tapez **janvier à décembre 2009**, donc il ressemble à ceci :  
  
     **Graphique sur les ventes**  
  
     **Janvier à décembre 2009**  
  
4.  Sélectionnez **graphique des ventes**, puis cliquez sur le **gras** situé dans le **police** section sur la **accueil** onglet du ruban.  
  
5.  Sélectionnez **janvier à décembre 2009**, puis, dans le **police** section sur la **accueil** onglet, définissez la taille de police sur **10**.  
  
6.  (Facultatif) Vous devrez peut-être rendre les **titre** zone de texte agrandir pour prendre en charge les deux lignes de texte en abaissant les doubles flèches lorsque vous cliquez au milieu du bord inférieur.  
  
     Ce titre s'affiche alors dans la partie supérieure du rapport. En l’absence d’en-tête de page défini, les éléments situés au-dessus du corps du rapport font office d’en-tête de rapport.  
  
7.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="Save"></a> 9. Enregistrer le rapport  
  
#### <a name="to-save-the-report"></a>Pour enregistrer le rapport  
  
1.  Basculez en mode création de rapport.  
  
2.  À partir du bouton Générateur de rapports, cliquez sur **Enregistrer sous**.  
  
3.  Dans **Nom**, tapez **Histogramme des commandes client**.  
  
4.  Cliquez sur **Enregistrer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez terminé le didacticiel Ajout d'un histogramme à un rapport. Pour en savoir plus sur les graphiques, consultez [Graphiques &#40;Générateur de rapports et SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) et [Graphiques sparkline et barres de données &#40;Générateur de rapports et SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels &#40;Générateur de rapports&#41;](report-builder-tutorials.md)   
 [Générateur de rapports dans SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
