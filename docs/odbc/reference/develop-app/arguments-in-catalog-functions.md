---
description: Arguments dans les fonctions de catalogue
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ef53514f41d28e93648970b03fa53927529d8344
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483132"
---
# <a name="arguments-in-catalog-functions"></a>Arguments dans les fonctions de catalogue
Toutes les fonctions de catalogue acceptent les arguments avec lesquels une application peut limiter l’étendue des données retournées. Par exemple, le premier et le deuxième appel à **SQLTables** dans le code suivant retournent un jeu de résultats contenant des informations sur toutes les tables, tandis que le troisième appel retourne des informations sur la table Orders :  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, NULL, 0, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "%", SQL_NTS, NULL, 0);  
SQLTables(hstmt3, NULL, 0, NULL, 0, "Orders", SQL_NTS, NULL, 0);  
```  
  
 Les arguments de chaîne de fonction de catalogue se répartissent en quatre types différents : argument ordinaire (OA), argument de valeur de modèle (PV), argument d’identificateur (ID) et argument de liste de valeurs (VL). La plupart des arguments de chaîne peuvent être de l’un des deux types différents, en fonction de la valeur de l’attribut d’instruction SQL_ATTR_METADATA_ID. Le tableau suivant répertorie les arguments pour chaque fonction de catalogue et décrit le type de l’argument pour une SQL_TRUE ou SQL_FALSE valeur de SQL_ATTR_METADATA_ID.  
  
|Fonction|Argument|Tapez quand SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_FALSE|Tapez quand SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_TRUE|  
|--------------|--------------|---------------------------------------------------------------|--------------------------------------------------------------|  
|**SQLColumnPrivileges**|*Nomcatalogue* *SchemaName* *TableName* , *ColumnName*|OA OA OA PV|ID ID ID|  
|**SQLColumns**|*Nomcatalogue* *SchemaName* *TableName* , *ColumnName*|OA PV PV PV|ID ID ID|  
|**SQLForeignKeys**|*PKCatalogName* *PKSchemaName* *PKTableName* *FKCatalogName* *FKSchemaName* *FKTableName*|OA OA OA OA OA|ID ID ID ID ID|  
|**SQLPrimaryKeys**|*Nomcatalogue* *SchemaName* *TableName*|OA OA OA|ID ID ID|  
|**SQLProcedureColumns**|*Nomcatalogue* *SchemaName* - *CNAME* *ColumnName*|OA PV PV PV|ID ID ID|  
|**SQLProcedures**|*Nomcatalogue* *SchemaName* - *CNAME*|OA PV PV|ID ID ID|  
|**SQLSpecialColumns**|*Nomcatalogue* *SchemaName* *TableName*|OA OA OA|ID ID ID|  
|**SQLStatistics**|*Nomcatalogue* *SchemaName* *TableName*|OA OA OA|ID ID ID|  
|**SQLTablePrivileges**|*Nomcatalogue* *SchemaName* *TableName*|OA PV PV|ID ID ID|  
|**SQLTables**|*Nomcatalogue* *SchemaName* *TableName* *TABLETYPE*|PV PV PV DE LICENCE EN VOLUME|ID ID VL|  
  
 Cette section contient les rubriques suivantes :  
  
-   [Arguments ordinaires](../../../odbc/reference/develop-app/ordinary-arguments.md)  
  
-   [Arguments de valeur de modèle](../../../odbc/reference/develop-app/pattern-value-arguments.md)  
  
-   [Arguments d’identificateur](../../../odbc/reference/develop-app/identifier-arguments.md)  
  
-   [Arguments de liste de valeurs](../../../odbc/reference/develop-app/value-list-arguments.md)
