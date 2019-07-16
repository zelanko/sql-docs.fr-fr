---
title: Champs de descripteur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], fields
- header fields [ODBC]
- record fields [ODBC]
ms.assetid: f38623c8-fdd4-4601-b1f0-97c593d31177
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5025bf5eee4b0b65342e7ce47cbbde4ae9ef6b7e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106169"
---
# <a name="descriptor-fields"></a>Champs de descripteur
Les descripteurs contiennent *en-tête* et *enregistrement* champs qui décrivent complètement les colonnes ou paramètres.  
  
 Un descripteur contient une seule copie des champs d’en-tête suivants. Modification d’un champ d’en-tête affecte toutes les colonnes ou paramètres.  
  
|||  
|-|-|  
|SQL_DESC_ALLOC_TYPE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_COUNT|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 Un descripteur contient zéro ou plusieurs enregistrements de descripteurs. Chaque enregistrement décrit une colonne ou un paramètre, selon le type de descripteur. Lorsqu’une nouvelle colonne ou un paramètre est lié, un nouvel enregistrement est ajouté au descripteur. Une colonne ou un paramètre est indépendant, un enregistrement est supprimé à partir du descripteur. Chaque enregistrement contient une seule copie des champs suivants :  
  
|||  
|-|-|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_DESC_LOCAL_TYPE_NAME|  
|SQL_DESC_BASE_COLUMN_NAME|SQL_DESC_NAME|  
|SQL_DESC_BASE_TABLE_NAME|SQL_DESC_NULLABLE|  
|SQL_DESC_CASE_SENSITIVE|SQL_DESC_OCTET_LENGTH|  
|SQL_DESC_CATALOG_NAME|SQL_DESC_OCTET_LENGTH_PTR|  
|SQL_DESC_CONCISE_TYPE|SQL_DESC_PARAMETER_TYPE|  
|SQL_DESC_DATA_PTR|SQL_DESC_PRECISION|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_DESC_SCALE|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|SQL_DESC_SCHEMA_NAME|  
|SQL_DESC_DISPLAY_SIZE|SQL_DESC_SEARCHABLE|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_DESC_TABLE_NAME|  
|SQL_DESC_INDICATOR_PTR|SQL_DESC_TYPE|  
|SQL_DESC_LABEL|SQL_DESC_TYPE_NAME|  
|SQL_DESC_LENGTH|SQL_DESC_UNNAMED|  
|SQL_DESC_LITERAL_PREFIX|SQL_DESC_UNSIGNED|  
|SQL_DESC_LITERAL_SUFFIX|SQL_DESC_UPDATABLE|  
  
 Plusieurs attributs d’instruction correspondant au champ d’en-tête d’un descripteur. Définition de ces attributs via un appel à **SQLSetStmtAttr** et en définissant le champ d’en-tête de descripteur correspondant en appelant **SQLSetDescField** ont le même effet. Vaut également pour **SQLGetStmtAttr** et **SQLGetDescField**, lesquels récupérer les mêmes informations. Appel des fonctions d’instruction au lieu des fonctions de descripteur a l’avantage qu’un handle de descripteur n’est pas à récupérer.  
  
 Les champs d’en-tête suivant peuvent être définis en définissant les attributs d’instruction :  
  
|||  
|-|-|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 Cette section contient les rubriques suivantes.  
  
-   [Nombre d’enregistrements](../../../odbc/reference/develop-app/record-count.md)  
  
-   [Enregistrements de descripteurs liés](../../../odbc/reference/develop-app/bound-descriptor-records.md)  
  
-   [Champs différés](../../../odbc/reference/develop-app/deferred-fields.md)  
  
-   [Vérification de la cohérence](../../../odbc/reference/develop-app/consistency-check.md)
