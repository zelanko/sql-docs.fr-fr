---
title: "Méthode getColumnType (SQLServerResultSetMetaData) | Documents Microsoft"
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
- SQLServerResultSetMetaData.getColumnType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 81815a41-9265-4574-a4d8-f6341a68d9fd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ad090a3ad5377be43f0c91febb79cfbfc56b5330
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getcolumntype-method-sqlserverresultsetmetadata"></a>Méthode getColumnType (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le type SQL de la colonne désignée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getColumnType(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *colonne*  
  
 Un **int** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique le type JDBC comme défini dans java.sql.Types.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getColumnType est spécifiée par la méthode getColumnType dans l’interface java.sql.ResultSetMetaData.  
  
 [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Version 3.0 du pilote JDBC comporte des modifications de comportement dans la colonne DATA_TYPE. Consultez [SQLServerDatabaseMetaData.getColumns](../../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  

