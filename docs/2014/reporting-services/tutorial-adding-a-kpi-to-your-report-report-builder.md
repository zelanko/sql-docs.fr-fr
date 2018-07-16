---
title: 'Didacticiel : ajout d’un indicateur de performance clé à un rapport (Générateur de rapports) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1bf77859-0b33-4f40-abaf-ebeeb6ebb1f8
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: f06fa546153ef62edda97c173a8c4fb9cc4d9362
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276165"
---
# <a name="tutorial-adding-a-kpi-to-your-report-report-builder"></a>Didacticiel : ajout d'un indicateur de performance clé à un rapport (Générateur de rapports)
  Un indicateur de performance clé (KPI) est une valeur mesurable qui revêt une importance significative sur le plan opérationnel. Ce didacticiel vous apprend comment inclure un indicateur de performance clé dans un rapport. Dans ce scénario, le récapitulatif des ventes par sous-catégories de produits est l'indicateur de performance clé. L'état actuel de l'indicateur de performance clé est indiqué à l'aide de couleurs, de jauges et d'indicateurs.  
  
 L'illustration suivante montre le rapport que vous allez créer.  
  
 ![rs_AddKPITutorial](../../2014/tutorials/media/rs-addkpitutorial.gif "rs_AddKPITutorial")  
  
##  <a name="BackToTop"></a> Ce que vous allez apprendre  
 Dans ce didacticiel, vous allez apprendre à ajouter un indicateur de performance clé en définissant la couleur d'arrière-plan des cellules de tableau selon la valeur de la cellule. Vous apprendrez à ajouter et configurer une jauge et un indicateur. Vous apprendrez également à écrire l'expression qui définit la couleur d'arrière-plan des cellules de tableau.  
  
 Ce didacticiel contient les procédures suivantes :  
  
