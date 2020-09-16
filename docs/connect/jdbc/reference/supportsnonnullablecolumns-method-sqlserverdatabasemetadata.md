---
description: Méthode supportsNonNullableColumns (SQLServerDatabaseMetaData)
title: Méthode supportsNonNullableColumns (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsNonNullableColumns
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7c32ea64-460e-4636-8a3b-07c8abeed687
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f7ef982726532c66448cd5dd5fd46219db8fba0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450301"
---
# <a name="supportsnonnullablecolumns-method-sqlserverdatabasemetadata"></a>Méthode supportsNonNullableColumns (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si les colonnes dans cette base de données peuvent être définies comme n'acceptant pas la valeur Null.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsNonNullableColumns()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** en cas de prise en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode supportsNonNullableColumns est spécifiée par la méthode supportsNonNullableColumns de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
