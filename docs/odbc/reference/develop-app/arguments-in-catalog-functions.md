---
title: Arguments de fonctions de catalogue | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- arguments in catalog functions [ODBC]
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], about arguments
- functions [ODBC], catalog functions
ms.assetid: f5e0abec-8f24-42e0-b94f-16dd1f2004fd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f8939b2e1ae81c3eb171e78753e7fc3b6cc17ae
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="arguments-in-catalog-functions"></a>Arguments de fonctions de catalogue
Toutes les fonctions de catalogue acceptent des arguments avec lequel une application peut restreindre l’étendue des données retournées. Par exemple, les premier et deuxième appels à **SQLTables** dans le code suivant retourne un jeu de résultats contenant plus d’informations sur toutes les tables, tandis que le troisième appel retourne des informations sur la table Orders :  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, NULL, 0, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "%", SQL_NTS, NULL, 0);  
SQLTables(hstmt3, NULL, 0, NULL, 0, "Orders", SQL_NTS, NULL, 0);  
```  
  
 Arguments de chaîne de fonction de catalogue est comprise dans les quatre types différents : ordinaire (OA), argument de valeur de modèle (PV), l’argument identificateur (ID) et liste argument valeur (licence en volume). La plupart des arguments de chaîne peuvent être l’une de deux types différents, selon la valeur de l’attribut d’instruction SQL_ATTR_METADATA_ID. Le tableau suivant répertorie les arguments pour chaque fonction de catalogue et décrit le type de l’argument pour une valeur SQL_TRUE ou SQL_FALSE de SQL_ATTR_METADATA_ID.  
  
|Fonction|Argument|Type de SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_FALSE|Type de SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_TRUE|  
|--------------|--------------|---------------------------------------------------------------|--------------------------------------------------------------|  
|**SQLColumnPrivileges**|*Nom de catalogue* *SchemaName* *TableName* *nom de colonne*|OA OA OA PV|ID ID ID ID|  
|**SQLColumns**|*Nom de catalogue* *SchemaName* *TableName* *nom de colonne*|OA PV PV PV|ID ID ID ID|  
|**SQLForeignKeys**|*PKCatalogName* *PKSchemaName* *PKTableName* *FKCatalogName* *FKSchemaName* *FKTableName*|OA OA OA OA OA OA|ID ID ID ID ID ID|  
|**SQLPrimaryKeys**|*Nom de catalogue* *SchemaName* *TableName*|OA OA OA|ID DE L’ID ID|  
|**SQLProcedureColumns**|*Nom de catalogue* *SchemaName* *ProcName* *nom de colonne*|OA PV PV PV|ID ID ID ID|  
|**SQLProcedures**|*Nom de catalogue* *SchemaName* *ProcName*|OA PV PV|ID DE L’ID ID|  
|**SQLSpecialColumns**|*Nom de catalogue* *SchemaName* *TableName*|OA OA OA|ID DE L’ID ID|  
|**SQLStatistics**|*Nom de catalogue* *SchemaName* *TableName*|OA OA OA|ID DE L’ID ID|  
|**SQLTablePrivileges**|*Nom de catalogue* *SchemaName* *TableName*|OA PV PV|ID DE L’ID ID|  
|**SQLTables**|*Nom de catalogue* *SchemaName* *TableName* *TableType*|LICENCES EN VOLUME DE PV PV PV|LICENCES EN VOLUME DE ID ID ID|  
  
 Cette section contient les rubriques suivantes.  
  
-   [Arguments ordinaires](../../../odbc/reference/develop-app/ordinary-arguments.md)  
  
-   [Arguments de valeur de modèle](../../../odbc/reference/develop-app/pattern-value-arguments.md)  
  
-   [Arguments de l’identificateur](../../../odbc/reference/develop-app/identifier-arguments.md)  
  
-   [Arguments de liste de valeurs](../../../odbc/reference/develop-app/value-list-arguments.md)