1.  [Créer un rapport de tableau et le jeu de données à partir de l’Assistant tableau ou matrice](#Table)  
  
2.  [Organiser les données, choisissez la disposition et le Style à partir de l’Assistant tableau ou matrice](#CompleteWizard)  
  
3.  [Utiliser des couleurs d’arrière-plan pour afficher un indicateur de performance clé](#BackgroundColors)  
  
4.  [Afficher un indicateur de performance clé à l’aide d’une jauge](#Gauge)  
  
5.  [Afficher un indicateur de performance clé à l’aide d’un indicateur](#Indicator)  
  
6.  [Ajouter un titre de rapport](#Title)  
  
7.  [Enregistrer le rapport](#Save)  
  
> [!NOTE]  
>  Dans ce didacticiel, les étapes de l'Assistant sont consolidées sous forme de deux procédures : l'une pour créer le dataset, et l'autre pour créer une table. Pour obtenir des instructions pas à pas sur l’accès à un serveur de rapports, le choix d’une source de données, la création d’un dataset et l’exécution de l’Assistant, consultez le premier didacticiel de cette série : [Didacticiel : création d’un rapport de tableau de base &#40;Générateur de rapports&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Durée estimée pour effectuer ce didacticiel : 15 minutes.  
  
## <a name="requirements"></a>Spécifications  
 Pour plus d’informations sur les spécifications, consultez [Éléments requis pour les didacticiels &#40;Générateur de rapports&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="Table"></a> 1. Créer un rapport de tableau et un dataset à partir de l'Assistant Tableau ou matrice  
 À partir de la **mise en route** boîte de dialogue, choisissez une source de données partagée, créez un dataset incorporé et afficher les données dans une table.  
  
> [!NOTE]  
>  Dans ce didacticiel, la requête contient les valeurs de données, afin qu'il ne soit pas nécessaire de disposer d'une source de données externe. Cela rend la requête assez longue. Dans un environnement métier, une requête ne contient pas les données. Ceci est nécessaire à des fins de formation uniquement.  
  
#### <a name="to-create-a-new-table"></a>Pour créer une table  
  
1.  Cliquez sur **Démarrer**, pointez sur **Programmes**, sur **Générateur de rapports Microsoft SQL Server 2012**, puis cliquez sur **Générateur de rapports version**.  
  
     La boîte de dialogue **Mise en route** s'affiche.  
  
    > [!NOTE]  
    >  Si le **mise en route** boîte de dialogue n’apparaît pas, à partir du bouton Générateur de rapports, cliquez sur **New**.  
  
2.  Dans le volet gauche, assurez-vous que **Nouveau rapport** est sélectionné.  
  
3.  Dans le volet droit, cliquez sur **Assistant Tableau ou matrice**.  
  
4.  Dans la page Choisir un jeu de données, cliquez sur **créer un jeu de données**.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans la page **Choisir une connexion à une source de données** , sélectionnez une source de données existante ou naviguez jusqu’au serveur de rapports, puis sélectionnez une source de données. Si aucune source de données n’est disponible ou que vous n’avez pas accès à un serveur de rapports, vous pouvez utiliser une source de données incorporée à la place. Pour plus d’informations, consultez [Didacticiel : création d’un rapport de tableau de base &#40;Générateur de rapports&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
7.  Cliquez sur **Suivant**.  
  
8.  Dans la page **Créer une requête** , cliquez sur **Modifier en tant que texte**.  
  
9. Copiez et collez la requête suivante dans le volet de requête :  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Mini Battery Charger' as Product, CAST(1056.00 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Accessories' as Subcategory,  
       'Telephoto Conversion Lens' as Product, CAST(1380.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,'Accessories' as Subcategory,    
       'USB Cable' as Product, CAST(780.00 AS money) AS Sales, 26 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3798.00 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Business Videographer' as Product, CAST(10400.00 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-10' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Social Videographer' as Product, CAST(3000.00 AS money) AS Sales, 60 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Advanced Digital' as Product, CAST(7234.50 AS money) AS Sales, 39 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Compact Digital' as Product, CAST(10836.00 AS money) AS Sales, 84 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Consumer Digital' as Product, CAST(2550.00 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera 35mm' as Product, CAST(18530.00 AS money) AS Sales, 34 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera' as Product, CAST(26576.00 AS money) AS Sales, 88 as Quantity  
    ```  
  
10. Cliquez sur **Suivant**.  
  
##  <a name="CompleteWizard"></a> 2. Organiser les données, choisir la mise en page et le style à partir de l'Assistant Tableau ou matrice  
 Utilisez l'Assistant pour obtenir une conception initiale dans laquelle afficher les données. Le volet de visualisation de l'Assistant vous aide à visualiser le résultat du regroupement des données avant de terminer la conception de la table ou de la matrice.  
  
#### <a name="to-organize-data-into-groups-choose-a-layout-and-a-style"></a>Pour organiser les données en groupes, choisir une mise en page et un style  
  
1.  Dans la page Organiser les champs, faites glisser Product vers **Valeurs**.  
  
2.  Faites glisser Quantity vers **Valeurs** et placez-le sous Product.  
  
     Quantity est synthétisé à l'aide de la fonction Sum, la fonction de synthèse par défaut des champs numériques.  
  
3.  Faites glisser Sales vers **Valeurs** et placez-le sous Quantity.  
  
     Les étapes 1, 2 et 3 spécifient les données à afficher dans le tableau.  
  
4.  Faites glisser SalesDate vers **Groupes de lignes**.  
  
5.  Faites glisser Subcategory vers **Groupes de lignes** et placez-le sous SalesDate.  
  
     Les étapes 4 et 5 organisent les valeurs des champs par date, puis par l'ensemble des ventes pour chaque date.  
  
6.  Cliquez sur **Suivant**.  
  
     Lorsque vous exécutez le rapport, le tableau affiche chaque date, toutes les commandes pour chaque date et tous les produits, quantités et totaux de ventes pour chaque commande.  
  
7.  Dans la page Choisir la disposition, sous **Options**, vérifiez que **Afficher les sous-totaux et les totaux généraux** est sélectionné.  
  
8.  Vérifiez que **Bloqué, sous-total ci-dessous** est sélectionné.  
  
9. Désactivez l’option **Développer/Réduire les groupes**.  
  
     Dans ce didacticiel, le rapport que vous créez n'utilise pas la fonctionnalité d'exploration vers le bas qui permet à un utilisateur de développer une hiérarchie de groupe parente afin d'afficher les lignes de groupes enfants et les lignes de détails.  
  
10. Cliquez sur **Suivant**.  
  
11. Dans la page Choisir un style, dans le volet Styles, sélectionnez un style.  
  
     L'illustration du rapport finalisé montre le rapport dans le style Océan.  
  
12. Cliquez sur **Terminer**.  
  
     Le tableau est ajouté à l'aire de conception. Le tableau possède cinq colonnes et cinq lignes. Le volet Groupes de lignes affiche trois lignes : SalesDate, Subcategory et Details. Les données de détail sont toutes les données récupérées par la requête de dataset.  
  
13. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Pour chaque produit vendu à une date spécifique, le tableau affiche le nom du produit, la quantité vendue et le total des ventes. Les données sont organisées par date de vente, puis par sous-catégorie.  
  
##  <a name="BackgroundColors"></a> 3. Utiliser les couleurs d'arrière-plan pour afficher un indicateur de performance clé  
 Les couleurs d'arrière-plan peuvent avoir la valeur d'une expression qui est évaluée lorsque vous exécutez le rapport.  
  
#### <a name="to-display-the-present-state-of-a-kpi-by-using-background-colors"></a>Pour afficher l'état actuel d'un KPI en utilisant des couleurs d'arrière-plan  
  
1.  Dans la table, avec le bouton droit deux cellules vers le bas à partir de la `[Sum(Sales)]` cellule (ligne de sous-total qui affiche les ventes d’une sous-catégorie), puis cliquez sur **propriétés de la zone texte**.  
  
2.  Dans **remplir**, cliquez sur le **fx** situé en regard du **couleur de remplissage** option et entrez l’expression suivante dans la **définir l’expression pour : BackgroundColor** champ :  
  
 `=IIF(Sum(Fields!Sales.Value) >= 5000 ,"Lime", IIF(Sum(Fields!Sales.Value) < 2500, "Red","Yellow"))`  
  
 La couleur d'arrière-plan passe au vert, à l'aide de la nuance de vert nommée « Citron vert », pour chaque cellule qui contient une somme agrégée pour `[Sum(Sales)]` supérieure ou égale à 5000. Les valeurs de `[Sum(Sales)]` entre 2500 et 5000 sont colorées en jaune. Les valeurs inférieures à 2500 sont colorées en rouge.  
  
1.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
2.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Dans la ligne de sous-total qui affiche les ventes d'une sous-catégorie, la couleur d'arrière-plan de la cellule est le rouge, le jaune ou le vert, selon la valeur de la somme des ventes.  
  
##  <a name="Gauge"></a> 4. Afficher un indicateur de performance clé à l'aide d'une jauge  
 Une jauge représente une valeur unique dans un dataset. Ce didacticiel utilise une jauge linéaire horizontale, car sa forme et sa simplicité la rendent facile à lire, même lorsqu'elle est de petite taille et qu'elle est utilisée dans une cellule de tableau. Pour plus d’informations, consultez [Jauges &#40;Générateur de rapports et SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md).  
  
#### <a name="to-display-the-present-state-of-a-kpi-using-a-gauge"></a>Pour afficher l'état présent d'un KPI à l'aide d'une jauge  
  
1.  Basculez en mode Conception.  
  
2.  Dans la table, le Gestionnaire de colonnes avec le bouton droit de la cellule que vous avez modifié dans la procédure précédente, pointez sur **insérer une colonne**, puis cliquez sur **droite**. Une nouvelle colonne est ajoutée au tableau.  
  
3.  Type **KPI** dans l’en-tête de colonne.  
  
4.  Sur le **insérer** sous l’onglet le **régions de données** de groupe, cliquez sur **jauge**, puis cliquez sur l’aire de conception en dehors de la table. La boîte de dialogue **Sélectionner le type de jauge** s’affiche.  
  
5.  Cliquez sur **linéaire**. Le premier type de jauge linéaire, **Horizontal**, est sélectionné.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Une jauge est ajoutée à l'aire de conception.  
  
7.  À partir du volet des données de rapport, faites glisser Sales vers la jauge. Lorsque vous faites glisser Sales sur la jauge, le volet Données de jauge s'ouvre.  
  
8.  Supprimez Sales dans le **valeurs** liste.  
  
     Une fois le champ déposé sur la jauge, les valeurs qu'il contient sont agrégées à l'aide de la fonction intégrée Sum.  
  
9. Cliquez sur le pointeur de la jauge et cliquez sur **propriétés du pointeur**.  
  
10. Dans **Type pointeur**, sélectionnez **barre**. Le pointeur abandonne sa forme de marqueur pour prendre celle d'une barre qui sera plus visible une fois que la jauge aura été ajoutée au tableau.  
  
11. Cliquez sur **remplissage du pointeur**. Dans **couleur secondaire,** choisir **jaune**. Le motif de remplissage dégradé passe du blanc au jaune.  
  
12. Cliquez avec le bouton droit sur l’échelle de la jauge, puis cliquez sur **Propriétés de l’échelle**.  
  
13. Définir le **maximale** option sur 25000.  
  
    > [!NOTE]  
    >  Au lieu d’une constante comme 25000, vous pouvez utiliser une expression pour calculer dynamiquement la valeur de l’option **Maximum** . L'expression utilise alors la fonctionnalité d'agrégation et est semblable à l'expression `=Max(Sum(Fields!Sales.value), "Tablix1")`.  
  
14. Faites glisser la jauge dans le tableau jusqu'à la troisième cellule de la ligne de sous-total qui affiche les ventes d'une sous-catégorie de la colonne que vous avez insérée.  
  
    > [!NOTE]  
    >  Vous devrez peut-être redimensionner la colonne afin que la jauge linéaire horizontale s'ajuste à la taille des cellules. Pour redimensionner la colonne, cliquez sur un en-tête de colonne, puis utilisez les poignées pour redimensionner les cellules horizontalement et verticalement.  
  
15. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
     La longueur horizontale de la barre de la jauge varie en fonction de la valeur du KPI.  
  
16. (Facultatif) Ajoutez une aiguille maximale pour gérer le dépassement de capacité afin que toute valeur apparaissant dans la plage maximale de l'échelle renvoie constamment à cette aiguille :  
  
    1.  Ouvrez le volet Propriétés.  
  
    2.  Cliquez sur l’échelle. Les propriétés de l'échelle linéaire s'affichent alors dans le volet Propriétés.  
  
    3.  Dans le **aiguilles d’échelle** catégorie, développez le **MaximumPin** nœud.  
  
    4.  Définir le **activer** propriété `True`. Une aiguille s'affiche alors derrière la valeur maximale de l'échelle.  
  
    5.  Définissez **BorderColor** à `Lime`.  
  
17. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="Indicator"></a> 5. Afficher un indicateur de performance clé à l'aide d'un indicateur  
 Les indicateurs sont de petites jauges simples qui permettent d'obtenir en un coup d'œil des valeurs de données. En raison de leur taille et de leur simplicité, les indicateurs sont souvent utilisés dans les tableaux et les matrices. Pour plus d’informations, consultez [Indicateurs &#40;Générateur de rapports et SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md).  
  
#### <a name="to-display-the-present-state-of-a-kpi-using-an-indicator"></a>Pour afficher l'état présent d'un KPI à l'aide d'un indicateur  
  
1.  Basculez en mode Conception.  
  
2.  Dans la table, le Gestionnaire de colonnes avec le bouton droit de la cellule que vous avez modifié dans la procédure précédente, pointez sur **insérer une colonne**, puis cliquez sur **droite**. Une nouvelle colonne est ajoutée au tableau.  
  
3.  Type **KPI** dans l’en-tête de colonne.  
  
4.  Cliquez sur la cellule correspondant au sous-total de la sous-catégorie.  
  
5.  Sur le **insérer** sous l’onglet le **régions de données** de groupe, double-cliquez sur **indicateur.**  
  
     La boîte de dialogue **Sélectionner un type d’indicateur** s’ouvre.  
  
6.  Cliquez sur **formes**. Le premier type de forme, **3 indicateurs (sans bordure),** est sélectionné.  
  
     Vous allez utiliser cet indicateur dans le didacticiel.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     L'indicateur est ajouté à l'aire de conception.  
  
8.  Cliquez avec le bouton droit sur l’indicateur, puis cliquez sur **Propriétés de l’indicateur**.  
  
9. Cliquez sur **valeur et états**.  
  
10. Dans la liste déroulante valeur, sélectionnez **[SUM (Sales)]**, mais ne modifiez pas les autres options.  
  
     Par défaut, la synchronisation des données se produit au niveau de la région de données et vous voyez s’afficher la valeur **Tablix1**, le nom de la région de données de table dans le rapport, dans la zone **Étendue de synchronisation** .  
  
     Dans ce rapport, vous pouvez également modifier l'étendue d'un indicateur placé dans la cellule du sous-total de la sous-catégorie pour synchroniser le champ SalesDate.  
  
11. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="Title"></a> 6. Ajouter un titre de rapport  
 Un titre de rapport s'affiche dans la partie supérieure du rapport. Vous pouvez placer le titre du rapport dans un en-tête de rapport, ou si le rapport n'en utilise pas, dans une zone de texte située en haut du corps du rapport. Vous allez utiliser la zone de texte placée automatiquement en haut du corps du rapport.  
  
 Vous pouvez améliorer le texte en appliquant différents types de styles de police, de tailles et de couleurs à des expressions et des caractères spécifiques. Pour plus d’informations, consultez [Mettre en forme du texte dans une zone de texte &#40;Générateur de rapports et SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).  
  
#### <a name="to-add-a-report-title"></a>Pour ajouter un titre de rapport  
  
1.  Dans l'aire de conception, cliquez sur **Cliquez pour ajouter un titre**.  
  
2.  Type **Product Sales KPI**, puis cliquez en dehors de la zone de texte.  
  
3.  Si vous le souhaitez, avec le bouton droit de la zone de texte qui contient **Product Sales KPI**, cliquez sur **propriétés de la zone texte**, puis, sous l’onglet Police, sélectionnez les différents styles de police, les tailles et couleurs.  
  
4.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="Save"></a> 7. Enregistrer le rapport  
 Enregistrez le rapport sur un serveur de rapports ou sur votre ordinateur. Si vous n'enregistrez pas le rapport sur le serveur de rapports, plusieurs fonctionnalités de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] telles que les parties de rapports et les sous-rapports ne sont pas disponibles.  
  
#### <a name="to-save-the-report-on-a-report-server"></a>Pour enregistrer le rapport sur un serveur de rapports  
  
1.  À partir du bouton **Générateur de rapports** , cliquez sur **Enregistrer sous**.  
  
2.  Cliquez sur **Sites et serveurs récents**.  
  
3.  Sélectionnez ou tapez le nom du serveur de rapports sur lequel vous êtes autorisé à enregistrer des rapports.  
  
     Le message « Connexion au serveur de rapports » s'affiche. Une fois la connexion établie, le contenu du dossier de rapports spécifié par l'administrateur du serveur de rapports s'affiche comme emplacement par défaut des rapports.  
  
4.  Dans **Nom**, remplacez le nom par défaut par **Product Sales KPI**.  
  
5.  Cliquez sur **Enregistrer**.  
  
 Le rapport est enregistré sur le serveur de rapports. Le nom du serveur de rapports auquel vous êtes connecté est indiqué dans la barre d'état située au bas de la fenêtre.  
  
#### <a name="to-save-the-report-on-your-computer"></a>Pour enregistrer le rapport sur votre ordinateur  
  
1.  À partir du bouton **Générateur de rapports** , cliquez sur **Enregistrer sous**.  
  
2.  Cliquez sur **Bureau**, **Mes documents**ou **Poste de travail**, puis naviguez jusqu’au dossier où vous souhaitez enregistrer le rapport.  
  
> [!NOTE]  
>  Si vous n’avez pas accès à un serveur de rapports, cliquez sur **Bureau**, **Mes documents**ou **Poste de travail** et enregistrez le rapport sur votre ordinateur.  
  
1.  Dans **Nom**, remplacez le nom par défaut par **Product Sales KPI**.  
  
2.  Cliquez sur **Enregistrer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez terminé le didacticiel d'ajout d'un indicateur de performance clé à votre rapport. Pour plus d’informations, consultez jauges (Générateur de rapports) [indicateurs &#40;Générateur de rapports et SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels &#40;Générateur de rapports&#41;](report-builder-tutorials.md)   
 [Générateur de rapports dans SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
