---
title: "Méthode allTablesAreSelectable (SQLServerDatabaseMetaData) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.allTablesAreSelectable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eb340450-45a7-49c8-84bc-1b9dd5ee842f
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6d605d9c9725c5819af595115292e1cc3752ec0c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="alltablesareselectable-method-sqlserverdatabasemetadata"></a>Méthode allTablesAreSelectable (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère si l’utilisateur actuel dispose d’autorisations pour toutes les tables qui sont retournées par la [getTables](../../../connect/jdbc/reference/gettables-method-sqlserverdatabasemetadata.md) méthode dans une instruction SELECT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean allTablesAreSelectable()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si l’utilisateur dispose des autorisations pour appeler utiliser toutes les tables. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode allTablesAreSelectable est spécifiée par la méthode allTablesAreSelectable dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membres de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
