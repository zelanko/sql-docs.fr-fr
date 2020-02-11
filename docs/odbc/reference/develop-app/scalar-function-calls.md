---
title: Appels de fonction scalaires | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 37209a75c03a051e3def4d26fa0d4e7f85d0e91d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67897749"
---
# <a name="scalar-function-calls"></a>Appels de fonctions scalaires
Les fonctions scalaires retournent une valeur pour chaque ligne. Par exemple, la fonction scalaire valeur absolue prend une colonne numérique comme argument et retourne la valeur absolue de chaque valeur de la colonne. La séquence d’échappement pour l’appel d’une fonction scalaire est  
  
 **{FN**  _scalaire-fonction_ **}**  
  
 où *Scala-Function* est l’une des fonctions énumérées dans [l’annexe E : fonctions scalaires](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md). Pour plus d’informations sur la séquence d’échappement de fonction scalaire, consultez [séquence d’échappement de fonction scalaire](../../../odbc/reference/appendixes/scalar-function-escape-sequence.md) dans l’annexe C : grammaire SQL.  
  
 Par exemple, les instructions SQL suivantes créent le même jeu de résultats de noms de clients en majuscules. La première instruction utilise la syntaxe de séquence d’échappement. La deuxième instruction utilise la syntaxe native pour Ingres pour OS/2 et n’est pas interopérable.  
  
```  
SELECT {fn UCASE(Name)} FROM Customers  
  
SELECT uppercase(Name) FROM Customers  
```  
  
 Une application peut mélanger des appels à des fonctions scalaires qui utilisent la syntaxe native et des appels aux fonctions scalaires qui utilisent la syntaxe ODBC. Par exemple, supposons que les noms de la table Employee sont stockés sous la forme d’un nom, d’une virgule et d’un prénom. L’instruction SQL suivante crée un jeu de résultats des noms des employés dans la table Employee. L’instruction utilise la fonction de **sous-chaîne** de fonction scalaire ODBC et la fonction scalaire SQL Server **charIndex** et s’exécute correctement uniquement sur SQL Server.  
  
```  
SELECT {fn SUBSTRING(Name, 1, CHARINDEX(',', Name) - 1)} FROM Customers  
```  
  
 Pour une interopérabilité maximale, les applications doivent utiliser la fonction de **conversion** scalaire pour s’assurer que la sortie d’une fonction scalaire est le type requis. La fonction **Convert** convertit les données d’un type de données SQL vers le type de données SQL spécifié. La syntaxe de la fonction **Convert** est  
  
 **Convert (** _value_exp_ **,** _data_type_**)**  
  
 où *value_exp* est un nom de colonne, le résultat d’une autre fonction scalaire, ou une valeur littérale, et *data_type* est un mot clé qui correspond au nom de **#define** utilisé par un identificateur de type de données SQL, tel que défini dans l' [annexe D : types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md). Par exemple, l’instruction SQL suivante utilise la fonction **Convert** pour s’assurer que la sortie de la fonction « **caillé** » est une date, et non une estampille ou des données de type caractère :  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, {fn CONVERT({fn CURDATE()}, SQL_DATE)}, ?, ?)  
```  
  
 Pour déterminer quelles fonctions scalaires sont prises en charge par une source de données, une application appelle **SQLGetInfo** avec les options SQL_CONVERT_FUNCTIONS, SQL_NUMERIC_FUNCTIONS, SQL_STRING_FUNCTIONS, SQL_SYSTEM_FUNCTIONS et SQL_TIMEDATE_FUNCTIONS. Pour déterminer les opérations de conversion prises en charge par la fonction **Convert** , une application appelle **SQLGetInfo** avec l’une des options qui commencent par SQL_CONVERT.
