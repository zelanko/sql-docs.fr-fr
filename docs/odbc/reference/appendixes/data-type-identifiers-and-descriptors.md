---
title: Identifiants et descripteurs de type de données Microsoft Docs
ms.custom: ''
ms.date: 02/02/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
- descriptors [ODBC], data types
- verbose data types [ODBC]
- data types [ODBC], descriptors
- concise data types [ODBC]
ms.assetid: f0077c9b-8eb2-4b5f-8c4c-7436fdef37ab
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f65bc86213f99112daf17c67a4ca522490d32149
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284482"
---
# <a name="data-type-identifiers-and-descriptors"></a>Identificateurs et descripteurs des types de données
Les types de données énumérés dans les sections [SQL Data Types](../../../odbc/reference/appendixes/sql-data-types.md) et [C Data Types](../../../odbc/reference/appendixes/c-data-types.md) plus tôt dans cette annexe sont des types de données « concis » : chaque identifiant fait référence à un seul type de données. Il existe une correspondance individuelle entre l’identifiant et le type de données. Toutefois, dans tous les cas, les descripteurs n’utilisent pas une seule valeur pour identifier les types de données. Dans certains cas, ils utilisent un type de données "verbose" et un sous-code type. Pour tous les types de données, sauf les types de dates et de données d’intervalle, l’identifiant de type verbeux est le même que l’identifiant de type concis et la valeur dans SQL_DESC_DATETIME_INTERVAL_CODE est égale à 0. Toutefois, pour les types de données de date et d’intervalle, un type verbeux (SQL_DATETIME ou SQL_INTERVAL) est stocké dans SQL_DESC_TYPE, un type concis est stocké dans SQL_DESC_CONCISE_TYPE et un sous-code pour chaque type concis est stocké dans SQL_DESC_DATETIME_INTERVAL_CODE. La mise en place d’un de ces champs affecte les autres. Pour plus d’informations sur ces domaines, consultez la description de la fonction [SQLSetDescField.](../../../odbc/reference/syntax/sqlsetdescfield-function.md)  
  
 Lorsque le champ SQL_DESC_TYPE ou SQL_DESC_CONCISE_TYPE est défini pour certains types de données, les champs SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_LENGTH, SQL_DESC_PRECISION et SQL_DESC_SCALE sont automatiquement définis en valeurs par défaut, le cas échéant pour le type de données. Pour plus d’informations, voir la description du champ SQL_DESC_TYPE dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Si l’un des ensembles de valeurs par défaut n’est pas approprié, l’application doit définir explicitement le champ descripteur par le biais d’un appel à **SQLSetDescField**.  
  
 Le tableau suivant affiche l’identifiant de type concis, l’identifiant de type verbeux et le sous-code de type pour chaque date et intervalle SQL et C type identifiant. Comme le montre ce tableau, pour les types de données de date et d’intervalle, les champs de SQL_DESC_TYPE et de SQL_DESC_DATETIME_INTERVAL_CODE ont les mêmes constantes manifestes tant pour les types de données SQL (dans les descripteurs de mise en œuvre) que pour les types de données C (dans les descripteurs d’application).  
  
|Type SQL concise|Type Concise C|Type Verbose|DATETIME_INTERVAL_CODE|  
|----------------------|--------------------|------------------|------------------------------|  
|SQL_TYPE_DATE|SQL_C_TYPE_DATE|SQL_DATETIME|SQL_CODE_DATE|  
|SQL_TYPE_TIME|SQL_C_TYPE_TIME|SQL_DATETIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_DATETIME|SQL_CODE_TIMESTAMP|  
|SQL_INTERVAL_MONTH|SQL_C_INTERVAL_MONTH|SQL_INTERVAL|SQL_CODE_MONTH|  
|SQL_INTERVAL_YEAR|SQL_C_INTERVAL_YEAR|SQL_INTERVAL|SQL_CODE_YEAR|  
|SQL_INTERVAL_YEAR_TO_MONTH|SQL_C_INTERVAL_YEAR_TO_MONTH|SQL_INTERVAL|SQL_CODE_YEAR_TO_MONTH|  
|SQL_INTERVAL_DAY|SQL_C_INTERVAL_DAY|SQL_INTERVAL|SQL_CODE_DAY|  
|SQL_INTERVAL_HOUR|SQL_C_INTERVAL_HOUR|SQL_INTERVAL|SQL_CODE_HOUR|  
|SQL_INTERVAL_MINUTE|SQL_C_INTERVAL_MINUTE|SQL_INTERVAL|SQL_CODE_MINUTE|  
|SQL_INTERVAL_SECOND|SQL_C_INTERVAL_SECOND|SQL_INTERVAL|SQL_CODE_SECOND|  
|SQL_INTERVAL_DAY_TO_HOUR|SQL_C_INTERVAL_DAY_TO_HOUR|SQL_INTERVAL|SQL_CODE_DAY_TO_HOUR|  
|SQL_INTERVAL_DAY_TO_MINUTE|SQL_C_INTERVAL_DAY_TO_MINUTE|SQL_INTERVAL|SQL_CODE_DAY_TO_MINUTE|  
|SQL_INTERVAL_DAY_TO_SECOND|SQL_C_INTERVAL_DAY_TO_SECOND|SQL_INTERVAL|SQL_CODE_DAY_TO_SECOND|  
|SQL_INTERVAL_HOUR_TO_MINUTE|SQL_C_INTERVAL_HOUR_TO_MINUTE|SQL_INTERVAL|SQL_CODE_HOUR_TO_MINUTE|  
|SQL_INTERVAL_HOUR_TO_SECOND|SQL_C_INTERVAL_HOUR_TO_SECOND|SQL_INTERVAL|SQL_CODE_HOUR_TO_SECOND|  
|SQL_INTERVAL_MINUTE_TO_SECOND|SQL_C_INTERVAL_MINUTE_TO_SECOND|SQL_INTERVAL|SQL_CODE_MINUTE_TO_SECOND|
