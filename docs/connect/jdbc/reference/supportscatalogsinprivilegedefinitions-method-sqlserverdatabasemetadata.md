---
title: Méthode supportsCatalogsInPrivilegeDefinitions | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsCatalogsInPrivilegeDefinitions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cc18f99e-c19f-4bd0-96ae-b9a6a0de1926
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72b43529354693acfb3d73248d7aab0eb2ab5140
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789647"
---
# <a name="supportscatalogsinprivilegedefinitions-method-sqlserverdatabasemetadata"></a>Méthode supportsCatalogsInPrivilegeDefinitions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si un nom de catalogue peut être utilisé dans une instruction de définition de privilège.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsCatalogsInPrivilegeDefinitions()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si pris en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode supportsCatalogsInPrivilegeDefinitions est spécifiée par la méthode supportsCatalogsInPrivilegeDefinitions dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
