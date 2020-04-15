---
title: Appels de fonction scalar Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function calls
ms.assetid: 10cb4dcf-4cd8-4a56-8725-d080bd3ffe47
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 349599a51b2996f419e6c8656a71bc9e30146542
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304260"
---
# <a name="scalar-function-calls"></a>Appels de fonctions scalaires
Les fonctions Scalar retournent une valeur pour chaque rangée. Par exemple, la fonction scalaire de valeur absolue prend une colonne numérique comme argument et renvoie la valeur absolue de chaque valeur dans la colonne. La séquence d’évasion pour appeler une fonction scalaire est  
  
 **fonction**_scalaire_ **}** de fn    
  
 où *la fonction scalaire* est l’une des fonctions énumérées à [l’Annexe E: Scalar Functions](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md). Pour plus d’informations sur la séquence d’évasion de la fonction scalaire, voir [Scalar Function Escape Sequence](../../../odbc/reference/appendixes/scalar-function-escape-sequence.md) à l’annexe C: SQL Grammar.  
  
 Par exemple, les relevés SQL suivants créent le même ensemble de résultats de noms de clients de uppercase. La première déclaration utilise la syntaxe de séquence d’évacuation. La deuxième déclaration utilise la syntaxe indigène pour Les Ingres pour OS/2 et n’est pas interopérable.  
  
```  
SELECT {fn UCASE(Name)} FROM Customers  
  
SELECT uppercase(Name) FROM Customers  
```  
  
 Une application peut mélanger les appels vers des fonctions scalaires qui utilisent la syntaxe native et les appels vers des fonctions scalaires qui utilisent la syntaxe ODBC. Supposons, par exemple, que les noms dans le tableau des employés sont stockés sous forme de nom de famille, de virgule et de prénom. La déclaration suivante de SQL crée un ensemble de résultats des noms de famille des employés dans le tableau des employés. L’instruction utilise la fonction scalaire D’ODBC **SUBSTRING** et la fonction scalaire DE SQL Server **CHARINDEX** et ne s’exécutera correctement que sur SQL Server.  
  
```  
SELECT {fn SUBSTRING(Name, 1, CHARINDEX(',', Name) - 1)} FROM Customers  
```  
  
 Pour une interopérabilité maximale, les applications doivent utiliser la fonction scalaire **CONVERT** pour s’assurer que la sortie d’une fonction scalaire est le type requis. La fonction **CONVERT** convertit les données d’un type de données SQL au type de données SQL spécifié. La syntaxe de la fonction **CONVERT** est  
  
 **CONVERT (** _value_exp_ **,** _data_type_**)**  
  
 *lorsqu’value_exp* est un nom de colonne, le résultat d’une autre fonction scalaire, ou une valeur littérale, et *data_type* est un mot clé qui correspond au nom **#define** qui est utilisé par un identifiant de type de données SQL tel que défini à [l’annexe D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md). Par exemple, l’instruction SQL suivante utilise la fonction **CONVERT** pour s’assurer que la sortie de la fonction **CURDATE** est une date, au lieu d’un timestamp ou des données de caractère :  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, {fn CONVERT({fn CURDATE()}, SQL_DATE)}, ?, ?)  
```  
  
 Pour déterminer quelles fonctions scalaires sont prises en charge par une source de données, une application appelle **SQLGetInfo** avec les options SQL_CONVERT_FUNCTIONS, SQL_NUMERIC_FUNCTIONS, SQL_STRING_FUNCTIONS, SQL_SYSTEM_FUNCTIONS et SQL_TIMEDATE_FUNCTIONS. Pour déterminer quelles opérations de conversion sont prises en charge par la fonction **CONVERT,** une application appelle **SQLGetInfo** avec l’une des options qui commencent par SQL_CONVERT.
