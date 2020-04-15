---
title: Conversion des données des types de données C à SQL (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8fb707e77df7d793277d4a23146adc980eede6fd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304658"
---
# <a name="converting-data-from-c-to-sql-data-types"></a>Conversion de données de C en types de données SQL
Lorsqu’une application appelle **SQLExecute** ou **SQLExecDirect**, le conducteur récupère les données pour tous les paramètres liés à **SQLBindParameter** à partir d’emplacements de stockage de l’application. Lorsqu’une application appelle **SQLSetPos**, le conducteur récupère les données pour une mise à jour ou ajoute des opérations à partir de colonnes liées à **SQLBindCol**. Pour les paramètres de données à l’exécution, l’application envoie les données de paramètre avec **SQLPutData**. Si nécessaire, le conducteur convertit les données du type de données spécifiée par *l’argument ValueType* dans **SQLBindParameter** au type de données spécifié par *l’argument de ParameterType* dans **SQLBindParameter,** puis envoie les données à la source de données.  
  
 Le tableau suivant montre les conversions prises en charge des types de données ODBC C aux types de données ODBC SQL. Un cercle rempli indique la conversion par défaut pour un type de données SQL (le type de données C à partir duquel les données seront converties lorsque la valeur de *ValueType* ou du champ descripteur SQL_DESC_CONCISE_TYPE est SQL_C_DEFAULT). Un cercle creux indique une conversion soutenue.  
  
 Le format des données converties n’est pas affecté par le paramètre de pays Windows®.  
  
 ![Conversions prises en charge : de types de données ODBC C en SQL](../../../odbc/reference/appendixes/media/apd1b.gif "apd1b")  
  
 Les tableaux des sections suivantes décrivent comment le conducteur ou la source de données convertit les données envoyées à la source de données; les conducteurs sont tenus d’appuyer les conversions de tous les types de données ODBC C aux types de données SQL ODBC qu’ils prennent en charge. Pour un type de données ODBC C donné, la première colonne du tableau énumère les valeurs d’entrée légales de *l’argument De ParameterType* dans **SQLBindParameter**. La deuxième colonne énumère les résultats d’un test effectué par le conducteur pour déterminer s’il peut convertir les données. La troisième colonne répertorie le SQLSTATE retourné pour chaque résultat par **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**, **SQLSetPos**, ou **SQLPutData**. Les données ne sont envoyées à la source de données que si SQL_SUCCESS est retournée.  
  
 Si l’argument *de ParameterType* dans **SQLBindParameter** contient l’identifiant d’un type de données SQL ODBC qui n’est pas indiqué dans le tableau pour un type de données C donné, **SQLBindParameter** retourne SQLSTATE 07006 (violation d’attribut de type de données restreintes). Si l’argument *de ParameterType* contient un identifiant spécifique au conducteur et que le conducteur n’appuie pas la conversion du type de données spécifique ODBC C à ce type de données SQL spécifique au conducteur, **SQLBindParameter renvoie** SQLSTATE HYC00 (fonction facultative non mise en œuvre).  
  
 Si les arguments *De ParameterValuePtr* et *StrLen_or_IndPtr* spécifiés dans **SQLBindParameter** sont tous deux des pointeurs nuls, cette fonction renvoie SQLSTATE HY009 (utilisation invalide du pointeur nul). Bien qu’elle ne soit pas indiquée dans les tableaux, une application établit la valeur du tampon longueur/indicateur pointé par *l’argument StrLen_or_IndPtr* de **SQLBindParameter** ou la valeur de *l’argument StrLen_or_IndPtr* de **SQLPutData** pour SQL_NULL_DATA de spécifier une valeur de données NULL SQL. *(L’argument StrLen_or_IndPtr* correspond au SQL_DESC_OCTET_LENGTH_PTR champ de l’APD.) L’application définit ces valeurs à SQL_NTS de \*spécifier que la valeur dans *ParameterValuePtr* dans **SQLBindParameter** ou \* *DataPtr* dans **SQLPutData** (pointée par le champ SQL_DESC_DATA_PTR de l’APD) est une chaîne à durée nulle.  
  
 Les termes suivants sont utilisés dans les tableaux :  
  
-   **Longueur d’octet des données** - Nombre d’octets de données SQL disponibles pour envoyer à la source de données, si oui ou non les données seront tronquées avant qu’elles ne soient envoyées à la source de données. Pour les données de chaîne, cela n’inclut pas d’espace pour le caractère de non-terminaison.  
  
-   **Longueur d’octet de colonne** - Nombre d’octets requis pour stocker les données à la source de données.  
  
-   **Longueur d’octet de caractère** - Nombre maximum d’octets nécessaires pour afficher les données sous forme de caractère. Ceci est tel que défini pour chaque type de données SQL dans [la taille d’affichage](../../../odbc/reference/appendixes/display-size.md), sauf la longueur des octets de caractère est dans les octets, tandis que la taille d’affichage est en caractères.  
  
-   **Nombre de chiffres** - Nombre de caractères utilisés pour représenter un nombre, y compris le signe moins, point décimal, et exposant (si nécessaire).  
  
-   **Mots dans**   
     ***italiques*** - Éléments de la grammaire SQL. Pour la syntaxe des éléments de grammaire, voir [Annexe C: SQL Grammar](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [C en SQL : Caractère](../../../odbc/reference/appendixes/c-to-sql-character.md)  
  
-   [C en SQL : Numérique](../../../odbc/reference/appendixes/c-to-sql-numeric.md)  
  
-   [C en SQL : bit](../../../odbc/reference/appendixes/c-to-sql-bit.md)  
  
-   [C en SQL : Binary](../../../odbc/reference/appendixes/c-to-sql-binary.md)  
  
-   [C en SQL : Date](../../../odbc/reference/appendixes/c-to-sql-date.md)  
  
-   [C en SQL : GUID](../../../odbc/reference/appendixes/c-to-sql-guid.md)  
  
-   [C en SQL : Temps](../../../odbc/reference/appendixes/c-to-sql-time.md)  
  
-   [C en SQL : Timestamp](../../../odbc/reference/appendixes/c-to-sql-timestamp.md)  
  
-   [C en SQL : Intervalles d’années-mois](../../../odbc/reference/appendixes/c-to-sql-year-month-intervals.md)  
  
-   [C en SQL : Intervalles de jours-heures](../../../odbc/reference/appendixes/c-to-sql-day-time-intervals.md)  
  
-   [Exemples de conversion de données C en SQL](../../../odbc/reference/appendixes/c-to-sql-data-conversion-examples.md)
