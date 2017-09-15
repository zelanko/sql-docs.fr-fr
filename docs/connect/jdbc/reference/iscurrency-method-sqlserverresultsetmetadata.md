---
title: "Méthode isCurrency (SQLServerResultSetMetaData) | Documents Microsoft"
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
- SQLServerResultSetMetaData.isCurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7fe25d90-693c-4d3b-9dd2-0f8351c5a9ed
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d174c5a63cf47ef53eb05634a94ea5506001db4e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="iscurrency-method-sqlserverresultsetmetadata"></a>Méthode isCurrency (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si la colonne désignée est une valeur de devise.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isCurrency(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *colonne*  
  
 Un **int** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si la colonne est une valeur de devise. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isCurrency est spécifiée par la méthode isCurrency dans l’interface java.sql.ResultSetMetaData.  
  
 Cette méthode retournera **true** uniquement avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] les types de données money et smallmoney.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Membres de SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
