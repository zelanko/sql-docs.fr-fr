---
title: Conversion de données à partir de C en Types de données SQL | Microsoft Docs
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019119"
---
# <a name="converting-data-from-c-to-sql-data-types"></a>Conversion de données de C en types de données SQL
Lorsqu’une application appelle **SQLExecute** ou **SQLExecDirect**, le pilote récupère les données pour tous les paramètres liés avec **SQLBindParameter** à partir d’emplacements de stockage dans l’application. Lorsqu’une application appelle **SQLSetPos**, le pilote récupère les données pour une mise à jour ou ajouter une opération à partir de colonnes liées avec **SQLBindCol**. Pour les paramètres de data-at-execution, l’application envoie les données de paramètre avec **SQLPutData**. Si nécessaire, le pilote convertit les données à partir du type de données spécifié par le *ValueType* argument dans **SQLBindParameter** au type de données spécifié par le *ParameterType*argument dans **SQLBindParameter**, puis envoie les données à la source de données.  
  
 Le tableau suivant répertorie les conversions prises en charge à partir d’ODBC C types de données aux types de données ODBC SQL. Un cercle plein indique la conversion par défaut pour un type de données SQL (le type de données C à partir de laquelle les données seront converties lorsque la valeur de *ValueType* ou le champ de descripteur SQL_DESC_CONCISE_TYPE est SQL_C_DEFAULT). Un cercle creux indique une conversion prises en charge.  
  
 Le format des données converties n’est pas affecté par le paramètre de pays Windows®.  
  
 ![Conversions prises en charge : ODBC C en types de données SQL](../../../odbc/reference/appendixes/media/apd1b.gif "apd1b")  
  
 Les tableaux dans les sections suivantes décrivent comment le pilote ou une source de données convertit les données envoyées à la source de données ; pilotes sont requis pour prendre en charge les conversions à partir de tous les types de données ODBC C pour les types de données SQL ODBC pris en charge. Pour un type de données ODBC C donné, la première colonne de la table répertorie les valeurs d’entrée autorisées de le *ParameterType* argument dans **SQLBindParameter**. La seconde colonne répertorie les résultats de test qui le pilote effectue pour déterminer si elle peut convertir les données. La troisième colonne contient la valeur SQLSTATE retournée pour chaque résultat par **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**, **SQLSetPos**, ou **SQLPutData**. Données sont envoyées à la source de données uniquement si la valeur SQL_SUCCESS est retournée.  
  
 Si le *ParameterType* argument dans **SQLBindParameter** contient l’identificateur d’un type de données SQL ODBC qui ne figure pas dans la table pour un type de données C donné, **SQLBindParameter**retourne SQLSTATE 07006 (violation de l’attribut de type de données restreint). Si le *ParameterType* argument contient un identificateur propre au pilote et le pilote ne prend pas en charge la conversion à partir du type de données ODBC C spécifique à ce type de données SQL spécifiques au pilote, **SQLBindParameter** retourne SQLSTATE HYC00 (fonctionnalité facultative non implémentée).  
  
 Si le *ParameterValuePtr* et *StrLen_or_IndPtr* les arguments spécifiés dans **SQLBindParameter** sont les deux pointeurs null, que fonction retourne SQLSTATE HY009 (non valide utilisation d’un pointeur null). Même si elle n’est pas représentée dans les tables, une application définit la valeur de la mémoire tampon de longueur / d’indicateur vers lequel pointée le *StrLen_or_IndPtr* argument de **SQLBindParameter** ou la valeur de la  *StrLen_or_IndPtr* argument de **SQLPutData** avec la valeur SQL_NULL_DATA pour spécifier une valeur de données NULL SQL. (Le *StrLen_or_IndPtr* argument correspond au champ SQL_DESC_OCTET_LENGTH_PTR du descripteur APD.) L’application définit ces valeurs à SQL_NTS pour spécifier que la valeur de \* *ParameterValuePtr* dans **SQLBindParameter** ou \* *DataPtr*dans **SQLPutData** (désigné par le champ SQL_DESC_DATA_PTR du descripteur APD) est une chaîne se terminant par null.  
  
 Les termes suivants sont utilisés dans les tables :  
  
-   **Longueur d’octet de données** : nombre d’octets de données SQL disponibles pour envoyer à la source de données, ou non les données seront tronquées avant son envoi à la source de données. Données de chaînes, cela n’inclut pas d’espace pour le caractère de fin de la valeur null.  
  
-   **Longueur d’octet de colonne** -nombre d’octets requis pour stocker les données à la source de données.  
  
-   **Longueur d’octet de caractère** - Maximum nombre d’octets nécessaires pour afficher les données sous forme de caractère. Il s’agit comme défini pour chaque type de données SQL dans [taille afficher](../../../odbc/reference/appendixes/display-size.md), sauf que la longueur d’octet de caractère est en octets, tandis que la taille d’affichage est en caractères.  
  
-   **Nombre de chiffres** : nombre de caractères utilisés pour représenter un nombre, y compris le signe moins, une virgule décimale et un exposant (si nécessaire).  
  
-   **Mots dans**   
     ***italique*** -éléments de la grammaire SQL. Pour connaître la syntaxe d’éléments de syntaxe, consultez [annexe c : Grammaire SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Cette section contient les rubriques suivantes.  
  
-   [C en SQL : Caractère](../../../odbc/reference/appendixes/c-to-sql-character.md)  
  
-   [C en SQL : Numérique](../../../odbc/reference/appendixes/c-to-sql-numeric.md)  
  
-   [C en SQL : Bit](../../../odbc/reference/appendixes/c-to-sql-bit.md)  
  
-   [C en SQL : fichier binaire](../../../odbc/reference/appendixes/c-to-sql-binary.md)  
  
-   [C en SQL : Date](../../../odbc/reference/appendixes/c-to-sql-date.md)  
  
-   [C en SQL : GUID](../../../odbc/reference/appendixes/c-to-sql-guid.md)  
  
-   [C en SQL : heure](../../../odbc/reference/appendixes/c-to-sql-time.md)  
  
-   [C en SQL : Horodatage](../../../odbc/reference/appendixes/c-to-sql-timestamp.md)  
  
-   [C en SQL : Intervalles d’années-mois](../../../odbc/reference/appendixes/c-to-sql-year-month-intervals.md)  
  
-   [C en SQL : Intervalles de jours-heures](../../../odbc/reference/appendixes/c-to-sql-day-time-intervals.md)  
  
-   [Exemples de conversion de données C en SQL](../../../odbc/reference/appendixes/c-to-sql-data-conversion-examples.md)
