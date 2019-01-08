---
title: 'Didacticiel : Rapport cartographique (Générateur de rapports) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 8d831356-7efa-40cc-ae95-383b3eecf833
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 43135554b1340b92f4801a0f08e002142b443981
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53359861"
---
# <a name="tutorial-map-report-report-builder"></a>Didacticiel : Rapport cartographique (Générateur de rapports)
  Ce didacticiel est conçu pour vous aider à découvrir les fonctionnalités cartographiques que vous pouvez utiliser pour afficher des données de rapport sur un arrière-plan géographique.  
  
 Les cartes sont basées sur des données spatiales qui comportent en général des points, des lignes et des polygones. Par exemple, un polygone peut représenter le contour d'un comté, une ligne peut représenter une route, et un point peut représenter l'emplacement d'une ville. Chaque type de données spatiales est affiché sur une couche séparée sous la forme d'un jeu d'éléments cartographiques.  
  
 Pour faire varier l'apparence des éléments cartographiques, vous devez spécifier un champ dont les valeurs font correspondre les éléments cartographiques aux données analytiques d'un dataset. Vous pouvez également définir des règles qui font varier la couleur, la taille ou d'autres propriétés en fonction des plages de données.  
  
 Dans ce didacticiel, vous allez créer un rapport cartographique qui affiche les emplacements des magasins dans les comtés de l'État de New York.  
  
##  <a name="BackToTop"></a> Ce que vous allez apprendre  
 Dans ce didacticiel, vous apprendrez à effectuer les tâches suivantes :  
  
