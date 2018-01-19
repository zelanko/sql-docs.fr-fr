---
title: "À l’aide des opérateurs PIVOT et UNPIVOT | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: PIVOT_TSQL
helpviewer_keywords:
- FROM clause, UNPIVOT operator
- unpivoting tables
- table pivoting [SQL Server]
- UNPIVOT operator
- crosstab query
- PIVOT operator
- rotating table-valued expressions
- pivoting tables
- FROM clause, PIVOT operator
- rotating columns
ms.assetid: 24ba54fc-98f7-4d35-8881-b5158aac1d66
caps.latest.revision: "35"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 5ee91826fe19979d411c10baf2ab4c60f225d0bb
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="from---using-pivot-and-unpivot"></a>DE - à l’aide des opérateurs PIVOT et UNPIVOT
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Vous pouvez utiliser la `PIVOT` et `UNPIVOT` des opérateurs relationnels pour modifier une expression de table dans une autre table. `PIVOT`fait pivoter une expression de table en activant les valeurs uniques d’une colonne dans l’expression en plusieurs colonnes dans la sortie et effectue des agrégations dans laquelle elles sont requises sur les valeurs de colonne restantes qui doivent figurer dans la sortie finale. `UNPIVOT`effectue l’opération inverse en appliquant une rotation de colonnes d’une expression de table incluse dans les valeurs de colonne.  
  
 La syntaxe de `PIVOT` fournit plus simple et plus lisible que la syntaxe qui peut-être être spécifiée dans le cas contraire dans une série complexe de `SELECT...CASE` instructions. Pour obtenir une description complète de la syntaxe de `PIVOT`, consultez [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md).  
  
## <a name="syntax"></a>Syntaxe  
 La syntaxe suivante indique comment utiliser le `PIVOT` opérateur.  
  
```  
SELECT <non-pivoted column>,  
    [first pivoted column] AS <column name>,  
    [second pivoted column] AS <column name>,  
    ...  
    [last pivoted column] AS <column name>  
FROM  
    (<SELECT query that produces the data>)   
    AS <alias for the source query>  
PIVOT  
(  
    <aggregation function>(<column being aggregated>)  
FOR   
[<column that contains the values that will become column headers>]   
    IN ( [first pivoted column], [second pivoted column],  
    ... [last pivoted column])  
) AS <alias for the pivot table>  
<optional ORDER BY clause>;  
```  

## <a name="remarks"></a>Notes  
Les identificateurs de colonne dans la `UNPIVOT` clause suivre le classement de catalogue. Pour [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], le classement est toujours `SQL_Latin1_General_CP1_CI_AS`. Pour [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] contenant-contenus partielle des bases de données, le classement est toujours `Latin1_General_100_CI_AS_KS_WS_SC`. Si la colonne est combinée avec d’autres colonnes, puis une clause collate (`COLLATE DATABASE_DEFAULT`) est nécessaire pour éviter les conflits.  

  
## <a name="basic-pivot-example"></a>Exemple PIVOT de base  
 L'exemple de code suivant produit un tableau à deux colonnes et quatre lignes.  
  
```  
USE AdventureWorks2014 ;  
GO  
SELECT DaysToManufacture, AVG(StandardCost) AS AverageCost   
FROM Production.Product  
GROUP BY DaysToManufacture;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 DaysToManufacture AverageCost
 ----------------- -----------
 0                 5.0885
 1                 223.88
 2                 359.1082
 4                 949.4105
 ```
  
 Aucun produit n'est défini avec trois `DaysToManufacture`.  
  
 Le code suivant affiche le même résultat, croisé dynamiquement pour que les valeurs `DaysToManufacture` deviennent les en-têtes de colonne. Une colonne est fournie pour trois `[3]` jours même si les résultats sont `NULL`.  
  
```  
-- Pivot table with one row and five columns  
SELECT 'AverageCost' AS Cost_Sorted_By_Production_Days,   
[0], [1], [2], [3], [4]  
FROM  
(SELECT DaysToManufacture, StandardCost   
    FROM Production.Product) AS SourceTable  
PIVOT  
(  
AVG(StandardCost)  
FOR DaysToManufacture IN ([0], [1], [2], [3], [4])  
) AS PivotTable;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
Cost_Sorted_By_Production_Days 0           1           2           3           4         
------------------------------ ----------- ----------- ----------- ----------- -----------
AverageCost                    5.0885      223.88      359.1082    NULL        949.4105
```
  
## <a name="complex-pivot-example"></a>Exemple PIVOT complexe  
 Un scénario classique consiste à utiliser l'opérateur `PIVOT` pour générer des rapports à tabulation croisée afin de synthétiser des données. Par exemple, supposons que vous souhaitiez interroger la table `PurchaseOrderHeader` de l'exemple de base de données `AdventureWorks2014` pour déterminer le nombre de commandes traitées par certains employés. La requête suivante fournit ce rapport, ventilé par fournisseur.  
  
```  
USE AdventureWorks2014;  
GO  
SELECT VendorID, [250] AS Emp1, [251] AS Emp2, [256] AS Emp3, [257] AS Emp4, [260] AS Emp5  
FROM   
(SELECT PurchaseOrderID, EmployeeID, VendorID  
FROM Purchasing.PurchaseOrderHeader) p  
PIVOT  
(  
COUNT (PurchaseOrderID)  
FOR EmployeeID IN  
( [250], [251], [256], [257], [260] )  
) AS pvt  
ORDER BY pvt.VendorID;  
```  
  
 Voici un jeu de résultats partiel.  
  
