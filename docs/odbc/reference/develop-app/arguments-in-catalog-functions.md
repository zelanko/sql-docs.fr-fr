---
title: Arguments dans les fonctions de catalogue | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arguments in catalog functions [ODBC]
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], about arguments
- functions [ODBC], catalog functions
ms.assetid: f5e0abec-8f24-42e0-b94f-16dd1f2004fd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 649c00f1db486dab4a996138be4e26b0e270fbae
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106291"
---
# <a name="arguments-in-catalog-functions"></a>Arguments dans les fonctions de catalogue
Toutes les fonctions de catalogue acceptent des arguments avec laquelle une application peut restreindre l’étendue des données retournées. Par exemple, les première et deuxième appels à **SQLTables** dans le code suivant retourne un jeu de résultats contenant des informations sur toutes les tables, tandis que le troisième appel retourne des informations sur la table Orders :  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, NULL, 0, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "%", SQL_NTS, NULL, 0);  
SQLTables(hstmt3, NULL, 0, NULL, 0, "Orders", SQL_NTS, NULL, 0);  
```  
  
 Arguments de chaîne de fonction de catalogue se répartissent en quatre types différents : ordinaire (OA), argument de valeur de modèle (PV), l’argument identificateur (ID) et liste argument valeur (LV). La plupart des arguments de chaîne peuvent être un des deux types différents, selon la valeur de l’attribut d’instruction SQL_ATTR_METADATA_ID. Le tableau suivant répertorie les arguments pour chaque fonction de catalogue et décrit le type de l’argument pour une valeur SQL_TRUE ou SQL_FALSE de SQL_ATTR_METADATA_ID.  
  
|Fonction|Argument|Type quand SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_FALSE|Type quand SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_TRUE|  
|--------------|--------------|---------------------------------------------------------------|--------------------------------------------------------------|  
|**SQLColumnPrivileges**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA OA OA PV|ID : ID ID ID|  
|**SQLColumns**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA PV PV PV|ID : ID ID ID|  
|**SQLForeignKeys**|*PKCatalogName* *PKSchemaName* *PKTableName* *FKCatalogName* *FKSchemaName* *FKTableName*|OA OA OA OA OA OA|ID ID ID ID ID ID|  
|**SQLPrimaryKeys**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID : ID ID|  
|**SQLProcedureColumns**|*CatalogName* *SchemaName* *ProcName* *ColumnName*|OA PV PV PV|ID : ID ID ID|  
|**SQLProcedures**|*CatalogName* *SchemaName* *ProcName*|OA PV PV|ID : ID ID|  
|**SQLSpecialColumns**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID : ID ID|  
|**SQLStatistics**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID : ID ID|  
|**SQLTablePrivileges**|*CatalogName* *SchemaName* *TableName*|OA PV PV|ID : ID ID|  
|**SQLTables**|*CatalogName* *SchemaName* *TableName* *TableType*|PV PV PV LV|ID ID ID LV|  
  
 Cette section contient les rubriques suivantes.  
  
-   [Arguments ordinaires](../../../odbc/reference/develop-app/ordinary-arguments.md)  
  
-   [Arguments de valeur de modèle](../../../odbc/reference/develop-app/pattern-value-arguments.md)  
  
-   [Arguments d’identificateur](../../../odbc/reference/develop-app/identifier-arguments.md)  
  
-   [Arguments de liste de valeurs](../../../odbc/reference/develop-app/value-list-arguments.md)
