---
title: 'Didacticiel : création d’un rapport au format libre (Générateur de rapports) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 87288b59-faf2-4b1d-a8e4-a7582baedf2f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 332c67f47c8096cbeb5a94c4e2a288cd532038cf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66098949"
---
# <a name="tutorial-creating-a-free-form-report-report-builder"></a>Didacticiel : création d'un rapport au format libre (Générateur de rapports)
  Ce didacticiel vous apprend à créer un rapport de forme libre SSRS qui ressemble à une lettre type. Vous pouvez organiser les éléments du rapport pour créer un formulaire avec des zones de texte, des images et autres régions de données.  
  
 Le rapport que vous créez dans ce didacticiel est basé sur des exemples de données de vente incluses dans le didacticiel. Le rapport regroupe les informations par secteur de vente et affiche le nom du directeur des ventes pour le secteur, ainsi que des informations détaillées et de synthèse sur les ventes. Vous allez utiliser la région de données de liste comme base du rapport de forme libre, puis ajouterez un panneau décoratif avec une image, du texte statique avec des données insérées, un tableau pour afficher les informations détaillées, et éventuellement, un graphique à secteurs et un histogramme pour afficher les informations de synthèse.  
  
##  <a name="BackToTop"></a>Ce que vous allez apprendre  
 Ce didacticiel vous apprendra à effectuer les opérations suivantes :  
  
