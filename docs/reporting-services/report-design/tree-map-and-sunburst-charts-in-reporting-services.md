---
title: Graphiques de compartimentage et en rayons de soleil dans SQL Server Reporting Services | Microsoft Docs
description: Découvrez comment représenter visuellement des données hiérarchiques à l’aide d’un graphique de compartimentage ou d’un graphique en rayons de soleil dans le Générateur de rapports.
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: ''
ms.date: 04/26/2019
ms.openlocfilehash: af294ac47e7523f0b0dba5a57bbf2318bbe8c149
ms.sourcegitcommit: 93e4fd75e8fe0cc85e7949c9adf23b0e1c275465
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84255432"
---
# <a name="treemap-and-sunburst-charts-in-reporting-services"></a>Graphiques de compartimentage et en rayons de soleil dans Reporting Services 

Les visualisations sous la forme de graphiques de compartimentage et en rayons de soleil de SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sont parfaites pour représenter visuellement des données hiérarchiques. Cet article présente une vue d’ensemble de l’ajout d’un graphique de compartimentage ou d’un graphique en rayons de soleil à un rapport [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Il inclut également un exemple de requête AdventureWorks pour vous aider à démarrer.  
  
##  <a name="treemap-chart"></a><a name="bkmk_treemap_chart"></a> Graphique de compartimentage  

Un graphique de compartimentage divise la zone de graphique en rectangles représentant les différents niveaux et tailles relatives de la hiérarchie de données. Le mappage ressemble à arbre, avec un tronc, des branches et des ramifications de plus en plus petites. Chaque rectangle est subdivisé en rectangles plus petits représentant un niveau inférieur dans la hiérarchie. Les rectangles de niveau supérieur du graphique de compartimentage sont disposés avec le plus grand rectangle en haut à gauche du graphique et le plus petit en bas à droite.  À l’intérieur d’un rectangle, le niveau suivant dans la hiérarchie est également organisé en rectangles allant de l’angle supérieur gauche à l’angle inférieur droit.  

Par exemple, dans l’exemple de graphique de compartimentage suivant, le territoire « Southwest » est le plus grand et « Germany » le plus petit. Dans le territoire« Southwest », les « Road Bikes » sont plus importants que les « Mountain Bikes ».  

![ssrs_treemap_example](../../reporting-services/report-design/media/ssrs-treemap-example.png "ssrs_treemap_example")  
  
### <a name="to-insert-a-treemap-chart-and-set-up-the-sample-adventureworks-data"></a>Pour insérer un graphique de compartimentage et configurer l’échantillon de données Adventureworks  

> [!NOTE]
> Avant d’ajouter un graphique à votre rapport, créez une source de données et un jeu de données.  Pour obtenir des exemples de données et un exemple de requête, consultez [Échantillon de données Adventureworks](#bkmk_sample_data).  
  
1. Cliquez avec le bouton droit sur l’aire de conception, puis sélectionnez **Insérer** > **Graphique**. Sélectionnez l’icône **Compartimentage**.

    ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon")  

2. Repositionnez et redimensionnez le graphique. Pour l’échantillon de données, un graphique de 5 pouces de large est un bon début.  
  
3. Ajoutez les champs suivants à partir de l’échantillon de données :  
  
    * **Valeurs** : LineTotal
    * **Category Groups** (Groupes de catégories) (dans l’ordre suivant) :
        1. CategoryName (Nom de catégorie)
        2. SubcategoryName (Nom de sous-catégorie)
    * **Groupes de séries** : TerritoryName  

    ![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")
  
4. Pour optimiser la taille de page pour la forme générale d’un graphique de compartimentage, positionnez la légende en bas.  
  
5. Pour ajouter des info-bulles qui affichent la sous-catégorie et le total de la ligne, cliquez sur **LineTotal** (Total de la ligne), puis sélectionnez **Propriétés de la série**.  
  
     ![ssrs_visualization_seriesproperties](../../reporting-services/report-design/media/ssrs-visualization-seriesproperties.png "ssrs_visualization_seriesproperties")  
  
     Définissez la propriété **Tooltip** (Info-bulle) sur la valeur suivante :  
  
    ```
    =Fields!SubcategoryName.Value &": " &Format(Sum(Fields!LineTotal.Value),"C")  
    ```  
  
    Pour plus d’informations, consultez [Afficher des info-bulles dans une série &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md).  
  
6. Remplacez le titre par défaut du graphique par **Categorized Sales by Territory** (Ventes classées par territoire).  
  
7. Le nombre de valeurs d’étiquette qui s’affichent est affecté par la taille de la police, la taille de la zone de graphique et la taille des différents rectangles. Pour afficher d’autres étiquettes, définissez la propriété **Label Font** (Police de l’étiquette) de **LineTotal** (Total de la ligne) sur **10 pt**, à la place de la valeur par défaut **8 pt**.  

##  <a name="sunburst-chart"></a><a name="bkmk_sunburst_chart"></a> Graphique en rayons de soleil  

Dans un graphique en rayons de soleil, la hiérarchie est représentée par une série de cercles. Le plus haut niveau de la hiérarchie se trouve au centre et les niveaux inférieurs de la hiérarchie sont des anneaux affichés à l’extérieur du centre.  Le niveau le plus bas de la hiérarchie est l’anneau extérieur.  
  
![ssrs_sunburst_example](../../reporting-services/report-design/media/ssrs-sunburst-example.png "ssrs_sunburst_example")  
  
### <a name="to-insert-a-sunburst-chart-and-set-up-the-sample-adventureworks-data"></a>Pour insérer un graphique en rayons de soleil et configurer l’échantillon de données Adventureworks

> [!NOTE]
> Avant d’ajouter un graphique à votre rapport, créez une source de données et un jeu de données. Pour obtenir des exemples de données et un exemple de requête, consultez [Échantillon de données Adventureworks](#bkmk_sample_data).  
  
1. Cliquez avec le bouton droit sur l’aire de conception, puis sélectionnez **Insérer** > **Graphique**. Sélectionnez l’icône **Rayons**.

     ![ssrs_sunburst_icon](../../reporting-services/media/ssrs-sunburst-icon.png "ssrs_sunburst_icon")  
  
2. Repositionnez et redimensionnez le graphique. Pour l’échantillon de données, un graphique de 5 pouces de large est un bon début.  
  
3. Ajoutez les champs suivants à partir de l’échantillon de données :  

    * **Valeurs** : LineTotal
    * **Category Groups** (Groupes de catégories) (dans l’ordre suivant) :
        1. CategoryName (Nom de catégorie)
        2. SubcategoryName (Nom de sous-catégorie)
        3. SalesReasonName (Nom du motif de vente)
    * **Groupes de séries** : TerritoryName  

    ![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")
  
4. Pour optimiser la taille de page pour la forme générale d’un graphique en rayons de soleil, positionnez la légende en bas.  
  
5. Remplacez le titre par défaut du graphique par **Categorized Sales by Territory** (Ventes classées par territoire, avec motif de vente).  
  
6. Pour ajouter les valeurs des groupes de catégories au graphique en rayons de soleil en tant qu’étiquettes, définissez la propriété d’étiquette comme suit : **Visible=true** et **UseValueAsLabel=False**.<br /><br /> Les valeurs d’étiquette qui s’affichent sont affectées par la taille de la police, la taille de la zone de graphique et la taille des différents rectangles.  Pour afficher d’autres étiquettes, définissez la propriété **Label Font** (Police de l’étiquette) de **LineTotal** (Total de la ligne) sur **10 pt**, à la place de la valeur par défaut **8 pt**.

    ![ssrs_sunburst_linetotalproperties](../../reporting-services/report-design/media/ssrs-sunburst-linetotalproperties.png "ssrs_sunburst_linetotalproperties")
  
7. Si vous voulez utiliser une autre plage de couleurs, modifiez la propriété **Palette** du graphique.  

     ![ssrs_visualization_palette](../../reporting-services/report-design/media/ssrs-visualization-palette.png "ssrs_visualization_palette")  

##  <a name="sample-adventureworks-data"></a><a name="bkmk_sample_data"></a> Échantillon de données Adventureworks

Cette section présente un exemple de requête et les étapes de base pour la création d’une source de données et d’un jeu de données dans [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)]. Si votre rapport contient déjà une source de données et le jeu de données, vous pouvez ignorer cette section.  
  
La requête retourne des données de détail des ventes d’AdventureWorks par secteur de vente, catégorie de produit, sous-catégorie de produit et motif de vente.  
  
1. **Obtenez les données**.  
  
     La requête de cette section porte sur la base de données AdventureWorks disponible au téléchargement sur GitHub : [AdventureWorks 2016 full database backup](https://github.com/Microsoft/sql-server-samples/releases).  

2. **Créez une source de données**.  
  
    1. Sous **Données du rapport**, cliquez avec le bouton droit sur **Sources de données**, puis sélectionnez **Ajouter une source de données**.  
  
    2. Cliquez sur **Utiliser une connexion incorporée dans mon rapport**.  
  
    3. Dans Type de connexion, sélectionnez **Microsoft SQL Server**.  
  
    4. Entrez la chaîne de connexion à votre serveur et à la base de données. Par exemple :  
  
        ```
        Data Source=[server name];Initial Catalog=AdventureWorks2016  
        ```  
  
    5. Pour vérifier la connexion, cliquez sur le bouton **Tester la connexion**, puis sélectionnez **OK**.  
  
     Pour plus d’informations sur la création d’une source de données, consultez [Ajouter et vérifier une connexion de données &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
3. **Créez un jeu de données**.  
  
    1. Sous **Données du rapport**, cliquez avec le bouton droit sur **Datasets**, puis sélectionnez **Ajouter un Dataset**.  
  
    2. Cliquez sur **Utiliser un dataset incorporé dans mon rapport**.  
  
    3. Sélectionnez la source de données que vous avez créée.  
  
    4. Sélectionnez le type de requête **Texte**, puis copiez et collez la requête suivante dans la zone de texte **Requête** :  
  
        ```sql
        SELECT    Sales.SalesOrderHeader.SalesOrderID, Sales.SalesOrderHeader.OrderDate, Sales.SalesOrderDetail.SalesOrderDetailID, Sales.SalesOrderDetail.ProductID, Sales.SalesOrderDetail.LineTotal,   
                                 Sales.SalesOrderDetail.UnitPrice, Sales.SalesOrderDetail.OrderQty, Production.Product.Name, Production.Product.ProductNumber, Sales.SalesTerritory.TerritoryID, lower(Sales.SalesTerritory.Name) AS TerritoryName,   
                                 Production.ProductSubcategory.Name AS SubcategoryName, Production.ProductCategory.Name AS CategoryName, Sales.SalesReason.SalesReasonID, Sales.SalesReason.Name AS SalesReasonName  
        FROM            Sales.SalesOrderDetail INNER JOIN  
                                 Sales.SalesOrderHeader ON Sales.SalesOrderDetail.SalesOrderID = Sales.SalesOrderHeader.SalesOrderID INNER JOIN  
                                 Production.Product ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID INNER JOIN  
                                 Sales.SalesTerritory ON Sales.SalesOrderHeader.TerritoryID = Sales.SalesTerritory.TerritoryID AND Sales.SalesOrderHeader.TerritoryID = Sales.SalesTerritory.TerritoryID AND   
                                 Sales.SalesOrderHeader.TerritoryID = Sales.SalesTerritory.TerritoryID INNER JOIN  
                                 Production.ProductSubcategory ON Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID AND   
                                 Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID AND   
                                 Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID INNER JOIN  
                                 Production.ProductCategory ON Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID AND   
                                 Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID AND   
                                 Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID INNER JOIN  
                                 Sales.SalesOrderHeaderSalesReason ON Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID AND   
                                 Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID AND Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID AND   
                                 Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID INNER JOIN  
                                 Sales.SalesReason ON Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID AND   
                                 Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID AND Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID AND   
                                 Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID  
        ```  
  
    5. Sélectionnez **OK**.  
  
     Pour plus d’informations sur la création d’un dataset, consultez [Créer un dataset partagé ou incorporé &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi

* [Mode création de dataset partagé &#40;Générateur de rapports&#41;](../../reporting-services/report-builder/shared-dataset-design-view-report-builder.md)

* [Afficher des info-bulles dans une série &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md)

* [Tutoriel : Graphiques de compartimentage dans Power BI](https://support.powerbi.com/knowledgebase/articles/556200-tutorial-treemaps-in-power-bi)

* [Graphique de compartimentage : Applications de visualisation des données de Microsoft Research pour Office](https://research.microsoft.com/projects/msrdatavis/treemap.aspx)