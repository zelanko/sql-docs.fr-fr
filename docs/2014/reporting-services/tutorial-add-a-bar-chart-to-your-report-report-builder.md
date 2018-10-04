---
title: 'Didacticiel : ajouter un graphique à barres à un rapport (Générateur de rapports) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 6956ebd6-0217-4087-a4fa-5cc1c3804691
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 25d3fafc654ab1c272d7688e49d67cd2af5d1820
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106799"
---
# <a name="tutorial-add-a-bar-chart-to-your-report-report-builder"></a>Didacticiel : ajouter un graphique à barres à un rapport (Générateur de rapports)
  Un graphique à barres représente les données de catégorie horizontalement. Cela peut aider à :  
  
-   améliorer la lisibilité des noms de catégorie longs ;  
  
-   améliorer la compréhension des heures représentées sous forme de valeurs ;  
  
-   comparer la valeur relative de plusieurs séries.  
  
 L'illustration suivante montre le graphique à barres que vous allez créer, avec les ventes de 2008 et 2009 pour les cinq meilleurs commerciaux, par ordre alphabétique.  
  
 ![rs_BarChartTutorial](../../2014/tutorials/media/rs-barcharttutorial.gif "rs_BarChartTutorial")  
  
##  <a name="BackToTop"></a> Ce que vous allez apprendre  
 Dans ce didacticiel, vous apprendrez à effectuer les tâches suivantes :  
  
