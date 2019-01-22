---
title: Identificateurs et descripteurs de Type de données | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d50d0bdfe31db1ad002c4915d7afa2c2decb79bb
ms.sourcegitcommit: 480961f14405dc0b096aa8009855dc5a2964f177
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2019
ms.locfileid: "54419944"
---
# <a name="data-type-identifiers-and-descriptors"></a>Identificateurs et descripteurs des types de données
Les types de données répertoriés dans le [les Types de données SQL](../../../odbc/reference/appendixes/sql-data-types.md) et [les Types de données C](../../../odbc/reference/appendixes/c-data-types.md) sections plus haut dans cette annexe sont des types de données « concis » : Chaque identificateur fait référence à un seul type de données. Il existe une correspondance univoque entre l’identificateur et le type de données. Descripteurs, toutefois, ne faire pas dans tous les cas utilisent une valeur unique pour identifier les types de données. Dans certains cas, ils utilisent un type de données « commentaires » et un sous-code de type. Pour tous les types de données à l’exception des types de données date/heure et intervalle, l’identificateur de type détaillée est identique à l’identificateur de type concis et la valeur SQL_DESC_DATETIME_INTERVAL_CODE est égale à 0. Pour les types de données datetime et interval, toutefois, un type verbose (SQL_DATETIME ou SQL_INTERVAL) est stocké dans SQL_DESC_TYPE, un type concis est stocké dans SQL_DESC_CONCISE_TYPE, et un sous-code pour chaque type concis est stocké dans la valeur SQL_DESC_DATETIME_INTERVAL_CODE. Définition de l’une de ces champs affecte les autres. Pour plus d’informations sur ces champs, consultez la [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) description de fonction.  
  
 Lorsque le champ SQL_DESC_TYPE ou SQL_DESC_CONCISE_TYPE est défini pour certains types de données, les champs SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_LENGTH, SQL_DESC_PRECISION et SQL_DESC_SCALE sont automatiquement définis pour les valeurs par défaut, selon le cas pour les données type. Pour plus d’informations, consultez la description du champ SQL_DESC_TYPE dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Si un de l’ensemble de valeurs par défaut ne convient pas, l’application doit définir explicitement le champ de descripteur via un appel à **SQLSetDescField**.  
  
 Le tableau suivant présente l’identificateur de type concis, un identificateur de type verbose et un sous-code de type pour chaque date/heure et un intervalle de SQL et un identificateur de type C. Comme indiqué dans cette table, pour les types de données datetime et l’intervalle, les champs SQL_DESC_TYPE et SQL_DESC_DATETIME_INTERVAL_CODE ont les constantes manifestes mêmes pour les types de données SQL (dans les descripteurs d’implémentation) et pour les types de données C (dans l’application descripteurs).  
  
|Type concis de SQL|Type concis de C|Type détaillée|DATETIME_INTERVAL_CODE|  
|----------------------|--------------------|------------------|------------------------------|  
|SQL_TYPE_DATE|SQL_C_TYPE_DATE|SQL_DATETIME|SQL_CODE_DATE|  
|SQL_TYPE_TIME|SQL_C_TYPE_TIME|SQL_DATETIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_DATETIME|SQL_CODE_TIMESTAMP|  
|SQL_INTERVAL_MONTH|SQL_C_INTERVAL_MONTH|SQL_INTERVAL|SQL_CODE_MONTH|  
|SQL_INTERVAL_YEAR|SQL_C_INTERVAL_YEAR|SQL_INTERVAL|SQL_CODE_YEAR|  
|SQL_INTERVAL_YEAR_TO_MONTH|SQL_C_INTERVAL_YEAR_TO_MONTH|SQL_INTERVAL|SQL_CODE_YEAR_TO_MONTH|  
|S|SQL_INTERVAL_DAY|SQL_C_INTERVAL_DAY|SQL_INTERVAL|SQL_CODE_DAY|  
|SQL_INTERVAL_HOUR|SQL_C_INTERVAL_HOUR|SQL_INTERVAL|SQL_CODE_HOUR|  
|SQL_INTERVAL_MINUTE|SQL_C_INTERVAL_MINUTE|SQL_INTERVAL|SQL_CODE_MINUTE|  
|SQL_INTERVAL_SECOND|SQL_C_INTERVAL_SECOND|SQL_INTERVAL|SQL_CODE_SECOND|  
|SQL_INTERVAL_DAY_TO_HOUR|SQL_C_INTERVAL_DAY_TO_HOUR|SQL_INTERVAL|SQL_CODE_DAY_TO_HOUR|  
|SQL_INTERVAL_DAY_TO_MINUTE|SQL_C_INTERVAL_DAY_TO_MINUTE|SQL_INTERVAL|SQL_CODE_DAY_TO_MINUTE|  
|SQL_INTERVAL_DAY_TO_SECOND|SQL_C_INTERVAL_DAY_TO_SECOND|SQL_INTERVAL|SQL_CODE_DAY_TO_SECOND|  
|SQL_INTERVAL_HOUR_TO_MINUTE|SQL_C_INTERVAL_HOUR_TO_MINUTE|SQL_INTERVAL|SQL_CODE_HOUR_TO_MINUTE|  
|SQL_INTERVAL_HOUR_TO_SECOND|SQL_C_INTERVAL_HOUR_TO_SECOND|SQL_INTERVAL|SQL_CODE_HOUR_TO_SECOND|  
|SQL_INTERVAL_MINUTE_TO_SECOND|SQL_C_INTERVAL_MINUTE_TO_SECOND|SQL_INTERVAL|SQL_CODE_MINUTE_TO_SECOND|