1.  [Créer une carte avec une couche de polygones à partir de l’Assistant carte](#Map)  
  
2.  [Ajouter une couche de points pour les emplacements de Store de l’affichage](#PointLayer)  
  
3.  [Ajouter une couche de lignes pour afficher un itinéraire](#LineLayer)  
  
4.  [Ajouter un arrière-plan de mosaïques Bing Maps](#TileLayer)  
  
5.  [Rendre une couche transparente](#Transparent)  
  
6.  [Faites varier la couleur du comté selon les ventes](#Vary)  
  
    1.  [Créer une relation entre les données spatiales et analytiques](#Relationship)  
  
    2.  [Spécifier des règles de couleur pour les polygones](#ColorRules)  
  
    3.  [Mettre en forme les données dans l’échelle de couleurs en tant que devises](#ColorScale)  
  
    4.  [Créer une légende](#NewLegend)  
  
    5.  [Associer une légende et des règles de couleur](#Associate)  
  
    6.  [Supprimer la couleur des comtés sans données](#NoData)  
  
7.  [Ajouter un Point personnalisé](#CustomPoint)  
  
8.  [Centrer la vue cartographique](#CenterView)  
  
9. [Ajouter un titre de rapport](#Title)  
  
10. [Enregistrer le rapport](#Save)  
  
> [!NOTE]  
>  Dans ce didacticiel, les étapes de l'Assistant sont consolidées sous forme de deux procédures : l'une pour créer le dataset, et l'autre pour créer une table. Pour obtenir des instructions détaillées sur l’accès à un serveur de rapports, choisissez une source de données, créer un jeu de données et exécuter l’Assistant, consultez le premier didacticiel de cette série : [Didacticiel : Création d’un rapport de tableau de base &#40;Générateur de rapports&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Durée estimée pour effectuer ce didacticiel : 30 minutes  
  
## <a name="requirements"></a>Configuration requise  
 Pour plus d’informations sur les spécifications, consultez [Éléments requis pour les didacticiels &#40;Générateur de rapports&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="Map"></a> 1. Créer une carte avec une couche de polygones à partir de l'Assistant Carte  
 Ajoutez une carte à votre rapport à partir de la bibliothèque de cartes. La carte a une couche qui affiche les comtés de l'État de New York. La forme de chaque comté est un polygone basé sur les données spatiales incorporées dans la carte de la bibliothèque de cartes.  
  
#### <a name="to-add-a-map-with-the-map-wizard-in-a-new-report"></a>Pour ajouter une carte dans un nouveau rapport à l'aide de l'Assistant Carte  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **le Générateur de rapports**, puis cliquez sur **le Générateur de rapports**.  
  
     La boîte de dialogue Mise en route s'affiche.  
  
    > [!NOTE]  
    >  Si la boîte de dialogue Mise en route ne s'affiche pas, à partir du bouton Générateur de rapports, cliquez sur **Nouveau**.  
  
2.  Dans le volet gauche, assurez-vous que **Rapport** est sélectionné.  
  
3.  Dans le volet droit, cliquez sur **Assistant Carte**.  
  
4.  Cliquez sur **Créer**.  
  
5.  Dans la page**Choisir une source de données spatiales** , assurez-vous que l'option **Bibliothèque de cartes** est sélectionnée.  
  
6.  Dans le volet Bibliothèque de cartes, développez **States by County** sous **USA**, puis cliquez sur **New York**.  
  
     Le volet Aperçu de la carte affiche la carte des comtés de New York.  
  
7.  Cliquer sur **Suivant**.  
  
8.  Dans la page **Choisir des options de vue cartographique et de données spatiales** , acceptez les valeurs par défaut. Par défaut, les éléments cartographiques d'une bibliothèque de cartes sont incorporés automatiquement dans la définition de rapport.  
  
9. Cliquer sur **Suivant**.  
  
10. Dans la page **Choisir la visualisation de la carte** , vérifiez que l'option **Carte simple** est sélectionnée et cliquez sur **Suivant**.  
  
11. Dans la page **Choisir le thème de couleurs et la visualisation des données** , sélectionnez l'option **Afficher les étiquettes** .  
  
12. Si elle est activée, désactivez l'option **Carte unicolore** .  
  
13. Dans la liste déroulante **Champ de données** , cliquez sur #COUNTYNAME. Le volet Aperçu de la carte de l'Assistant affiche les éléments suivants :  
  
    -   un titre avec le texte **Titre de la carte**;  
  
    -   une carte qui affiche les comtés de l'État de New York, avec chaque comté dans une couleur différente et les noms des comtés affichés à un endroit quelconque sur la zone du comté ;  
  
    -   une légende contenant un titre et une liste d'éléments de 1 à 5 ;  
  
    -   une échelle de couleurs contenant les valeurs de 0 à 160 et la valeur Aucune couleur ;  
  
    -   une échelle des distances qui affiche les kilomètres (km) et les miles (mi).  
  
14. Cliquez sur **Terminer**.  
  
     La carte est ajoutée à l'aire de conception.  
  
15. Cliquez sur la carte pour la sélectionner et afficher le volet **Couches**. Le volet **Couches** affiche une couche de polygones du type de couche **Incorporé**. Chaque comté est un élément cartographique incorporé sur cette couche.  
  
    > [!NOTE]  
    >  Si vous ne voyez pas le volet **Couches** , celui-ci se trouve peut-être à l'extérieur de votre vue actuelle. Utilisez la barre de défilement au bas de la fenêtre du mode Conception pour changer votre vue. Sinon, sous l'onglet **Affichage** , désactivez l'option **Propriétés** ou **Données du rapport** pour disposer d'une plus grande surface d'exposition.  
  
16. Cliquez avec le bouton droit sur le titre de la carte, puis cliquez sur **Propriétés du titre**.  
  
17. Remplacez le texte du titre par **Ventes par magasin**.  
  
18. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
19. Affichez l'aperçu du rapport.  
  
 Le rapport rendu affiche le titre de la carte, la carte et l'échelle des distances. Les comtés sont sur une couche de polygones de la carte. Chaque comté est un polygone dont la couleur varie à partir d'une palette de couleurs, mais les couleurs ne sont pas associées à des données. L'échelle des distances affiche les distances en kilomètres et en miles.  
  
 La légende de la carte et l'échelle de couleurs n'apparaissent pas encore, car il n'y a pas de données analytiques associées à chaque comté. Vous ajouterez ultérieurement des données analytiques dans ce didacticiel.  
  
##  <a name="PointLayer"></a> 2. Ajouter une couche de points pour afficher des emplacements de magasins  
 Utilisez l'Assistant Couche pour ajouter une couche de points qui affiche les emplacements des magasins.  
  
> [!NOTE]  
>  Dans ce didacticiel, la requête contient les valeurs de données, afin qu'il ne soit pas nécessaire de disposer d'une source de données externe. Cela rend la requête assez longue. Dans un environnement métier, une requête ne contient pas les données. Ceci est nécessaire à des fins de formation uniquement.  
  
#### <a name="to-add-a-point-layer-based-on-a-sql-server-spatial-query"></a>Pour ajouter une couche de points basée sur une requête spatiale SQL Server  
  
1.  Basculez en mode Conception.  
  
2.  Double-cliquez sur la carte pour afficher le volet **Couches** . Dans la barre d’outils, cliquez sur le bouton **Assistant Nouvelle couche** ![rs_IconMapLayerWizard](../../2014/tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard").  
  
3.  Dans la page **Choisir une source de données spatiales** , sélectionnez **Requête spatiale SQL Server**et cliquez sur **Suivant**.  
  
4.  Dans la page **Choisir un dataset avec des données spatiales SQL Server** , cliquez sur **Ajouter un nouveau dataset avec des données spatiales SQL Server**, puis sur **Suivant**.  
  
5.  Dans la page **Choisir une connexion à une source de données spatiales SQL Server** , sélectionnez une source de données existante ou naviguez jusqu'au serveur de rapports, puis sélectionnez une source de données.  
  
6.  Cliquer sur **Suivant**.  
  
7.  Dans la page Créer une requête, cliquez sur **Modifier en tant que texte**.  
  
8.  Collez le texte ci-après dans le volet Requête :  
  
    ```  
    Select 114 as StoreKey, 'Contoso Albany Store' as StoreName, 1125 as SellingArea, 'Albany' as City, 'Albany' as County,   
     CAST(1000000 as money) as Sales, CAST('POINT(-73.7472924218681 42.6564617079878)' as geography) AS SpatialLocation  
    UNION ALL SELECT 115 AS StoreKey, 'Contoso New York No.1 Store' AS  StoreName, 500 as SellingArea, 'New York' AS City, 'New York City' as County,  
     CAST('2000000' as money) as Sales, CAST('POINT(-73.9922069374483 40.7549638237402)' as geography) AS SpatialLocation  
    UNION ALL Select 116 as StoreKey, 'Contoso Rochester No.1 Store' as StoreName, 462 as SellingArea, 'Rochester' as City,  'Monroe' as County,    
     CAST(3000000 as money) as Sales, CAST('POINT(-77.624041566786 43.1547066024338)' as geography)  AS SpatialLocation  
    UNION ALL Select 117 as StoreKey, 'Contoso New York No.2 Store' as StoreName, 700 as SellingArea, 'New York' as City,'New York City' as County,    
      CAST(4000000 as money) as Sales, CAST('POINT(-73.9712488 40.7830603)' as geography) AS SpatialLocation  
    UNION ALL Select 118 as StoreKey, 'Contoso Syracuse Store' as StoreName, 680 as SellingArea, 'Syracuse' as City, 'Onondaga' as County,  
     CAST(5000000 as money) as Sales, CAST('POINT(-76.1349120532546 43.0610223535974)' as geography) AS SpatialLocation  
    UNION ALL Select 120 as StoreKey, 'Contoso Plattsburgh Store' as StoreName, 560 as SellingArea, 'Plattsburgh' as City,  'Clinton' as County,  
     CAST(6000000 as money) as Sales, CAST('POINT(-73.4728622833178 44.7028831413324)' as geography) AS SpatialLocation  
    UNION ALL Select 121 as StoreKey, 'Contoso Brooklyn Store' as StoreName, 1125 as SellingArea, 'Brooklyn' as City, 'New York City' as County,  
     CAST(7000000 as money) as Sales, CAST('POINT (-73.9638533447143 40.6785123489351)' as geography) AS SpatialLocation  
    UNION ALL Select 122 as StoreKey, 'Contoso Oswego Store' as StoreName, 500 as SellingArea, 'Oswego' as City, 'Oswego' as County,    
     CAST(8000000 as money) as Sales, CAST('POINT(-76.4602850815536 43.4353224527794)' as geography) AS SpatialLocation  
    UNION ALL Select 123 as StoreKey, 'Contoso Ithaca Store' as StoreName, 460 as SellingArea, 'Ithaca' as City, 'Tompkins' as County,  
     CAST(9000000 as money) as Sales, CAST('POINT(-76.5001866085881 42.4310489934743)' as geography) AS SpatialLocation  
    UNION ALL Select 124 as StoreKey, 'Contoso Rochester No.2 Store' as StoreName, 700 as SellingArea, 'Rochester' as City, 'Monroe' as County,    
     CAST(100000 as money) as Sales, CAST('POINT(-77.6240415667866 43.1547066024338)' as geography) AS SpatialLocation  
    UNION ALL Select 125 as StoreKey, 'Contoso Queens Store' as StoreName, 700 as SellingArea,'Queens' as City, 'New York City' as County,  
     CAST(500000 as money) as Sales, CAST('POINT(-73.7930979029883 40.7152781765927)' as geography) AS SpatialLocation  
    UNION ALL Select 126 as StoreKey, 'Contoso Elmira Store' as StoreName, 680 as SellingArea, 'Elmira' as City, 'Chemung' as County,  
     CAST(800000 as money) as Sales, CAST('POINT(-76.7397414783301 42.0736492742663)' as geography) AS SpatialLocation  
    UNION ALL Select 127 as StoreKey, 'Contoso Poestenkill Store' as StoreName, 455 as SellingArea, 'Poestenkill' as City, 'Rensselaer' as County,    
    CAST(1500000 as money) as Sales, CAST('POINT(-73.5626737425063 42.6940551238618)' as geography) AS SpatialLocation  
    ```  
  
9. Dans la barre d’outils du Concepteur de requêtes, cliquez sur **Exécuter** (**!**).  
  
     Le jeu de résultats affiche sept colonnes : StoreKey, StoreName, SellingArea, City, County, Sales et SpatialLocation. Ces données représentent un ensemble de magasins de l'État de New York qui vendent des biens de consommation. Chaque ligne du jeu de résultats contient un identificateur de magasin, le nom du magasin, la zone disponible pour l'affichage des produits, la ville et le comté dans lesquels il se trouve, le chiffre d'affaires total et l'emplacement spatial en longitude et en latitude. La surface d'exposition varie entre 455 pieds carrés (environ 42 mètres carrés) et 1 125 pieds carrés (environ 104 mètres carrés).  
  
10. Cliquer sur **Suivant**.  
  
     Le dataset de rapport nommé DataSet1 est créé automatiquement. Après avoir terminé l'exécution de l'Assistant, vous pouvez utiliser le volet des données de rapport pour afficher la collection de champs correspondante.  
  
11. Sur le **choisir les données spatiales et les options de vue cartographique** page, vérifiez que le **champ Spatial** est `SpatialLocation` et que le **type de couche** est **Point**. Acceptez les autres valeurs par défaut dans cette page.  
  
     La vue cartographique affiche des cercles pour marquer l'emplacement de chaque magasin.  
  
12. Cliquer sur **Suivant**.  
  
13. Spécifiez un type de carte qui affiche des marqueurs variant en fonction des données analytiques. Dans la page Choisir la visualisation de la carte, cliquez sur **Carte à marqueurs analytique**, puis sur **Suivant**.  
  
14. Dans la page **Choisir le dataset analytique** , cliquez sur DataSet1. Ce dataset contient à la fois les données analytiques et les données spatiales à afficher sur la nouvelle couche de points.  
  
15. Cliquer sur **Suivant**.  
  
16. Dans la page **Choisir le thème de couleurs et la visualisation des données** , désactivez l'option **Utiliser les couleurs de marqueur pour visualiser les données** , puis sélectionnez l'option **Utiliser les types de marqueur pour visualiser les données**.  
  
17. Dans **Champ de données**, sélectionnez `[Sum(SellingArea)]` pour faire varier les types de marqueurs en fonction de la taille qu'un magasin réserve à l'affichage des produits.  
  
18. Cliquez sur **Terminer**.  
  
     La couche est ajoutée au rapport. La légende affiche les types de marqueur en fonction des valeurs de SellingArea.  
  
     Double-cliquez sur la carte pour afficher le volet **Couches** . Le volet **Couche** affiche une nouvelle couche, PointLayer1, avec comme type de source de données spatiales **DataRegion**.  
  
19. Ajoutez un titre de légende. Cliquez avec le bouton droit sur le titre de légende, puis cliquez sur **Propriétés du titre de légende**.  
  
20. Supprimez le titre, puis tapez **Surface d'exposition (en pieds carrés)**.  
  
21. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
22. Consultez les valeurs par défaut définies par l'Assistant. Dans le volet **Couches**, cliquez avec le bouton droit sur la couche de points, puis cliquez sur **Règle de type de marqueur**.  
  
     Sous l'onglet **Général** , les marqueurs sont répertoriés dans l'ordre dans lequel ils apparaissent dans l'Explorateur d'objets. Sous l'onglet **Distribution** , le nombre de sous-plages est 5. Sous l'onglet **Légende** , le texte de la légende est défini pour afficher la valeur de début et de fin de chaque plage.  
  
23. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
24. Affichez l'aperçu du rapport.  
  
 La carte affiche les emplacements des magasins dans l'État de New York. Le type de marqueur de chaque magasin est basé sur la surface d'exposition. Cinq plages de surface d'exposition ont été calculées automatiquement.  
  
##  <a name="LineLayer"></a> 3. Ajouter une couche de lignes pour afficher un itinéraire  
 Utilisez l'Assistant Couche pour ajouter une couche qui affiche un itinéraire entre deux magasins. Dans ce didacticiel, l'itinéraire est créé à partir de trois emplacements de magasin. Dans une application d'entreprise, l'itinéraire choisi peut être le meilleur itinéraire entre des magasins.  
  
#### <a name="to-add-a-line-layer-to-map"></a>Pour ajouter une couche de lignes à une carte  
  
1.  Basculez en mode Conception.  
  
2.  Double-cliquez sur la carte pour afficher le volet **Couches** . Dans la barre d'outils, cliquez sur **Assistant Nouvelle couche**.  
  
3.  Dans la page **Choisir une source de données spatiales** , sélectionnez **Requête spatiale SQL Server** et cliquez sur **Suivant**.  
  
4.  Dans la page **Choisir un dataset avec des données spatiales SQL Server** , cliquez sur **Ajouter un nouveau dataset avec des données spatiales SQL Server** , puis sur **Suivant**.  
  
5.  Dans **Choisir une connexion à une source de données spatiales SQL Server**, sélectionnez DataSource1, la source de données que vous avez créée dans la première procédure.  
  
6.  Cliquer sur **Suivant**.  
  
7.  Dans la page **Créer une requête** , cliquez sur **Modifier en tant que texte**. Le concepteur de requêtes bascule en mode texte.  
  
8.  Collez le texte ci-après dans le volet Requête :  
  
    ```  
    SELECT N'Path' AS Name, CAST('LINESTRING(  
       -76.5001866085881 42.4310489934743,  
       -76.4602850815536 43.4353224527794,  
       -73.4728622833178 44.7028831413324)' AS geography) as Route  
    ```  
  
9. Cliquer sur **Suivant**.  
  
     Un itinéraire qui relie les trois magasins apparaît sur la carte.  
  
10. Dans la page **Choisir des options de vue cartographique et de données spatiales** , vérifiez que le **Champ spatial** est **Route** et que le **Type de couche** est **Ligne**. Acceptez les autres valeurs par défaut.  
  
     La vue cartographique affiche un itinéraire allant d'un magasin situé dans la partie nord de l'État de New York à un magasin situé dans la partie sud de l'État de New York.  
  
11. Cliquer sur **Suivant**.  
  
12. Dans la page **Choisir la visualisation de la carte** , cliquez sur l'option **Carte linéaire simple**, puis sur **Suivant**.  
  
13. Dans la page **Choisir le thème de couleurs et la visualisation des données**, sélectionnez l'option **Carte unicolore**. L'itinéraire s'affiche dans une couleur unique selon le thème sélectionné.  
  
14. Cliquez sur **Terminer**.  
  
 La carte affiche une nouvelle couche de lignes avec **DataSet**comme type de source de données spatiales. Dans cet exemple, les données spatiales proviennent d'un dataset mais aucune donnée analytique n'est associée à la ligne.  
  
##  <a name="TileLayer"></a> 4. Ajouter un arrière-plan de mosaïques Bing  
 Ajoutez une couche qui affiche un arrière-plan de mosaïques Bing Maps.  
  
#### <a name="to-add-a-virtual-earth-tile-background"></a>Pour ajouter un arrière-plan de mosaïques Virtual Earth  
  
1.  Basculez en mode Conception.  
  
2.  Double-cliquez sur la carte pour afficher le volet **Couches** . Dans la barre d’outils, cliquez sur **ajouter une couche**![rs_IconMapAddLayer](../../2014/tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer").  
  
3.  Dans la liste déroulante, cliquez sur **Couche de mosaïques**.  
  
     La dernière couche du volet **Couche** est TileLayer1. Par défaut, la couche de mosaïques affiche le style de carte routière.  
  
    > [!NOTE]  
    >  Dans l'Assistant, vous pouvez également ajouter une couche de mosaïques dans la page **Choisir des options de vue cartographique et de données spatiales** . Pour ce faire, sélectionnez **Ajouter un arrière-plan Bing Maps pour cette vue cartographique**. Dans un rapport rendu, l'arrière-plan de mosaïques affiche des mosaïques Bing Maps pour le centre et le niveau de zoom du point de vue de la carte actuels.  
  
4.  Cliquez sur la flèche bas sur TileLayer1, puis sur **Propriétés des mosaïques**.  
  
5.  Dans la zone **Type**, sélectionnez **Aérien**. La vue aérienne ne contient pas de texte.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Transparent"></a> 5. Rendre une couche transparente  
 Pour permettre aux éléments d'une couche de laisser transparaître une autre couche, vous pouvez ajuster l'ordre des couches et la transparence de chaque couche afin d'obtenir l'effet souhaité.  
  
#### <a name="to-set-the-transparency-of-a-layer"></a>Pour définir la transparence d'une couche  
  
1.  Basculez en mode Conception.  
  
2.  Double-cliquez sur la carte pour afficher le volet **Couches** .  
  
3.  Cliquez sur la flèche bas sur PolygonLayer1, puis sur **Données de la couche**. La boîte de dialogue **Propriétés des couches de polygones de la carte** s'ouvre.  
  
4.  Cliquez sur **Visibilité**.  
  
5.  Dans l'option **Transparence (%)**, tapez **30**.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 L'aire de conception affiche les comtés en couleurs translucides.  
  
##  <a name="Vary"></a> 6. Faire varier la couleur du comté selon les ventes  
 Chaque comté de la couche de polygones a une couleur différente car le processeur de rapports attribue automatiquement une valeur de couleur de la palette de couleurs selon le thème que vous avez choisi dans la dernière page de l'Assistant Carte.  
  
 Dans les étapes suivantes, spécifiez une règle de couleur pour associer des couleurs spécifiques à une plage de ventes des magasins pour chaque comté. Les couleurs rouge-jaune-vert indiquent des chiffres d'affaires relatifs élevés-moyens-bas. Mettez en forme l'échelle de couleurs pour afficher la devise. Affichez les plages de chiffres d'affaires annuels dans une nouvelle légende. Pour les comtés qui ne contiennent pas de magasins, utilisez la valeur Aucune couleur pour indiquer qu'il n'existe pas de données associées.  
  
###  <a name="Relationship"></a> 6 a. Créer une relation entre des données spatiales et des données analytiques  
 Pour faire varier les formes de comté par couleur en fonction des données analytiques, vous devez tout d'abord associer des données analytiques aux données spatiales. Dans ce didacticiel, vous utiliserez une correspondance basée sur le nom du comté.  
  
##### <a name="to-build-a-relationship-between-spatial-data-and-analytical-data"></a>Pour générer une relation entre des données spatiales et des données analytiques  
  
1.  Basculez en mode Conception.  
  
2.  Double-cliquez sur la carte pour afficher le volet **Couches** .  
  
3.  Cliquez sur la flèche bas sur PolygonLayer1, puis sur **Données de la couche**. La boîte de dialogue **Propriétés des couches de polygones de la carte** s'ouvre.  
  
4.  Cliquez sur **Données analytiques**.  
  
5.  Dans la zone de liste déroulante, sélectionnez DataSet1. Ce dataset a été créé par l'Assistant lorsque vous avez spécifié la requête de données spatiales pour les comtés.  
  
6.  Dans **Champs à mettre en correspondance**, cliquez sur **Ajouter**. Une nouvelle ligne est ajoutée.  
  
7.  Dans **Depuis un dataset spatial**, dans la liste déroulante, cliquez sur COUNTYNAME.  
  
8.  Dans **Depuis un dataset analytique**, dans la liste déroulante, cliquez sur [County].  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. Affichez l'aperçu du rapport.  
  
 En spécifiant un champ de correspondance de la source de données spatiales et du dataset analytique, vous permettez au processeur de regrouper les données analytiques en fonction des éléments cartographiques. Un élément cartographique lié aux données a une correspondance valide pour les valeurs que vous avez spécifiées.  
  
 Chaque comté qui contient un magasin a une couleur basée sur la palette de couleurs du style que vous avez choisi dans l'Assistant.  
  
###  <a name="ColorRules"></a> 6 b. Spécifier des règles de couleur pour les polygones  
 Pour créer une règle qui fait varier la couleur de chaque comté en fonction des ventes des magasins, vous devez spécifier les valeurs de plage, le nombre de divisions dans la plage que vous souhaitez afficher, ainsi que les couleurs à utiliser.  
  
##### <a name="to-specify-color-rules-for-all-polygons-that-have-associated-data"></a>Pour spécifier des règles de couleur pour tous les polygones ayant des données associées  
  
1.  Basculez en mode Conception.  
  
2.  Cliquez sur la flèche bas sur PolygonLayer1, puis sur **Règle de couleur de polygone**. La boîte de dialogue **Propriétés des règles de couleur de la carte** s'ouvre. Remarquez que l'option de la règle de couleur **Visualiser les données à l'aide de la palette de couleurs** est sélectionnée. Cette option a été définie par l'Assistant.  
  
3.  Sélectionnez **Visualiser les données à l'aide de plages de couleurs**. L'option de palette est remplacée par les options de couleur de début, intermédiaire et de fin.  
  
4.  Définissez des valeurs de plage pour le chiffre d'affaires par comté. Dans **Champ de données**, dans la liste déroulante, sélectionnez `[Sum(Sales)]`.  
  
5.  Pour modifier le format afin d'afficher la devise en milliers, remplacez l'expression par ce qui suit : `=Sum(Fields!Sales.Value)/1000`  
  
6.  Modifiez **Couleur de début** en choisissant la valeur **Rouge**.  
  
7.  Modifiez **Couleur de fin** en choisissant la valeur **Vert**.  
  
     **Rouge** représente les chiffres de ventes bas, **Jaune** les chiffres de ventes moyens et **Vert** les chiffres de ventes élevés. Le processeur de rapports calcule une plage de couleurs en fonction de ces valeurs et des options sélectionnées dans la page **Distribution** .  
  
8.  Cliquez sur **Distribution**.  
  
9. Vérifiez que le type de distribution est **Optimal**. Pour l'expression de l'étape 5, la distribution optimale divise les valeurs en sous-plages présentant un équilibre entre le nombre d'éléments dans chaque plage et l'étendue de chaque plage.  
  
10. Acceptez les valeurs par défaut pour les autres options de cette page. Lorsque vous sélectionnez le type de distribution optimal, le nombre de sous-plages est calculé lors de l'exécution du rapport.  
  
11. Cliquez sur **Légende**.  
  
12. Dans **Options d'échelle de couleurs**, vérifiez que l'option **Afficher dans l'échelle de couleurs** est sélectionnée.  
  
13. Dans **Afficher dans cette légende**, dans la liste déroulante, sélectionnez la ligne vierge. Pour le moment, vous afficherez uniquement les plages de couleurs dans l'échelle de couleurs.  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 L'échelle de couleurs affiche cinq couleurs : rouge, orange, jaune, jaune vert et vert. Chaque couleur représente une plage de ventes calculée automatiquement selon les ventes par comté.  
  
###  <a name="ColorScale"></a> 6c. Mettre en forme les données de l'échelle de couleurs en tant que devises  
 Par défaut, les données ont un format général. Vous pouvez appliquer des formats personnalisés.  
  
##### <a name="to-set-the-format-for-the-color-scale"></a>Pour définir la mise en forme de l'échelle de couleurs  
  
1.  Cliquez avec le bouton droit sur l'échelle de couleurs, puis cliquez sur **Propriétés de l'échelle de couleurs**.  
  
2.  Cliquez sur **Nombre**.  
  
3.  Dans **Catégorie**, cliquez sur **Devise**.  
  
4.  Dans **Nombre de décimales**, tapez **0**. Cette mise en forme ne spécifie pas de décimales pour les valeurs monétaires.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Affichez l'aperçu du rapport.  
  
 L'échelle de couleurs affiche les chiffres d'affaires annuels au format monétaire pour chaque plage.  
  
###  <a name="NewLegend"></a> 6d. Créer une légende  
 Par défaut, toutes les règles s'affichent dans la première légende. Pour améliorer l'affichage d'une carte, vous pouvez ajouter des légendes.  
  
 Pour modifier l'affichage par défaut, il y a deux étapes : créez une légende, puis associez les résultats des règles d'une couche à la nouvelle légende.  
  
##### <a name="to-create-a-new-legend"></a>Pour créer une légende  
  
1.  Basculez en mode Conception.  
  
2.  Cliquez avec le bouton droit sur la carte à l'extérieur de la fenêtre d'affichage, puis cliquez sur **Ajouter une légende**. Une nouvelle légende est ajoutée à la carte à un emplacement par défaut.  
  
3.  Cliquez avec le bouton droit sur la légende, puis cliquez sur **Propriétés de la légende**.  
  
4.  Dans **Options de position**, cliquez sur l'emplacement qui spécifie où vous souhaitez afficher la légende par rapport à la fenêtre d'affichage. La carte sur l'aire de conception est mise à jour pour afficher vos sélections.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Cliquez sur **Titre** sur la légende pour sélectionner le titre de légende.  
  
7.  Cliquez encore sur **Titre** pour passer en mode d'insertion pour le texte. Remplacez **Titre** par **Ventes (en milliers)**, puis cliquez à l'extérieur du texte.  
  
 La légende est développée pour afficher le titre.  
  
###  <a name="Associate"></a> 6e. Associer une légende aux règles de couleur  
 Chaque légende peut afficher un ou plusieurs jeux de résultats des règles.  
  
##### <a name="to-associate-a-legend-with-color-rules"></a>Pour associer une légende à des règles de couleur  
  
1.  Double-cliquez sur la carte pour afficher le volet **Couche** .  
  
2.  Cliquez sur la flèche bas sur PolygonLayer1, puis sur **Règle de couleur de polygone**. La boîte de dialogue **Propriétés des règles de couleur de la carte** s'ouvre.  
  
3.  Cliquez sur **Légende**.  
  
4.  Dans **Options d'échelle de couleurs**, désactivez **Afficher dans l'échelle de couleurs**.  
  
5.  Dans **Options de légende**, sélectionnez Legend2 dans la liste déroulante. L'option de texte de légende s'affiche. Par défaut, le texte de la légende est mis en forme avec une chaîne de format [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] générale. Le 0 dans N0 indique l'absence de chiffres décimaux.  
  
6.  Dans **texte de légende**, utilisez le format suivant pour spécifier une devise sans chiffres décimaux : `#FROMVALUE {C0} - #TOVALUE {C0}`  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Dans l'aire de conception, la légende affiche les plages de couleurs avec des exemples de données mises en forme en tant que devises.  
  
8.  Affichez l'aperçu du rapport.  
  
 Les comtés qui ont des magasins et des ventes associés s'affichent en fonction des règles de couleur. Les comtés qui n'ont pas de ventes n'ont aucune couleur.  
  
###  <a name="NoData"></a> 6F. Modifier la couleur des comtés sans données  
 Vous pouvez définir les options d'affichage par défaut pour tous les éléments cartographiques d'une couche. Les règles de couleur ont priorité sur ces options d'affichage.  
  
##### <a name="to-set-the-display-properties-for-all-elements-on-a-layer"></a>Pour définir les propriétés d'affichage de tous les éléments d'une couche  
  
1.  Basculez en mode Conception.  
  
2.  Double-cliquez sur la carte pour afficher le volet **Couches** .  
  
3.  Cliquez sur la flèche bas sur PolygonLayer1, puis sur **Propriétés des polygones**. La boîte de dialogue **Propriétés des polygones de la carte** s'ouvre. Les options d'affichage définies dans cette boîte de dialogue s'appliquent à tous les polygones de la couche avant les options d'affichage basées sur les règles.  
  
4.  Cliquez sur **Remplir**.  
  
5.  Vérifiez que le style de remplissage est **Plein.** Les dégradés et les motifs s'appliquent à toutes les couleurs.  
  
6.  Dans **Couleur**, cliquez sur la flèche bas, puis sur **Bleu acier clair**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  Affichez l'aperçu du rapport.  
  
 Les comtés sans données associées s'affichent en bleu. Seuls les comtés qui ont des données analytiques associées s'affichent dans les couleurs allant du **Rouge** au **Vert** en fonction des règles de couleur que vous avez spécifiées.  
  
##  <a name="CustomPoint"></a> 7. Ajouter un point personnalisé  
 Pour représenter un nouveau magasin qui n'a pas encore été construit, spécifiez un point et utilisez le type de marqueur **Punaise** .  
  
#### <a name="to-add-a-custom-point"></a>Pour ajouter un point personnalisé  
  
1.  Basculez en mode Conception.  
  
2.  Double-cliquez sur la carte pour afficher le volet **Couches** . Dans la barre d'outils, cliquez sur **Ajouter une couche**, puis sur **Couche de points**.  
  
     Une nouvelle couche de points est ajoutée à la carte. Par défaut, le type de données spatiales de la couche de points est **Incorporé**.  
  
3.  Cliquez sur la flèche bas sur PointLayer2, puis sur **Ajouter un point**.  
  
4.  Déplacez le pointeur sur le point de vue de la carte. Le curseur se transforme en croix.  
  
5.  Cliquez sur l'emplacement de la carte où vous souhaitez ajouter un point. Dans ce didacticiel, cliquez sur un emplacement d'un comté, près du début de l'itinéraire. Un point marqué par un cercle est ajouté à la couche à l'emplacement où vous avez cliqué. Par défaut, le point est sélectionné.  
  
6.  Cliquez avec le bouton droit sur le point que vous avez ajouté, puis cliquez sur **Propriétés des points incorporés**.  
  
7.  Sélectionnez l'option **Remplacer les options de point pour cette couche**. Des pages supplémentaires s'affichent dans la boîte de dialogue. Les valeurs que vous définissez ici ont priorité sur les options d'affichage de la couche et sur les règles de couleur.  
  
8.  Cliquez sur **Marqueur**.  
  
9. Pour **Type de marqueur**, sélectionnez **Étoile**.  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. Affichez l'aperçu du rapport.  
  
 Le nouveau point que vous avez ajouté est affiché sous forme d' **Étoile**.  
  
#### <a name="to-add-a-label-for-the-custom-point"></a>Pour ajouter une étiquette au point personnalisé  
  
1.  Basculez en mode Conception.  
  
2.  Cliquez avec le bouton droit sur le point que vous venez d'ajouter, puis cliquez sur **Propriétés du point incorporé**.  
  
3.  Cliquez sur **Étiquettes**.  
  
4.  Dans **Texte d'étiquette**, tapez **Nouveau magasin**.  
  
5.  Dans **Emplacement**, cliquez sur **Haut**.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Affichez l'aperçu du rapport.  
  
 L'étiquette s'affiche au-dessus de l'emplacement du magasin.  
  
##  <a name="CenterView"></a> Centrer la vue cartographique  
 Modifiez le centre et le niveau de zoom du point de vue de la carte.  
  
#### <a name="to-change-the-viewport"></a>Pour modifier la fenêtre de carte  
  
1.  Cliquez avec le bouton droit sur le point de vue de la carte, puis cliquez sur **Propriétés de la fenêtre de carte**.  
  
2.  Cliquez sur **Centrer et zoomer**.  
  
3.  Assurez-vous que l'option **Définir un centre d'affichage et un niveau de zoom** est sélectionnée.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  Cliquez avec le bouton gauche de la souris sur le point de vue de la carte, puis faites glisser le centre de la fenêtre d'affichage vers l'emplacement de votre choix.  
  
6.  Utilisez la roulette de la souris pour modifier le niveau de zoom de la fenêtre d'affichage.  
  
7.  Affichez l'aperçu du rapport.  
  
 En mode Conception, la carte apparaît sur la surface d'affichage et la vue est basée sur les exemples de données. Dans le rapport rendu, la vue cartographique est centrée dans la vue que vous avez spécifiée.  
  
##  <a name="Title"></a> Ajouter un titre de rapport  
  
#### <a name="to-add-a-report-title"></a>Pour ajouter un titre de rapport  
  
1.  Dans l'aire de conception, cliquez sur **Cliquez pour ajouter un titre**.  
  
2.  Tapez **Ventes des magasins de New York** , puis cliquez à l'extérieur de la zone de texte.  
  
 Ce titre s'affiche alors dans la partie supérieure du rapport. En l'absence d'en-tête de page défini, les éléments situés au-dessus du corps du rapport font office d'en-tête de rapport.  
  
##  <a name="Save"></a> Enregistrer le rapport  
  
#### <a name="to-save-the-report"></a>Pour enregistrer le rapport  
  
1.  Basculez en mode Conception.  
  
2.  À partir du bouton Générateur de rapports, cliquez sur **Enregistrer sous**.  
  
3.  Dans **Nom**, tapez **Ventes des magasins de New York**.  
  
 Cliquez sur **Enregistrer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Ceci conclut la procédure pas à pas décrivant comment ajouter une carte à votre rapport.  
  
 Pour plus d’informations, consultez [Maps &#40;Générateur de rapports et SSRS&#41; ](report-design/maps-report-builder-and-ssrs.md) et l’entrée de blog [cartographiques ajustement de données spatiales pour SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=152771) sur blogs.msdn.com.  
  
 Pour plus de didacticiels, consultez [didacticiels &#40;Générateur de rapports&#41;](report-builder-tutorials.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels &#40;Générateur de rapports&#41;](report-builder-tutorials.md)   
 [Générateur de rapports dans SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)   
 [Assistant Carte et Assistant Couche &#40;Générateur de rapports et SSRS&#41;](report-design/map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)   
 [Modifier l’affichage des polygones, des lignes et des points à l’aide de règles et de données analytiques &#40;Générateur de rapports et SSRS&#41;](report-design/vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  
