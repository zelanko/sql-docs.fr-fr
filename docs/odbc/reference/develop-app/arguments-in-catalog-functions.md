---
title: Arguments dans les fonctions de catalogue (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 819c10d0b137d5e0999c1e10bf22810392509f76
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288165"
---
# <a name="arguments-in-catalog-functions"></a>Arguments dans les fonctions de catalogue
Toutes les fonctions de catalogue acceptent les arguments avec lesquels une application peut restreindre la portée des données retournées. Par exemple, les premier et deuxième appels vers **SQLTables** dans le code suivant renvoient un ensemble de résultats contenant des informations sur toutes les tables, tandis que le troisième appel renvoie des informations sur le tableau des commandes :  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, NULL, 0, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "%", SQL_NTS, NULL, 0);  
SQLTables(hstmt3, NULL, 0, NULL, 0, "Orders", SQL_NTS, NULL, 0);  
```  
  
 Les arguments de chaîne de fonction de catalogue tombent dans quatre types différents : argument ordinaire (OA), argument de valeur de modèle (PV), argument d’identification (ID), et argument de liste de valeur (VL). La plupart des arguments de chaîne peuvent être de l’un des deux types différents, selon la valeur de l’attribut de SQL_ATTR_METADATA_ID déclaration. Le tableau suivant énumère les arguments pour chaque fonction de catalogue et décrit le type de l’argument pour une valeur SQL_TRUE ou SQL_FALSE de SQL_ATTR_METADATA_ID.  
  
|Fonction|Argument|Tapez quand SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID - SQL_FALSE|Tapez quand SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID - SQL_TRUE|  
|--------------|--------------|---------------------------------------------------------------|--------------------------------------------------------------|  
|**SQLColumnPrivileges**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA OA OA PV|ID ID ID ID|  
|**SQLColumns**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA PV PV PV|ID ID ID ID|  
|**SQLForeignKeys**|*PKCatalogName* *PKSchemaName* *PKTableName* *FKCatalogName* *FKSchemaName* *FKTableName*|OA OA OA OA OA OA|ID ID ID ID ID ID|  
|**SQLPrimaryKeys**|*Nom du catalogue* *SchemaName* *TableName*|OA OA OA|ID ID ID|  
|**SQLProcedureColumns**|*CatalogName* *SchemaName* *ProcName* *ColumnNameName*|OA PV PV PV|ID ID ID ID|  
|**SQLProcedures**|*CatalogueName* *SchemaName* *ProcName*|OA PV PV|ID ID ID|  
|**SQLSpecialColumns**|*Nom du catalogue* *SchemaName* *TableName*|OA OA OA|ID ID ID|  
|**SQLStatistics**|*Nom du catalogue* *SchemaName* *TableName*|OA OA OA|ID ID ID|  
|**SQLTablePrivileges**|*Nom du catalogue* *SchemaName* *TableName*|OA PV PV|ID ID ID|  
|**SQLTables**|*CatalogueName* *SchemaName* *TableName* *TableType*|PV PV PV VL|ID ID ID VL|  
  
 Cette section contient les rubriques suivantes :  
  
-   [Arguments ordinaires](../../../odbc/reference/develop-app/ordinary-arguments.md)  
  
-   [Arguments de valeur de modèle](../../../odbc/reference/develop-app/pattern-value-arguments.md)  
  
-   [Arguments d’identificateur](../../../odbc/reference/develop-app/identifier-arguments.md)  
  
-   [Arguments de liste de valeurs](../../../odbc/reference/develop-app/value-list-arguments.md)
