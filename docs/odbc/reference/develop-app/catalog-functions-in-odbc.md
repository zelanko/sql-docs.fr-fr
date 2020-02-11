---
title: Fonctions de catalogue dans ODBC | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a8cd46fbc8f633ef31f00fa60ced885f9455f185
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68062726"
---
# <a name="catalog-functions-in-odbc"></a>Fonctions de catalogue dans ODBC
ODBC contient les fonctions de catalogue suivantes :  
  
|Fonction|Description|  
|--------------|-----------------|  
|**SQLTables**|Retourne une liste de catalogues, de schémas, de tables ou de types de table dans la source de données.|  
|**SQLColumns**|Retourne une liste de colonnes dans une ou plusieurs tables.|  
|**SQLStatistics**|Retourne une liste de statistiques sur une table unique. Retourne également une liste d’index associés à cette table.|  
|**SQLSpecialColumns**|Retourne une liste de colonnes qui identifie de façon unique une ligne dans une table unique. Retourne également une liste des colonnes de cette table qui sont mises à jour automatiquement.|  
|**SQLPrimaryKeys**|Retourne une liste de colonnes qui composent la clé primaire d’une table unique.|  
|**SQLForeignKeys**|Retourne une liste de clés étrangères dans une table unique ou une liste de clés étrangères dans d’autres tables qui font référence à une table unique.|  
|**SQLTablePrivileges**|Retourne la liste des privilèges associés à une ou plusieurs tables.|  
|**SQLColumnPrivileges**|Retourne la liste des privilèges associés à une ou plusieurs colonnes dans une table unique.|  
|**SQLProcedures**|Retourne une liste de procédures dans la source de données.|  
|**SQLProcedureColumns**|Retourne une liste de paramètres d’entrée et de sortie, la valeur de retour et les colonnes du jeu de résultats d’une procédure unique.|  
|**SQLGetTypeInfo**|Retourne une liste des types de données SQL pris en charge par la source de données. Ces types de données sont généralement utilisés dans les instructions **Create table** et **ALTER TABLE** .|  
  
 Comme **SQLTables**, **SQLColumns**, **SQLStatistics**et **SQLSpecialColumns** sont conformes à l’interface CLI de groupe ouverte, et **SQLGetTypeInfo** est conforme à la norme ISO 92 CLI, elles sont implémentées par la plupart des pilotes. Les autres fonctions de catalogue sont au niveau de la conformité ODBC.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Données retournées par les fonctions de catalogue](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)  
  
-   [Arguments dans les fonctions de catalogue](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)  
  
-   [Vues de schéma](../../../odbc/reference/develop-app/schema-views.md)
