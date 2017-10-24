---
title: AYANT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9bff75a84689090f6e416db052a2561e57fa98a6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="select---having-transact-sql"></a>SELECT - ayant (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Indique un critère de recherche pour un groupe ou une fonction d'agrégation. HAVING ne peut être utilisé qu'avec l'instruction SELECT. HAVING est généralement utilisé dans une clause GROUP BY. Lorsque GROUP BY n'est pas utilisé, HAVING se comporte comme une clause WHERE.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ HAVING <search condition> ]  
```  
  
## <a name="arguments"></a>Arguments  
\<search_condition > Spécifie la condition de recherche pour le groupe ou l’agrégat répondre aux.  
  
 Le **texte**, **image**, et **ntext** des types de données ne peut pas être utilisés dans une clause HAVING.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise une clause `HAVING` simple, extrait le total de chaque `SalesOrderID` depuis la table `SalesOrderDetail` qui dépasse les `$100000.00`.  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT SalesOrderID, SUM(LineTotal) AS SubTotal  
FROM Sales.SalesOrderDetail  
GROUP BY SalesOrderID  
HAVING SUM(LineTotal) > 100000.00  
ORDER BY SalesOrderID ;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L’exemple suivant utilise un `HAVING` pour extraire le total pour chaque clause `SalesAmount` à partir de la `FactInternetSales` table lorsque la `OrderDateKey` correspond à l’année 2004 ou version ultérieure.  
  
```  
-- Uses AdventureWorks  
  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales   
FROM FactInternetSales  
GROUP BY OrderDateKey   
HAVING SUM(SalesAmount) > 80000  
ORDER BY OrderDateKey;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [GROUP BY &#40; Transact-SQL &#41;](../../t-sql/queries/select-group-by-transact-sql.md)   
 [OÙ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  


