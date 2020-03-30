---
title: 'Leçon 3 : Définir un dataset pour le rapport Table | Microsoft Docs'
description: Après avoir défini une source de données pour le rapport paginé, vous devez spécifier un dataset. Dans SQL Server Reporting Services, les données utilisées par les rapports sont contenues dans des datasets.
ms.date: 05/01/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 25c62e0cd615748a764937d6dc2b8e4c952e59a1
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75244305"
---
# <a name="lesson-3-define-a-dataset-for-the-table-report---sql-server-reporting-services"></a>Leçon 3 : Définir un dataset pour le rapport Table - SQL Server Reporting Services

Après avoir défini une source de données pour le rapport paginé, vous devez spécifier un dataset. Dans [!INCLUDE[ssrsnoversion](../includes/ssrsnoversion-md.md)], les données utilisées par les rapports sont contenues dans des *datasets*. Un dataset contient un pointeur vers la source des données et une requête que doivent utiliser le rapport, les champs calculées et les variables.

Utilisez le Concepteur de requêtes du Concepteur de rapports pour définir le dataset. Pour ce tutoriel, vous allez créer une requête qui récupère des informations de commande client à partir de la base de données AdventureWorks2016.

## <a name="define-a-transact-sql-query-for-report-data"></a>Définir une requête Transact-SQL pour les données du rapport  

1. Dans le volet **Données du rapport**, sélectionnez **Nouveau** > **Dataset**. La boîte de dialogue **Propriétés du dataset** s’ouvre avec la section **Requête** affichée.

    ![vs-data_set_properties_dialog](media/lesson-3-defining-a-dataset-for-the-table-report-reporting-services/vs-dataset-properties-dialog.png)

2. Dans la zone **Nom**, tapez « AdventureWorksDataset ».

3. En dessous, sélectionnez la case d’option **Utiliser un dataset incorporé dans mon rapport**.

4. Dans la zone de liste déroulante **Source de données**, sélectionnez AdventureWorks2016.

5. Pour **Type de requête**, sélectionnez la case d’option **Texte**.

6. Tapez ou copiez et collez la requête Transact-SQL suivante dans la zone de texte **Requête**.

    ```T-SQL
    SELECT
       soh.OrderDate AS [Date],
       soh.SalesOrderNumber AS [Order],
       pps.Name AS [Subcat],
       pp.Name as [Product],
       SUM(sd.OrderQty) AS [Qty],
       SUM(sd.LineTotal) AS [LineTotal]
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
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name,soh.SalesPersonID  
    HAVING ppc.Name = 'Clothing'
    ```

7. (Facultatif) Sélectionnez le bouton **Concepteur de requêtes**. La requête est affichée dans le *Concepteur de requêtes* textuel. Pour voir les résultats de la requête, sélectionnez le bouton **d’exécution** ![ssrs_querydesigner_run](media/ssrs-querydesigner-run.png) dans la barre d’outils du **Concepteur de requêtes**. Le dataset affiché contient six champs tirés de quatre tables de la base de données AdventureWorks2016. La requête utilise des fonctionnalités Transact-SQL telles que des alias. Par exemple, la table SalesOrderHeader est intitulée *soh*.

8. Sélectionnez **OK** pour quitter le **Concepteur de requêtes**.

9. Sélectionnez **OK** pour quitter la boîte de dialogue **Propriétés du dataset** .

Le volet **Données du rapport** affiche les champs et le dataset AdventureWorksDataset.

   ![ssrs_adventureworksdataset](media/ssrs-adventureworksdataset.png)

## <a name="next-steps"></a>Étapes suivantes

Vous venez de spécifier une requête qui permet de récupérer des données pour votre rapport. Maintenant, vous allez créer la disposition du rapport. Passez à la [Leçon 4 : Ajout d’une table au rapport &#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md).

## <a name="see-also"></a>Voir aussi

[Outils de conception de requêtes &#40;SSRS&#41;](../reporting-services/report-data/query-design-tools-ssrs.md)
[Type de connexion SQL Server &#40;SSRS&#41;](../reporting-services/report-data/sql-server-connection-type-ssrs.md)
[Tutoriel : Écriture d’instructions Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md)
