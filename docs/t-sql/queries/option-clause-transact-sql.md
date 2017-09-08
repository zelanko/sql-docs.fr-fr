---
title: "Clause de l’OPTION (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPTION clause
- OPTION_TSQL
- OPTION
- OPTION_clause_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- clauses [SQL Server], OPTION
- OPTION clause
ms.assetid: f47e2f3f-9302-4711-9d66-16b1a2a7ffe3
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b5457a572985c9a83984efbe9ce90811e22cf2d4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="option-clause-transact-sql"></a>Clause OPTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Spécifie que l'indicateur de requête indiqué doit être utilisé dans l'ensemble de la requête. Chaque indicateur de requête ne peut être spécifié qu'une seule fois, bien que plusieurs indicateurs de requête soient autorisés. Une seule clause OPTION peut être spécifiée avec l'instruction.  
  
 Cette clause peut être spécifiée dans les instructions SELECT, DELETE, UPDATE et MERGE.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
[ OPTION ( <query_hint> [ ,...n ] ) ]   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
OPTION ( <query_option> [ ,...n ] )  
  
<query_option> ::=  
    LABEL = label_name |  
    <query_hint>  
  
<query_hint> ::=  
    HASH JOIN   
    | LOOP JOIN   
    | MERGE JOIN  
    | FORCE ORDER  
    | { FORCE | DISABLE } EXTERNALPUSHDOWN  
```  
  
## <a name="arguments"></a>Arguments  
 *query_hint*  
 Mots clés spécifiant les indicateurs d'optimiseur utilisés pour personnaliser la façon dont le moteur de base de données traite l'instruction. Pour plus d’informations, consultez [Indicateurs de requête &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-an-option-clause-with-a-group-by-clause"></a>A. À l’aide d’une clause OPTION avec une clause GROUP BY  
 L'exemple suivant montre comment la clause `OPTION` est utilisée avec une clause `GROUP BY`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, OrderQty, SUM(LineTotal) AS Total  
FROM Sales.SalesOrderDetail  
WHERE UnitPrice < $5.00  
GROUP BY ProductID, OrderQty  
ORDER BY ProductID, OrderQty  
OPTION (HASH GROUP, FAST 10);  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-select-statement-with-a-label-in-the-option-clause"></a>B. Instruction SELECT avec une étiquette dans la clause OPTION  
 L’exemple suivant montre un simple [!INCLUDE[ssDW](../../includes/ssdw-md.md)] instruction SELECT avec une étiquette dans la clause OPTION.  
  
```  
-- Uses AdventureWorks  
  
SELECT * FROM FactResellerSales  
  OPTION ( LABEL = 'q17' );  
```  
  
### <a name="c-select-statement-with-a-query-hint-in-the-option-clause"></a>C. Instruction SELECT avec un indicateur de requête dans la clause OPTION  
 L’exemple suivant montre une instruction SELECT qui utilise un indicateur de requête HASH JOIN dans la clause OPTION.  
  
```  
-- Uses AdventureWorks  
  
SELECT COUNT (*) FROM dbo.DimCustomer a  
INNER JOIN dbo.FactInternetSales b   
ON (a.CustomerKey = b.CustomerKey)  
OPTION (HASH JOIN);  
```  
  
### <a name="d-select-statement-with-a-label-and-multiple-query-hints-in-the-option-clause"></a>D. Instruction SELECT avec une étiquette et plusieurs indicateurs de requête dans la clause OPTION  
 L’exemple suivant est un [!INCLUDE[ssDW](../../includes/ssdw-md.md)] instruction SELECT qui contient une étiquette et plusieurs indicateurs de requête. Lorsque la requête est exécutée sur les nœuds de calcul, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] appliquera une jointure de hachage ou une jointure de fusion, en fonction de la stratégie qui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] décide est le plus approprié.  
  
```  
-- Uses AdventureWorks  
  
