---
title: Conformité du champ de descripteur | Microsoft Docs
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
ms.openlocfilehash: afdb1f18ad641224d13373436dd58f1919a3d280
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67952344"
---
# <a name="descriptor-field-conformance"></a>Conformité des champs de descripteur
Le tableau suivant indique le niveau de conformité de chaque champ d’en-tête de descripteur ODBC, où ce est bien défini.  
  
|Fonction|Niveau de conformité|  
|--------------|-----------------------|  
|SQL_DESC_ALLOC_TYPE|Core|  
|SQL_DESC_ARRAY_SIZE|Core|  
|SQL_DESC_ARRAY_STATUS_PTR|Core (pour APD, dpi et IRD); Niveau 1 (pour ARD)|  
|SQL_DESC_BIND_OFFSET_PTR|Core|  
|SQL_DESC_BIND_TYPE|Core|  
|SQL_DESC_COUNT|Core|  
|SQL_DESC_ROWS_PROCESSED_PTR|Core|  
  
 Le tableau suivant indique le niveau de conformité de chaque champ d’enregistrement de descripteur ODBC, où ce est bien défini.  
  
|Fonction|Niveau de conformité|  
|--------------|-----------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Level 2|  
|SQL_DESC_BASE_COLUMN_NAME|Core|  
|SQL_DESC_BASE_TABLE_NAME|Niveau 1|  
|SQL_DESC_CASE_SENSITIVE|Core|  
|SQL_DESC_CATALOG_NAME|Level 2|  
|SQL_DESC_CONCISE_TYPE|Core|  
|SQL_DESC_DATA_PTR|Core|  
|CODE SQL_DESC_DATETIME_INTERVAL_|Noyau [1]|  
|PRÉCISION SQL_DESC_DATETIME_INTERVAL_|Noyau [1]|  
|SQL_DESC_DISPLAY_SIZE|Core|  
|SQL_DESC_FIXED_PREC_SCALE|Core|  
|SQL_DESC_INDICATOR_PTR|Core|  
|SQL_DESC_LABEL|Level 2|  
|SQL_DESC_LENGTH|Core|  
|SQL_DESC_LITERAL_PREFIX|Core|  
|SQL_DESC_LITERAL_SUFFIX|Core|  
|SQL_DESC_LOCAL_TYPE_NAME|Core|  
|SQL_DESC_NAME|Core|  
|SQL_DESC_NULLABLE|Core|  
|SQL_DESC_OCTET_LENGTH|Core|  
|SQL_DESC_OCTET_LENGTH_PTR|Core|  
|SQL_DESC_PARAMETER_TYPE|Core/niveau 2 [2]|  
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
  
 [1] la prise en charge de ces champs d’enregistrement est requise uniquement si le pilote prend en charge les types de données applicables.  
  
 [2] pour la conformité au niveau du noyau, le pilote doit prendre en charge SQL_PARAM_INPUT. Pour la conformité de l’interface de niveau 2, le pilote doit également prendre en charge SQL_PARAM_INPUT_OUTPUT et SQL_PARAM_OUTPUT.
