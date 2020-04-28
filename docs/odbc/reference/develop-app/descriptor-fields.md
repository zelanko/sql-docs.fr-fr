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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94e70de7d237c2eca9aee81979cb19d5295561b5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305920"
---
# <a name="descriptor-fields"></a>Champs de descripteur
Les descripteurs contiennent des champs d' *en-tête* et d' *enregistrement* qui décrivent complètement des colonnes ou des paramètres.  
  
 Un descripteur contient une seule copie des champs d’en-tête suivants. La modification d’un champ d’en-tête affecte toutes les colonnes ou tous les paramètres.  
  
|||  
|-|-|  
|SQL_DESC_ALLOC_TYPE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_COUNT|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 Un descripteur contient zéro ou plusieurs enregistrements de descripteur. Chaque enregistrement décrit une colonne ou un paramètre, en fonction du type de descripteur. Lorsqu’une nouvelle colonne ou un nouveau paramètre est lié, un nouvel enregistrement est ajouté au descripteur. Lorsqu’une colonne ou un paramètre est indépendant, un enregistrement est supprimé du descripteur. Chaque enregistrement contient une copie unique des champs suivants :  
  
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
  
 De nombreux attributs d’instruction correspondent au champ d’en-tête d’un descripteur. La définition de ces attributs via un appel à **SQLSetStmtAttr** et la définition du champ d’en-tête du descripteur correspondant en appelant **SQLSetDescField** ont le même effet. Il en va de même pour **SQLGetStmtAttr** et **SQLGetDescField**, qui récupèrent les mêmes informations. L’appel des fonctions d’instruction à la place des fonctions de descripteur présente l’avantage qu’il n’est pas nécessaire de récupérer un handle de descripteur.  
  
 Les champs d’en-tête suivants peuvent être définis en définissant des attributs d’instruction :  
  
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
