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
manager: craigg
ms.openlocfilehash: 84c870d45cc487fc9ec5497e43b764bd4187d2f6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63217625"
---
# <a name="catalog-functions-in-odbc"></a>Fonctions de catalogue dans ODBC
ODBC contient les fonctions de catalogue suivantes :  
  
|Fonction|Description|  
|--------------|-----------------|  
|**SQLTables**|Retourne une liste des catalogues, des schémas, des tables ou des types de tables dans la source de données.|  
|**SQLColumns**|Retourne une liste de colonnes dans une ou plusieurs tables.|  
|**SQLStatistics**|Retourne une liste des statistiques sur une seule table. Retourne également une liste des index associés à cette table.|  
|**SQLSpecialColumns**|Retourne une liste de colonnes qui identifie de façon unique une ligne dans une table unique. Retourne également une liste de colonnes dans cette table sont automatiquement mises à jour.|  
|**SQLPrimaryKeys**|Retourne une liste de colonnes qui composent la clé primaire d’une table unique.|  
|**SQLForeignKeys**|Retourne une liste de clés étrangères dans une seule table ou une liste de clés étrangères dans d’autres tables qui font référence à une seule table.|  
|**SQLTablePrivileges**|Retourne une liste de privilèges associés à une ou plusieurs tables.|  
|**SQLColumnPrivileges**|Retourne une liste de privilèges associés à une ou plusieurs colonnes dans une table unique.|  
|**SQLProcedures**|Retourne une liste des procédures dans la source de données.|  
|**SQLProcedureColumns**|Retourne une liste de paramètres d’entrée et de sortie, la valeur de retour et les colonnes du jeu de résultats d’une procédure unique.|  
|**SQLGetTypeInfo**|Retourne une liste des types de données SQL pris en charge par la source de données. Ces types de données sont généralement utilisés dans **CREATE TABLE** et **ALTER TABLE** instructions.|  
  
 Étant donné que **SQLTables**, **SQLColumns**, **SQLStatistics**, et **SQLSpecialColumns** conformes à la CLI de groupe ouvert et **SQLGetTypeInfo** est conforme à la norme ISO CLI 92, ils sont implémentés par la plupart des pilotes. Les autres fonctions de catalogue sont dans le niveau de conformité ODBC.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Données retournées par les fonctions de catalogue](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)  
  
-   [Arguments dans les fonctions de catalogue](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)  
  
-   [Vues de schéma](../../../odbc/reference/develop-app/schema-views.md)
