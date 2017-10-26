---
title: "Méthode getColumnDisplaySize (SQLServerResultSetMetaData) | Documents Microsoft"
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
- SQLServerResultSetMetaData.getColumnDisplaySize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 21c25443-bd2b-4b60-9798-4efe2c158952
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 10eb09f395c661e7cc46629662d62e43bd937f05
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getcolumndisplaysize-method-sqlserverresultsetmetadata"></a>Méthode getColumnDisplaySize (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la largeur maximale normale, en caractères, pour la colonne désignée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getColumnDisplaySize(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *colonne*  
  
 Un **int** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique la largeur maximale. Si la largeur n'est pas connue, retourne 0.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getColumnDisplaySize est spécifiée par la méthode getColumnDisplaySize dans l’interface java.sql.ResultSetMetaData.  
  
 [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Version 3.0 du pilote JDBC comporte des modifications de comportement dans la colonne COLUMN_SIZE. Consultez [SQLServerDatabaseMetaData.getColumns](../../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  

