---
title: Appels de fonctions scalaires | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 0e02a217579e70a3b7461037750a919efec14458
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52515469"
---
# <a name="scalar-function-calls"></a>Appels de fonctions scalaires
Fonctions scalaires retournent une valeur pour chaque ligne. Par exemple, la fonction scalaire de valeur absolue prend une colonne numérique en tant qu’argument et retourne la valeur absolue de chaque valeur dans la colonne. Est la séquence d’échappement pour appeler une fonction scalaire  
  
 **{fn** *fonction scalaire* **}**   
  
 où *fonction scalaire* est une des fonctions répertoriées dans [annexe e : Fonctions scalaires](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md). Pour plus d’informations sur la séquence d’échappement de fonction scalaire, consultez [scalaire séquence d’échappement de fonction](../../../odbc/reference/appendixes/scalar-function-escape-sequence.md) dans l’annexe c : Grammaire SQL.  
  
 Par exemple, les instructions SQL suivantes créent le même jeu de résultats du client en majuscules des noms. La première instruction utilise la syntaxe de la séquence d’échappement. La deuxième instruction utilise la syntaxe native pour Ingres pour OS/2 et n’est pas interopérable.  
  
```  
SELECT {fn UCASE(Name)} FROM Customers  
  
SELECT uppercase(Name) FROM Customers  
```  
  
 Une application peut combiner des appels aux fonctions scalaires qui utilisent la syntaxe native et les appels aux fonctions scalaires qui utilisent la syntaxe ODBC. Par exemple, supposons que les noms dans la table des employés sont stockés en tant que nom de famille, une virgule et un prénom. L’instruction SQL suivante crée un jeu de résultats des noms d’employés dans la table Employee. L’instruction utilise la fonction scalaire ODBC **sous-chaîne** et la fonction scalaire SQL Server **CHARINDEX** et s’exécute correctement uniquement sur SQL Server.  
  
```  
SELECT {fn SUBSTRING(Name, 1, CHARINDEX(',', Name) - 1)} FROM Customers  
```  
  
 Pour une interopérabilité maximale, les applications doivent utiliser le **convertir** fonction scalaire pour vous assurer que la sortie d’une fonction scalaire est le type requis. Le **convertir** fonction convertit les données à partir d’un type de données SQL vers le type de données SQL spécifié. La syntaxe de la **convertir** est (fonction)  
  
 **CONVERTIR (** *value_exp* **,** _data_type_**)**  
  
 où *value_exp* est un nom de colonne, le résultat d’une autre fonction scalaire ou une valeur littérale, et *data_type* est un mot clé qui correspond à la **#define** nom qui est utilisé par un Identificateur de type de données SQL comme défini dans [annexe d : Types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md). Par exemple, l’instruction SQL suivante utilise le **convertir** (fonction) pour vous assurer que la sortie de la **CURDATE** (fonction) est une date, au lieu d’un horodatage ou caractères de données :  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, {fn CONVERT({fn CURDATE()}, SQL_DATE)}, ?, ?)  
```  
  
 Pour déterminer les fonctions scalaires sont prises en charge par une source de données, une application appelle **SQLGetInfo** avec la SQL_CONVERT_FUNCTIONS SQL_NUMERIC_FUNCTIONS, SQL_STRING_FUNCTIONS, SQL_SYSTEM_FUNCTIONS et SQL_TIMEDATE_ Options de fonctions. Pour déterminer les opérations de conversion sont pris en charge par le **convertir** (fonction), une application appelle **SQLGetInfo** avec les options qui commencent par SQL_CONVERT.
