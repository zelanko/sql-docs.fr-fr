---
title: "Graphiques de compartimentage et en rayons de soleil dans Reporting Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "08/31/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12307c8f-bca7-4d21-8ad5-0c07d819865b
caps.latest.revision: 17
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 16
---
# Graphiques de compartimentage et en rayons de soleil dans Reporting Services
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

  Les visualisations sous la forme de compartimentage et de rayons de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sont parfaites pour représenter visuellement des données hiérarchiques.   Cette rubrique présente une vue d’ensemble de l’ajout d’un graphique de compartimentage ou d’un graphique en rayon de soleil à un rapport [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Elle inclut également un exemple de requête Adventureworks pour vous aider à commencer.  
  
##  <a name="bkmk_treemap_chart"></a> Graphique de compartimentage  
 ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon")  
  
 Un graphique de compartimentage divise la zone de graphique en rectangles représentant les niveaux et les tailles relatives de la hiérarchie de données. Le mappage ressemble à arbre, avec un tronc, des branches et des ramifications de plus en plus petites. Chaque rectangle est subdivisé en rectangles plus petits représentant un niveau inférieur dans la hiérarchie. Les rectangles de niveau supérieur du graphique de compartimentage sont disposés avec le plus grand rectangle dans l’angle supérieur gauche du graphique et le plus petit dans l’angle inférieur droit.  À l’intérieur d’un rectangle, le niveau suivant dans la hiérarchie est également organisé en rectangles allant de l’angle supérieur gauche à l’angle inférieur droit.  
  
 Par exemple, dans l’exemple de graphique de compartimentage suivant, le territoire « Southwest » est le plus grand, et « Germany » le plus petit. Dans le territoire« Southwest », les « Road Bikes » sont plus importants que les « Mountain Bikes ».  
  
 ![ssrs_treemap_example](../../reporting-services/report-design/media/ssrs-treemap-example.png "ssrs_treemap_example")  
  
### Pour insérer un graphique de compartimentage et configurer l’échantillon de données Adventureworks  
 **Remarque :** avant d’ajouter un graphique à votre rapport, créez une source de données et un jeu de données.  Pour des exemples de données et de requête, voir la section [Échantillon de données Adventureworks](#bkmk_sample_data) dans cette rubrique.  
  
1.  Cliquez avec le bouton droit sur l’aire de conception, cliquez sur **Insérer**, puis sur **Graphique**.  
  
     Sélectionnez Arborescence ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon").  
  
     ![ssrs_insert_treemap_sunburst](../../reporting-services/report-design/media/ssrs-insert-treemap-sunburst.png "ssrs_insert_treemap_sunburst")  
  
2.  Repositionnez et redimensionnez le graphique.   Pour l’échantillon de données, un graphique de 5 pouces de large est un bon début.  
  
3.  Ajoutez les champs suivants à partir de l’échantillon de données :  
  
    |||  
    |-|-|  
    |![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")|**Values :** (Valeurs) LineTotal (Total de la ligne)<br /><br /> **Category Groups :** (Groupes de catégories ) ajoutez-les dans l’ordre suivant :<br /><br /> 1) CategoryName (Nom de catégorie)<br /><br /> 2) SubcategoryName (Nom de sous-catégorie)<br /><br /> **Series Groups :** (Groupes de séries) TerritoryName (Nom de territoire)|  
  
4.  Pour optimiser la taille de page pour la forme générale d’un graphique de compartimentage, positionnez la légende en bas.  
  
5.  Pour ajouter des info-bulles qui affichent la sous-catégorie et le total de la ligne, cliquez sur **LineTotal** (Total de la ligne), puis sur **Propriétés de la série**.  
  
     ![ssrs_visualization_seriesproperties](../../reporting-services/report-design/media/ssrs-visualization-seriesproperties.png "ssrs_visualization_seriesproperties")  
  
     Définissez la propriété **Tooltip** (Info-bulle) comme suit :  
  
    ```  
    =Fields!SubcategoryName.Value &": " &Format(Sum(Fields!LineTotal.Value),"C")  
    ```  
  
     Pour plus d’informations, consultez [Afficher des info-bulles dans une série &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md).  
  
6.  Modifiez le titre par défaut du graphique en « Categorized Sales by Territory » (Ventes classées par territoire).  
  
7.  Le nombre de valeurs d’étiquette qui s’affichent est affecté par la taille de la police, la taille de la zone de graphique et la taille des différents rectangles.  Pour afficher d’autres étiquettes, définissez la propriété de police de l’étiquette LineTotal (Total de la ligne) sur 10 pt au lieu de la valeur par défaut de 8 pt.  
  
 ![Icône de flèche utilisée avec le lien Retour en haut](../../analysis-services/instances/media/uparrow16x16.png "Icône de flèche utilisée avec le lien Retour en haut") [Dans cette rubrique](#bkmk_top)  
  
##  <a name="bkmk_sunburst_chart"></a> Graphique en rayons de soleil  
 ![ssrs_sunburst_icon](../../reporting-services/media/ssrs-sunburst-icon.png "ssrs_sunburst_icon")  
  
 Dans un graphique en rayons, la hiérarchie est représentée par une série de cercles, avec le plus haut niveau de la hiérarchie au centre et les niveaux inférieurs à l’extérieur du centre.  Le niveau le plus bas de la hiérarchie est l’anneau extérieur.  
  
 ![ssrs_sunburst_example](../../reporting-services/report-design/media/ssrs-sunburst-example.png "ssrs_sunburst_example")  
  
### Pour insérer un graphique à rayon et configurer l’échantillon de données Adventureworks  
 **Remarque :** avant d’ajouter un graphique à votre rapport, créez une source de données et un jeu de données.  Pour des exemples de données et de requête, voir la section [Échantillon de données Adventureworks](#bkmk_sample_data) dans cette rubrique.  
  
1.  Cliquez avec le bouton droit sur l’aire de conception, cliquez sur **Insérer**, puis sur **Graphique**.  
  
     Sélectionnez Rayons ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon").  
  
     ![ssrs_insert_treemap_sunburst](../../reporting-services/report-design/media/ssrs-insert-treemap-sunburst.png "ssrs_insert_treemap_sunburst")  
  
2.  Repositionnez et redimensionnez le graphique.   Pour l’échantillon de données, un graphique de 5 pouces de large est un bon début.  
  
3.  Ajoutez les champs suivants à partir de l’échantillon de données :  
  
    |||  
    |-|-|  
    |![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")|**Values :** (Valeurs) LineTotal (Total de la ligne)<br /><br /> **Category Groups :** (Groupes de catégories ) ajoutez-les dans l’ordre suivant :<br /><br /> 1) CategoryName (Nom de catégorie)<br /><br /> 2) SubcategoryName (Nom de sous-catégorie)<br /><br /> 3) SalesReasonName (Nom du motif de vente)<br /><br /> **Series Groups :** (Groupes de séries) TerritoryName (Nom de territoire)|  
  
4.  Pour optimiser la taille de page pour la forme générale d’un graphique en rayons de soleil, positionnez la légende en bas.  
  
5.  Modifiez le titre par défaut du graphique en « Categorized Sales by Territory » (Ventes classées par territoire, avec motif de vente).  
  
6.  |||  
    |-|-|  
    |![ssrs_sunburst_linetotalproperties](../../reporting-services/report-design/media/ssrs-sunburst-linetotalproperties.png "ssrs_sunburst_linetotalproperties")|Pour ajouter les valeurs des groupes de catégories au graphique en rayons de soleil en tant qu’étiquettes, définissez la propriété d’étiquette comme suit : **Visible** = true et **UseValueAsLabel**=False.<br /><br /> Les valeurs d’étiquette qui s’affichent sont affectées par la taille de la police, la taille de la zone de graphique et la taille des différents rectangles.  Pour afficher d’autres étiquettes, définissez la propriété de police de l’étiquette LineTotal (Total de la ligne) sur 8 pt au lieu de la valeur par défaut de 10 pt.|  
  
7.  Si vous voulez utiliser une autre plage de couleurs, modifiez la propriété **Palette** du graphique.  
  
     ![ssrs_visualization_palette](../../reporting-services/report-design/media/ssrs-visualization-palette.png "ssrs_visualization_palette")  
  
 ![Icône de flèche utilisée avec le lien Retour en haut](../../analysis-services/instances/media/uparrow16x16.png "Icône de flèche utilisée avec le lien Retour en haut") [Dans cette rubrique](#bkmk_top)  
  
##  <a name="bkmk_sample_data"></a> Échantillon de données Adventureworks  
 Cette section présente un exemple de requête et les étapes de base pour la création d’une source de données et d’un jeu de données dans [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]. Si votre rapport contient déjà une source de données et le jeu de données, vous pouvez ignorer cette section.  
  
 La requête retourne des données de détail des ventes d’Adventureworks par secteur de vente, catégorie de produit, sous-catégorie de produit et motif de vente.  
  
1.  **Obtenir les données :**  
  
     La requête de cette section porte sur la base de données Adventureworks disponible en téléchargement  [Adventure Works 2014 Full Database Backup](https://msftdbprodsamples.codeplex.com/releases/view/125550).  
  
     Pour plus d’informations sur l’installation de la base de données, voir [How to install Adventure Works 2014 Sample Databases.pdf](https://msftdbprodsamples.codeplex.com/releases/view/125550)(Comment installer les échantillons de base de données Adventure Works 2014) (en anglais).  
  
2.  **Créer une source de données :**  
  
    1.  Dans le volet **Données du rapport**, cliquez avec le bouton droit sur **Sources de données**, puis cliquez sur **Ajouter une source de données**.  
  
    2.  Cliquez sur **Utiliser une connexion incorporée dans mon rapport**.  
  
    3.  Sélectionnez le type de connexion **Microsoft SQL Server**.  
  
    4.  Tapez la chaîne de connexion à votre serveur et à la base de données, par exemple :  
  
        ```  
        Data Source=[server name];Initial Catalog=AdventureWorks2014  
        ```  
  
    5.  Il est judicieux de vérifier avec le bouton **Tester la connexion** , puis de cliquer sur **OK**.  
  
     Pour plus d’informations, consultez [Ajouter et vérifier une connexion de données &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
3.  **Créer un jeu de données :**  
  
    -   Dans le volet **Données du rapport**, cliquez avec le bouton droit sur **Datasets**, puis cliquez sur **Ajouter un dataset**.  
  
    -   Cliquez sur **Utiliser un dataset incorporé dans mon rapport**.  
  
    -   Sélectionnez la source de données que vous avez créée aux étapes précédentes.  
  
    -   Sélectionnez le type de requête **Texte** , puis copiez et collez la requête suivante dans la zone de texte **Requête** :  
  
        ```  
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
  
    -   Cliquez sur **OK**.  
  
     Pour plus d’informations sur la création d’un dataset, consultez [Créer un dataset partagé ou incorporé &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).  
  
 ![Icône de flèche utilisée avec le lien Retour en haut](../../analysis-services/instances/media/uparrow16x16.png "Icône de flèche utilisée avec le lien Retour en haut") [Dans cette rubrique](#bkmk_top)  
  
## Voir aussi  
 [Mode création de dataset partagé &#40;Générateur de rapports&#41;](../../reporting-services/report-builder/shared-dataset-design-view-report-builder.md)   
 [Afficher des info-bulles dans une série &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md)   
 [Tutorial: Treemaps in Power BI (Didacticiel : graphiques de compartimentage dans Power BI)](https://support.powerbi.com/knowledgebase/articles/556200-tutorial-treemaps-in-power-bi)   
 [Treemap: Microsoft Research Data Visualization Apps for Office (Graphique de compartimentage : applications de visualisation de données de Microsoft Research pour Office)](http://research.microsoft.com/en-us/projects/msrdatavis/treemap.aspx)  
  
  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]
