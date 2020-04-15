---
title: 'Annexe D : Types de données Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], defined
- SQL data types [ODBC], defined
- data types [ODBC]
- data types [ODBC], about data types
ms.assetid: 981d49c3-3531-4543-aa75-5bd9e4f67000
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c1abadb962e3a1ee9327bbb8d84e52d180b4a7e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292459"
---
# <a name="appendix-d-data-types"></a>Annexe D : Types de données
ODBC définit deux ensembles de types de données : les types de données SQL et les types de données C. Les types de données SQL indiquent le type de données stockées à la source de données. Les types de données C indiquent le type de données stockées dans les tampons d’application.  
  
 Les types de données SQL sont définis par chaque DBMS conformément à la norme SQL-92. Pour chaque type de données SQL spécifié dans la norme SQL-92, ODBC définit un identificateur de type, qui est une valeur **#define** qui est adoptée comme argument dans les fonctions ODBC ou retournée dans les métadonnées d’un ensemble de résultats. Les seuls types de données SQL-92 non pris en charge par ODBC sont le BIT (le type de SQL_BIT ODBC a des caractéristiques différentes), BIT_VARYING, TIME_WITH_TIMEZONE, TIMESTAMP_WITH_TIMEZONE et NATIONAL_CHARACTER. Les conducteurs sont responsables de la cartographie des types de données SQL spécifiques à la source de données aux identificateurs de type de données ODBC SQL et aux identificateurs de type de données SQL spécifiques au conducteur. Le type de données SQL est spécifié dans le domaine SQL_DESC_CONCISE_TYPE d’un descripteur de mise en œuvre.  
  
 ODBC définit les types de données C et leurs identifiants de type ODBC correspondants. Une application spécifie le type de données C du tampon qui recevra des données de jeu de résultats en passant l’identifiant de type C approprié dans l’argument *TargetType* dans un appel à **SQLBindCol** ou **SQLGetData**. Il spécifie le type C de la mémoire tampon contenant un paramètre de déclaration en passant l’identifiant de type C approprié dans *l’argument ValueType* dans un appel à **SQLBindParameter**. Le type de données C est spécifié dans le domaine SQL_DESC_CONCISE_TYPE d’un descripteur d’application.  
  
> [!NOTE]  
>  Il n’existe pas de types de données C spécifiques au conducteur.  
  
 Chaque type de données SQL correspond à un type de données ODBC C. Avant de renvoyer les données de la source de données, le pilote les convertit en type de données C spécifiés. Avant d’envoyer des données à la source de données, le pilote les convertit à partir du type de données C spécifié.  
  
 Cette annexe contient les sujets suivants.  
  
-   [Utilisation d’identificateurs de types de données](../../../odbc/reference/appendixes/using-data-type-identifiers.md)  
  
-   [Types de données SQL](../../../odbc/reference/appendixes/sql-data-types.md)  
  
-   [Type de données C](../../../odbc/reference/appendixes/c-data-types.md)  
  
-   [Identificateurs et descripteurs des types de données](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)  
  
-   [Identificateurs des pseudo-types](../../../odbc/reference/appendixes/pseudo-type-identifiers.md)  
  
-   [Transfert de données dans leur forme binaire](../../../odbc/reference/appendixes/transferring-data-in-its-binary-form.md)  
  
-   [Conseils pour les types de données d’intervalle et numériques](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md)  
  
-   [Contraintes du calendrier grégorien](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)  
  
-   [Taille de colonne, nombres décimaux, longueur en octets du transfert et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)  
  
-   [Conversion de données de SQL en types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)  
  
-   [Conversion de données de C en types de données SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)  
  
 Pour une explication des types de données ODBC, voir [Data Types dans ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md). Pour obtenir de l’information sur les types de données SQL spécifiques au conducteur, consultez la documentation du conducteur.
