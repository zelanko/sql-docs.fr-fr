---
title: Méthode supportsSchemasInPrivilegeDefinitions | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsSchemasInPrivilegeDefinitions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2957af1d-62d6-4375-b214-bbba9aafcc2d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e2c669d27df0762ee66e37c7fee7be03c0c0d1d1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47694962"
---
# <a name="supportsschemasinprivilegedefinitions-method-sqlserverdatabasemetadata"></a>Méthode supportsSchemasInPrivilegeDefinitions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si un nom de schéma peut être utilisé dans une instruction de définition de privilège.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsSchemasInPrivilegeDefinitions()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si pris en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode supportsSchemasInPrivilegeDefinitions est spécifiée par la méthode supportsSchemasInPrivilegeDefinitions dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
