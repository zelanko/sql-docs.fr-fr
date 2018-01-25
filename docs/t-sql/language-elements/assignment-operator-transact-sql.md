---
title: "= (Opérateur d’assignation) (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- operators [Transact-SQL], assignment
- assignment operators [Transact-SQL]
- headings [SQL Server columns]
- relationships [SQL Server], assignment operators
- column headings [SQL Server]
ms.assetid: c3040db6-21d6-40ac-a783-82c98ec006cc
caps.latest.revision: "29"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c21e0e9525a68c423cbf273d3a5a8ba3aa3da04a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="-assignment-operator-transact-sql"></a>= (Opérateur d’assignation) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Le signe égal (=) est le seul opérateur d'affectation de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Dans l'exemple qui suit, la variable `@MyCounter` est créée, puis l'opérateur d'affectation attribue à `@MyCounter` une valeur renvoyée par une expression.  
  
```  
DECLARE @MyCounter INT;  
SET @MyCounter = 1;  
```  
  
 L'opérateur d'affectation peut également être utilisé pour définir la relation entre l'en-tête d'une colonne et l'expression définissant les valeurs de la colonne. L'exemple suivant affiche les en-têtes de colonne `FirstColumnHeading` et `SecondColumnHeading`. La chaîne `xyz` s'affiche dans l'en-tête de colonne `FirstColumnHeading` pour toutes les lignes. Ensuite, chaque ID de produit extrait de la table `Product` est présenté dans l'en-tête de colonne `SecondColumnHeading`.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstColumnHeading = 'xyz',  
       SecondColumnHeading = ProductID  
FROM Production.Product;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Operators &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Compound, opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
