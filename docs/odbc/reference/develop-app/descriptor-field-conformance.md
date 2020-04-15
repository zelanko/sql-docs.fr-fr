---
title: Conformité de champ de descripteur (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptor field conformance levels [ODBC]
- conformance levels [ODBC], descriptor field
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 6c29d93b-696c-4960-bff3-4d6bc41bc513
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cce33adfdbfceef56936b22c549b6762521b4798
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305930"
---
# <a name="descriptor-field-conformance"></a>Conformité des champs de descripteur
Le tableau suivant indique le niveau de conformité de chaque champ d’en-tête descripteur ODBC, où cela est bien défini.  
  
|Fonction|Niveau de conformité|  
|--------------|-----------------------|  
|SQL_DESC_ALLOC_TYPE|Core|  
|SQL_DESC_ARRAY_SIZE|Core|  
|SQL_DESC_ARRAY_STATUS_PTR|Core (pour APD, DPI et DPI); Niveau 1 (pour ARD)|  
|SQL_DESC_BIND_OFFSET_PTR|Core|  
|SQL_DESC_BIND_TYPE|Core|  
|SQL_DESC_COUNT|Core|  
|SQL_DESC_ROWS_PROCESSED_PTR|Core|  
  
 Le tableau suivant indique le niveau de conformité de chaque champ d’enregistrement descripteur ODBC, où cela est bien défini.  
  
|Fonction|Niveau de conformité|  
|--------------|-----------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Niveau 2|  
|SQL_DESC_BASE_COLUMN_NAME|Core|  
|SQL_DESC_BASE_TABLE_NAME|Niveau 1|  
|SQL_DESC_CASE_SENSITIVE|Core|  
|SQL_DESC_CATALOG_NAME|Niveau 2|  
|SQL_DESC_CONCISE_TYPE|Core|  
|SQL_DESC_DATA_PTR|Core|  
|SQL_DESC_DATETIME_INTERVAL_ CODE|Noyau[1]|  
|SQL_DESC_DATETIME_INTERVAL_ PRECISION|Noyau[1]|  
|SQL_DESC_DISPLAY_SIZE|Core|  
|SQL_DESC_FIXED_PREC_SCALE|Core|  
|SQL_DESC_INDICATOR_PTR|Core|  
|SQL_DESC_LABEL|Niveau 2|  
|SQL_DESC_LENGTH|Core|  
|SQL_DESC_LITERAL_PREFIX|Core|  
|SQL_DESC_LITERAL_SUFFIX|Core|  
|SQL_DESC_LOCAL_TYPE_NAME|Core|  
|SQL_DESC_NAME|Core|  
|SQL_DESC_NULLABLE|Core|  
|SQL_DESC_OCTET_LENGTH|Core|  
|SQL_DESC_OCTET_LENGTH_PTR|Core|  
|SQL_DESC_PARAMETER_TYPE|Noyau/Niveau 2[2]|  
|SQL_DESC_PRECISION|Core|  
|SQL_DESC_ROWVER|Niveau 1|  
|SQL_DESC_SCALE|Core|  
|SQL_DESC_SCHEMA_NAME|Niveau 1|  
|SQL_DESC_SEARCHABLE|Core|  
|SQL_DESC_TABLE_NAME|Niveau 1|  
|SQL_DESC_TYPE|Core|  
|SQL_DESC_TYPE_NAME|Core|  
|SQL_DESC_UNNAMED|Core|  
|SQL_DESC_UNSIGNED|Core|  
|SQL_DESC_UPDATABLE|Core|  
  
 [1] Le soutien à ces champs de dossiers n’est nécessaire que si le conducteur prend en charge les types de données applicables.  
  
 [2] Pour la conformité de niveau de base, le conducteur doit soutenir SQL_PARAM_INPUT. Pour la conformité à l’interface de niveau 2, le conducteur doit également prendre en charge SQL_PARAM_INPUT_OUTPUT et SQL_PARAM_OUTPUT.