-   [Créer un rapport, une source de données et un dataset vides](#BlankReport)  
  
-   [Ajouter et configurer une liste](#List)  
  
-   [Ajouter des graphiques](#Graphics)  
  
-   [Ajouter du texte de forme libre](#Text)  
  
-   [Ajouter un tableau pour afficher les détails](#Table)  
  
-   [Mettre en forme les données](#Format)  
  
-   [Enregistrer le rapport](#Save)  
  
### <a name="other-optional-steps"></a>Autres étapes facultatives  
  
-   [Ajouter une ligne pour séparer les zones du rapport](#Line)  
  
-   [Ajouter la visualisation des données de synthèse](#Visualization)  
  
 Durée estimée pour effectuer le didacticiel : 20 minutes.  
  
## <a name="requirements"></a>Spécifications  
 Pour plus d’informations sur les spécifications, consultez [Éléments requis pour les didacticiels &#40;Générateur de rapports&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="BlankReport"></a>1. créer un rapport vide, une source de données et un jeu de données  
  
> [!NOTE]  
>  Dans ce didacticiel, la requête contient les valeurs de données, afin que le rapport n'ait pas besoin d'une source de données externe. L'utilisation de ce type de données internes est très utile à des fins pédagogiques, mais l'approche rend la requête longue. .  
  
#### <a name="to-create-a-blank-report"></a>Pour créer un rapport vierge  
  
1.  Cliquez sur **Démarrer**, pointez sur **Programmes**, sur **Générateur de rapports Microsoft SQL Server 2012**, puis cliquez sur **Générateur de rapports version**.  
  
    > [!NOTE]  
    >  La boîte de dialogue **Mise en route** s'affiche. Si elle ne s'affiche pas, à partir du bouton Générateur de rapports, cliquez sur **Nouveau**.  
  
2.  Dans le volet gauche de la boîte de dialogue **Mise en route** , assurez-vous que **Nouveau rapport** est sélectionné.  
  
3.  Dans le volet droit, cliquez sur **Rapport vierge**.  
  
#### <a name="to-create-a-new-data-source"></a>Pour créer une source de données  
  
1.  Dans le volet données du rapport, cliquez sur **nouveau**, puis sur **source de données**.  
  
2.  Dans la `Name` zone, tapez : **ListDataSource**  
  
3.  Cliquez sur **Utiliser une connexion incorporée dans mon rapport**.  
  
4.  Vérifiez que le type de connexion est Microsoft SQL Server, puis, dans la zone **Chaîne de connexion**, tapez **Data Source = \<nom_serveur>**  
  
     \<ServerName>, par exemple Rapport001, spécifie un ordinateur sur lequel une instance du SQL Server Moteur de base de données est installée. Dans la mesure où les données du rapport ne sont pas extraites d'une base de données SQL Server, vous n'avez pas besoin d'inclure le nom d'une base de données. La base de données par défaut sur le serveur spécifié est utilisée pour analyser la requête.  
  
5.  Cliquez sur **Informations d'identification**, puis entrez les informations d'identification requises pour se connecter à l'instance du moteur de base de données SQL Server.  
  
6.  Cliquez sur **OK**.  
  
#### <a name="to-create-a-new-dataset"></a>Création d’un jeu de données  
  
1.  Dans le volet données du rapport, cliquez sur **nouveau**, puis sur **DataSet**.  
  
2.  Dans la `Name` zone, tapez : **ListDataset.**  
  
3.  Cliquez sur **Utiliser un dataset incorporé dans mon rapport**, puis vérifiez que la source de données est **ListDataSource**.  
  
4.  Vérifiez que le type de requête **Texte** est sélectionné, puis cliquez sur **Concepteur de requêtes**.  
  
5.  Cliquez sur **Modifier en tant que texte**.  
  
6.  Copiez et collez la requête suivante dans le volet de requête :  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity  
    ```  
  
7.  Cliquez sur l'icône Exécuter pour exécuter la requête.  
  
     Les résultats de la requête sont les données qui peuvent être affichées dans votre rapport.  
  
     ![Concepteur de requêtes](../../2014/tutorials/media/tutorial-querydesigner.png "Concepteur de requêtes")  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="List"></a>2. Ajouter et configurer une liste  
 
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fournit trois modèles de région de données : tableau, matrice et liste. Ces modèles sont tous basés sur une région de données de tableau matriciel.  
  
 Dans ce didacticiel, vous allez utiliser une liste pour afficher les informations de ventes pour les secteurs de vente dans un rapport ayant l'apparence d'un bulletin d'informations. Les informations sont regroupées par secteur. Vous allez ajouter un nouveau groupe de lignes qui regroupe les données par secteur, puis vous supprimerez le groupe de lignes Détails intégré. Le modèle de liste est idéal pour la création de rapports de forme libre. Pour plus d’informations, consultez la page [répertorie &#40;générateur de rapports et les&#41;SSRS ](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Ce rapport utilise le format de papier Letter (8,5 X 11) et des marges de 1 pouce. Une page de rapport de plus de 9 pouces de haut ou de plus de 6,5 pouces de large peut générer des pages vierges.  
  
#### <a name="to-add-a-list"></a>Pour ajouter une liste  
  
1.  Sous l'onglet **Insertion** du ruban, dans la zone **Régions de données** , cliquez sur **Liste** , puis faites glisser la liste dans le corps du rapport. Définissez la taille de la liste sur 7 pouces de haut et 6,25 pouces de large.  
  
2.  Cliquez dans la liste, cliquez avec le bouton droit en haut de la liste, puis cliquez sur **Propriétés du tableau matriciel**.  
  
     ![Ajout de liste](../../2014/tutorials/media/tutorial-addinglistwithnumbers.png "Ajout de liste")  
  
3.  Dans la liste déroulante **Nom du dataset** , sélectionnez **ListDataset**.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  Cliquez avec le bouton droit dans la liste, puis cliquez sur **Propriétés du rectangle**.  
  
     ![Commande des propriétés de rectangle](../../2014/tutorials/media/tutorial-rectanglepropertiescommand.png "Commande des propriétés de rectangle")  
  
6.  Sous l'onglet **Général** , activez la case à cocher **Insérer un saut de page après** .  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-add-a-new-row-group-and-to-delete-the-details-group"></a>Pour ajouter un nouveau groupe de lignes et supprimer le groupe Détails  
  
1.  Dans le volet Groupes de lignes, cliquez avec le bouton droit sur le groupe Détails, pointez sur **Ajouter un groupe**, puis cliquez sur **Groupe parent**.  
  
     ![Commande du groupe parent](../../2014/tutorials/media/tutorial-parentgroupcommand.png "Commande du groupe parent")  
  
2.  Dans la liste déroulante, sélectionnez `[Territory].`  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Une colonne est ajoutée à la liste. La colonne contient la cellule `[Territory].`.  
  
4.  Cliquez avec le bouton droit sur la colonne Territory dans la liste, puis cliquez sur **Supprimer les colonnes**.  
  
     ![Supprimer les colonnes](../../2014/tutorials/media/tutorial-deletecolumnscommand.png "Supprimer les colonnes")  
  
5.  Sélectionnez **Supprimer les colonnes uniquement**.  
  
     ![Boîte de dialogue Supprimer les colonnes](../../2014/tutorials/media/tutorial-deletecolumnsdialog.png "boîte de dialogue Supprimer les colonnes")  
  
6.  Dans le volet Groupes de lignes, cliquez avec le bouton droit sur le groupe **Détails** , puis cliquez sur **Supprimer le groupe**.  
  
     ![Supprimer le groupe des détails](../../2014/tutorials/media/tutorial-deletedetailsgroup.png "Supprimer le groupe des détails")  
  
7.  Cliquez sur **supprimer le groupe uniquement**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Graphics"></a>3. ajouter des graphiques  
 L'un des avantages de l'utilisation d'une région de données de liste est que vous pouvez ajouter des éléments de rapport comme des rectangles et des zones de texte n'importe où, sans être limité par une disposition tabulaire. Vous allez améliorer l'apparence du rapport en ajoutant un graphique (un rectangle rempli avec une couleur).  
  
#### <a name="to-add-graphic-elements-to-the-report"></a>Pour ajouter des éléments graphiques au rapport  
  
1.  Sous l’onglet **Insérer** du ruban, cliquez sur **rectangle**, puis faites glisser un rectangle dans l’angle supérieur gauche de la liste. Définissez la taille du rectangle sur 7 pouces de haut et 1 pouce de large.  
  
2.  Cliquez avec le bouton droit sur le rectangle, puis cliquez sur **Propriétés du rectangle**.  
  
3.  Cliquez sur l'onglet **Remplissage** .  
  
4.  Dans la liste déroulante **Couleur de remplissage** , cliquez sur **Couleurs supplémentaires**, puis sélectionnez la couleur **Gris foncé** .  
  
     ![Sélectionner la couleur de remplissage](../../2014/tutorials/media/tutorial-selectfillcolorwithnumbers.png "Sélectionner la couleur de remplissage")  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Le côté gauche du rapport a maintenant un graphique vertical formé d'un rectangle gris foncé.  
  
##  <a name="Text"></a>4. Ajouter un texte de forme libre  
 Une zone de texte contient du texte statique qui est répété sur chaque page de rapport, ainsi que des champs de données.  
  
#### <a name="to-add-text-to-the-report"></a>Pour ajouter du texte au rapport  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Sous l'onglet **Insertion** du ruban, cliquez sur **Zone de texte**, puis faites glisser une zone de texte en haut à gauche de la liste, à l'intérieur du rectangle que vous avez ajouté précédemment. Définissez la taille de la zone de texte sur environ 3 pouces de haut et 5 pouces de large.  
  
3.  Placez le curseur dans la partie supérieure de la zone de texte, puis tapez **Bulletin d'informations pour** .  
  
     ![Ajouter un texte de titre au bulletin d'informations](../../2014/tutorials/media/tutorial-newsletterfor.png "Ajouter un texte de titre au bulletin d'informations")  
  
    > [!NOTE]  
    >  Veillez à inclure l'espace supplémentaire après « pour ». Cet espace sépare le texte du champ que vous allez ajouter à l'étape suivante.  
  
4.  Faites glisser le champ Territory vers la zone de texte et placez-le après le texte que vous avez tapé à l'étape 3.  
  
     ![Ajouter le champ du secteur de vente](../../2014/tutorials/media/tutorial-addterritorialfield.png "Ajouter le champ du secteur de vente")  
  
5.  Sélectionnez tout le texte, cliquez avec le bouton droit, puis cliquez sur **Propriétés du texte**.  
  
6.  Cliquez sur l'onglet **Police** .  
  
7.  Dans la liste **Police** , sélectionnez **Times New Roman**; dans **Taille** , sélectionnez **20 pt**; dans **Couleur** , sélectionnez **Rouge**.  
  
     ![Propriétés du texte](../../2014/tutorials/media/tutorial-textpropertieswithnumbers.png "Propriétés du texte")  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. Placez le curseur sous le texte que vous avez tapé à l'étape 3 et tapez **Bonjour** .  
  
    > [!NOTE]  
    >  Veillez à inclure l'espace supplémentaire après « Bonjour ». Cet espace sépare le texte du champ que vous allez ajouter à l'étape suivante.  
  
10. Faites glisser le champ FullName vers la zone de texte et placez-le après le texte que vous avez tapé à l'étape 9, puis tape une virgule (,).  
  
     ![Ajouter le champ du nom complet](../../2014/tutorials/media/tutorial-addfullnamefield.png "Ajouter le champ du nom complet")  
  
11. Sélectionnez le texte que vous avez ajouté aux étapes 9 et 10, cliquez avec le bouton droit, puis cliquez sur **Propriétés du texte**.  
  
12. Cliquez sur l'onglet **Police** .  
  
13. Dans la liste **Police** , sélectionnez **Times New Roman**; dans **Taille** , sélectionnez **16 pt**; dans **Couleur** , sélectionnez **Noir** .  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
15. Placez le curseur sous le texte que vous avez ajouté aux étapes 9 à 13, puis copiez et collez le texte grec suivant :  
  
    ```  
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin sed dolor in ipsum pulvinar egestas. Sed sed lacus at leo ornare ultricies. Vivamus velit risus, euismod nec sodales gravida, gravida in dui. Etiam ullamcorper elit vitae justo fermentum ut ullamcorper augue sodales. Ut placerat, nisl quis feugiat adipiscing, nibh est aliquet est, mollis faucibus mauris lectus quis arcu. In mollis tincidunt lacinia. In vitae erat ut lorem tincidunt luctus. Curabitur et magna nunc, sit amet adipiscing nisi. Nulla rhoncus elementum orci nec tincidunt. Aliquam imperdiet cursus erat vel tincidunt. Donec et neque ac urna rutrum sodales. In id purus et nisl dignissim dapibus. Sed rhoncus metus at felis feugiat eu tempor dolor vehicula. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam faucibus consectetur diam eu pellentesque.   
    Nulla facilisi. Proin ligula enim, porta ut tincidunt id, adipiscing sit amet eros. Ut purus sem, bibendum et vulputate sit amet, facilisis eget magna. Sed aliquam erat non erat eleifend hendrerit. Ut a ligula est, sit amet eleifend enim. Ut et nisl enim, sit amet adipiscing augue. Vivamus eu arcu ac libero posuere elementum. Integer condimentum bibendum venenatis. Integer odio tellus, feugiat in pellentesque semper, interdum nec sem. Sed cursus euismod sem, ut elementum sapien placerat vel.   
    ```  
  
16. Sélectionnez le texte que vous avez ajouté à l'étape 15, cliquez avec le bouton droit, puis cliquez sur **Propriétés du texte**.  
  
17. Cliquez sur l'onglet **Police** .  
  
18. Dans la liste **Police** , sélectionnez **Arial**; dans **Taille** , sélectionnez **10 pt**; dans **Couleur** , sélectionnez **Noir**.  
  
19. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     ![Ajouter le texte du bulletin d'informations](../../2014/tutorials/media/tutorial-newslettertext.png "Ajouter le texte du bulletin d'informations")  
  
20. Placez le curseur sous le texte que vous avez collé à étape 15, puis tapez **Félicitations pour le total de vos ventes,** .  
  
    > [!NOTE]  
    >  Veillez à inclure l'espace supplémentaire après la virgule. Cet espace sépare le texte du champ que vous allez ajouter à l'étape suivante.  
  
21. Faites glisser le champ Ventes vers la zone de texte, placez-le après le texte que vous avez tapé à l'étape 20, puis tapez un point d'exclamation (!).  
  
22. Mettez en surbrillance le champ Sales, cliquez avec le bouton droit sur le champ, puis cliquez sur **expression**.  
  
23. Dans la zone d'expression, modifiez l'expression pour inclure la fonction Sum comme suit :  
  
    ```  
    =Sum(Fields!Sales.value)  
    ```  
  
24. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     ![Ajouter une expression au champ des ventes](../../2014/tutorials/media/tutorial-addexpressiontosalesfield.png "Ajouter une expression au champ des ventes")  
  
25. Sélectionnez le texte que vous avez ajouté aux étapes 20 à 23, cliquez avec le bouton droit, puis cliquez sur **Propriétés du texte**.  
  
26. Cliquez sur l'onglet **Police** .  
  
27. Dans la liste **Police** , sélectionnez **Times New Roman**; dans **Taille** , sélectionnez **16 pt**; dans **Couleur** , sélectionnez **Rouge**.  
  
28. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
29. Sélectionnez `[Sum(Sales)]` , puis sous l'onglet **Accueil** , dans le groupe **Nombre** , cliquez sur le bouton **Devise** .  
  
     ![Ajouter un symbole monétaire](../../2014/tutorials/media/tutorial-addcurrencysymbol.png "Ajouter un symbole monétaire")  
  
30. Cliquez avec le bouton droit sur la zone de texte contenant le texte « Cliquez pour ajouter un titre », puis cliquez sur **Supprimer**.  
  
31. Sélectionnez la zone de liste et à l'aide des touches de direction, déplacez-la vers le haut de la page.  
  
32. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Le rapport affiche le texte statique et chaque page du rapport inclut des données relatives à un secteur de vente. Les ventes sont mises en forme en tant que valeurs monétaires.  
  
 ![Aperçu du bulletin d'informations](../../2014/tutorials/media/tutorial-newsletters.png "Aperçu du bulletin d'informations")  
  
##  <a name="Table"></a>5. Ajouter une table pour afficher les détails des ventes  
 Utilisez l'Assistant Nouveau tableau ou nouvelle matrice pour ajouter un tableau au rapport de forme libre. Après avoir terminé l'Assistant, vous ajouterez manuellement une ligne pour les totaux.  
  
#### <a name="to-add-a-table"></a>Pour ajouter un tableau  
  
1.  Sous l'onglet **Insertion** du ruban, dans la zone **Régions de données** , cliquez sur **Tableau**, puis sur **Assistant Tableau**.  
  
2.  Dans la page Choisir un dataset, cliquez sur **ListDataset**.  
  
3.  Cliquez sur **Suivant**.  
  
4.  Dans la page **Organiser les champs** , faites glisser le champ Product de **Champs disponibles** vers **Valeurs**.  
  
5.  Répétez l'étape 4 pour SalesDate, Quantity et Sales. Placez SalesDate sous Product, Quantity sous SalesDate et Sales sous SalesDate.  
  
6.  Cliquez sur **Suivant**.  
  
7.  Dans la page **Choisir la disposition** , observez la mise en page de la table.  
  
     Le tableau est très simple. Il comporte cinq colonnes et aucun groupe de lignes ni de colonnes. Dans la mesure où il ne comporte aucun groupe, les options de mise en page relatives aux groupes ne sont pas disponibles. Vous mettrez manuellement à jour le tableau ultérieurement de manière à inclure un total.  
  
8.  Cliquez sur **Suivant**.  
  
9. Dans la page **Choisir un style** , dans le volet **Styles** , sélectionnez **Ardoise**.  
  
10. Cliquez sur **Terminer**.  
  
11. Faites glisser le tableau sous la zone de texte que vous avez ajoutée dans la leçon 4.  
  
    > [!NOTE]  
    >  Assurez-vous que le tableau est à l'intérieur de la liste.  
  
12. Vérifiez que la table est sélectionnée, puis, dans le volet Groupe de lignes, cliquez avec le bouton droit sur Détails, pointez sur **Ajouter un total**, puis cliquez sur **Après**.  
  
     ![Ajouter le total du rapport](../../2014/tutorials/media/tutorial-addtotal.png "Ajouter le total du rapport")  
  
13. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Le rapport affiche un tableau avec les détails des ventes et les totaux.  
  
 ![Total des ventes dans le rapport](../../2014/tutorials/media/tutorial-reportsalestotals.png "Total des ventes dans le rapport")  
  
##  <a name="Format"></a>6. mettre en forme les données  
 Mettez en forme les données numériques sous forme de valeurs monétaires et les dates sous forme de jour et heure.  
  
#### <a name="to-format-fields-table"></a>Pour mettre en forme les champs du tableau  
  
1.  Cliquez sur **conception** pour basculer en mode conception.  
  
2.  Cliquez sur les cellules du tableau qui contiennent `[Sum(SalesSales)]` et sous l'onglet **Accueil** , dans le groupe **Nombre** , cliquez sur le bouton **Devise** .  
  
     ![Ajouter un symbole monétaire à la somme des ventes](../../2014/tutorials/media/tutorial-sumsales-currencysymbol.png "Ajouter un symbole monétaire à la somme des ventes")  
  
3.  Cliquez sur la cellule qui contient `[SalesDate]` et dans le groupe **Nombre** , dans la liste déroulante, sélectionnez **Date**.  
  
4.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Le rapport affiche maintenant les données mises en forme et est plus facile à lire.  
  
 ![Mettre en forme le total des ventes dans le rapport](../../2014/tutorials/media/tutorial-reportsalestotals-formatted.png "Mettre en forme le total des ventes dans le rapport")  
  
##  <a name="Save"></a>7. enregistrer le rapport  
 Vous pouvez enregistrer les rapports sur un serveur de rapports, dans une bibliothèque SharePoint ou sur l'ordinateur. Vous pouvez également exporter le rapport dans de nombreux formats tels que Word et PDF ; pour ce faire, exécutez le rapport, puis sélectionnez le format dans le menu **Exporter** .  
  
 Dans ce didacticiel, enregistrez le rapport sur un serveur de rapports. Si vous n'avez pas accès à un serveur de rapports, enregistrez le rapport sur votre ordinateur.  
  
#### <a name="to-save-the-report-on-a-report-server"></a>Pour enregistrer le rapport sur un serveur de rapports  
  
1.  À partir du bouton **Générateur de rapports** , cliquez sur **Enregistrer sous**.  
  
2.  Cliquez sur **Sites et serveurs récents**.  
  
3.  Sélectionnez ou tapez le nom du serveur de rapports sur lequel vous êtes autorisé à enregistrer des rapports.  
  
     Le message « Connexion au serveur de rapports » s'affiche. Une fois la connexion établie, le contenu du dossier de rapports spécifié par l'administrateur du serveur de rapports s'affiche comme emplacement par défaut des rapports.  
  
4.  Dans `Name`, remplacez le nom par défaut par **SalesInformationByTerritory**.  
  
5.  Cliquez sur **Enregistrer**.  
  
 Le rapport est enregistré sur le serveur de rapports. Le nom du serveur de rapports auquel vous êtes connecté est indiqué dans la barre d'état située au bas de la fenêtre.  
  
#### <a name="to-save-the-report-on-your-computer"></a>Pour enregistrer le rapport sur votre ordinateur  
  
1.  À partir du bouton **Générateur de rapports** , cliquez sur **Enregistrer sous**.  
  
2.  Cliquez sur **Bureau**, **Mes documents**ou **Poste de travail**, puis naviguez jusqu'au dossier où vous souhaitez enregistrer le rapport.  
  
3.  Dans `Name`, remplacez le nom par défaut par **SalesInformationByTerritory**.  
  
4.  Cliquez sur **Enregistrer**.  
  
##  <a name="Line"></a>8. (facultatif) ajouter une ligne pour séparer les zones du rapport  
 Ajoutez une ligne pour séparer la zone éditoriale de la zone de détails dans le rapport.  
  
#### <a name="to-add-a-line"></a>Pour ajouter une ligne  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Sous l'onglet **Insertion** du ruban, dans la zone **Éléments de rapport** , cliquez sur **Ligne**.  
  
3.  Dessinez une ligne sous la zone de texte de forme libre que vous avez ajoutée dans la leçon 4.  
  
4.  Cliquez sur la ligne.  
  
5.  Cliquez sur l'onglet **Accueil** .  
  
6.  Dans la zone **Bordure** , sélectionnez une largeur de **4 1/2** points et la couleur **Rouge**.  
  
     ![Ajouter une ligne au rapport](../../2014/tutorials/media/tutorial-reportwithline.png "Ajouter une ligne au rapport")  
  
##  <a name="Visualization"></a>9. (facultatif) ajouter la visualisation des données de synthèse  
 Les rectangles vous aident à contrôler le rendu du rapport. Placez un graphique à secteurs et un histogramme à l'intérieur d'un rectangle pour vérifier que le rendu du rapport est conforme à vos attentes  
  
#### <a name="to-add-a-rectangle"></a>Pour ajouter un rectangle  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Sous l'onglet **Insertion** du ruban, dans la zone **Éléments de rapport** , cliquez sur **Rectangle**, puis fait glisser le rectangle à l'intérieur de la liste, à droite du tableau. Définissez la taille du rectangle sur 2 pouces de large et 4 pouces de haut.  
  
3.  Alignez le haut du rectangle et le haut du tableau.  
  
#### <a name="to-add-a-pie-chart"></a>Pour ajouter un graphique à secteurs  
  
1.  Sous l'onglet **Insertion** du ruban, dans la zone **Visualisations des données** , cliquez sur **Graphique** , puis sur **Assistant Graphique**.  
  
2.  Dans la page Choisir un dataset, cliquez sur **ListDataset**, puis sur **Suivant**.  
  
3.  Cliquez sur **Secteurs**, puis sur **Suivant**.  
  
4.  Sur la page Organiser les champs du graphique, faites glisser Product vers **Catégories**.  
  
5.  Faites glisser Quantity vers **valeurs**, puis cliquez sur **suivant**.  
  
6.  Dans la page **Choisir un style** , dans le volet **Styles** , sélectionnez **Ardoise**.  
  
7.  Cliquez sur **Terminer**.  
  
8.  Redimensionnez le graphique qui s'affiche dans le coin supérieur gauche du rapport afin qu'il fasse 1,5 pouce de haut et 2 pouces de large.  
  
9. Faites glisser le graphique à l'intérieur du rectangle.  
  
     ![Ajouter un graphique en secteurs](../../2014/tutorials/media/tutorial-addpiechart.png "Ajouter un graphique en secteurs")  
  
10. Cliquez avec le bouton droit sur le titre du graphique, puis cliquez sur **Propriétés du titre**.  
  
11. Dans la boîte de dialogue **Propriétés du titre du graphique** , dans le texte du titre, tapez **Quantités de produits vendues**.  
  
12. Cliquez sur l'onglet **Police** , puis dans la liste **Taille** , cliquez sur **10pt**.  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-add-a-column-chart"></a>Pour ajouter un histogramme  
  
1.  Sous l'onglet **Insertion** du ruban, dans la zone **Visualisations des données** , cliquez sur **Graphique** , puis sur **Assistant Graphique**.  
  
2.  Dans la page **choisir un DataSet** , cliquez sur **ListDataset**, puis sur **suivant**.  
  
3.  Cliquez sur **Colonne**, puis sur **Suivant**.  
  
4.  Dans la page organiser les champs du graphique, faites glisser le champ produit vers **catégories**.  
  
5.  Faites glisser Sales vers **Valeurs** , puis cliquez sur **Suivant**.  
  
     Les valeurs s'affichent sur l'axe vertical.  
  
6.  Dans la page **Choisir un style** , dans le volet **Styles** , sélectionnez **Ardoise**.  
  
7.  Cliquez sur **Terminer**.  
  
     Un histogramme est ajouté dans le coin supérieur gauche du rapport.  
  
8.  Redimensionnez le graphique de sorte qu'il fasse 2 pouces de large sur 2 pouces de haut.  
  
9. Faites glisser le graphique à l'intérieur du rectangle, sous le graphique à secteurs.  
  
     ![Ajouter un histogramme](../../2014/tutorials/media/tutorial-addcolumnchart.png "Ajouter un histogramme")  
  
10. Cliquez avec le bouton droit sur le titre du graphique, puis cliquez sur **Propriétés du titre**.  
  
11. Dans la boîte de dialogue **Propriétés du titre du graphique** , dans le texte du titre, tapez **Ventes de produits**.  
  
12. Cliquez sur l'onglet **Police** , puis dans la liste **Taille** , cliquez sur **10pt**, puis sur **OK**.  
  
13. Dans l'histogramme, cliquez avec le bouton droit sur l'axe vertical, puis désélectionnez **Afficher le titre de l'axe**.  
  
14. Répétez l'étape 13 pour l'axe horizontal.  
  
15. Cliquez avec le bouton droit sur la légende, puis cliquez sur **Supprimer la légende**.  
  
    > [!NOTE]  
    >  Le fait de supprimer le titre des axes et la légende rend un petit graphique plus lisible.  
  
 ![Changer les titres des graphiques et supprimer le titre de l'axe](../../2014/tutorials/media/tutorial-columnchart-newtitle-noaxistitle.png "Changer les titres des graphiques et supprimer le titre de l'axe")  
  
#### <a name="to-verify-the-charts-are-inside-the-rectangle"></a>Pour vérifier que les graphiques sont à l'intérieur du rectangle  
  
1.  Cliquez sur le rectangle que vous avez ajouté précédemment dans cette leçon.  
  
     Dans le volet Propriétés, la propriété `Name` affiche le nom du rectangle.  
  
     ![Nom du rectangle](../../2014/tutorials/media/tutorial-rectanglename.png "Nom du rectangle")  
  
2.  Cliquez sur le graphique à secteurs.  
  
3.  Dans le volet **Propriétés** , vérifiez que la `Parent` propriété contient le nom du rectangle.  
  
     ![Propriété parente du graphique en secteurs](../../2014/tutorials/media/tutorial-piechart-parentproperty.png "Propriété parente du graphique en secteurs")  
  
4.  Cliquez sur l'histogramme et répétez les étapes 2 et 3.  
  
    > [!NOTE]  
    >  Si les graphiques ne sont pas à l'intérieur du rectangle, le rapport rendu n'affiche pas les graphiques ensemble.  
  
#### <a name="to-make-the-charts-the-same-size"></a>Pour donner la même taille aux graphiques  
  
1.  Cliquez sur le graphique à secteurs, appuyez sur la touche Ctrl, puis cliquez sur l'histogramme.  
  
2.  Les deux graphiques étant sélectionnés, cliquez avec le bouton droit, pointez sur **Disposition**, puis cliquez sur **Uniformiser la largeur**.  
  
     ![Uniformiser les largeurs des graphiques](../../2014/tutorials/media/tutorial-makechartssamewidth.png "Uniformiser les largeurs des graphiques")  
  
    > [!NOTE]  
    >  L'élément sur lequel vous cliquez en premier détermine la largeur de tous les éléments sélectionnés.  
  
3.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Le rapport affiche maintenant les données de synthèse des ventes dans un graphique à secteurs et un histogramme.  
  
 ![Didacticiel SSRS, rapport au format libre](../../2014/tutorials/media/tutorial-reportfinal.png "Didacticiel SSRS, rapport au format libre")  
  
## <a name="more-information"></a>Informations complémentaires  
 Pour plus d’informations sur les listes, consultez [tables, matrices et listes &#40;générateur de rapports et ssrs&#41;](report-design/tables-matrices-and-lists-report-builder-and-ssrs.md), [répertorie les &#40;Générateur de rapports et SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md), les zones de région de données de tableau [matriciel &#40;générateur de rapports et SSRS&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md), ainsi que les [cellules, lignes et colonnes de région de données de tableau matriciel &#40;générateur de rapports&#41; et SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).  
  
 Pour plus d’informations sur les concepteurs de requêtes, consultez [Concepteurs de requêtes &#40;Générateur de rapports&#41;](../../2014/reporting-services/query-designers-report-builder.md) et [Interface utilisateur du concepteur de requêtes textuel &#40;Générateur de rapports&#41;](report-data/text-based-query-designer-user-interface-report-builder.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels &#40;Générateur de rapports&#41;](report-builder-tutorials.md)   
 [Générateur de rapports dans SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
