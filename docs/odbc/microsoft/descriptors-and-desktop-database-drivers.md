---
description: Descripteurs et pilotes pour les bases de données de poste de travail
title: Descripteurs et pilotes de base de données de bureau | Microsoft Docs
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
ms.openlocfilehash: 80565f912ef3136dc03cf7216ff3f997ee3eeba3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340795"
---
# <a name="descriptors-and-desktop-database-drivers"></a>Descripteurs et pilotes pour les bases de données de poste de travail
Un descripteur est une structure de données qui contient des informations sur les données de colonne ou les paramètres dynamiques. **SQLGetDescField** peut être utilisé pour récupérer les descripteurs pris en charge ci-dessous. Les descripteurs de paramètre d’implémentation (IPD) ne sont pas remplis automatiquement, car **SQLDescribeParam** n’est pas pris en charge. Les champs de descripteur qui ne sont pas disponibles via Jet (tels que SQL_DESC_BASE_TABLE_NAME) ne sont pas non plus pris en charge.  
  
 Pour plus d’informations sur les champs de descripteur pris en charge par jet, consultez le *Guide du programmeur Microsoft jet moteur de base de données*.  
  
 Pour plus d’informations sur les descripteurs, consultez les rubriques sous « descripteurs » dans le *Guide de référence du programmeur ODBC*.  
  
|Champs de descripteur|Niveau de support|  
|-----------------------|-------------------|  
|SQL_DESC_ALLOC_TYPE|Prise en charge|  
|SQL_DESC_ARRAY_SIZE|Pris en charge uniquement pour ARD|  
|SQL_DESC_ARRAY_STATUS_PTR|Prise en charge|  
|SQL_DESC_BIND_OFFSET_PTR|Prise en charge|  
|SQL_DESC_BIND_TYPE|Prise en charge|  
|SQL_DESC_COUNT|Prise en charge|  
|SQL_DESC_ROWS_PROCESSED_PTR|Pris en charge uniquement pour ARD|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Prise en charge|  
|SQL_DESC_BASE_COLUMN_NAME|Pris en charge (nouveau)|  
|SQL_DESC_BASE_TABLE_NAME|Pris en charge (nouveau)|  
|SQL_DESC_CASE_SENSITIVE|Toujours FALSe|  
|SQL_DESC_CATALOG_NAME|Non pris en charge|  
|SQL_DESC_CONCISE_TYPE|Prise en charge|  
|SQL_DESC_DATA_PTR|Prise en charge|  
|SQL_DESC_DATETIME_INTERVAL_CODE|Prise en charge|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|Pris en charge pour les types d’intervalle C|  
|SQL_DESC_DISPLAY_SIZE|Prise en charge|  
|SQL_DESC_FIXED_PREC_SCALE|Pris en charge (vrai pour Money)|  
|SQL_DESC_INDICATOR_PTR|Prise en charge|  
|SQL_DESC_LABEL|Prise en charge|  
|SQL_DESC_LENGTH|Prise en charge|  
|SQL_DESC_LITERAL_PREFIX|Prise en charge|  
|SQL_DESC_LITERAL_SUFFIX|Prise en charge|  
|SQL_DESC_LOCAL_TYPE_NAME|Non pris en charge (retourne une chaîne vide)|  
|SQL_DESC_NAME|Prise en charge|  
|SQL_DESC_NULLABLE|Prise en charge<br /><br /> **Remarque** Non pris en charge dans les versions précédentes de Jet 4,0|  
|SQL_DESC_NUM_PREC_RADIX|Prise en charge|  
|SQL_DESC_OCTET_LENGTH|Prise en charge|  
|SQL_DESC_OCTET_LENGTH_PTR|Prise en charge|  
|SQL_DESC_PARAMETER_TYPE|Uniquement les paramètres d’entrée|  
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
