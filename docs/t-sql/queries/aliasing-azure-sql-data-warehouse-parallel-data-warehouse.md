---
title: "Alias (entrepôt de données SQL Azure, Parallel Data Warehouse) | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b3a5c74-05cf-4385-8ee6-6176d003cb8a
caps.latest.revision: "11"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9b5d66e6a78de33403961b1f991aab34124e862a
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="aliasing-azure-sql-data-warehouse-parallel-data-warehouse"></a>Alias (entrepôt de données SQL Azure, entrepôt de données en parallèle)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Les alias permettent la substitution temporaire d’une chaîne courte et facile à mémoriser à la place d’un nom de table ou une colonne dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] [!INCLUDE[DWsql](../../includes/dwsql-md.md)] requêtes. Alias de table sont souvent utilisés dans les requêtes de jointure, car la syntaxe de jointure requiert que les noms d’objet complet lors du référencement de colonnes.  
  
 Alias doivent être conformes aux règles d’affectation des noms d’objet de mots simples. Pour plus d’informations, consultez « Règles d’affectation de noms d’objet » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]. Alias ne peut pas contenir des espaces et ne peut pas être mis entre guillemets simples ou doubles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
object_source [ AS ] alias  
```  
  
## <a name="arguments"></a>Arguments  
 *object_source*  
 Le nom de la table source ou de la colonne.  
  
 AS  
 Une préposition alias facultatif. Lorsque vous travaillez avec un alias de variable de plage, le mot clé AS est interdite.  
  
 *alias*  
 Le nom de référence temporaire souhaitée pour la table ou la colonne. N’importe quel nom d’objet valide peut être utilisé. Pour plus d’informations, consultez « Règles d’affectation de noms d’objet » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L’exemple suivant montre une requête avec plusieurs jointures. Alias de table et de colonne sont illustrées dans cet exemple.  
  
-   Alias de colonne : Les deux colonnes et expressions impliquant des colonnes dans la liste select sont des alias dans cet exemple. `SalesTerritoryRegion AS SalesTR`montre un alias de colonne simple. `Sum(SalesAmountQuota) AS TotalSales`montre comment  
  
-   Alias de table : `dbo.DimSalesTerritory AS st` illustre la création de la `st` alias pour le `dbo.DimSalesTerritory` table.  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) AS TotalSales, SalesTerritoryRegion AS SalesTR,  
    RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) AS RankResult  
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.FactSalesQuota AS sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory AS st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
  
```  
  
 Le mot clé AS peut être exclu, comme illustré ci-dessous, mais il est souvent inclus pour une meilleure lisibilité.  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) TotalSales, SalesTerritoryRegion SalesTR,  
RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) RankResult  
FROM dbo.DimEmployee e  
INNER JOIN dbo.FactSalesQuota sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  
  
  
