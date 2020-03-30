---
title: HAVING (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/21/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HAVING
- HAVING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restricting conditions for result set
- search conditions [SQL Server], HAVING clause
- HAVING clause
- HAVING clause, about HAVING clause
ms.assetid: 55650709-001e-42f4-902f-ead09a3c34af
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2a574e3f7348c4641665b067193c54604145386c
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "76315609"
---
# <a name="select---having-transact-sql"></a>SELECT - HAVING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Indique un critère de recherche pour un groupe ou une fonction d'agrégation. HAVING ne peut être utilisé qu'avec l'instruction SELECT. HAVING est généralement utilisé avec une clause GROUP BY. Sans la clause GROUP BY, un seul groupe agrégé est implicitement utilisé.   
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ HAVING <search condition> ]  
```  
  
## <a name="arguments"></a>Arguments  
\<search_condition> spécifie un ou plusieurs prédicats devant être remplis pour les groupes et/ou agrégats. Pour plus d’informations sur les prédicats et conditions de recherche, consultez [Condition de recherche &#40;Transact-SQL&#41;](../../t-sql/queries/search-condition-transact-sql.md).  
  
 Les types de données **text**, **image** et **ntext** ne peuvent pas être utilisés avec une clause HAVING.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise une clause `HAVING` simple, extrait le total de chaque `SalesOrderID` depuis la table `SalesOrderDetail` qui dépasse les `$100000.00`.  
  
```sql
USE AdventureWorks2012 ;  
GO  
SELECT SalesOrderID, SUM(LineTotal) AS SubTotal  
FROM Sales.SalesOrderDetail  
GROUP BY SalesOrderID  
HAVING SUM(LineTotal) > 100000.00  
ORDER BY SalesOrderID ;  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L’exemple suivant utilise une clause `HAVING` pour récupérer le `SalesAmount` total qui dépasse `80000` pour chaque `OrderDateKey` de la table `FactInternetSales`.  
  
```sql
-- Uses AdventureWorks  
  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales   
FROM FactInternetSales  
GROUP BY OrderDateKey   
HAVING SUM(SalesAmount) > 80000  
ORDER BY OrderDateKey;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [GROUP BY &#40;Transact-SQL&#41;](../../t-sql/queries/select-group-by-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  
  
  

