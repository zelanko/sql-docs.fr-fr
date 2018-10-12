---
title: Méthode getColumnClassName (SQLServerResultSetMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.getColumnClassName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2c118790-5dd2-4b10-93b6-7f065ee324ce
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a8e76d8dc4944440eeae5017f6e383af27ad4103
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680321"
---
# <a name="getcolumnclassname-method-sqlserverresultsetmetadata"></a>Méthode getColumnClassName (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le nom complet de la classe Java dont les instances sont créées si la méthode [getObject](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md) de la classe [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) est appelée pour récupérer une valeur à partir de la colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getColumnClassName(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *column*  
  
 Un **int** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 **String** contenant le nom complet de la classe.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getColumnClassName est spécifiée par la méthode getColumnClassName dans l’interface java.sql.ResultSetMetaData.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerResultSetMetaData, méthodes](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData, membres](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
