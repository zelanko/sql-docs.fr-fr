---
title: Créer des fonctions définies par l’utilisateur (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SCHEMABINDING clause
- schema-bound functions [SQL Server]
- user-defined functions [SQL Server], creating
- CREATE FUNCTION statement
- valid statements [SQL Server]
ms.assetid: f0d5dd10-73fd-4e05-9177-07f56552bdf7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 37a6846d8c185549bd6c54f32cb5ab02eb564d1d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68211710"
---
# <a name="create-user-defined-functions-database-engine"></a>Créer des fonctions définies par l'utilisateur (moteur de base de données)
  Cette rubrique décrit comment créer une fonction définie par l'utilisateur dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour créer une fonction définie par l'utilisateur :**  
  
     [Créer une fonction scalaire](#Scalar)  
  
     [Créer une fonction table](#TVF)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   Les fonctions définies par l'utilisateur ne permettent pas d'exécuter des actions qui modifient l'état des bases de données.  
  
-   Les fonctions définies par l'utilisateur ne peuvent pas contenir de clause OUTPUT INTO avec une table comme cible.  
  
-   Les fonctions définies par l'utilisateur ne peuvent pas renvoyer plusieurs jeux de résultats. Utilisez une procédure stockée si vous devez renvoyer plusieurs jeux de résultats.  
  
-   La gestion des erreurs est restreinte dans une fonction définie par l'utilisateur. Une fonction UDF ne prend pas en charge les tentatives... CATCH @ERROR ou RAISERROR.  
  
-   Les fonctions définies par l'utilisateur ne peuvent pas appeler une procédure stockée, mais elles peuvent appeler une procédure stockée étendue.  
  
-   Les fonctions définies par l'utilisateur ne peuvent pas utiliser des tables SQL dynamiques ou temporaires. Les variables de table sont autorisées.  
  
-   Les instructions SET ne sont pas autorisées dans une fonction définie par l'utilisateur.  
  
-   La clause FOR XML n'est pas autorisée.  
  
-   Les fonctions définies par l'utilisateur peuvent être imbriquées ; en d'autres termes, une fonction définie par l'utilisateur peut en appeler une autre. Le niveau d'imbrication est incrémenté lorsque la fonction appelée commence à s'exécuter, et décrémenté lorsque l'exécution est terminée. Les fonctions définies par l'utilisateur peuvent être imbriquées jusqu'à 32 niveaux. Le dépassement des niveaux d'imbrication maximum autorisés, provoque l'échec de la totalité de la chaîne de fonctions appelantes. Toute référence à du code managé depuis une fonction Transact-SQL définie par l'utilisateur compte pour un niveau parmi les 32 niveaux d'imbrication possibles. Les méthodes appelées à partir du code managé ne comptent pas par rapport à cette limite.  
  
-   Les instructions Service Broker suivantes ne peuvent pas être incluses dans la définition d'une fonction Transact-SQL définie par l'utilisateur :  
  
    -   BEGIN DIALOG CONVERSATION  
  
    -   END CONVERSATION  
  
    -   GET CONVERSATION GROUP  
  
    -   MOVE CONVERSATION  
  
    -   RECEIVE  
  
    -   SEND  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Nécessite l'autorisation CREATE FUNCTION dans la base de données et l'autorisation ALTER sur le schéma dans lequel la fonction est en cours de création. Si la fonction spécifie un type défini par l'utilisateur, elle requiert l'autorisation EXECUTE sur le type.  
  
##  <a name="scalar-functions"></a><a name="Scalar"></a>Fonctions scalaires  
 L'exemple suivant illustre la création d'une fonction scalaire à instructions multiples dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] . À partir d'une valeur d'entrée unique ( `ProductID`), la fonction retourne une valeur de donnée unique, en l'occurrence, la quantité totale du produit spécifié en stock.  
  
```  
IF OBJECT_ID (N'dbo.ufnGetInventoryStock', N'FN') IS NOT NULL  
    DROP FUNCTION ufnGetInventoryStock;  
GO  
CREATE FUNCTION dbo.ufnGetInventoryStock(@ProductID int)  
RETURNS int   
AS   
-- Returns the stock level for the product.  
BEGIN  
    DECLARE @ret int;  
    SELECT @ret = SUM(p.Quantity)   
    FROM Production.ProductInventory p   
    WHERE p.ProductID = @ProductID   
        AND p.LocationID = '6';  
     IF (@ret IS NULL)   
        SET @ret = 0;  
    RETURN @ret;  
END;  
GO  
  
```  
  
 Dans l'exemple suivant, la fonction `ufnGetInventoryStock` est utilisée pour déterminer la quantité en stock des produits dont la valeur `ProductModelID` est comprise entre 75 et 80.  
  
```  
SELECT ProductModelID, Name, dbo.ufnGetInventoryStock(ProductID)AS CurrentSupply  
FROM Production.Product  
WHERE ProductModelID BETWEEN 75 and 80;  
  
```  
  
##  <a name="table-valued-functions"></a><a name="TVF"></a>Fonctions table  
 L'exemple suivant crée une fonction table en ligne dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] . À partir d'un paramètre d'entrée unique (storeID), la fonction retourne les colonnes `ProductID`, `Name`, ainsi que le total cumulé des ventes ( `YTD Total` ) pour chaque produit vendu au magasin du client.  
  
```  
IF OBJECT_ID (N'Sales.ufn_SalesByStore', N'IF') IS NOT NULL  
    DROP FUNCTION Sales.ufn_SalesByStore;  
GO  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
  
```  
  
 L'exemple suivant appelle la fonction et spécifie l'ID client 602.  
  
```  
SELECT * FROM Sales.ufn_SalesByStore (602);  
  
```  
  
 L'exemple suivant crée une fonction table dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] . À partir d'un paramètre d'entrée unique, `EmployeeID` , la fonction retourne la liste de tous les employés qui sont sous la responsabilité directe ou indirecte de l'employé spécifié. La fonction est ensuite appelée en spécifiant l'ID d'employé 19.  
  
```  
IF OBJECT_ID (N'dbo.ufn_FindReports', N'TF') IS NOT NULL  
    DROP FUNCTION dbo.ufn_FindReports;  
GO  
CREATE FUNCTION dbo.ufn_FindReports (@InEmpID INTEGER)  
RETURNS @retFindReports TABLE   
(  
    EmployeeID int primary key NOT NULL,  
    FirstName nvarchar(255) NOT NULL,  
    LastName nvarchar(255) NOT NULL,  
    JobTitle nvarchar(50) NOT NULL,  
    RecursionLevel int NOT NULL  
)  
--Returns a result set that lists all the employees who report to the   
--specific employee directly or indirectly.*/  
AS  
BEGIN  
WITH EMP_cte(EmployeeID, OrganizationNode, FirstName, LastName, JobTitle, RecursionLevel) -- CTE name and columns  
    AS (  
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, 0 -- Get the initial list of Employees for Manager n  
        FROM HumanResources.Employee e   
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        WHERE e.BusinessEntityID = @InEmpID  
        UNION ALL  
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, RecursionLevel + 1 -- Join recursive member to anchor  
        FROM HumanResources.Employee e   
            INNER JOIN EMP_cte  
            ON e.OrganizationNode.GetAncestor(1) = EMP_cte.OrganizationNode  
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        )  
-- copy the required columns to the result of the function   
   INSERT @retFindReports  
   SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
   FROM EMP_cte   
   RETURN  
END;  
GO  
-- Example invocation  
SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
FROM dbo.ufn_FindReports(1);  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions définies par l’utilisateur](user-defined-functions.md)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql)  
  
  
