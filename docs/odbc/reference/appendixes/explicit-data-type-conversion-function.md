---
title: Fonction explicite de conversion de type de type de données (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- explicit data type conversion functions [ODBC]
- data type conversion functions [ODBC]
- functions [ODBC], explicit data type conversion functions
ms.assetid: d5789450-b668-4753-96c8-6789e955e7ed
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2de8a8cb6177e9210e8d48c0ce097d13c9a276fd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306990"
---
# <a name="explicit-data-type-conversion-function"></a>Fonctions de conversion de types de données explicites
La conversion explicite de type de données est spécifiée en termes de définitions de type de données SQL.  
  
 La syntaxe ODBC pour la fonction explicite de conversion de type de données ne limite pas les conversions. La validité de conversions spécifiques d’un type de données à un autre type de données sera déterminée par chaque implémentation spécifique au conducteur. Le conducteur, en traduisant la syntaxe ODBC en syntaxe indigène, rejettera les conversions qui, bien que légales dans la syntaxe ODBC, ne sont pas prises en charge par la source de données. La fonction ODBC **SQLGetInfo**, avec les options de conversion (comme SQL_CONVERT_BIGINT, SQL_CONVERT_BINARY, SQL_CONVERT_INTERVAL_YEAR_MONTH, etc.), fournit un moyen de s’enquérir des conversions prises en charge par la source de données.  
  
 Le format de la fonction **CONVERT** est :  
  
 **CONVERT (** _value_exp_, _data_type_**)**  
  
 La fonction renvoie la valeur spécifiée par *value_exp* convertie en *data_type*spécifiée , où *data_type* est l’un des mots clés suivants :  
  
|||  
|-|-|  
|SQL_BIGINT|SQL_INTERVAL_HOUR_TO_MINUTE|  
|SQL_BINARY|SQL_INTERVAL_HOUR_TO_SECOND|  
|SQL_BIT|SQL_INTERVAL_MINUTE_TO_SECOND|  
|SQL_CHAR|SQL_LONGVARBINARY|  
|SQL_DECIMAL|SQL_LONGVARCHAR|  
|SQL_DOUBLE|SQL_NUMERIC|  
|SQL_FLOAT|SQL_REAL|  
|SQL_GUID|SQL_SMALLINT|  
|SQL_INTEGER|SQL_DATE|  
|SQL_INTERVAL_MONTH|SQL_TIME|  
|SQL_INTERVAL_YEAR|SQL_TIMESTAMP|  
|SQL_INTERVAL_YEAR_TO_MONTH|SQL_TINYINT|  
|SQL_INTERVAL_DAY|SQL_VARBINARY|  
|SQL_INTERVAL_HOUR|SQL_VARCHAR|  
|SQL_INTERVAL_MINUTE|SQL_WCHAR|  
|SQL_INTERVAL_SECOND|SQL_WLONGVARCHAR|  
|SQL_INTERVAL_DAY_TO_HOUR|SQL_WVARCHAR|  
|SQL_INTERVAL_DAY_TO_MINUTE||  
|SQL_INTERVAL_DAY_TO_SECOND||  
  
 La syntaxe ODBC pour la fonction explicite de conversion de type de données ne prend pas en charge les spécifications du format de conversion. Si les spécifications des formats explicites sont prises en charge par la source de données sous-jacente, un pilote doit spécifier une valeur par défaut ou implémenter des spécifications de format.  
  
 L’argument *value_exp* peut être un nom de colonne, le résultat d’une autre fonction scalaire, ou un numérique ou une chaîne littérale. Par exemple :  
  
```  
{ fn CONVERT( { fn CURDATE() }, SQL_CHAR ) }  
```  
  
 convertit la sortie de la fonction échaudée CURDATE en une chaîne de caractères.  
  
 Étant donné qu’ODBC n’exige pas un type de données pour les valeurs de retour des fonctions scalaires (parce que les fonctions sont souvent spécifiques à la source de données), les applications doivent utiliser la fonction scalaire CONVERT dans la mesure du possible pour forcer la conversion de type de données.  
  
 Les deux exemples suivants illustrent l’utilisation de la fonction **CONVERT.** Ces exemples supposent l’existence d’un tableau appelé EMPLOYEES, avec une colonne EMPNO de type SQL_SMALLINT et une colonne EMPNAME de type SQL_CHAR.  
  
 Si une demande spécifie la déclaration suivante de SQL :  
  
```  
SELECT EMPNO FROM EMPLOYEES WHERE {fn CONVERT(EMPNO,SQL_CHAR)} LIKE '1%'  
```  
  
-   Un conducteur d’ORACLE traduit la déclaration SQL à :  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE to_char(EMPNO) LIKE '1%'  
    ```  
  
-   Un conducteur de SQL Server traduit la déclaration SQL à :  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE convert(char,EMPNO) LIKE '1%'  
    ```  
  
 Si une demande spécifie la déclaration suivante de SQL :  
  
```  
SELECT {fn ABS(EMPNO)}, {fn CONVERT(EMPNAME,SQL_SMALLINT)}  
   FROM EMPLOYEES WHERE EMPNO <> 0  
```  
  
-   Un conducteur d’ORACLE traduit la déclaration SQL à :  
  
    ```  
    SELECT abs(EMPNO), to_number(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```  
  
-   Un conducteur de SQL Server traduit la déclaration SQL à :  
  
    ```  
    SELECT abs(EMPNO), convert(smallint, EMPNAME) FROM EMPLOYEES  
       WHERE EMPNO <> 0  
    ```  
  
-   Un chauffeur d’Ingres traduit la déclaration SQL à :  
  
    ```  
    SELECT abs(EMPNO), int2(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```
