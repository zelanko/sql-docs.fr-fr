---
title: Fonctions de catalogue à ODBC ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], listed
- functions [ODBC], catalog functions
ms.assetid: 4f28f557-7eca-4905-aa6d-45a6cf501a66
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c6731018b99f2f3043e48ee7c174a08cb9ef71fc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306230"
---
# <a name="catalog-functions-in-odbc"></a>Fonctions de catalogue dans ODBC
ODBC contient les fonctions de catalogue suivantes :  
  
|Fonction|Description|  
|--------------|-----------------|  
|**SQLTables**|Renvoie une liste de catalogues, schémas, tableaux ou types de table dans la source de données.|  
|**SQLColumns**|Retourne une liste de colonnes dans une ou plusieurs tables.|  
|**SQLStatistics**|Retourne une liste de statistiques sur un tableau unique. Retourne également une liste d’index associés à ce tableau.|  
|**SQLSpecialColumns**|Retourne une liste de colonnes qui identifie uniquement une ligne dans une seule table. Renvoie également une liste de colonnes dans ce tableau qui sont automatiquement mises à jour.|  
|**SQLPrimaryKeys**|Retourne une liste de colonnes qui composent la clé principale d’une seule table.|  
|**SQLForeignKeys**|Retourne une liste de clés étrangères dans une seule table ou une liste de clés étrangères dans d’autres tableaux qui se réfèrent à une seule table.|  
|**SQLTablePrivileges**|Retourne une liste de privilèges associés à une ou plusieurs tables.|  
|**SQLColumnPrivileges**|Renvoie une liste de privilèges associés à une ou plusieurs colonnes dans un seul tableau.|  
|**SQLProcedures**|Renvoie une liste de procédures dans la source de données.|  
|**SQLProcedureColumns**|Retourne une liste des paramètres d’entrée et de sortie, la valeur de retour et les colonnes dans l’ensemble de résultat d’une seule procédure.|  
|**SQLGetTypeInfo**|Renvoie une liste des types de données SQL pris en charge par la source de données. Ces types de données sont généralement utilisés dans les instructions **CREATE TABLE** et **ALTER TABLE.**|  
  
 Parce que **SQLTables**, **SQLColumns**, **SQLStatistics**, et **SQLSpecialColumns** se conforment à l’Open Group CLI, et **SQLGetTypeInfo** conforme à l’ISO 92 CLI, ils sont mis en œuvre par la plupart des conducteurs. Les fonctions restantes du catalogue se trouvent au niveau de conformité ODBC.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Données retournées par les fonctions de catalogue](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)  
  
-   [Arguments dans les fonctions de catalogue](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)  
  
-   [Vues de schéma](../../../odbc/reference/develop-app/schema-views.md)