1.  [Créer un graphique à partir de l’Assistant graphique](#Chart)  
  
2.  [Choisissez le Type de graphique](#ChartType)  
  
3.  [Afficher toutes les valeurs de catégorie sur l’axe Vertical](#AllValues)  
  
4.  [Modifier l’affichage des noms sur l’axe Vertical](#Sort)  
  
5.  [Déplacer la légende](#Legend)  
  
6.  [Déplacer le titre du graphique](#ChartTitle)  
  
7.  [Mettre en forme et étiqueter l’axe Horizontal](#Horizontal)  
  
8.  [Ajouter un filtre pour afficher les cinq valeurs supérieures](#Filter)  
  
9. [Ajouter un titre de rapport](#Title)  
  
10. [Enregistrer le rapport](#Save)  
  
> [!NOTE]  
>  Dans ce didacticiel, les étapes de l'Assistant sont consolidées en une seule procédure. Pour obtenir des instructions pas à pas sur l’accès à un serveur de rapports, la création d’un dataset et le choix d’une source de données, consultez le premier didacticiel de cette série : [Didacticiel : création d’un rapport de tableau de base &#40;Générateur de rapports&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Durée estimée pour effectuer ce didacticiel : 15 minutes.  
  
## <a name="requirements"></a>Spécifications  
 Pour plus d’informations sur les spécifications, consultez [Éléments requis pour les didacticiels &#40;Générateur de rapports&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="Chart"></a> 1. Créer un rapport de graphique à partir de l'Assistant Graphique  
 À partir de la **mise en route** boîte de dialogue, créez un dataset incorporé, choisir une source de données partagée et créer un graphique à barres à l’aide de l’Assistant graphique.  
  
> [!NOTE]  
>  Dans ce didacticiel, la requête contient les valeurs des données : elle n’a donc pas besoin d’une source de données externe. Cela rend la requête assez longue. Dans un environnement métier, une requête ne contient pas les données. Ceci est nécessaire à des fins de formation uniquement.  
  
#### <a name="to-create-a-new-chart-report"></a>Pour créer un rapport de graphique  
  
1.  Cliquez sur **Démarrer**, pointez sur **Programmes**, sur **Générateur de rapports Microsoft SQL Server 2012**, puis cliquez sur **Générateur de rapports version**.  
  
     La boîte de dialogue **Mise en route** s'affiche.  
  
    > [!NOTE]  
    >  Si le **mise en route** boîte de dialogue ne pas s’affichent, cliquez sur le bouton Générateur de rapports, puis cliquez sur **New**.  
  
2.  Dans le volet gauche, assurez-vous que **Nouveau rapport** est sélectionné.  
  
3.  Dans le volet droit, cliquez sur **Assistant Graphique**.  
  
4.  Dans la page **Choisir un dataset** , cliquez sur **Créer un dataset**, puis sur **Suivant**.  
  
5.  Dans la page **Choisir une connexion à une source de données** , sélectionnez une source de données existante ou naviguez jusqu’au serveur de rapports, sélectionnez une source de données, puis cliquez sur **Suivant**. Vous devrez peut-être entrer un nom d'utilisateur et un mot de passe.  
  
    > [!NOTE]  
    >  La source de données que vous choisissez n'a pas d'importance, tant que vous disposez des autorisations appropriées. Vous n'allez pas récupérer de données à partir de la source de données. Pour plus d’informations, consultez [Autres manières d’obtenir une connexion de données &#40;Générateur de rapports&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
6.  Dans la page **Créer une requête** , cliquez sur **Modifier en tant que texte**.  
  
7.  Collez la requête suivante dans le volet de requête :  
  
    ```  
    SELECT 'Luis' as FirstName, 'Alverca' as LastName, CAST(170000.00 AS money) AS SalesYear2009, CAST(150000. AS money) AS SalesYear2008  
    UNION SELECT 'Jeffrey' as FirstName, 'Zeng' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(190000. AS money) AS SalesYear2008  
    UNION SELECT 'Houman' as FirstName, 'Pournasseh' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Robin' as FirstName, 'Wood' as LastName, CAST(75000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'Daniela' as FirstName, 'Guaita' as LastName,  CAST(170000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'John' as FirstName, 'Yokim' as LastName, CAST(160000. AS money) AS SalesYear2009, CAST(195000. AS money) AS SalesYear2008  
    UNION SELECT 'Delphine' as FirstName, 'Ribaute' as LastName, CAST(180000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Robert' as FirstName, 'Hernady' as LastName, CAST(140000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Tanja' as FirstName, 'Plate' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(160000. AS money) AS SalesYear2008  
    UNION SELECT 'David' as FirstName, 'Bradley' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Michal' as FirstName, 'Jaworski' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(220000. AS money) AS SalesYear2008  
    UNION SELECT 'Chris' as FirstName, 'Ashton' as LastName, CAST(195000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Pongsiri' as FirstName, 'Hirunyanitiwatna' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(215000. AS money) AS SalesYear2008  
    UNION SELECT 'Brian' as FirstName, 'Burke' as LastName, CAST(187000. AS money) AS SalesYear2009, CAST(207000. AS money) AS SalesYear2008  
    ```  
  
8.  (Facultatif) Cliquez sur le bouton Exécuter (**!**) pour voir les données sur lesquelles votre graphique sera basé.  
  
9. Cliquez sur **Suivant**.  
  
##  <a name="ChartType"></a> 2. Choisir le type de graphique  
 Vous avez le choix entre plusieurs types de graphiques prédéfinis.  
  
#### <a name="to-add-a-column-chart"></a>Pour ajouter un histogramme  
  
1.  Dans la page **Choisir un type de graphique** , l’histogramme est le type de graphique par défaut.  
  
2.  Cliquez sur **Barre**, puis sur **Suivant**.  
  
     Sur le **organiser les champs du graphique** page, il existe quatre champs dans le **champs disponibles** volet : FirstName, LastName, SalesYear2009 et SalesYear2008.  
  
3.  Faites glisser LastName vers le volet Catégories.  
  
4.  Faites glisser SalesYear2009 vers le volet valeurs. SalesYear2009 représente le montant des ventes de chaque commercial pour l'année 2009. Le volet Valeurs affiche `[Sum(SalesYear2009)]`, car le graphique affiche l'agrégat pour chaque produit.  
  
5.  Faites glisser SalesYear2008 vers le volet valeurs sous SalesYear2009. SalesYear2008 représente le montant des ventes de chaque commercial pour l'année 2008.  
  
6.  Cliquez sur **Suivant**.  
  
7.  Sur le **choisir un style** page, dans le volet Styles, sélectionnez un style.  
  
     Un style spécifie un style de police, un jeu de couleurs et un style de bordure. Lorsque vous sélectionnez un style, le volet Aperçu affiche un aperçu du graphique avec ce style.  
  
8.  Cliquez sur **Terminer**.  
  
     Le graphique est ajouté à l'aire de conception.  
  
9. Cliquez sur le graphique pour afficher ses poignées. Faites glisser l'angle inférieur droit du graphique pour augmenter sa taille.  
  
10. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Le rapport affiche le graphique à barres des ventes de chaque commercial pour les années 2008 et 2009. La longueur de la barre correspond au total des ventes.  
  
##  <a name="AllValues"></a> 3. Modifier l'affichage des noms sur l'axe vertical  
 Par défaut, seules quelques-unes des valeurs de l'axe vertical s'affichent. Vous pouvez modifier le graphique pour afficher toutes les catégories.  
  
#### <a name="to-display-all-sales-persons-along-the-category-axis-of-a-bar-chart"></a>Pour afficher tous les commerciaux le long de l'axe des abscisses d'un graphique à barres  
  
1.  Basculez en mode création de rapport.  
  
2.  Cliquez sur l’axe vertical, puis cliquez sur **propriétés de l’axe Vertical**.  
  
3.  Sous **Plage et intervalle de l’axe**, dans la zone **Intervalle** , tapez **1**.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  Avec le bouton droit vertical **titre de l’axe** et désactivez le **afficher le titre de l’axe** case à cocher.  
  
6.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
> [!NOTE]  
>  Si vous ne parvenez pas à lire les noms des commerciaux sur l'axe vertical, vous pouvez augmenter la taille de votre graphique ou modifier les options de mise en forme des étiquettes d'axe.  
  
###  <a name="CategoryExpression"></a> Afficher le nom et prénom sur l’axe Vertical  
 Vous pouvez modifier l'expression de catégorie pour inclure le nom suivi du prénom de chaque commercial.  
  
##### <a name="to-change-the-category-expression"></a>Pour modifier l'expression de catégorie  
  
1.  Basculez en mode création de rapport.  
  
2.  Double-cliquez sur le graphique pour afficher le volet **Données du graphique** .  
  
3.  Dans la zone **Groupes de catégories** , cliquez avec le bouton droit sur le champ [LastName], puis cliquez sur **Propriétés du groupe de catégories**.  
  
4.  Dans Étiquette, cliquez sur le bouton Expression (Fx).  
  
5.  Tapez l’expression suivante : `=Fields!LastName.Value & ", " & Fields!FirstName.Value`  
  
     Cette expression concatène le nom, une virgule et le prénom.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Si les prénoms n'apparaissent pas lorsque vous exécutez le rapport, vous pouvez actualiser les données manuellement. Toujours en mode Aperçu, sous l’onglet **Exécuter** du groupe **Navigation** , cliquez sur **Actualiser**.  
  
> [!NOTE]  
>  Si vous ne parvenez pas à lire les noms des commerciaux sur l'axe vertical, vous pouvez augmenter la taille de votre graphique ou modifier les options de mise en forme des étiquettes d'axe.  
  
##  <a name="Sort"></a> 4. Modifier l'ordre de tri des noms sur l'axe vertical  
 Lorsque vous triez les données d'un graphique, vous modifiez l'ordre des valeurs sur l'axe des abscisses.  
  
#### <a name="to-sort-the-names-in-alphabetical-order-on-the-bar-chart"></a>Pour trier les noms dans l'ordre alphabétique sur le graphique à barres  
  
1.  Basculez en mode création de rapport.  
  
2.  Double-cliquez sur le graphique pour afficher le volet **Données du graphique** .  
  
3.  Dans la zone **Groupes de catégories** , cliquez avec le bouton droit sur le champ [LastName], puis cliquez sur **Propriétés du groupe de catégories**.  
  
4.  Cliquez sur **Tri**. La page **Modifiez les options de tri** affiche une liste d’expressions de tri. Par défaut, cette liste a une expression de tri identique à l'expression de groupe de la catégorie d'origine.  
  
5.  Dans l’ordre de tri, cliquez sur l’expression (**Fx**) bouton.  
  
6.  Tapez l’expression suivante : `=Fields!LastName.Value & ", " & Fields!FirstName.Value`  
  
7.  Cliquez sur **OK**.  
  
8.  Sur le **propriétés du groupe de catégories** page, dans le **ordre** liste déroulante, sélectionnez **Z à A**. L'ordre alphabétique inversé est ainsi sélectionné de sorte que les noms apparaissent dans l'ordre de bas en haut.  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Les noms sur l’axe horizontal sont triés dans l’ordre inverse, avec **Alerca** en haut et **Zeng** en bas.  
  
##  <a name="Legend"></a> 5. Déplacer la légende  
 Pour améliorer la lisibilité des valeurs du graphique, vous pouvez déplacer la légende du graphique. Par exemple, dans un graphique à barres horizontales, vous pouvez modifier la position de la légende de manière à l'afficher au-dessus ou en dessous de la zone de graphique. Cela permet d'augmenter l'espace horizontal entre les barres.  
  
#### <a name="to-display-the-legend-below-the-chart-area-of-a-bar-chart"></a>Pour afficher la légende sous la zone de graphique d'un graphique à barres  
  
1.  Basculez en mode création de rapport.  
  
2.  Cliquez avec le bouton droit sur la légende du graphique.  
  
3.  Sélectionnez **Propriétés de la légende**.  
  
4.  Pour **Position de la légende**, sélectionnez une position différente. Par exemple, choisissez de positionner le graphique en bas au centre.  
  
     Lorsque la légende est placée en haut ou en bas d'un graphique, la disposition de la légende change de vertical à horizontal. Vous pouvez sélectionner une autre disposition dans la liste déroulante **Disposition** .  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="ChartTitle"></a> 6. Intituler le graphique  
  
#### <a name="to-change-the-chart-title-above-the-chart-area-of-a-bar-chart"></a>Pour modifier le titre d'un graphique à barres au-dessus de la zone de graphique  
  
1.  Basculez en mode création de rapport.  
  
2.  Sélectionnez les mots **titre du graphique** en haut du graphique, puis tapez le texte suivant : **ventes pour 2008 et 2009**.  
  
3.  Cliquez n'importe où en dehors du texte.  
  
4.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="Horizontal"></a> 7. Mettre en forme et étiqueter l'axe horizontal  
 Par défaut, l'axe horizontal affiche les valeurs dans un format général qui est mis à l'échelle automatiquement pour s'ajuster à la taille du graphique.  
  
#### <a name="to-format-the-numbers-on-the-horizontal-axis"></a>Pour mettre en forme les nombres sur l'axe horizontal  
  
1.  Basculez en mode création de rapport.  
  
2.  Cliquez sur l'axe horizontal en bas du graphique pour le sélectionner.  
  
     Dans le ruban, sur le **accueil** sous l’onglet le **nombre** de groupe, cliquez sur le **devise** bouton. Les étiquettes de l'axe horizontal changent et utilisent une devise.  
  
3.  (Facultatif) Supprimez les chiffres décimaux. Près du bouton **Devise** , cliquez deux fois sur le bouton **Réduire les décimales** .  
  
4.  Cliquez avec le bouton droit sur l’axe horizontal, puis cliquez sur **Propriétés de l’axe horizontal**.  
  
5.  Sur le **nombre** onglet, sélectionnez **afficher les valeurs en milliers.**  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Avec le bouton droit **titre de l’axe** et cliquez sur **propriétés du titre axe**.  
  
8.  Dans le **texte du titre** , tapez **ventes en milliers** et cliquez sur **OK**.  
  
9. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Le rapport affiche les montants des ventes sur l'axe horizontal sous forme de devises en milliers, sans chiffres décimaux.  
  
##  <a name="Filter"></a> 8. Ajouter un filtre pour afficher les cinq valeurs supérieures  
 Vous pouvez ajouter un filtre au graphique pour spécifier les données du dataset à inclure ou exclure dans le graphique.  
  
#### <a name="to-add-a-filter-and-display-the-top-five-values"></a>Pour ajouter un filtre et afficher les cinq valeurs supérieures  
  
1.  Basculez en mode création de rapport.  
  
2.  Double-cliquez sur le graphique pour afficher le volet **Données du graphique** .  
  
3.  Dans la zone **Groupes de catégories** , cliquez avec le bouton droit sur le champ [LastName], puis cliquez sur **Propriétés du groupe de catégories**.  
  
4.  Cliquez sur **Filtres**. La page **Modifiez les filtres** peut afficher une liste d’expressions de filtre. Par défaut, cette liste est vide.  
  
5.  Cliquez sur **Ajouter**. Un nouveau filtre vide apparaît.  
  
6.  Dans **Expression**, type **[SUM (salesyear2009)]**. Cette opération crée l’expression sous-jacente `=Sum(Fields!SalesYear2009.Value)`, que vous pouvez voir si vous cliquez sur le **fx** bouton.  
  
7.  Vérifiez que le type de données est **Text**.  
  
8.  Dans **Opérateur**, sélectionnez **N supérieurs** dans la liste déroulante.  
  
9. Dans **Valeur**, tapez l’expression suivante : **=5**  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Si les résultats ne sont pas filtrés lorsque vous exécutez le rapport, vous pouvez actualiser les données manuellement. Sous l’onglet **Exécuter** , dans le groupe **Navigation** , cliquez sur **Actualiser**.  
  
 Le graphique affiche les noms des cinq meilleurs commerciaux issus des données de ventes 2009.  
  
##  <a name="Title"></a> 9. Ajouter un titre de rapport  
  
#### <a name="to-add-a-report-title"></a>Pour ajouter un titre de rapport  
  
1.  Dans l'aire de conception, cliquez sur **Cliquez pour ajouter un titre**.  
  
2.  Type **graphique à barres des ventes**, appuyez sur entrée, puis tapez **cinq meilleurs vendeurs pour 2009**, donc il ressemble à ceci :  
  
     **Graphique à barres des ventes**  
  
     **Cinq meilleurs vendeurs pour 2009**  
  
3.  Sélectionnez **Graphique à barres des ventes**, puis cliquez sur le bouton **Gras** .  
  
4.  Sélectionnez **cinq meilleurs vendeurs pour 2009**, puis, dans le **police** section sur la **accueil** onglet, définissez la taille de police sur **10**.  
  
5.  (Facultatif) Vous devrez peut-être agrandir la zone de texte Titre pour contenir les deux lignes de texte.  
  
     Ce titre s'affiche alors dans la partie supérieure du rapport. En l’absence d’en-tête de page défini, les éléments situés au-dessus du corps du rapport font office d’en-tête de rapport.  
  
6.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="Save"></a> 10. Enregistrer le rapport  
  
#### <a name="to-save-the-report"></a>Pour enregistrer le rapport  
  
1.  Basculez en mode création de rapport.  
  
2.  À partir du bouton **Générateur de rapports** , cliquez sur **Enregistrer sous**.  
  
3.  Dans **Nom**, tapez **Graphique à barres des ventes**.  
  
4.  Cliquez sur **Enregistrer**.  
  
 Votre rapport est enregistré sur le serveur de rapports.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez réalisé le didacticiel d'ajout d'un graphique à barres à votre rapport. Pour en savoir plus sur les graphiques, consultez [Graphiques &#40;Générateur de rapports et SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) et [Graphiques sparkline et barres de données &#40;Générateur de rapports et SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels &#40;Générateur de rapports&#41;](report-builder-tutorials.md)   
 [Générateur de rapports dans SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
