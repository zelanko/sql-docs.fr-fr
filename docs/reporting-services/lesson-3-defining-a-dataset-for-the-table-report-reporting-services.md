---
title: 'Leçon 3 : définition d’un jeu de données destiné à un rapport de table (Reporting Services) | Microsoft Docs'
ms.date: 05/23/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bec3fb7737cd8621952dc71cbad80c0af5159151
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56292921"
---
# <a name="lesson-3-defining-a-dataset-for-the-table-report-reporting-services"></a>Leçon 3 : définition d'un jeu de données destiné à un rapport de table (Reporting Services)
Après avoir défini une source de données, vous devez spécifier un dataset. Dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], les données utilisées par les rapports sont contenues dans des *datasets*. Les datasets contiennent un pointeur qui renvoient à la source des données, la requête que doit utiliser le rapport ainsi que des champs et variables calculées.  
  
Utilisez le Concepteur de requêtes du Concepteur de rapports pour définir le dataset. Au cours de ce didacticiel, vous allez créer une requête qui extrait les informations sur les bons de commande depuis la base de données [!INCLUDE [ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] .  
  
### <a name="to-define-a-transact-sql-query-for-report-data"></a>Pour définir une requête Transact-SQL pour les données du rapport  
  
1.  Dans le volet **Données de rapport**, cliquez sur **Nouveau**, puis sur **Dataset...**. La boîte de dialogue **Propriétés du dataset** s'ouvre.  
  
2.  Dans la zone **Nom** , tapez **AdventureWorksDataset**.  
  
3.  Cliquez sur **Utiliser un dataset incorporé dans mon rapport**.  
  
4.  Sélectionnez la source de données que vous avez créée dans la leçon précédente, [!INCLUDE [ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)].   
5. Sélectionnez **Texte** comme **Type de requête**.  
  
6.  Tapez ou copiez et collez la requête Transact-SQL ci-après dans la zone **Requête** .  
  
    ```  
    SELECT   
       soh.OrderDate AS [Date],   
       soh.SalesOrderNumber AS [Order],   
       pps.Name AS Subcat, pp.Name as Product,    
       SUM(sd.OrderQty) AS Qty,  
       SUM(sd.LineTotal) AS LineTotal  
    FROM Sales.SalesPerson sp   
       INNER JOIN Sales.SalesOrderHeader AS soh   
          ON sp.BusinessEntityID = soh.SalesPersonID  
       INNER JOIN Sales.SalesOrderDetail AS sd   
          ON sd.SalesOrderID = soh.SalesOrderID  
       INNER JOIN Production.Product AS pp   
          ON sd.ProductID = pp.ProductID  
       INNER JOIN Production.ProductSubcategory AS pps   
          ON pp.ProductSubcategoryID = pps.ProductSubcategoryID  
       INNER JOIN Production.ProductCategory AS ppc   
          ON ppc.ProductCategoryID = pps.ProductCategoryID  
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name,   
       soh.SalesPersonID  
    HAVING ppc.Name = 'Clothing'  
    ```  
  
7.  (Facultatif) Cliquez sur le bouton **Concepteur de requêtes** . La requête est affichée dans le Concepteur de requêtes textuel. Vous pouvez utiliser le concepteur de requêtes graphique en cliquant sur l’option **Modifier en tant que texte**. Pour afficher les résultats de la requête, cliquez sur le bouton d’exécution ![ssrs_querydesigner_run](../reporting-services/media/ssrs-querydesigner-run.png)  qui figure dans la barre d’outils du Concepteur de requêtes.  
  
    Vous pouvez consulter les données contenues dans six champs à partir de quatre tables différentes de la base de données [!INCLUDE [ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] . La requête utilise des fonctionnalités Transact-SQL telles que des alias. Par exemple, la table SalesOrderHeader est intitulée *soh*.  
  
8.  Cliquez sur **OK** pour quitter le Concepteur de requêtes.  
  
9.  Cliquez sur **OK** pour quitter la boîte de dialogue **Propriétés du dataset** .  
  
    Les champs et votre dataset **AdventureWorksDataset** s’affichent dans le volet des données de rapport.  
    ![ssrs_adventureworksdataset](../reporting-services/media/ssrs-adventureworksdataset.png)  
  
## <a name="next-task"></a>Tâche suivante  
Vous venez de spécifier une requête qui permet d'extraire les données pour votre rapport. Vous allez ensuite créer la disposition du rapport. Consultez la [leçon 4 : Ajout d’une table au rapport &#40;Reporting Services&#41;](../reporting-services/lesson-4-adding-a-table-to-the-report-reporting-services.md).  
  
## <a name="see-also"></a> Voir aussi  
[Outils de création de requêtes &#40;SSRS&#41;](../reporting-services/report-data/query-design-tools-ssrs.md)  
[Type de connexion SQL Server &#40;SSRS&#41;](../reporting-services/report-data/sql-server-connection-type-ssrs.md)  
[Didacticiel : Écriture d’instructions Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
  

