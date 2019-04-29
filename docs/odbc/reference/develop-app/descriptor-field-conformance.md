---
title: Conformité des champs de descripteur | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 193bdadaf36e975b1f79327bfef161daaaed427b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63049849"
---
# <a name="descriptor-field-conformance"></a>Conformité des champs de descripteur
Le tableau suivant indique le niveau de la conformité de chaque champ d’en-tête descripteur ODBC, où il s’agit bien défini.  
  
|Fonction|Niveau de conformité|  
|--------------|-----------------------|  
|SQL_DESC_ALLOC_TYPE|Noyau|  
|SQL_DESC_ARRAY_SIZE|Noyau|  
|SQL_DESC_ARRAY_STATUS_PTR|Core (pour APD dpi et IRD) ; Niveau 1 (ARD)|  
|SQL_DESC_BIND_OFFSET_PTR|Noyau|  
|SQL_DESC_BIND_TYPE|Noyau|  
|SQL_DESC_COUNT|Noyau|  
|SQL_DESC_ROWS_PROCESSED_PTR|Noyau|  
  
 Le tableau suivant indique le niveau de conformité de chaque champ d’enregistrement du descripteur ODBC où cela est bien défini.  
  
|Fonction|Niveau de conformité|  
|--------------|-----------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Niveau 2|  
|SQL_DESC_BASE_COLUMN_NAME|Noyau|  
|SQL_DESC_BASE_TABLE_NAME|Niveau 1|  
|SQL_DESC_CASE_SENSITIVE|Noyau|  
|SQL_DESC_CATALOG_NAME|Niveau 2|  
|SQL_DESC_CONCISE_TYPE|Noyau|  
|SQL_DESC_DATA_PTR|Noyau|  
|SQL_DESC_DATETIME_INTERVAL_ CODE|Core [1]|  
|SQL_DESC_DATETIME_INTERVAL_ PRECISION|Core [1]|  
|SQL_DESC_DISPLAY_SIZE|Noyau|  
|SQL_DESC_FIXED_PREC_SCALE|Noyau|  
|SQL_DESC_INDICATOR_PTR|Noyau|  
|SQL_DESC_LABEL|Niveau 2|  
|SQL_DESC_LENGTH|Noyau|  
|SQL_DESC_LITERAL_PREFIX|Noyau|  
|SQL_DESC_LITERAL_SUFFIX|Noyau|  
|SQL_DESC_LOCAL_TYPE_NAME|Noyau|  
|SQL_DESC_NAME|Noyau|  
|SQL_DESC_NULLABLE|Noyau|  
|SQL_DESC_OCTET_LENGTH|Noyau|  
|SQL_DESC_OCTET_LENGTH_PTR|Noyau|  
|SQL_DESC_PARAMETER_TYPE|Niveau du noyau/2 [2]|  
|SQL_DESC_PRECISION|Noyau|  
|SQL_DESC_ROWVER|Niveau 1|  
|SQL_DESC_SCALE|Noyau|  
|SQL_DESC_SCHEMA_NAME|Niveau 1|  
|SQL_DESC_SEARCHABLE|Noyau|  
|SQL_DESC_TABLE_NAME|Niveau 1|  
|SQL_DESC_TYPE|Noyau|  
|SQL_DESC_TYPE_NAME|Noyau|  
|SQL_DESC_UNNAMED|Noyau|  
|SQL_DESC_UNSIGNED|Noyau|  
|SQL_DESC_UPDATABLE|Noyau|  
  
 [1] prise en charge pour ces champs d’enregistrement est requis uniquement si le pilote prend en charge les types de données applicable.  
  
 [2] pour la conformité au niveau du noyau, le pilote doit prendre en charge SQL_PARAM_INPUT. Pour la conformité de l’interface de niveau 2, le pilote doit également prendre en charge SQL_PARAM_INPUT_OUTPUT et SQL_PARAM_OUTPUT.
