---
title: 'Tutoriel : Création d’un rapport de tableau de base (Générateur de rapports) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d9e30521-f8ae-4c45-89c3-d40727f622f7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 93213609abbc3e274cc61207d02b3828f9b90d7d
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66099030"
---
# <a name="tutorial-creating-a-basic-table-report-report-builder"></a>Tutoriel : Création d'un rapport de tableau de base (Générateur de rapports)
  Ce didacticiel vous apprend à créer un rapport de tableau de base à partir des exemples de données de ventes. L’illustration suivante montre le rapport que vous allez créer.  
  
 ![rs_CreateBasicReportTutorial](../../2014/tutorials/media/rs-createbasicreporttutorial.gif "rs_CreateBasicReportTutorial")  
  
##  <a name="BackToTop"></a> Ce que vous allez apprendre  
 Dans ce didacticiel, vous apprendrez à effectuer les tâches suivantes :  
  
1.  [Créer un nouveau rapport à partir de la mise en route](#CreateTable)  
  
    1.  [Spécifiez une connexion de données dans l’Assistant tableau](#DataConnection)  
  
    2.  [Créer une requête dans l’Assistant tableau](#Query)  
  
    3.  [Organiser les données en groupes dans l’Assistant tableau](#Groups)  
  
    4.  [Ajouter des lignes de sous-total et de Total dans l’Assistant tableau](#Subtotals)  
  
    5.  [Choisissez un Style dans l’Assistant tableau](#Style)  
  
2.  [Format des données en tant que devises](#FormatCurrency)  
  
3.  [Format des données en tant que Date](#FormatDate)  
  
4.  [Modifier la largeur de colonne](#Width)  
  
5.  [Ajouter un titre de rapport](#Title)  
  
6.  [Enregistrer le rapport](#Save)  
  
7.  [Exporter le rapport](#Export)  
  
 Durée estimée pour effectuer ce didacticiel : 20 minutes.  
  
## <a name="requirements"></a>Configuration requise  
 Pour plus d’informations sur les spécifications, consultez [Éléments requis pour les didacticiels &#40;Générateur de rapports&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="CreateTable"></a> 1. Créer un nouveau rapport à partir de la mise en route  
 Créer un rapport de tableau à partir de la **mise en route** boîte de dialogue. Il existe deux modes : création de rapport et création de dataset partagé. En mode création de rapport, vous pouvez spécifier les données dans le volet des données de rapport et la disposition du rapport dans l'aire de conception. En mode création de dataset partagé, vous créez des requêtes de dataset à partager avec d'autres utilisateurs. Dans ce didacticiel, vous allez utiliser le mode création de rapport.  
  
#### <a name="to-create-a-new-report"></a>Pour créer un rapport  
  
1.  Cliquez sur **Démarrer**, pointez sur **Programmes**, sur **Générateur de rapports Microsoft SQL Server 2012**, puis cliquez sur **Générateur de rapports version**.  
  
     Le **mise en route** boîte de dialogue s’ouvre.  
  
    > [!NOTE]  
    >  Si le **mise en route** boîte de dialogue n’apparaît pas, à partir de la **le Générateur de rapports** bouton, cliquez sur **New**.  
  
2.  Dans le volet gauche, assurez-vous que **Nouveau rapport** est sélectionné.  
  
3.  Dans le volet droit, vérifiez que **Assistant Tableau ou matrice** est sélectionné.  
  
##  <a name="DataConnection"></a> 1a. Spécifier une connexion de données dans l'Assistant Tableau  
 Une connexion de données contient les informations nécessaires pour se connecter à une source de données externe telle qu'une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . En règle générale, vous obtenez les informations de connexion et le type d'informations d'identification à utiliser auprès du propriétaire de la source de données. Pour spécifier une connexion de données, vous pouvez utiliser une source de données partagée sur le serveur de rapports ou créer une source de données incorporée utilisée uniquement dans ce rapport.  
  
 Dans ce didacticiel, vous allez utiliser une source de données incorporée. Pour en savoir plus sur l’utilisation des sources de données partagées, consultez [Autres procédures pour l’obtention d’une connexion de données &#40;Générateur de rapports&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
#### <a name="to-create-an-embedded-data-source"></a>Pour créer une source de données incorporée  
  
1.  Dans la page **Choisir un dataset** , sélectionnez **Créer un dataset**, puis cliquez sur **Suivant**. La page **Choisir une connexion à une source de données** s’ouvre.  
  
2.  Cliquez sur **Nouveau**. La boîte de dialogue **Propriétés de la source de données** s'ouvre.  
  
3.  Dans **nom**, type **ventes de produits** un nom pour la source de données.  
  
4.  Dans **Sélectionner un type de connexion**, assurez-vous que **Microsoft SQL Server** est sélectionné.  
  
5.  Dans **chaîne de connexion**, tapez le texte suivant, où  *\<nom_serveur >* est le nom d’une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
    ```  
    Data Source=<servername>  
    ```  
  
     Dans la mesure où vous utilisez une requête qui contient les données au lieu de récupérer ces dernières à partir d'une base de données, la chaîne de connexion n'inclut pas le nom de la base de données. Pour plus d’informations, voir [Éléments requis pour les didacticiels (Générateur de rapports)](../reporting-services/report-builder-tutorials.md).  
  
6.  Cliquez sur **Informations d'identification**. Entrez les informations d'identification nécessaires pour accéder à la source de données externe.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Vous revenez à la page **Choisir une connexion à une source de données** .  
  
8.  Pour vous assurer que vous pouvez vous connecter à la source de données, cliquez sur **Tester la connexion**.  
  
     Le message « La connexion a été correctement créée » s'affiche.  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. Cliquer sur **Suivant**.  
  
##  <a name="Query"></a> 1b. Créer une requête dans l'Assistant Tableau  
 Dans un rapport, vous pouvez utiliser un dataset partagé qui comprend une requête prédéfinie, ou vous pouvez créer un dataset incorporé utilisable uniquement dans votre rapport. Dans ce didacticiel, vous allez créer un dataset incorporé.  
  
> [!NOTE]  
>  Dans ce didacticiel, la requête contient les valeurs de données, afin qu'il ne soit pas nécessaire de disposer d'une source de données externe. Cela rend la requête assez longue. Dans un environnement métier, une requête ne contient pas les données. Ceci est nécessaire à des fins de formation uniquement.  
  
#### <a name="to-create-a-query"></a>Pour créer une requête  
  
1.  Dans la page **Créer une requête** , le concepteur de requêtes relationnelles est ouvert. Pour ce didacticiel, vous utiliserez le Concepteur de requêtes textuel.  
  
     Cliquez sur **Modifier en tant que texte**. Le Concepteur de requêtes textuel affiche un volet de requête et un volet de résultats.  
  
2.  Collez la requête [!INCLUDE[tsql](../includes/tsql-md.md)] ci-après dans la zone **Requête** .  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(9924.60 AS money) AS Sales, 68 as Quantity  
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
  
3.  Dans la barre d’outils du Concepteur de requêtes, cliquez sur **Exécuter** (**!**).  
  
     La requête s'exécute et affiche le jeu de résultats pour les champs SalesDate, Subcategory, Product, Sales et Quantity.  
  
     Dans le jeu de résultats, les en-têtes de colonnes sont basés sur les noms présents dans la requête. Dans le dataset, les en-têtes de colonnes deviennent les noms de champs et sont enregistrés dans le rapport. Après avoir terminé l'Assistant, vous pouvez utiliser le volet des données de rapport pour afficher la collection de champs de dataset.  
  
4.  Cliquer sur **Suivant**.  
  
##  <a name="Groups"></a> 1c. Organiser les données en groupes dans l'Assistant Tableau  
 Lorsque vous sélectionnez des champs à regrouper, vous concevez un tableau dont les lignes et les colonnes affichent des données de détail et des données agrégées.  
  
#### <a name="to-organize-data-into-groups"></a>Pour organiser les données en groupes  
  
1.  Dans la page **Organiser les champs** , faites glisser Product vers **Valeurs**.  
  
2.  Faites glisser Quantity vers **Valeurs** et placez-le sous Product.  
  
     Quantity est automatiquement agrégé par la fonction Sum, l'agrégat par défaut des champs numériques. La valeur est [Sum(Quantity)].  
  
     Vous pouvez ouvrir la liste déroulante pour consulter les autres fonctions d'agrégation disponibles. Ne modifiez pas la fonction d'agrégation.  
  
3.  Faites glisser Sales vers **Valeurs** et placez-le sous [Sum(Quantity)].  
  
     Sales est agrégé par la fonction Sum. La valeur est [Sum(Sales)].  
  
     Les étapes 1, 2 et 3 spécifient les données à afficher dans le tableau.  
  
4.  Faites glisser SalesDate vers **Groupes de lignes**.  
  
5.  Faites glisser Subcategory vers **Groupes de lignes** et placez-le sous SalesDate.  
  
     Les étapes 4 et 5 organisent les valeurs des champs par date, puis par sous-catégorie de produits pour chaque date.  
  
6.  Cliquer sur **Suivant**.  
  
##  <a name="Subtotals"></a> 1d. Ajouter des lignes de sous-total et de total dans l'Assistant Tableau  
 Après avoir créé des groupes, vous pouvez ajouter et mettre en forme les lignes dans lesquelles afficher les valeurs agrégées des champs. Vous pouvez afficher toutes les données ou laisser l'utilisateur développer/réduire les données regroupées de manière interactive.  
  
#### <a name="to-add-subtotals-and-totals"></a>Pour ajouter des sous-totaux et des totaux  
  
1.  Dans la page **Choisir la disposition** , sous **Options**, vérifiez que **Afficher les sous-totaux et les totaux généraux** est sélectionné.  
  
2.  Vérifiez que **Bloqué, sous-total ci-dessous** est sélectionné.  
  
     Le volet Aperçu de l'Assistant affiche un tableau avec cinq lignes. Lorsque vous exécutez le rapport, chaque ligne est affichée de la manière suivante :  
  
    1.  La première ligne est répétée une fois pour le tableau afin d'afficher les en-têtes de colonnes.  
  
    2.  La deuxième ligne est répétée une fois pour chaque élément de ligne dans la commande client et affiche le nom du produit, la quantité commandée et le total de ligne.  
  
    3.  La troisième ligne est répétée une fois pour chaque commande client afin d'afficher les sous-totaux par commande.  
  
    4.  La quatrième ligne est répétée une fois pour chaque date de commande afin d'afficher les sous-totaux par jour.  
  
    5.  La cinquième ligne est répétée une fois pour le tableau afin d'afficher les totaux généraux.  
  
3.  Décochez l’option **Développer/Réduire les groupes**. Dans ce didacticiel, le rapport que vous créez n'utilise pas la fonctionnalité d'exploration vers le bas qui permet à un utilisateur de développer une hiérarchie de groupe parente afin d'afficher les lignes de groupes enfants et les lignes de détails.  
  
4.  Cliquer sur **Suivant**.  
  
##  <a name="Style"></a> 1e. Choisir un style dans l'Assistant Tableau  
 Un style spécifie un style de police, un jeu de couleurs et un style de bordure.  
  
#### <a name="to-specify-a-table-style"></a>Pour spécifier un style de tableau  
  
1.  Sur le **choisir un Style** page, dans le volet Styles, sélectionnez océan.  
  
     Le volet Aperçu affiche un aperçu du tableau avec ce style.  
  
2.  Éventuellement, cliquez sur les autres styles pour voir l'aperçu correspondant.  
  
3.  Cliquez sur **Terminer**.  
  
 Le tableau est ajouté à l'aire de conception. Le tableau possède 5 colonnes et 5 lignes. Le volet Groupes de lignes affiche trois groupes de lignes : SalesDate, Subcategory et Details. Les données de détail sont toutes les données récupérées par la requête de dataset.  
  
##  <a name="FormatCurrency"></a> 2. Mettre en forme les données en tant que devises  
 Par défaut, les données de synthèse du champ Sales affichent un nombre général. Appliquez une mise en forme pour afficher ce nombre dans un format monétaire. Activez/désactivez **Styles des espaces réservés** pour afficher les zones de texte mises en forme et le texte de l’espace réservé en tant qu’exemples de valeurs.  
  
#### <a name="to-format-a-currency-field"></a>Pour mettre en forme un champ monétaire  
  
1.  Cliquez sur **Conception** pour basculer en mode Conception.  
  
2.  Cliquez sur la cellule de la deuxième ligne (sous la ligne des en-têtes de colonnes) de la colonne Sales et faites glisser la souris vers le bas de façon à sélectionner toutes les cellules qui contiennent `[Sum(Sales)]`.  
  
3.  Sous l’onglet **Accueil** , dans le groupe **Nombre** , cliquez sur le bouton **Devise** . Les cellules changent pour afficher le format de devise.  
  
     Si votre paramètre régional est Anglais (États-Unis), le texte d’exemple par défaut est [**$12,345.00**]. Si vous ne voyez pas un exemple de valeur monétaire, cliquez sur **Styles des espaces réservés** dans le **numéros** de groupe, puis cliquez sur **exemples de valeurs**.  
  
4.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Les valeurs de synthèse de Sales s'affichent sous forme de devises.  
  
##  <a name="FormatDate"></a> 3. Mettre en forme les données de date  
 Par défaut, le champ SalesDate affiche les informations de date et d'heure. Vous pouvez le mettre en forme de sorte qu'il n'affiche que la date.  
  
#### <a name="to-format-a-date-field-as-the-default-format"></a>Pour appliquer à un champ de date le format par défaut  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Cliquez sur la cellule qui contient `[SalesDate]`.  
  
3.  Dans le ruban, sur le **accueil** sous l’onglet le **nombre** groupe, dans la liste déroulante, sélectionnez **Date**.  
  
     La cellule affiche la date d’exemple **[1/31/2000]**. Si vous ne voyez pas s’afficher d’exemple de date, cliquez sur **Styles des espaces réservés** dans le groupe **Nombres** , puis cliquez sur **Valeurs d’aperçu**.  
  
4.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Les valeurs de SalesDate s'affichent dans le format de date par défaut.  
  
#### <a name="to-change-the-date-format-to-a-custom-format"></a>Pour appliquer à une date un format personnalisé  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Cliquez sur la cellule qui contient `[SalesDate]`.  
  
3.  Sur le **accueil** sous l’onglet le **nombre** , cliquez sur le Lanceur de boîte de dialogue.  
  
     Il s'agit de la petite flèche située à l'angle droit du groupe. La boîte de dialogue **Propriétés de la zone de texte** s’ouvre.  
  
4.  Dans le volet Catégorie, vérifiez que **Date** est sélectionné.  
  
5.  Dans le volet **Type** , sélectionnez **January 31, 2000**.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     La cellule affiche l’exemple de date **[January 31, 2000]**.  
  
7.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 La valeur affichée du champ SalesDate correspond au mois dans sa forme textuelle et non numérique.  
  
##  <a name="Width"></a> 4. Modifier la largeur des colonnes  
 Par défaut, chaque cellule d'un tableau contient une zone de texte. Une zone de texte s'étend verticalement pour accueillir le texte lors du rendu de la page. Dans le rapport rendu, chaque ligne s'étend en fonction de la hauteur de la plus grande zone de texte rendue dans la ligne. La hauteur de la ligne dans l'aire de conception n'a aucun impact sur la hauteur de la ligne dans le rapport rendu.  
  
 Pour réduire l'espace vertical occupé par chaque ligne, augmentez la largeur de colonne afin d'accueillir le contenu attendu des zones de texte dans la colonne sur une seule ligne.  
  
#### <a name="to-change-the-width-of-table-columns"></a>Pour modifier la largeur des colonnes d'un tableau  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Cliquez sur la table pour que les poignées de ligne et de colonne apparaissent au-dessus et à côté de la table.  
  
     Les barres grises le long du haut et du côté de la table sont les poignées de colonne et de ligne.  
  
3.  Placez le curseur entre les séparateurs de colonne pour qu'il se transforme en flèche à deux pointes. Faites glisser les colonnes pour les redimensionner. Par exemple, agrandissez la colonne Product de sorte que le nom des produits tienne sur une seule ligne.  
  
4.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="Title"></a> 5. Ajouter un titre de rapport  
 Un titre de rapport s'affiche dans la partie supérieure du rapport. Vous pouvez placer le titre du rapport dans un en-tête de rapport, ou si le rapport n'en utilise pas, dans une zone de texte située en haut du corps du rapport. Dans ce didacticiel, vous allez utiliser la zone de texte placée automatiquement en haut du corps du rapport.  
  
 Vous pouvez améliorer le texte en appliquant différents types de styles de police, de tailles et de couleurs à des expressions et des caractères spécifiques. Pour plus d’informations, consultez [Mettre en forme du texte dans une zone de texte &#40;Générateur de rapports et SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).  
  
#### <a name="to-add-a-report-title"></a>Pour ajouter un titre de rapport  
  
1.  Dans l'aire de conception, cliquez sur **Cliquez pour ajouter un titre**.  
  
2.  Tapez **Product Sales**, puis cliquez à l’extérieur de la zone de texte.  
  
3.  Cliquez avec le bouton droit sur la zone de texte qui contient **Product Sales** , puis cliquez sur **Propriétés de la zone de texte**.  
  
4.  Dans la boîte de dialogue **Propriétés de la zone de texte** , cliquez sur **Police**.  
  
5.  Dans la liste **Taille** , sélectionnez **18pt**.  
  
6.  Dans la liste **Couleur** , sélectionnez **Bleuet**.  
  
7.  Sélectionnez **Gras**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Save"></a> 6. Enregistrer le rapport  
 Enregistrez le rapport sur un serveur de rapports ou sur votre ordinateur. Si vous n'enregistrez pas le rapport sur le serveur de rapports, plusieurs fonctionnalités de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] telles que les parties de rapports et les sous-rapports ne sont pas disponibles.  
  
#### <a name="to-save-the-report-on-a-report-server"></a>Pour enregistrer le rapport sur un serveur de rapports  
  
1.  À partir du bouton **Générateur de rapports** , cliquez sur **Enregistrer sous**.  
  
2.  Cliquez sur **Sites et serveurs récents**.  
  
3.  Sélectionnez ou tapez le nom du serveur de rapports sur lequel vous êtes autorisé à enregistrer des rapports.  
  
     Le message « Connexion au serveur de rapports » s'affiche. Une fois la connexion établie, le contenu du dossier de rapports spécifié par l'administrateur du serveur de rapports s'affiche comme emplacement par défaut des rapports.  
  
4.  Dans **Nom**, remplacez le nom par défaut par **Ventes de produits**.  
  
5.  Cliquez sur **Enregistrer**.  
  
 Le rapport est enregistré sur le serveur de rapports. Le nom du serveur de rapports auquel vous êtes connecté est indiqué dans la barre d'état située au bas de la fenêtre.  
  
#### <a name="to-save-the-report-on-your-computer"></a>Pour enregistrer le rapport sur votre ordinateur  
  
1.  À partir du bouton **Générateur de rapports** , cliquez sur **Enregistrer sous**.  
  
2.  Cliquez sur **Bureau**, **Mes documents**ou **Poste de travail**, puis naviguez jusqu’au dossier où vous souhaitez enregistrer le rapport.  
  
3.  Dans **Nom**, remplacez le nom par défaut par **Ventes de produits**.  
  
4.  Cliquez sur **Enregistrer**.  
  
##  <a name="Export"></a> 7. Exporter le rapport  
 Les rapports peuvent être exportés vers différents formats, par exemple Microsoft Excel et les fichiers de valeurs séparées par des virgules (CSV). Pour plus d’informations, consultez [exportation des rapports &#40;Générateur de rapports et SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md).  
  
 Dans ce didacticiel, vous allez exporter le rapport vers Excel et définir une propriété du rapport afin de fournir un nom personnalisé pour l'onglet de classeur.  
  
#### <a name="to-specify-the-workbook-tab-name"></a>Pour spécifier le nom de l'onglet de classeur  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Cliquez n'importe où en dehors du rapport.  
  
3.  . Dans le volet Propriétés, recherchez la propriété InitialPageName et tapez **Product Sales Excel**.  
  
    > [!NOTE]  
    >  Si le volet Propriétés n’est pas visible, cliquez sur l’onglet Affichage sur le ruban, puis cliquez sur **propriétés**.  
  
#### <a name="to-export-a-report-to-excel"></a>Pour exporter un rapport vers Excel  
  
1.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
2.  . Dans le ruban, cliquez sur **exporter**, puis cliquez sur **Excel**.  
  
     La boîte de dialogue **Enregistrer sous** s'affiche.  
  
3.  Accédez à la **Documents** dossier.  
  
4.  Dans le **nom de fichier** zone de texte, tapez **Product Sales Excel**.  
  
5.  Vérifiez que le type de fichier est **classeur Excel**.  
  
6.  Cliquez sur **Enregistrer**.  
  
#### <a name="to-view-the-report-in-excel"></a>Pour afficher le rapport dans Excel  
  
1.  Ouvrez le **Documents** dossier et double-cliquez sur **ventes de produits Excel.xlsx**.  
  
2.  Vérifiez que le nom de l’onglet de classeur est **Product Sales Excel**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Ceci conclut la procédure pas à pas décrivant comment créer un rapport de tableau de base. Pour plus d’informations sur les tables, consultez [Tables, matrices et listes &#40;Générateur de rapports et SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels &#40;Générateur de rapports&#41;](report-builder-tutorials.md)   
 [Générateur de rapports dans SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
