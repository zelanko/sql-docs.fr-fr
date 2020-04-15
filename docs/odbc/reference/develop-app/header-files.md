---
title: Fichiers d’en-tête (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- header files [ODBC]
ms.assetid: b4a03273-5e30-4d7b-826e-02f8f28ba078
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 62364d828e7b1f1ed8c70cae7ae1fc7dc3bc33fc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300189"
---
# <a name="header-files"></a>Fichiers d’en-tête
Le fichier d’en-tête Sql.h contient des prototypes pour les fonctions et les fonctionnalités du niveau de conformité Core ODBC Interface. Le fichier d’en-tête Sqlext.h contient des prototypes pour les fonctions et les caractéristiques des niveaux de conformation de niveau 1 et niveau 2. Le fichier d’en-tête Sqltypes.h contient des définitions de type et des indicateurs pour les types de données SQL.  
  
 Les fichiers d’en-tête contiennent tous un **#define**, ODBCVER, qu’une application ou un pilote peut définir pour être compilé pour différentes versions d’ODBC.  
  
 Pour s’aligner sur l’ISO CLI et Open Group CLI, les fichiers d’en-tête contiennent des alias pour les types d’informations utilisés dans les appels à **SQLGetInfo**. Dans le tableau suivant, la colonne « nom ODBC » indique le nom ODBC pour le type d’information dans [ODBC API Reference](../../../odbc/reference/syntax/odbc-api-reference.md). La colonne "Alias in header file" indique le nom qui est utilisé dans l’ISO CLI et l’Open Group CLI. La valeur numérique réelle de ces noms manifestes est la même dans ODBC et les IGC standard. Ces alias permettent à une application ou à un pilote conforme aux normes de compiler avec les fichiers d’en-tête ODBC *3.x.*  
  
 Ces alias incluent des extensions d’abréviations dans les noms ODBC de sorte que les noms sont plus compréhensibles. "MAX" est étendu à "MAXIMUM", "LEN" à "LENGTH", "MULT" à "MULTIPLE", "OJ" à "OUTER_JOIN", et "TXN" à "TRANSACTION".  
  
|Nom ODBC|Alias dans le fichier d’en-tête|  
|---------------|--------------------------|  
|SQL_MAX_CATALOG_NAME_LEN|SQL_MAXIMUM_CATALOG_NAME_LENGTH|  
|SQL_MAX_COLUMN_NAME_LEN|SQL_MAXIMUM_COLUMN_NAME_LENGTH|  
|SQL_MAX_COLUMNS_IN_GROUP_BY|SQL_MAXIMUM_COLUMNS_IN_GROUP_BY|  
|SQL_MAX_COLUMNS_IN_ORDER_BY|SQL_MAXIMUM_COLUMNS_IN_ORDER_BY|  
|SQL_MAX_COLUMNS_IN_SELECT|SQL_MAXIMUM_COLUMNS_IN_SELECT|  
|SQL_MAX_COLUMNS_IN_TABLE|SQL_MAXIMUM_COLUMNS_IN_TABLE|  
|SQL_MAX_CONCURRENT_ACTIVITIES|SQL_MAXIMUM_CONCURRENT_ACTIVITIES|  
|SQL_MAX_CURSOR_NAME_LEN|SQL_MAXIMUM_CURSOR_NAME_LENGTH|  
|SQL_MAX_DRIVER_CONNECTIONS|SQL_MAXIMUM_DRIVER_CONNECTIONS|  
|SQL_MAX_IDENTIFIER_LEN|SQL_MAXIMUM_IDENTIFIER_LENGTH|  
|SQL_MAX_SCHEMA_NAME_LEN|SQL_MAXIMUM_SCHEMA_NAME_LENGTH|  
|SQL_MAX_STATEMENT_LEN|SQL_MAXIMUM_STATEMENT_LENGTH|  
|SQL_MAX_TABLE_NAME_LEN|SQL_MAXIMUM_TABLE_NAME_LENGTH|  
|SQL_MAX_TABLES_IN_SELECT|SQL_MAXIMUM_TABLES_IN_SELECT|  
|SQL_MAX_USER_NAME_LEN|SQL_MAXIMUM_USER_NAME_LENGTH|  
|SQL_MULT_RESULT_SETS|SQL_MULTIPLE_RESULT_SETS|  
|SQL_OJ_CAPABILITIES|SQL_OUTER_JOIN_CAPABILITIES|  
|SQL_TXN_CAPABLE|SQL_TRANSACTION_CAPABLE|  
|SQL_TXN_ISOLATION_OPTION|SQL_TRANSACTION_ISOLATION_OPTION|
