---
title: Conversion des données de SQL à C Data Types (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from SQL to C types [ODBC]
- data conversions from SQL to C types [ODBC], about converting
- data types [ODBC], C data types
- data types [ODBC], converting data
- data types [ODBC], SQL data types
- SQL data types [ODBC], converting to C types
- converting data from SQL to c types [ODBC]
- converting data from SQL to c types [ODBC], about converting
- C data types [ODBC], converting from SQL types
ms.assetid: 029727f6-d3f0-499a-911c-bcaf9714e43b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1a10730cb3910c55679c264583801cd57c83bfc3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284749"
---
# <a name="converting-data-from-sql-to-c-data-types"></a>Conversion de données de SQL en types de données C
Lorsqu’une application appelle **SQLFetch**, **SQLFetchScroll**ou **SQLGetData**, le conducteur récupère les données de la source de données. Si nécessaire, il convertit les données du type de données dans lequel le conducteur les a récupérées au type de données spécifié par l’argument *TargetType* dans **SQLBindCol** ou **SQLGetData.** Enfin, il stocke les données dans l’endroit indiqué par l’argument *TargetValuePtr* dans **SQLBindCol** ou **SQLGetData** (et le champ SQL_DESC_DATA_PTR de l’ARD).  
  
 Le tableau suivant montre les conversions prises en charge des types de données ODBC SQL aux types de données ODBC C. Un cercle rempli indique la conversion par défaut pour un type de données SQL (le type de données C auquel les données seront converties lorsque la valeur de *TargetType* est SQL_C_DEFAULT). Un cercle creux indique une conversion soutenue.  
  
 Pour une application ODBC *3.x* travaillant avec un pilote ODBC *2.x,* la conversion à partir de types de données spécifiques au conducteur peut ne pas être prise en charge.  
  
 Le format des données converties n’est pas affecté par le paramètre de pays Windows®.  
  
 Les tableaux des sections suivantes décrivent comment le conducteur ou la source de données convertit les données récupérées à partir de la source de données; les conducteurs sont tenus d’appuyer les conversions à tous les types de données ODBC C à partir des types de données SQL ODBC qu’ils prennent en charge. Pour un type de données ODBC SQL donné, la première colonne du tableau énumère les valeurs légales d’entrée de l’argument *TargetType* dans **SQLBindCol** et **SQLGetData**. La deuxième colonne énumère les résultats d’un test, souvent en utilisant l’argument *BufferLength* spécifié dans **SQLBindCol** ou **SQLGetData**, que le conducteur effectue pour déterminer s’il peut convertir les données. Pour chaque résultat, les troisième et quatrième colonnes dressent la liste des valeurs placées dans les tampons spécifiés par le *TargetValuePtr* et *StrLen_or_IndPtr* arguments spécifiés dans **SQLBindCol** ou **SQLGetData** après que le conducteur a tenté de convertir les données. *(L’argument StrLen_or_IndPtr* correspond au SQL_DESC_OCTET_LENGTH_PTR champ de l’ARD.) La dernière colonne énumère le SQLSTATE retourné pour chaque résultat par **SQLFetch**, **SQLFetchScroll**, ou **SQLGetData**.  
  
 Si l’argument *de TargetType* dans **SQLBindCol** ou **SQLGetData** contient un identifiant pour un type de données ODBC C qui n’est pas indiqué dans le tableau pour un type de données ODBC SQL donné, **SQLFetch**, **SQLFetchScroll**, ou **SQLGetData** retourne SQLSTATE 07006 (violation d’attribut de type de données restreinte). Si l’argument *de TargetType* contient un identifiant qui spécifie une conversion d’un type de données SQL spécifique au conducteur à un type de données ODBC C et que cette conversion n’est pas prise en charge par le conducteur, **SQLFetchScroll**, ou **SQLGetData** retourne SQLSTATE HYC00 (fonction facultative non mise en œuvre). **SQLFetchScroll**  
  
 Bien qu’il ne soit pas indiqué dans les tableaux, le conducteur retourne SQL_NULL_DATA dans le tampon spécifié par *l’argument StrLen_or_IndPtr* lorsque la valeur des données SQL est NULL. Pour une explication de l’utilisation de *StrLen_or_IndPtr* lorsque plusieurs appels sont effectués pour récupérer des données, consultez la description de la fonction [SQLGetData.](../../../odbc/reference/syntax/sqlgetdata-function.md) Lorsque les données SQL sont converties en données \*de caractère C, le nombre de caractères retournés dans *StrLen_or_IndPtr* n’inclut pas le byte de terminaison nulle. Si *TargetValuePtr* est un pointeur nul, **SQLGetData** retourne SQLSTATE HY009 (utilisation invalide du pointeur nul); dans **SQLBindCol**, cela débinde la colonne.  
  
 Les termes et conventions suivants sont utilisés dans les tableaux :  
  
-   **La longueur des données** est le nombre d’octets de données C disponibles pour revenir dans*le targetValuePtr*, si oui ou non les données seront tronquées avant qu’elles ne soient retournées à l’application. Pour les données de chaîne, cela n’inclut pas l’espace pour le caractère de non-terminaison.  
  
-   **La longueur des octets** de caractère est le nombre total d’octets nécessaires pour afficher les données en format de caractère. Ceci est tel que défini pour chaque type de données C dans la section [Taille d’affichage](../../../odbc/reference/appendixes/display-size.md), sauf que la longueur des octets de caractère est dans les octets tandis que la taille de l’écran est en caractères.  
  
-   Les mots en *italique* représentent des arguments de fonction ou des éléments de la grammaire SQL. Pour la syntaxe des éléments de grammaire, voir [Annexe C: SQL Grammar](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [SQL à C : Caractère](../../../odbc/reference/appendixes/sql-to-c-character.md)  
  
-   [SQL à C : Numérique](../../../odbc/reference/appendixes/sql-to-c-numeric.md)  
  
-   [SQL à C : bit](../../../odbc/reference/appendixes/sql-to-c-bit.md)  
  
-   [SQL à C : Binary](../../../odbc/reference/appendixes/sql-to-c-binary.md)  
  
-   [SQL à C : Date](../../../odbc/reference/appendixes/sql-to-c-date.md)  
  
-   [SQL à C : GUID](../../../odbc/reference/appendixes/sql-to-c-guid.md)  
  
-   [SQL à C : Temps](../../../odbc/reference/appendixes/sql-to-c-time.md)  
  
-   [SQL à C : Timestamp](../../../odbc/reference/appendixes/sql-to-c-timestamp.md)  
  
-   [SQL à C : Intervalles d’années-mois](../../../odbc/reference/appendixes/sql-to-c-year-month-intervals.md)  
  
-   [SQL à C : Intervalles de jours-heures](../../../odbc/reference/appendixes/sql-to-c-day-time-intervals.md)  
  
-   [Exemples de conversion de données SQL en C](../../../odbc/reference/appendixes/sql-to-c-data-conversion-examples.md)