SELECT COUNT (*) FROM dbo.DimCustomer a  
INNER JOIN dbo.FactInternetSales b   
ON (a.CustomerKey = b.CustomerKey)  
OPTION ( Label = 'CustJoin', HASH JOIN, MERGE JOIN);  
```  
  
### <a name="e-using-a-query-hint-when-querying-a-view"></a>E. À l’aide d’un indicateur de requête lors de l’interrogation d’une vue  
 L’exemple suivant crée une vue nommée CustomerView et utilise ensuite un indicateur de requête HASH JOIN dans une requête qui fait référence à une vue et une table.  
  
```  
-- Uses AdventureWorks  
  
CREATE VIEW CustomerView  
AS  
SELECT CustomerKey, FirstName, LastName FROM ssawPDW..DimCustomer;  
  
SELECT COUNT (*) FROM dbo.CustomerView a  
INNER JOIN dbo.FactInternetSales b  
ON (a.CustomerKey = b.CustomerKey)  
OPTION (HASH JOIN);  
  
DROP VIEW CustomerView;  
  
```  
  
### <a name="f-query-with-a-subselect-and-a-query-hint"></a>F. Requête avec une instruction de sous-sélection et un indicateur de requête  
 L’exemple suivant montre une requête qui contient une instruction de sous-sélection et un indicateur de requête. L’indicateur de requête est appliqué globalement. Indicateurs de requête ne sont pas autorisés à ajouter à l’instruction de sous-sélection.  
  
```  
-- Uses AdventureWorks  
  
CREATE VIEW CustomerView AS  
SELECT CustomerKey, FirstName, LastName FROM ssawPDW..DimCustomer;  
  
SELECT * FROM (  
SELECT COUNT (*) AS a FROM dbo.CustomerView a  
INNER JOIN dbo.FactInternetSales b  
ON ( a.CustomerKey = b.CustomerKey )) AS t  
OPTION (HASH JOIN);  
```  
  
### <a name="g-force-the-join-order-to-match-the-order-in-the-query"></a>G. Forcer l’ordre de jointure à l’ordre dans la requête  
 L’exemple suivant utilise l’indicateur ORDER de FORCE pour forcer le plan de requête pour utiliser l’ordre de jointure spécifié par la requête. Cela permet d’améliorer les performances de certaines requêtes ; toutes les requêtes.  
  
```  
-- Uses AdventureWorks  
  
-- Obtain partition numbers, boundary values, boundary value types, and rows per boundary  
-- for the partitions in the ProspectiveBuyer table of the ssawPDW database.  
SELECT sp.partition_number, prv.value AS boundary_value, lower(sty.name) AS boundary_value_type, sp.rows   
FROM sys.tables st JOIN sys.indexes si ON st.object_id = si.object_id AND si.index_id <2  
JOIN sys.partitions sp ON sp.object_id = st.object_id AND sp.index_id = si.index_id  
JOIN sys.partition_schemes ps ON ps.data_space_id = si.data_space_id   
JOIN sys.partition_range_values prv ON prv.function_id = ps.function_id   
JOIN sys.partition_parameters pp ON pp.function_id = ps.function_id   
JOIN sys.types sty ON sty.user_type_id = pp.user_type_id AND prv.boundary_id = sp.partition_number   
WHERE st.object_id = (SELECT object_id FROM sys.objects WHERE name = 'FactResellerSales')   
ORDER BY sp.partition_number  
OPTION ( FORCE ORDER )  
;  
```  
  
### <a name="h-using-externalpushdown"></a>H. À l’aide de EXTERNALPUSHDOWN  
 L’exemple suivant force la poussée vers le bas de la clause WHERE à la tâche MapReduce sur la table Hadoop externe.  
  
```  
SELECT ID FROM External_Table_AS A   
WHERE ID < 1000000  
OPTION (FORCE EXTERNALPUSHDOWN);  
```  
  
 L’exemple suivant empêche la poussée vers le bas de la clause WHERE à la tâche MapReduce sur la table Hadoop externe. Toutes les lignes sont retournées à PDW où la clause WHERE est appliquée.  
  
```  
SELECT ID FROM External_Table_AS A   
WHERE ID < 10  
OPTION (DISABLE EXTERNALPUSHDOWN);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Indicateurs de &#40; Transact-SQL &#41;](../../t-sql/queries/hints-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [FUSION &#40; Transact-SQL &#41;](../../t-sql/statements/merge-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)  
  
  


