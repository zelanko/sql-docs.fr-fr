---
title: 'Didacticiel : Introduction aux Expressions | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 2d05ef4c-5f91-48b2-8795-f0a201a0b3cc
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 096a0678ccb86c232d4eaca792aa143379710fea
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52399333"
---
# <a name="tutorial-introducing-expressions"></a>Didacticiel : Introduction aux Expressions
  Les expressions vous permettent de créer des rapports puissants et flexibles. Ce didacticiel vous apprend à créer et implémenter des expressions qui utilisent des fonctions et des opérateurs communs. Vous utiliserez le **Expression** boîte de dialogue pour écrire des expressions qui concatènent des valeurs de nom, recherchent des valeurs dans un dataset distinct, afficher des images différentes en fonction des valeurs de champ et ainsi de suite.  
  
 Le rapport est un rapport en barres avec des lignes en couleur alternées de lignes blanches. Le rapport inclut un paramètre de sélection de couleur pour les lignes non blanches.  
  
 L'illustration suivante montre un rapport similaire à celui que vous allez créer.  
  
 ![rs_ExpressionsTutorial](../../2014/tutorials/media/rs-expressionstutorial.gif "rs_ExpressionsTutorial")  
  
##  <a name="BackToTop"></a> Ce que vous allez apprendre  
 Dans ce didacticiel, vous apprendrez à effectuer les tâches suivantes :  
  
