---
description: Méthode supportsExtendedSQLGrammar (SQLServerDatabaseMetaData)
title: Méthode supportsExtendedSQLGrammar (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsExtendedSQLGrammar
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8deb1987-c4e3-4599-8e37-0a04ec20b480
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 24c8eece643ac147003d727861e77b22bbee236e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88478531"
---
# <a name="supportsextendedsqlgrammar-method-sqlserverdatabasemetadata"></a>Méthode supportsExtendedSQLGrammar (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si cette base de données prend en charge la grammaire SQL étendue ODBC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsExtendedSQLGrammar()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** en cas de prise en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode supportsExtendedSQLGrammer est spécifiée par la méthode supportsExtendedSQLGrammer dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
