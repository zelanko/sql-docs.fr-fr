---
title: Champs descripteur Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94e70de7d237c2eca9aee81979cb19d5295561b5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305920"
---
# <a name="descriptor-fields"></a>Champs de descripteur
Les descripteurs contiennent des champs *d’en-tête* et *d’enregistrement* qui décrivent complètement des colonnes ou des paramètres.  
  
 Un descripteur contient une seule copie des champs d’en-tête suivants. La modification d’un champ d’en-tête affecte toutes les colonnes ou paramètres.  
  
|||  
|-|-|  
|SQL_DESC_ALLOC_TYPE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_COUNT|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 Un descripteur contient zéro ou plus d’enregistrements descripteur. Chaque enregistrement décrit une colonne ou un paramètre, selon le type de descripteur. Lorsqu’une nouvelle colonne ou un nouveau paramètre est lié, un nouvel enregistrement est ajouté au descripteur. Lorsqu’une colonne ou un paramètre n’est pas lié, un enregistrement est supprimé du descripteur. Chaque enregistrement contient une seule copie des champs suivants :  
  
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
  
 De nombreux attributs de déclaration correspondent au champ d’en-tête d’un descripteur. Définir ces attributs par un appel à **SQLSetStmtAttr** et définir le champ d’en-tête descripteur correspondant en appelant **SQLSetDescField** ont le même effet. Il en va de même pour **SQLGetStmtAttr** et **SQLGetDescField**, qui récupèrent tous deux les mêmes informations. Appeler les fonctions de déclaration au lieu des fonctions descripteur a l’avantage qu’une poignée descripteur n’a pas à être récupérée.  
  
 Les champs d’en-tête suivants peuvent être définis en définissant les attributs de l’instruction :  
  
|||  
|-|-|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 Cette section contient les rubriques suivantes :  
  
-   [Nombre d'enregistrements](../../../odbc/reference/develop-app/record-count.md)  
  
-   [Enregistrements de descripteurs liés](../../../odbc/reference/develop-app/bound-descriptor-records.md)  
  
-   [Champs différés](../../../odbc/reference/develop-app/deferred-fields.md)  
  
-   [Vérification de la cohérence](../../../odbc/reference/develop-app/consistency-check.md)
