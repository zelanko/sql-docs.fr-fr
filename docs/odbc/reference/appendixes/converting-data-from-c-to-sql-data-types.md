---
title: Conversion de données de types de données C en SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], about converting
- converting data from c to SQL types [ODBC]
- data conversions from C to SQL types [ODBC], about converting
- data types [ODBC], C data types
- data types [ODBC], converting data
- SQL data types [ODBC], converting from C types
- data types [ODBC], SQL data types
- data conversions from C to SQL types [ODBC]
- C data types [ODBC], converting to SQL types
ms.assetid: ee0afe78-b58f-4d34-ad9b-616bb23653bd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aca333a6f3006b1f12cf44d1670e38556027e476
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68019119"
---
# <a name="converting-data-from-c-to-sql-data-types"></a>Conversion de données de C en types de données SQL
Quand une application appelle **SQLExecute** ou **SQLExecDirect**, le pilote récupère les données pour tous les paramètres liés à **SQLBindParameter** à partir des emplacements de stockage de l’application. Quand une application appelle **SQLSetPos**, le pilote récupère les données pour une opération de mise à jour ou d’ajout à partir des colonnes liées à **SQLBindCol**. Pour les paramètres de données en cours d’exécution, l’application envoie les données de paramètre avec **SQLPutData**. Si nécessaire, le pilote convertit les données du type de données spécifié par l’argument *ValueType* dans **SQLBindParameter** vers le type de données spécifié par l’argument *ParameterType* dans **SQLBindParameter**, puis envoie les données à la source de données.  
  
 Le tableau suivant montre les conversions prises en charge des types de données ODBC C en types de données ODBC SQL. Un cercle plein indique la conversion par défaut pour un type de données SQL (le type de données C à partir duquel les données seront converties lorsque la valeur de *ValueType* ou le champ de descripteur de SQL_DESC_CONCISE_TYPE est SQL_C_DEFAULT). Un cercle creux indique une conversion prise en charge.  
  
 Le format des données converties n’est pas affecté par le paramètre pays de l'® Windows.  
  
 ![Conversions prises en charge : de types de données ODBC C en SQL](../../../odbc/reference/appendixes/media/apd1b.gif "apd1b")  
  
 Les tableaux des sections suivantes décrivent comment le pilote ou la source de données convertit les données envoyées à la source de données ; les pilotes sont requis pour prendre en charge les conversions de tous les types de données ODBC C en types de données ODBC SQL qu’ils prennent en charge. Pour un type de données ODBC C donné, la première colonne de la table répertorie les valeurs d’entrée autorisées de l’argument *ParameterType* dans **SQLBindParameter**. La deuxième colonne répertorie les résultats d’un test effectué par le pilote pour déterminer s’il peut convertir les données. La troisième colonne répertorie le SQLSTATE renvoyé pour chaque résultat par **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**, **SQLSetPos**ou **SQLPutData**. Les données sont envoyées à la source de données uniquement si SQL_SUCCESS est retourné.  
  
 Si l’argument *ParameterType* dans **SQLBindParameter** contient l’identificateur d’un type de données SQL ODBC qui n’est pas indiqué dans la table pour un type de données C donné, **SQLBindParameter** retourne SQLSTATE 07006 (violation d’attribut de type de données restreint). Si l’argument *ParameterType* contient un identificateur spécifique au pilote et que le pilote ne prend pas en charge la conversion du type de données ODBC C spécifique en ce type de données SQL spécifique au pilote, **SQLBINDPARAMETER** retourne SQLState HYC00 (fonctionnalité facultative non implémentée).  
  
 Si les arguments *ParameterValuePtr* et *StrLen_or_IndPtr* spécifiés dans **SQLBindParameter** sont tous deux des pointeurs null, cette fonction retourne SQLState HY009 (utilisation non valide du pointeur null). Bien qu’il ne soit pas affiché dans les tables, une application définit la valeur de la mémoire tampon de longueur/indicateur désignée par l’argument *StrLen_or_IndPtr* de **SQLBindParameter** ou la valeur de l’argument *StrLen_or_IndPtr* de **SQLPutData** à SQL_NULL_DATA pour spécifier une valeur de données SQL null. (L’argument *StrLen_or_IndPtr* correspond au champ SQL_DESC_OCTET_LENGTH_PTR de l’APD.) L’application définit ces valeurs à SQL_NTS pour spécifier que la valeur dans \* *ParameterValuePtr* dans **SQLBindParameter** ou \* *DataPtr* dans **SQLPutData** (pointée par le champ SQL_DESC_DATA_PTR de APD) est une chaîne terminée par le caractère null.  
  
 Les termes suivants sont utilisés dans les tables :  
  
-   **Longueur en octets des** données : nombre d’octets de données SQL disponibles à envoyer à la source de données, que les données soient tronquées ou non avant d’être envoyées à la source de données. Pour les données de type chaîne, cela n’inclut pas d’espace pour le caractère de fin null.  
  
-   **Longueur d’octet de colonne** : nombre d’octets requis pour stocker les données au niveau de la source de données.  
  
-   **Longueur en octets du caractère** : nombre maximal d’octets nécessaires pour afficher les données sous forme de caractère. Cette valeur est définie pour chaque type de données SQL dans [taille d’affichage](../../../odbc/reference/appendixes/display-size.md), à l’exception de la longueur en octets du caractère, tandis que la taille d’affichage est de caractères.  
  
-   **Nombre de chiffres** : nombre de caractères utilisés pour représenter un nombre, y compris le signe moins, la virgule décimale et l’exposant (si nécessaire).  
  
-   **Mots dans**   
     ***italics*** : éléments de la grammaire SQL. Pour connaître la syntaxe des éléments de syntaxe, consultez [annexe C : grammaire SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [C en SQL : caractère](../../../odbc/reference/appendixes/c-to-sql-character.md)  
  
-   [C en SQL : numérique](../../../odbc/reference/appendixes/c-to-sql-numeric.md)  
  
-   [C en SQL : bit](../../../odbc/reference/appendixes/c-to-sql-bit.md)  
  
-   [C en SQL : binaire](../../../odbc/reference/appendixes/c-to-sql-binary.md)  
  
-   [C en SQL : date](../../../odbc/reference/appendixes/c-to-sql-date.md)  
  
-   [C en SQL : GUID](../../../odbc/reference/appendixes/c-to-sql-guid.md)  
  
-   [C en SQL : heure](../../../odbc/reference/appendixes/c-to-sql-time.md)  
  
-   [C en SQL : horodatage](../../../odbc/reference/appendixes/c-to-sql-timestamp.md)  
  
-   [C en SQL : intervalles d’années-mois](../../../odbc/reference/appendixes/c-to-sql-year-month-intervals.md)  
  
-   [C en SQL : intervalles de jours-heures](../../../odbc/reference/appendixes/c-to-sql-day-time-intervals.md)  
  
-   [Exemples de conversion de données C en SQL](../../../odbc/reference/appendixes/c-to-sql-data-conversion-examples.md)
