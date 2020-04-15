---
title: Taille de colonne, chiffres décimaux, Longueur Octet de transfert, taille d’affichage Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- display size of data types [ODBC]
- data types [ODBC], column size
- transfer octet length of data types [ODBC]
- size of data types [ODBC]
- data types [ODBC], display size
- decimal digits of data types [ODBC]
- data types [ODBC], decimal digits
- SQL data types [ODBC], column characteristics
- column size of data types [ODBC]
- data types [ODBC], transfer octet length
ms.assetid: 723107a1-be08-4ea3-a8c0-b2c45d38d1aa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 55b8e9dd305764a89601e9ffd5a337e42a8d8db3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306570"
---
# <a name="column-size-decimal-digits-transfer-octet-length-and-display-size---odbc"></a>Taille de colonne, chiffres décimaux, longueur d’octet de transfert, et taille d’affichage - ODBC
Les types de données sont caractérisés par leur taille de colonne (ou de paramètres), les chiffres décimaux, la longueur et la taille de l’affichage. Les fonctions ODBC suivantes renvoient ces attributs pour un paramètre dans une déclaration SQL ou pour un type de données SQL sur une source de données. Chaque fonction ODBC renvoie un ensemble différent de ces attributs, comme suit :  
  
-   **SQLDescribeCol** retourne la taille de la colonne et les chiffres décimaux des colonnes qu’il décrit.  
  
-   **SQLDescribeParam** retourne la taille du paramètre et les chiffres décimaux des paramètres qu’il décrit. **SQLBindParameter** définit la taille du paramètre et les chiffres décimaux pour un paramètre dans une déclaration SQL.  
  
-   Le catalogue fonctionne **SQLColumns**, **SQLProcedureColumns**, et **SQLGetTypeInfo** attributs de retour pour une colonne dans une table, ensemble de résultats, ou un paramètre de procédure et les attributs catalogue des types de données dans la source de données. **SQLColumns** retourne la taille de la colonne, les chiffres décimaux et la longueur d’une colonne dans des tableaux spécifiés (comme la table de base, la vue ou une table système). **SQLProcedureColumns** retourne la taille de la colonne, les chiffres décimaux et la longueur d’une colonne dans une procédure. **SQLGetTypeInfo** renvoie la taille maximale de la colonne et les chiffres décimaux minimaux et maximaux d’un type de données SQL sur une source de données.  
  
 Les valeurs retournées par ces fonctions pour la colonne ou la taille du paramètre correspondent à la « précision » telle que définie dans ODBC 2. *x*. Toutefois, les valeurs ne correspondent pas nécessairement aux valeurs retournées dans SQL_DESC_PRECISION ou tout autre champ descripteur. Il en va de même pour les chiffres décimaux, qui correspondent à l’échelle définie dans ODBC 2. *x*. Il ne correspond pas nécessairement aux valeurs retournées dans SQL_DESC_SCALE ou tout autre champ descripteur, mais provient de différents champs descripteur selon le type de données. Pour plus d’informations, voir [Taille de colonne](../../../odbc/reference/appendixes/column-size.md) et chiffres [décimaux](../../../odbc/reference/appendixes/decimal-digits.md).  
  
 De même, les valeurs de longueur d’octet de transfert ne proviennent pas de SQL_DESC_LENGTH. Ils viennent de la SQL_DESC_OCTET_LENGTH d’un champ d’un descripteur pour tous les caractères et les types binaires. Il n’y a pas de champ descripteur qui détient cette information pour d’autres types.  
  
 La valeur de taille d’affichage pour tous les types de données correspond à la valeur dans un champ descripteur unique, SQL_DESC_DISPLAY_SIZE.  
  
 Les champs descripteur décrivent les caractéristiques d’un ensemble de résultats. Les champs descripteur ne contiennent pas de valeurs valides sur les données avant l’exécution des relevés. Les valeurs pour la taille de colonne, les chiffres décimaux, et la taille d’affichage retourné par **SQLColumns**, **SQLProcedureColumns**, et **SQLGetTypeInfo**, d’autre part, les caractéristiques de retour des objets de base de données, tels que les colonnes de table et les types de données, qui existent dans le catalogue de la source de données. De même, dans son ensemble de résultats, **SQLColAttribute** retourne la taille de la colonne, les chiffres décimaux et la longueur d’octet de transfert des colonnes à la source de données ; ces valeurs ne sont pas nécessairement les mêmes que les valeurs dans les domaines SQL_DESC_PRECISION, SQL_DESC_SCALE et SQL_DESC_OCTET_LENGTH descripteur.  
  
 Pour plus d’informations sur ces champs descripteur, voir [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Rubriques connexes :  
  
-   [Taille de colonne](../../../odbc/reference/appendixes/column-size.md)  
-   [Nombres décimaux](../../../odbc/reference/appendixes/decimal-digits.md)  
-   [Longueur en octets du transfert](../../../odbc/reference/appendixes/transfer-octet-length.md)  
-   [Taille d’affichage](../../../odbc/reference/appendixes/display-size.md)