1.  [Créer un rapport de tableau et le jeu de données à partir de l’Assistant tableau ou matrice](#Setup)  
  
2.  [Mettre à jour les noms par défaut des données Source et le jeu de données](#UpdateNames)  
  
3.  [Prénom, initiale et le nom d’affichage](#Concatenate)  
  
4.  [Utilisez des Images pour afficher le sexe](#Gender)  
  
5.  [Rechercher le nom de CountryRegion](#Lookup)  
  
6.  [Compter les jours depuis le dernier achat](#Count)  
  
7.  [Utiliser un indicateur pour afficher la comparaison des ventes](#Indicator)  
  
8.  [Rendre le rapport « Bicolore » de rapports](#GreenBar)  
  
### <a name="other-optional-steps"></a>Autres étapes facultatives  
  
-   [Formater la colonne de Date](#DateFormat)  
  
-   [Ajouter un titre de rapport](#Title)  
  
-   [Enregistrer le rapport](#Save)  
  
 Durée estimée pour effectuer ce didacticiel : 30 minutes  
  
## <a name="requirements"></a>Configuration requise  
 Pour plus d’informations sur les spécifications, consultez [Éléments requis pour les didacticiels &#40;Générateur de rapports&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="Setup"></a> 1. Créer un rapport de tableau et un dataset à partir de l'Assistant Tableau ou matrice  
 Créez un rapport de tableau, une source de données et un dataset. Lorsque vous créez le tableau, n'incluez que quelques champs. Après avoir terminé l'Assistant, vous ajouterez manuellement des colonnes. L'Assistant vous permet de disposer facilement un tableau et d'appliquer un style.  
  
> [!NOTE]  
>  Dans ce didacticiel, la requête contient les valeurs de données, afin qu'il ne soit pas nécessaire de disposer d'une source de données externe. Cela rend la requête assez longue. Dans un environnement métier, une requête ne contient pas les données. Ceci est nécessaire à des fins de formation uniquement.  
  
> [!NOTE]  
>  Dans ce didacticiel, les étapes de l'Assistant sont consolidées en une seule procédure. Pour obtenir des instructions détaillées sur l’accès à un serveur de rapports, choisissez une source de données et créer un jeu de données, consultez le premier didacticiel de cette série : [Didacticiel : Création d’un rapport de tableau de base &#40;Générateur de rapports&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
#### <a name="to-create-a-new-table-report"></a>Pour créer un nouveau rapport de tableau  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **le Générateur de rapports**, puis cliquez sur **le Générateur de rapports**.  
  
     La boîte de dialogue **Mise en route** s'affiche.  
  
    > [!NOTE]  
    >  Si le **mise en route** boîte de dialogue n’apparaît pas, à partir de la **le Générateur de rapports** bouton, cliquez sur **New**.  
  
    > [!NOTE]  
    >  Si vous préférez utiliser la version ClickOnce du Générateur de rapports, ouvrez le Gestionnaire de rapports et cliquez sur **le Générateur de rapports**, ou accédez à un site SharePoint sur les Services de création de rapports des types de contenu tels que les rapports sont activés et cliquez sur  **Rapport du Générateur de rapports** sur le **Nouveau Document** menu sur le **Documents** onglet d’une bibliothèque de documents partagés.  
  
2.  Dans le volet gauche, assurez-vous que **Nouveau rapport** est sélectionné.  
  
3.  Dans le volet droit, cliquez sur **Assistant Tableau ou matrice**.  
  
4.  Dans la page **Choisir un dataset** , cliquez sur **Créer un dataset**.  
  
5.  Cliquer sur **Suivant**.  
  
6.  Dans la page **Choisir une connexion à une source de données**, sélectionnez une source de données de type **SQL Server**. Sélectionnez une source de données dans la liste ou naviguez jusqu'au serveur de rapports pour en sélectionner une.  
  
7.  Cliquer sur **Suivant**.  
  
8.  Dans la page **Créer une requête** , cliquez sur **Modifier en tant que texte**.  
  
9. Collez la requête suivante dans le volet de requête :  
  
    ```  
    SELECT 'Lauren' AS FirstName,'Johnson' AS LastName, 'American Samoa' AS StateProvince, 1 AS CountryRegionID,'Unknown' AS Gender, CAST(9996.60 AS money) AS YTDPurchase, CAST('2010-6-10' AS date) AS LastPurchase  
    UNION SELECT'Warren' AS FirstName, 'Pal' AS LastName, 'New South Wales' AS StateProvince, 2 AS CountryRegionID, 'Male' AS Gender, CAST(5747.25 AS money) AS YTDPurchase, CAST('2010-7-3' AS date) AS LastPurchase  
    UNION SELECT 'Fernando' AS FirstName, 'Ross' AS LastName, 'Alberta' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(9248.15 AS money) AS YTDPurchase, CAST('2010-10-17' AS date) AS LastPurchase  
    UNION SELECT 'Rob' AS FirstName, 'Caron' AS LastName, 'Northwest Territories' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(742.50 AS money) AS YTDPurchase, CAST('2010-4-29' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Bailey' AS LastName, 'British Columbia' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(1147.50 AS money) AS YTDPurchase, CAST('2010-6-15' AS date) AS LastPurchase  
    UNION SELECT  'Bridget' AS FirstName, 'She' AS LastName, 'Hamburg' AS StateProvince, 4 AS CountryRegionID, 'Female' AS Gender, CAST(7497.30 AS money) AS YTDPurchase, CAST('2010-5-10' AS date) AS LastPurchase  
    UNION SELECT 'Alexander' AS FirstName, 'Martin' AS LastName, 'Saxony' AS StateProvince, 4 AS CountryRegionID, 'Male' AS Gender, CAST(2997.60 AS money) AS YTDPurchase, CAST('2010-11-19' AS date) AS LastPurchase  
    UNION SELECT 'Yolanda' AS FirstName, 'Sharma' AS LastName ,'Micronesia' AS StateProvince, 5 AS CountryRegionID, 'Female' AS Gender, CAST(3247.95 AS money) AS YTDPurchase, CAST('2010-8-23' AS date) AS LastPurchase  
    UNION SELECT 'Marc' AS FirstName, 'Zimmerman' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1200.00 AS money) AS YTDPurchase, CAST('2010-11-16' AS date) AS LastPurchase  
    UNION SELECT 'Katherine' AS FirstName, 'Abel' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Female' AS Gender, CAST(2025.00 AS money) AS YTDPurchase, CAST('2010-12-1' AS date) AS LastPurchase  
    UNION SELECT 'Nicolas' as FirstName, 'Anand' AS LastName, 'Seine (Paris)' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1425.00 AS money) AS YTDPurchase, CAST('2010-12-11' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Peters' AS LastName, 'England' AS StateProvince, 12 AS CountryRegionID, 'Male' AS Gender, CAST(887.50 AS money) AS YTDPurchase, CAST('2010-8-15' AS date) AS LastPurchase  
    UNION SELECT 'Alison' AS FirstName, 'Nath' AS LastName, 'Alaska' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(607.50 AS money) AS YTDPurchase, CAST('2010-10-13' AS date) AS LastPurchase  
    UNION SELECT 'Grace' AS FirstName, 'Patterson' AS LastName, 'Kansas' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(1215.00 AS money) AS YTDPurchase, CAST('2010-10-18' AS date) AS LastPurchase  
    UNION SELECT 'Bobby' AS FirstName, 'Sanchez' AS LastName, 'North Dakota' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(6191.00 AS money) AS YTDPurchase, CAST('2010-9-17' AS date) AS LastPurchase  
    UNION SELECT 'Charles' AS FirstName, 'Reed' AS LastName, 'Nebraska' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8772.00 AS money) AS YTDPurchase, CAST('2010-8-27' AS date) AS LastPurchase  
    UNION SELECT 'Orlando' AS FirstName, 'Romeo' AS LastName, 'Texas' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8578.00 AS money) AS YTDPurchase, CAST('2010-7-29' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    ```  
  
     La requête spécifie les noms de colonne, notamment la date de naissance, le prénom, le nom, l'État ou la province, l'identifiant de pays/région, le sexe et les achats de l'année en cours jusqu'à ce jour.  
  
10. Dans la barre d’outils du Concepteur de requêtes, cliquez sur **Exécuter** (**!**). Le jeu de résultats affiche 20 lignes de données et inclut les colonnes suivantes : FirstName, LastName, StateProvince, CountryRegionID, Gender, Ytdpurcharse et LastPurchase.  
  
11. Cliquer sur **Suivant**.  
  
12. Dans la page **Organiser les champs** , faites glisser les champs suivants, dans l’ordre spécifié, de la liste **Champs disponibles** vers la liste **Valeurs** .  
  
    -   StateProvince  
  
    -   CountryRegionID  
  
    -   LastPurchase  
  
    -   YTDPurchase  
  
     Les champs CountryRegionID et YTDPurchase contenant des données numériques, l'agrégat SUM est appliqué par défaut.  
  
    > [!NOTE]  
    >  Les champs FirstName et LastName ne sont pas inclus. Vous les ajouterez dans une prochaine étape.  
  
13. Dans le **valeurs** liste, avec le bouton droit `CountryRegionID` et cliquez sur le **somme** option.  
  
     L'agrégat Sum n'est plus appliqué à CountryRegionID.  
  
14. Dans la liste **Valeurs** , cliquez avec le bouton droit sur **YTDPurchase** et cliquez sur l’option **Sum** .  
  
     L'agrégat Sum n'est plus appliqué à YTDPurchase.  
  
15. Cliquer sur **Suivant**.  
  
16. Dans la page **Choisir la disposition**, cliquez sur **Suivant**.  
  
17. Sur le **choisir un style** , cliquez sur **ardoise**, puis cliquez sur **Terminer**.  
  
##  <a name="UpdateNames"></a> 2. Mettre à jour les noms par défaut de la source de données et du dataset  
  
#### <a name="to-update-the-default-name-of-the-data-source"></a>Pour mettre à jour le nom par défaut de la source de données  
  
1.  Dans le volet Données du rapport, développez **Sources de données**.  
  
2.  Cliquez avec le bouton droit sur **DataSource1** et cliquez sur **Propriétés de la source de données**.  
  
3.  Dans la zone **Nom** , tapez **ExpressionsDataSource**.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-update-the-default-name-of-the-dataset"></a>Pour mettre à jour le nom par défaut du dataset  
  
1.  Dans le volet Données du rapport, développez **Datasets**.  
  
2.  Cliquez avec le bouton droit sur le **Dataset1** et cliquez sur **Propriétés du dataset**.  
  
3.  Dans la zone **Nom** , tapez **Expressions**.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Concatenate"></a> 3. Afficher le prénom, les initiales et le nom  
 Utilisez la fonction **Left** et l’opérateur **Concaténer** (**&**) dans une expression dont la valeur est un nom qui comprend une initiale et un nom. Vous pouvez générer l’expression pas à pas ou avancer dans la procédure et copier/coller l’expression à partir du didacticiel dans la boîte de dialogue **Expression**.  
  
#### <a name="to-add-the-name-column"></a>Pour ajouter la colonne Name  
  
1.  Cliquez avec le bouton droit sur la colonne **StateProvince**, pointez sur **Insérer une colonne** et cliquez sur **Gauche**.  
  
     Une nouvelle colonne est ajoutée à gauche de la colonne **StateProvince**.  
  
2.  Cliquez sur le titre de la nouvelle colonne et tapez **Name**.  
  
3.  Cliquez avec le bouton droit sur la cellule de données pour la colonne **Name** et cliquez sur **Expression**.  
  
4.  Dans la boîte de dialogue **Expression** , développez **Fonctions communes**, puis cliquez sur **Texte**.  
  
5.  Dans la liste **Élément** , double-cliquez sur **Left**.  
  
     La fonction **Left** est ajoutée à l’expression.  
  
6.  Dans la liste **Catégorie** , cliquez sur **Champs (Expressions)**.  
  
7.  Dans la liste **Valeurs** , double-cliquez sur **FirstName**.  
  
8.  Tapez **, 1)**  
  
     Cette expression extrait un caractère de la valeur **FirstName**, en partant de la gauche.  
  
9. Tapez **&" "&**  
  
10. Dans la liste **Valeurs** , double-cliquez sur **LastName**.  
  
     Expression complétée : `=Left(Fields!FirstName.Value, 1) &" "& Fields!LastName.Value`  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="Gender"></a> 4. Utiliser des images pour afficher le sexe  
 Utilisez des images pour afficher le sexe d'une personne et identifiez les valeurs de sexe inconnues à l'aide d'une troisième image. Ajoutez trois images cachées au rapport et une nouvelle colonne pour afficher les images, puis déterminez l'image qui apparaît dans la colonne en fonction de la valeur du champ Sexe.  
  
 Pour appliquer une couleur à la cellule du tableau qui contient l'image lors de la conversion du rapport en rapport en barres, ajoutez un rectangle puis ajoutez l'image au rectangle. Vous devez utiliser un rectangle car vous pouvez appliquez une couleur d'arrière-plan à un rectangle et non à une image.  
  
 Le didacticiel utilise des images installées avec Windows, mais vous pouvez utiliser l'image que vous voulez. Utilisez des images incorporées, il n'est pas nécessaire de les installer sur votre ordinateur local ou sur le serveur de rapports.  
  
#### <a name="to-add-images-to-the-report-body"></a>Pour ajouter des images au corps du rapport  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Sous l’onglet **Insérer** du ruban, cliquez sur **Image** et cliquez dans le corps du rapport, en dessous du tableau.  
  
     La boîte de dialogue **Propriétés de l’image** s’ouvre.  
  
3.  Cliquez sur **Importer** et naviguez vers C:\Users\Public\Public Pictures\Sample Pictures.  
  
4.  Cliquez sur Penguins.JPG et cliquez sur **Ouvrir**.  
  
     Dans la boîte de dialogue **Propriétés de l’image**, cliquez sur **Visibilité**, puis sur l’option **Masquer**.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Répétez les étapes 2 à 5, mais choisissez Koala.JPG.  
  
7.  Répétez les étapes 2 à 5, mais choisissez Tulips.JPG.  
  
#### <a name="to-add-the-gender-column"></a>Pour ajouter la colonne Gender  
  
1.  Cliquez avec le bouton droit sur la colonne **Name**, pointez sur **Insérer une colonne** et cliquez sur **Droite**.  
  
     Une nouvelle colonne est ajoutée à droite de la colonne **Name**.  
  
2.  Cliquez sur le titre de la nouvelle colonne et tapez **Gender**.  
  
#### <a name="to-add-a-rectangle"></a>Pour ajouter un rectangle  
  
-   Sous l’onglet **Insérer** du ruban, cliquez sur **Rectangle** et cliquez sur la cellule de données de la colonne **Gender**.  
  
     Un rectangle est ajouté à la cellule.  
  
#### <a name="to-add-an-image-to-the-rectangle"></a>Pour ajouter une image au rectangle.  
  
1.  Cliquez avec le bouton droit dans le rectangle, pointez sur **Insérer** puis cliquez sur **Image**.  
  
2.  Dans la boîte de dialogue **Propriétés de l’image**, cliquez sur la flèche pointant vers le bas située à côté de **Utiliser cette image** et sélectionnez une des images ajoutées, par exemple Penguins.JPG.  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-use-images-to-show-gender"></a>Pour utiliser des images pour afficher le sexe  
  
1.  Cliquez avec le bouton droit sur l’image dans la cellule de données de la colonne **Gender** et cliquez sur **Propriétés de l’image**.  
  
2.  Dans la boîte de dialogue **Propriétés de l’image**, cliquez sur le bouton d’expression **fx** situé à côté de la zone de texte **Utiliser cette image**.  
  
3.  Dans la boîte de dialogue **Expression**, développez **Fonctions communes** et cliquez sur **Flux de programme**.  
  
4.  Dans la liste **Élément** , double-cliquez sur **Switch**.  
  
5.  Dans la liste **Catégorie** , cliquez sur **Champs (Expressions)**.  
  
6.  Dans la liste **Valeurs** , double-cliquez sur **Gender**.  
  
7.  Tapez **="Male", "Koala",**  
  
8.  Dans la liste **Valeurs** , double-cliquez sur **Gender**.  
  
9. Tapez **="Female", "Penguins",**  
  
10. Dans la liste **Valeurs**, double-cliquez sur **Gender**.  
  
11. Tapez **="Unknown", "Tulips")**  
  
     Expression complétée : `=Switch(Fields!Gender.Value ="Male", "Koala",Fields!Gender.Value ="Female","Penguins",Fields!Gender.Value ="Unknown","Tulips")`  
  
12. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
13. Recliquez sur **OK** pour fermer la boîte de dialogue **Propriétés de l’image**.  
  
14. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="Lookup"></a> 5. Rechercher un nom de CountryRegion  
 Créez le dataset CountryRegion et utilisez la fonction **Lookup** pour afficher le nom d’un pays/région au lieu de l’identifiant de pays/région.  
  
#### <a name="to-create-the-countryregion-dataset"></a>Pour créer le dataset CountryRegion  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Dans le volet des données de rapport, cliquez sur **Nouveau** , puis sur **Dataset**.  
  
3.  Cliquez sur **Utiliser un dataset incorporé dans mon rapport**.  
  
4.  Dans la liste **Source de données**, sélectionnez ExpressionsDataSource.  
  
5.  Dans la zone **Nom** , tapez **CountryRegion**.  
  
6.  Vérifiez que le type de requête **Texte** est sélectionné et cliquez sur **Concepteur de requêtes**.  
  
7.  Cliquez sur **Modifier en tant que texte**.  
  
8.  Copiez et collez la requête suivante dans le volet de requête :  
  
    ```  
    SELECT 1 AS ID, 'American Samoa' AS CountryRegion  
    UNION SELECT 2 AS CountryRegionID, 'Australia' AS CountryRegion  
    UNION SELECT 3 AS ID, 'Canada' AS CountryRegion  
    UNION SELECT 4 AS ID, 'Germany' AS CountryRegion  
    UNION SELECT 5 AS ID, 'Micronesia' AS CountryRegion  
    UNION SELECT 6 AS ID, 'France' AS CountryRegion  
    UNION SELECT 7 AS ID, 'United States' AS CountryRegion  
    UNION SELECT 8 AS ID, 'Brazil' AS CountryRegion  
    UNION SELECT 9 AS ID, 'Mexico' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Japan' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Australia' AS CountryRegion  
    UNION SELECT 12 AS ID, 'United Kingdom' AS CountryRegion  
    ```  
  
9. Cliquez sur **Exécuter** (**!**) pour exécuter la requête.  
  
     Les résultats de la requête sont les identifiants et les noms des pays/régions.  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. Recliquez sur **OK** pour fermer la boîte de dialogue **Propriétés du dataset**.  
  
#### <a name="to-look-up-values-in-the-countryregion-dataset"></a>Pour rechercher des valeurs dans le dataset CountryRegion  
  
1.  Cliquez sur le **Country Region ID** titre de colonne et supprimez le texte : ID.  
  
2.  Cliquez avec le bouton droit sur la cellule de données pour la colonne **Country Region** et cliquez sur **Expression**.  
  
3.  Supprimez l'expression sauf le signe (=) de début.  
  
     L’expression restante est : `=`  
  
4.  Dans la boîte de dialogue **Expression**, développez **Fonctions communes** et cliquez sur **Divers**.  
  
5.  Dans la liste **Élément**, double-cliquez sur **Lookup**.  
  
6.  Dans la liste **Catégorie** , cliquez sur **Champs (Expressions)**.  
  
7.  Dans le **valeurs** , double-cliquez sur `CountryRegionID`.  
  
8.  Si le curseur ne se trouve pas déjà immédiatement après `CountryRegionID.Value`, placez-le à cet endroit.  
  
9. Supprimez la parenthèse de droite puis tapez **,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")**  
  
     Expression complétée : `=Lookup(Fields!CountryRegionID.Value,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")`  
  
     La syntaxe de la fonction **Lookup** spécifie une recherche entre CountryRegionID et ID dans le dataset CountryRegion qui retourne la valeur CountryRegion, également dans le dataset CountryRegion.  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="Count"></a> 6. Compter les jours depuis le dernier achat  
 Ajouter une colonne, puis utiliser le **maintenant** (fonction) ou le `ExecutionTime` variable globale intégrée pour calculer le nombre de jours écoulés depuis une personne dernière achats.  
  
#### <a name="to-add-the-days-ago-column"></a>Pour ajouter la colonne Days Ago  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Cliquez avec le bouton droit sur la colonne **Last Purchase** , pointez sur **Insérer une colonne**et cliquez sur **Droite**.  
  
     Une nouvelle colonne est ajoutée à droite de la colonne **Last Purchase** .  
  
3.  Dans l’en-tête de colonne, tapez **Days Ago**.  
  
4.  Cliquez avec le bouton droit sur la cellule de données pour la colonne **Days Ago** et cliquez sur **Expression**.  
  
5.  Dans la boîte de dialogue **Expression**, développez **Fonctions communes**, puis cliquez sur **Date & heure**.  
  
6.  Dans la liste **Élément**, double-cliquez sur **DateDiff**.  
  
7.  Si le curseur ne se trouve pas déjà immédiatement après `DateDiff(`, placez-le à cet endroit.  
  
8.  Tapez **"d",**  
  
9. Dans la liste **Catégorie** , cliquez sur **Champs (Expressions)**.  
  
10. Dans la liste **Valeurs**, double-cliquez sur **LastPurchase**.  
  
11. Si le curseur ne se trouve pas déjà immédiatement après `Fields!LastPurchase.Value`, placez-le à cet endroit.  
  
12. Tapez **,**  
  
13. Dans la liste **Catégorie**, recliquez sur **Date & heure**.  
  
14. Dans la liste **Élément**, double-cliquez sur **Now**.  
  
    > [!WARNING]  
    >  Dans les rapports de production, vous ne devez pas utiliser la fonction **Now** dans les expressions évaluées plusieurs fois pendant la génération du rapport (par exemple, dans les lignes de détails d’un rapport). La valeur de **Now** change de ligne en ligne et les différentes valeurs affectent les résultats de l’évaluation des expressions, ce qui entraîne des résultats légèrement incohérents. Vous devez utiliser à la place la variable globale `ExecutionTime` fournie par [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
15. Si le curseur ne se trouve pas déjà immédiatement après `Now(`, placez-le à cet endroit.  
  
16. Supprimez la parenthèse de gauche puis tapez **)**  
  
     Expression complétée : `=DateDiff("d", Fields!LastPurchase.Value, Now)`  
  
17. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Indicator"></a> 7. Utiliser un indicateur pour afficher la comparaison des ventes  
 Ajouter une nouvelle colonne et utiliser un indicateur pour indiquer si les achats year-to-date (YTD) d’une personne sont au-dessus ou au-dessous de la moyenne des qu'achats YTD. La fonction **Round** supprime les décimales des valeurs.  
  
 La configuration de l'indicateur et de ses états nécessite plusieurs étapes. Si vous le souhaitez dans la procédure « pour configurer l’indicateur », vous pouvez passer directement et copier/coller les expressions complétées à partir de ce didacticiel dans le **Expression** boîte de dialogue.  
  
#### <a name="to-add-the--or---avg-sales-column"></a>Pour ajouter la colonne + or - AVG Sales  
  
1.  Cliquez avec le bouton droit sur la colonne **YTD Purchase** , pointez sur **Insérer une colonne**et cliquez sur **Droite**.  
  
     Une nouvelle colonne est ajoutée à droite de la colonne **YTD Purchase**.  
  
2.  Cliquez sur le titre de la nouvelle colonne et tapez **+ or - AVG Sales**.  
  
#### <a name="to-add-an-indicator"></a>Pour ajouter un indicateur  
  
1.  Sous l’onglet **Insérer** du ruban, cliquez sur **Indicateur** et cliquez sur la cellule de données de la colonne **+ or - AVG Sales**.  
  
     La boîte de dialogue **Sélectionner un type d’indicateur** s’ouvre.  
  
2.  Dans le groupe **Directionnel** des jeux d’icônes, cliquez sur le jeu des trois flèches grises.  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-configure-the-indicator"></a>Pour configurer l'indicateur  
  
1.  Cliquez avec le bouton droit sur l’indicateur, cliquez sur **Propriétés de l’indicateur**, puis sur **Valeur et états**.  
  
2.  Cliquez sur le bouton d’expression **fx** situé à côté de la zone de texte **Valeur** .  
  
3.  Dans la boîte de dialogue **Expression** , développez **Fonctions communes**, puis cliquez sur **Math**.  
  
4.  Dans la liste **Élément**, double-cliquez sur **Round**.  
  
5.  Dans la liste **Catégorie**, cliquez sur **Champs (Expressions)**.  
  
6.  Dans la liste **Valeurs**, double-cliquez sur **YTDPurchase**.  
  
7.  Si le curseur ne se trouve pas déjà immédiatement après `Fields!YTDPurchase.Value`, placez-le à cet endroit.  
  
8.  Tapez **-**  
  
9. Redéveloppez **Fonctions communes** et cliquez sur **Agrégation**.  
  
10. Dans la liste **Élément**, double-cliquez sur **Avg**.  
  
11. Dans la liste **Catégorie** , cliquez sur **Champs (Expressions)**.  
  
12. Dans la liste **Valeurs**, double-cliquez sur **YTDPurchase**.  
  
13. Si le curseur ne se trouve pas déjà immédiatement après `Fields!YTDPurchase.Value`, placez-le à cet endroit.  
  
14. Tapez **, "Expressions"))**  
  
     Expression complétée : `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions"))`  
  
15. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
16. Dans la zone **Unité de mesure des états** , sélectionnez **Numérique**.  
  
17. Dans la ligne contenant la flèche pointant vers le bas, cliquez sur le bouton **fx** situé à droite de la zone de texte pour la valeur **Démarrer**.  
  
18. Dans la boîte de dialogue **Expression**, développez **Fonctions communes**, puis cliquez sur **Math**.  
  
19. Dans la liste **Élément**, double-cliquez sur **Round**.  
  
20. Dans la liste **Catégorie**, cliquez sur **Champs (Expressions)**.  
  
21. Dans la liste **Valeurs**, double-cliquez sur **YTDPurchase**.  
  
22. Si le curseur ne se trouve pas déjà immédiatement après `Fields!YTDPurchase.Value`, placez-le à cet endroit.  
  
23. Tapez **-**  
  
24. Redéveloppez **Fonctions communes** et cliquez sur **Agrégation**.  
  
25. Dans la liste **Élément**, double-cliquez sur **Avg**.  
  
26. Dans la liste **Catégorie** , cliquez sur **Champs (Expressions)**.  
  
27. Dans la liste **Valeurs**, double-cliquez sur **YTDPurchase**.  
  
28. Si le curseur ne se trouve pas déjà immédiatement après `Fields!YTDPurchase.Value`, placez-le à cet endroit.  
  
29. Tapez **, "Expressions")) < 0**  
  
     Expression complétée : `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) < 0`  
  
30. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
31. Dans la zone de texte de la valeur **Fin** , tapez **0**  
  
32. Cliquez sur la ligne contenant la flèche pointant à l’horizontale et cliquez sur **Supprimer**.  
  
33. Dans la ligne contenant la flèche pointant vers le haut, dans la zone **Démarrer**, tapez **0**  
  
34. Cliquez sur le bouton **fx** situé à droite de la zone de texte pour la valeur **Fin** .  
  
35. Dans le **Expression** boîte de dialogue zone, créez l’expression : `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) >0`  
  
36. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
37. Cliquez sur **OK** à nouveau pour fermer la boîte de dialogue **Propriétés de l’indicateur** .  
  
38. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
##  <a name="GreenBar"></a> 8. Rendre le rapport « Bicolore » de rapports  
 Utilisez un paramètre pour spécifier la couleur à appliquer aux lignes alternées dans le rapport, pour en faire un rapport en barres.  
  
#### <a name="to-add-a-parameter"></a>Pour ajouter un paramètre  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Dans le volet **Données du rapport**, cliquez avec le bouton droit sur **Paramètres** et cliquez sur **Ajouter un paramètre**.  
  
     La boîte de dialogue **Propriétés du paramètre de rapport** s'ouvre.  
  
3.  Dans **Invite**, tapez **Choisir une couleur**.  
  
4.  Dans la zone **Nom**, tapez **RowColor**.  
  
5.  Dans le volet gauche, cliquez sur **Valeurs disponibles**.  
  
6.  Cliquez sur **Spécifier les valeurs**.  
  
7.  Cliquez sur **Ajouter**.  
  
8.  Dans le **étiquette** , tapez : **Jaune**  
  
9. Dans la zone **Valeur** , tapez **Yellow**.  
  
10. Cliquez sur **Ajouter**.  
  
11. Dans la zone **Étiquette** , tapez **Green**.  
  
12. Dans la zone **Valeur** , tapez **PaleGreen**.  
  
13. Cliquez sur **Ajouter**.  
  
14. Dans la zone **Étiquette** , tapez **Blue**.  
  
15. Dans la zone **Valeur** , tapez **LightBlue**.  
  
16. Cliquez sur **Ajouter**.  
  
17. Dans la zone **Étiquette** , tapez **Pink**.  
  
18. Dans la zone **Valeur** , tapez **Pink**.  
  
19. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-apply-alternating-colors-to-detail-rows"></a>Pour appliquer des couleurs alternées aux lignes de détails  
  
1.  Cliquez sur l’onglet **Affichage** du ruban et vérifiez que **Propriétés** est sélectionné.  
  
2.  Cliquez sur la cellule de données pour la colonne **Name** et enfoncez la touche Maj.  
  
3.  Une par une, cliquez sur les autres cellules de la ligne.  
  
4.  Dans le volet Propriétés, cliquez sur **BackgroundColor**.  
  
     Si votre volet de propriétés répertorie les propriétés par catégorie, vous trouverez **BackgroundColor** sous la catégorie **Remplir**.  
  
5.  Cliquez sur la flèche pointant vers le bas, puis sur **Expression**.  
  
6.  Dans la boîte de dialogue **Expression**, développez **Fonctions communes** puis cliquez sur **Flux de programme**.  
  
7.  Dans la liste **Élément**, double-cliquez sur **IIf**.  
  
8.  Développez **Fonctions communes** et cliquez sur **Agrégation**.  
  
9. Dans la liste **Élément**, double-cliquez sur **RunningValue**.  
  
10. Dans la liste **Catégorie** , cliquez sur **Champs (Expressions)**.  
  
11. Dans la liste **Valeurs**, double-cliquez sur **FirstName**.  
  
12. Si le curseur ne se trouve pas déjà immédiatement après `Fields!FirstName.Value`, placez-le à cet endroit et tapez **,**  
  
13. Développez **Fonctions communes** et cliquez sur **Agrégation**.  
  
14. Dans la liste **Élément**, double-cliquez sur **Count**.  
  
15. Si le curseur ne se trouve pas déjà immédiatement après `Count(`, placez-le à cet endroit.  
  
16. Supprimez la parenthèse de gauche et tapez **, « Expressions »)**  
  
    > [!NOTE]  
    >  Expressions est le nom du dataset dans lequel sont comptées les lignes de données.  
  
17. Développez **Opérateurs** et cliquez sur **Arithmétique**.  
  
18. Dans la liste **Élément**, double-cliquez sur **Mod**.  
  
19. Si le curseur ne se trouve pas déjà immédiatement après `Mod`, placez-le à cet endroit.  
  
20. Tapez **2 =0,**  
  
    > [!IMPORTANT]  
    >  Veillez à inclure un espace avant de taper le chiffre 2.  
  
21. Cliquez sur **Paramètres** et dans la liste **Valeurs**, double-cliquez sur **RowColor**.  
  
22. Si le curseur ne se trouve pas déjà immédiatement après `Parameters!RowColor.Value`, placez-le à cet endroit.  
  
23. Tapez **, « White »)**  
  
     Expression complétée : `=IIf(RunningValue(Fields!FirstName.Value,Count, "Expressions") Mod 2 =0, Parameters!RowColor.Value, "White")`  
  
24. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="run-the-report"></a>Exécuter le rapport  
  
1.  Si vous ne vous trouvez pas sous l’onglet **Accueil**, cliquez sur **Accueil** pour retourner au mode Conception.  
  
2.  Cliquez sur **Exécuter**.  
  
3.  Dans la liste déroulante **Choisir une couleur**, sélectionnez la couleur des barres non blanches du rapport.  
  
4.  Cliquez sur **Afficher le rapport**.  
  
     Le rapport est généré et les lignes alternées sont de la couleur d'arrière-plan que vous avez choisie.  
  
##  <a name="DateFormat"></a> (facultatif) Formater la colonne de Date  
 Formatez la colonne **Last Purchase** qui contient des dates.  
  
#### <a name="to-format-date-column"></a>Pour formater la colonne de dates  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Cliquez avec le bouton droit sur la cellule de données pour la colonne **Last Purchase** et cliquez sur **Propriétés de la zone de texte**.  
  
3.  Dans la boîte de dialogue **Propriétés de la zone de texte**, cliquez sur **Nombre**, cliquez sur **Date**, puis sur le type **\*1/31/2000**.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Title"></a> (facultatif) Ajouter un titre de rapport  
 Ajoutez un titre au rapport.  
  
#### <a name="to-add-a-report-title"></a>Pour ajouter un titre de rapport  
  
1.  Dans l'aire de conception, cliquez sur **Cliquez pour ajouter un titre**.  
  
2.  Tapez **Synthèse de la comparaison des ventes**, puis cliquez à l’extérieur de la zone de texte.  
  
3.  Cliquez avec le bouton droit sur la zone de texte qui contient **Synthèse de la comparaison des ventes**, puis cliquez sur **Propriétés de la zone de texte**.  
  
4.  Dans la boîte de dialogue **Propriétés de la zone de texte**, cliquez sur **Police**.  
  
5.  Dans la liste **Taille**, sélectionnez **18pt**.  
  
6.  Dans la liste **Couleur**, sélectionnez **Gris**.  
  
7.  Sélectionnez **Gras** et **Italique**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Save"></a> (facultatif) Enregistrer le rapport  
 Vous pouvez enregistrer les rapports sur un serveur de rapports, dans une bibliothèque SharePoint ou sur l'ordinateur. Pour plus d’informations, consultez [Enregistrement des rapports &#40;Générateur de rapports&#41;](report-builder/saving-reports-report-builder.md).  
  
 Dans ce didacticiel, enregistrez le rapport sur un serveur de rapports. Si vous n'avez pas accès à un serveur de rapports, enregistrez le rapport sur votre ordinateur.  
  
#### <a name="to-save-the-report-to-a-report-server"></a>Pour enregistrer le rapport sur un serveur de rapports  
  
1.  À partir du bouton **Générateur de rapports** , cliquez sur **Enregistrer sous**.  
  
2.  Cliquez sur **Sites et serveurs récents**.  
  
3.  Sélectionnez ou tapez le nom du serveur de rapports sur lequel vous êtes autorisé à enregistrer des rapports.  
  
     Le message « Connexion au serveur de rapports » s'affiche. Une fois la connexion établie, le contenu du dossier de rapports spécifié par l’administrateur du serveur de rapports s’affiche comme emplacement par défaut des rapports.  
  
4.  Dans **Nom**, remplacez le nom par défaut par **Synthèse de la comparaison des ventes**.  
  
5.  Cliquez sur **Enregistrer**.  
  
 Le rapport est enregistré sur le serveur de rapports. Le nom du serveur de rapports auquel vous êtes connecté est indiqué dans la barre d'état située au bas de la fenêtre.  
  
#### <a name="to-save-the-report-to-your-computer"></a>Pour enregistrer le rapport sur votre ordinateur  
  
1.  À partir du bouton **Générateur de rapports** , cliquez sur **Enregistrer sous**.  
  
2.  Cliquez sur **Desktop`, `Mes Documents**, ou **mon ordinateur**, puis accédez au dossier où vous souhaitez enregistrer le rapport.  
  
3.  Dans **Nom**, remplacez le nom par défaut par **Synthèse de la comparaison des ventes**.  
  
4.  Cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Indicateurs &#40;Générateur de rapports et SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md)   
 [Images, zones de texte, rectangles et lignes &#40;Générateur de rapports et SSRS&#41;](report-design/rectangles-and-lines-report-builder-and-ssrs.md)   
 [Tables &#40;Générateur de rapports et SSRS&#41;](report-design/tables-report-builder-and-ssrs.md)   
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-data/report-datasets-ssrs.md)  
  
  
