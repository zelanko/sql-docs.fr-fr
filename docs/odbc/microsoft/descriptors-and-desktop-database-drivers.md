---
title: Descripteurs et pilotes de base de données de bureau (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- desktop database drivers [ODBC], descriptors
- Jet-based ODBC drivers [ODBC], descriptors
- descriptors [ODBC], Jet-supported descriptor fields
- ODBC desktop database drivers [ODBC], descriptors
ms.assetid: 9ae2d9b5-365f-4f0a-9116-defe9498b401
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ef79855f71d23e5a884822371f1894eb83442a9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303510"
---
# <a name="descriptors-and-desktop-database-drivers"></a>Descripteurs et pilotes pour les bases de données de poste de travail
Un descripteur est une structure de données qui contient des informations sur les données de colonne ou les paramètres dynamiques. **SQLGetDescField** peut être utilisé pour récupérer les descripteurs pris en charge énumérés ci-dessous. Les descripteurs paramètres de mise en œuvre (IPD) ne sont pas automatiquement peuplés parce que **SQLDescribeParam** n’est pas pris en charge. Les champs descripteur qui ne sont pas disponibles par Jet (comme SQL_DESC_BASE_TABLE_NAME) ne sont pas non plus pris en charge.  
  
 Pour plus d’informations sur les champs descripteur financés par Jet, consultez le *Guide du programmeur de moteurs microsoft Jet Database Engine .*  
  
 Pour plus d’informations sur les descripteurs, voir les sujets sous "Descriptors" dans la *référence du programmeur de l’ODBC*.  
  
|Champs descripteur|Niveau de support|  
|-----------------------|-------------------|  
|SQL_DESC_ALLOC_TYPE|Prise en charge|  
|SQL_DESC_ARRAY_SIZE|Pris en charge uniquement pour ARD|  
|SQL_DESC_ARRAY_STATUS_PTR|Prise en charge|  
|SQL_DESC_BIND_OFFSET_PTR|Prise en charge|  
|SQL_DESC_BIND_TYPE|Prise en charge|  
|SQL_DESC_COUNT|Prise en charge|  
|SQL_DESC_ROWS_PROCESSED_PTR|Pris en charge uniquement pour ARD|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Prise en charge|  
|SQL_DESC_BASE_COLUMN_NAME|Soutenu (NOUVEAU)|  
|SQL_DESC_BASE_TABLE_NAME|Soutenu (NOUVEAU)|  
|SQL_DESC_CASE_SENSITIVE|Toujours FALSE|  
|SQL_DESC_CATALOG_NAME|Non pris en charge|  
|SQL_DESC_CONCISE_TYPE|Prise en charge|  
|SQL_DESC_DATA_PTR|Prise en charge|  
|SQL_DESC_DATETIME_INTERVAL_CODE|Prise en charge|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|Pris en charge pour les types INTERVAL C|  
|SQL_DESC_DISPLAY_SIZE|Prise en charge|  
|SQL_DESC_FIXED_PREC_SCALE|Pris en charge (TRUE pour l’argent)|  
|SQL_DESC_INDICATOR_PTR|Prise en charge|  
|SQL_DESC_LABEL|Prise en charge|  
|SQL_DESC_LENGTH|Prise en charge|  
|SQL_DESC_LITERAL_PREFIX|Prise en charge|  
|SQL_DESC_LITERAL_SUFFIX|Prise en charge|  
|SQL_DESC_LOCAL_TYPE_NAME|Non pris en charge (retours empty string)|  
|SQL_DESC_NAME|Prise en charge|  
|SQL_DESC_NULLABLE|Prise en charge<br /><br /> **Note** Non pris en compte dans les versions précédant Jet 4.0|  
|SQL_DESC_NUM_PREC_RADIX|Prise en charge|  
|SQL_DESC_OCTET_LENGTH|Prise en charge|  
|SQL_DESC_OCTET_LENGTH_PTR|Prise en charge|  
|SQL_DESC_PARAMETER_TYPE|Seuls les paramètres d’entrée|  
|SQL_DESC_PRECISION|Prise en charge|  
|SQL_DESC_SCALE|Prise en charge|  
|SQL_DESC_SCHEMA_NAME|Non pris en charge|  
|SQL_DESC_SEARCHABLE|Prise en charge|  
|SQL_DESC_TABLE_NAME|Non pris en charge|  
|SQL_DESC_TYPE|Prise en charge|  
|SQL_DESC_TYPE_NAME|Prise en charge|  
|SQL_DESC_UNNAMED|Prise en charge|  
|SQL_DESC_UNSIGNED|Prise en charge|  
|SQL_DESC_UPDATABLE|Prise en charge|
