---
title: Conversion de données à partir de SQL en Types de données C | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 95a44698c12abf0de64c8d6f7d316e9156dc139c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019107"
---
# <a name="converting-data-from-sql-to-c-data-types"></a>Conversion de données de SQL en types de données C
Lorsqu’une application appelle **SQLFetch**, **SQLFetchScroll**, ou **SQLGetData**, le pilote récupère les données à partir de la source de données. Si nécessaire, il convertit les données à partir du type de données dans lequel, récupérés par le pilote pour le type de données spécifié par le *TargetType* argument dans **SQLBindCol** ou **SQLGetData.** Enfin, il stocke les données dans l’emplacement vers lequel pointé le *TargetValuePtr* argument dans **SQLBindCol** ou **SQLGetData** (et le champ SQL_DESC_DATA_PTR de la ARD).  
  
 Le tableau suivant répertorie les conversions prises en charge à partir d’ODBC SQL aux types de données ODBC C, les types de données. Un cercle plein indique la conversion par défaut pour un type de données SQL (le type de données C vers lequel les données seront converties lorsque la valeur de *TargetType* est SQL_C_DEFAULT). Un cercle creux indique une conversion prises en charge.  
  
 Pour une application ODBC *3.x* application fonctionne avec une application ODBC *2.x* pilote, la conversion de données spécifiques au pilote types ne peuvent pas être pris en charge.  
  
 Le format des données converties n’est pas affecté par le paramètre de pays Windows®.  
  
 Les tableaux dans les sections suivantes décrivent comment le pilote ou une source de données convertit les données récupérées à partir de la source de données ; pilotes sont requis pour prendre en charge des conversions à tous les types de données ODBC C à partir des types de données SQL ODBC pris en charge. Pour un type de données SQL ODBC donné, la première colonne de la table répertorie les valeurs d’entrée autorisées de le *TargetType* argument dans **SQLBindCol** et **SQLGetData**. La seconde colonne répertorie les résultats d’un test, souvent à l’aide de la *BufferLength* argument spécifié dans **SQLBindCol** ou **SQLGetData**, ce qui le pilote effectue vers déterminer si elle peut convertir les données. Pour chaque résultat, les troisième et quatrième colonnes répertorient les valeurs placées dans les mémoires tampons spécifiées par le *TargetValuePtr* et *StrLen_or_IndPtr* les arguments spécifiés dans **SQLBindCol** ou **SQLGetData** une fois que le pilote a tenté de convertir les données. (Le *StrLen_or_IndPtr* argument correspond au champ SQL_DESC_OCTET_LENGTH_PTR de la ARD.) La dernière colonne répertorie la valeur SQLSTATE retournée pour chaque résultat par **SQLFetch**, **SQLFetchScroll**, ou **SQLGetData**.  
  
 Si le *TargetType* argument dans **SQLBindCol** ou **SQLGetData** contient un identificateur pour un type de données ODBC C ne pas indiqué dans le tableau pour un type de données SQL ODBC donné,  **SQLFetch**, **SQLFetchScroll**, ou **SQLGetData** retourne SQLSTATE 07006 (violation de l’attribut de type de données restreint). Si le *TargetType* argument contient un identificateur qui spécifie une conversion à partir d’un type de données spécifiques au pilote SQL vers un type de données ODBC C et cette conversion n’est pas pris en charge par le pilote, **SQLFetch**, **SQLFetchScroll**, ou **SQLGetData** retourne SQLSTATE HYC00 (fonctionnalité facultative non implémentée).  
  
 Même si elle n’est pas représentée dans les tables, le pilote retourne SQL_NULL_DATA dans la mémoire tampon spécifiée par le *StrLen_or_IndPtr* argument lorsque la valeur de données SQL est NULL. Pour obtenir une explication de l’utilisation de *StrLen_or_IndPtr* lorsque plusieurs appels sont effectués pour récupérer des données, consultez le [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)description de fonction. Lorsque les données SQL sont converties en données caractères C, le nombre de caractères retournés dans \* *StrLen_or_IndPtr* n’inclut pas de l’octet de caractère nul de terminaison. Si *TargetValuePtr* est un pointeur null, **SQLGetData** retourne SQLSTATE HY009 (utilisation non valide d’un pointeur null) ; dans **SQLBindCol**, cela annule la liaison de la colonne.  
  
 Les conventions et les conditions suivantes sont utilisées dans les tables :  
  
-   **Longueur d’octet de données** est le nombre d’octets de données C disponibles à renvoyer dans **TargetValuePtr*, que les données seront tronquées avant d’être renvoyé à l’application ou non. Données de chaînes, cela n’inclut pas l’espace pour le caractère de fin de la valeur null.  
  
-   **Longueur d’octet de caractère** est le nombre total d’octets nécessaires pour afficher les données au format caractère. Il s’agit comme défini pour chaque type de données C dans la section [taille afficher](../../../odbc/reference/appendixes/display-size.md), sauf que la longueur d’octet de caractère est en octets, tandis que la taille d’affichage est en caractères.  
  
-   Les mots dans *italique* représentent les arguments de fonction ou des éléments de la grammaire SQL. Pour connaître la syntaxe d’éléments de syntaxe, consultez [annexe c : Grammaire SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Cette section contient les rubriques suivantes.  
  
-   [SQL pour c : Caractère](../../../odbc/reference/appendixes/sql-to-c-character.md)  
  
-   [SQL pour c : Numérique](../../../odbc/reference/appendixes/sql-to-c-numeric.md)  
  
-   [SQL pour c : Bit](../../../odbc/reference/appendixes/sql-to-c-bit.md)  
  
-   [SQL pour c : fichier binaire](../../../odbc/reference/appendixes/sql-to-c-binary.md)  
  
-   [SQL pour c : Date](../../../odbc/reference/appendixes/sql-to-c-date.md)  
  
-   [SQL pour c : GUID](../../../odbc/reference/appendixes/sql-to-c-guid.md)  
  
-   [SQL pour c : heure](../../../odbc/reference/appendixes/sql-to-c-time.md)  
  
-   [SQL pour c : Horodatage](../../../odbc/reference/appendixes/sql-to-c-timestamp.md)  
  
-   [SQL pour c : Intervalles d’années-mois](../../../odbc/reference/appendixes/sql-to-c-year-month-intervals.md)  
  
-   [SQL pour c : Intervalles de jours-heures](../../../odbc/reference/appendixes/sql-to-c-day-time-intervals.md)  
  
-   [Exemples de conversion de données SQL en C](../../../odbc/reference/appendixes/sql-to-c-data-conversion-examples.md)