```
VendorID    Emp1        Emp2        Emp3        Emp4        Emp5  
----------- ----------- ----------- ----------- ----------- -----------
1492        2           5           4           4           4
1494        2           5           4           5           4
1496        2           4           4           5           5
1498        2           5           4           4           4
1500        3           4           4           5           4
```
  
 Les résultats retournés par cette instruction de sous-sélection sont croisés dynamiquement sur la colonne `EmployeeID`.  
  
```  
SELECT PurchaseOrderID, EmployeeID, VendorID  
FROM PurchaseOrderHeader;  
```  
  
 Cela signifie que les valeurs uniques retournées par la colonne `EmployeeID` deviennent elles-mêmes des champs dans l'ensemble de résultats final. Par conséquent, il existe une colonne pour chaque numéro `EmployeeID` spécifié dans la clause PIVOT : dans ce cas les employés `164`, `198`, `223`, `231` et `233`. La colonne `PurchaseOrderID` sert de colonne de valeur par rapport à laquelle les colonnes retournées dans la sortie finale (colonnes de regroupement) sont regroupées. Dans ce cas, les colonnes de regroupement sont agrégées par la fonction `COUNT`. Un message d'avertissement apparaît indiquant qu'aucune valeur NULL figurant dans la colonne `PurchaseOrderID` n'a été prise en compte pour le calcul de la valeur `COUNT` de chaque employé.  
  
> [!IMPORTANT]  
>  Lorsque les fonctions d’agrégation sont utilisées avec `PIVOT`, la présence de valeurs null dans la colonne de valeur ne sont pas considérés lors du calcul d’une agrégation.  
  
 `UNPIVOT`effectue pratiquement l’opération inverse de `PIVOT`, en appliquant une rotation de colonnes dans les lignes. Supposons que la table générée dans l'exemple précédent soit stockée dans la base de données sous le nom `pvt` et que vous souhaitiez transformer les identificateurs de colonne `Emp1`, `Emp2`, `Emp3`, `Emp4` et `Emp5` en valeurs de ligne correspondant à un fournisseur particulier. Cela signifie que vous devez identifier deux colonnes supplémentaires. La colonne qui doit contenir les valeurs de colonne transformées (`Emp1`, `Emp2`,...) est la colonne `Employee` tandis que la colonne destinée à contenir les valeurs figurant actuellement dans les colonnes subissant la transformation est la colonne `Orders`. Ces colonnes correspondent à la *pivot_column* et *value_column*, respectivement, dans le [!INCLUDE[tsql](../../includes/tsql-md.md)] définition. La requête est la suivante.  
  
```  
-- Create the table and insert values as portrayed in the previous example.  
CREATE TABLE pvt (VendorID int, Emp1 int, Emp2 int,  
    Emp3 int, Emp4 int, Emp5 int);  
GO  
INSERT INTO pvt VALUES (1,4,3,5,4,4);  
INSERT INTO pvt VALUES (2,4,1,5,5,5);  
INSERT INTO pvt VALUES (3,4,3,5,4,4);  
INSERT INTO pvt VALUES (4,4,2,5,5,4);  
INSERT INTO pvt VALUES (5,5,1,5,5,5);  
GO  
-- Unpivot the table.  
SELECT VendorID, Employee, Orders  
FROM   
   (SELECT VendorID, Emp1, Emp2, Emp3, Emp4, Emp5  
   FROM pvt) p  
UNPIVOT  
   (Orders FOR Employee IN   
      (Emp1, Emp2, Emp3, Emp4, Emp5)  
)AS unpvt;  
GO  
```  
  
 Voici un jeu de résultats partiel.  
  
```
VendorID    Employee    Orders
----------- ----------- ------
1            Emp1       4
1            Emp2       3 
1            Emp3       5
1            Emp4       4
1            Emp5       4
2            Emp1       4
2            Emp2       1
2            Emp3       5
2            Emp4       5
2            Emp5       5
...
```
  
 Notez que `UNPIVOT` n’est pas l’inverse exact du `PIVOT`. `PIVOT`effectue une agrégation et, donc, fusionne possible plusieurs lignes en une seule ligne dans la sortie. `UNPIVOT`ne se reproduit pas le résultat d’expression de table à la table d’origine, car les lignes ont été fusionnées. En outre, valeurs null dans l’entrée de `UNPIVOT` disparaissent dans la sortie, alors qu’il a peut-être des valeurs null d’origine de l’entrée avant la `PIVOT` opération.  
  
 Le `Sales.vSalesPersonSalesByFiscalYears` afficher dans le [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] exemple de base de données utilise `PIVOT` pour retourner le total des ventes de chaque vendeur, par exercice comptable. Créer un script de la vue dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans **l’Explorateur d’objets**, recherchez celle-ci dans le **vues** dossier pour le [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] base de données. Cliquez sur le nom de la vue, puis **mode Script en tant que**.  
  
## <a name="see-also"></a>Voir aussi  
 [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)   
 [CASE (Transact-SQL)](../../t-sql/language-elements/case-transact-sql.md)  
  
  
