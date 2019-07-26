---
title: Méthode getMaxStatements (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxStatements
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 71d58431-b671-49c5-939a-f581d1fef7cd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2af23d551982787c7c20332f2c48049b95fd83d5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67981969"
---
# <a name="getmaxstatements-method-sqlserverdatabasemetadata"></a>Méthode getMaxStatements (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre maximal d'instructions actives autorisé pour cette base de données qui peuvent être ouvertes en même temps.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getMaxStatements()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **int** indiquant le nombre maximal d’instructions actives autorisé.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getMaxStatements est spécifiée par la méthode getMaxStatements dans l’interface java. Sql. DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
