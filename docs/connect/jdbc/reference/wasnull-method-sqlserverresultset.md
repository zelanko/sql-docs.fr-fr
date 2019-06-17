---
title: wasNull, méthode (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.wasNull
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d37f80ef-d72c-4429-ada3-1d685bdab6d7
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e4e8ae304208a6b4cf9c76fa26920ea16d45faca
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802533"
---
# <a name="wasnull-method-sqlserverresultset"></a>wasNull, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Vérifie si la dernière valeur lue était une valeur Null.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean wasNull()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si la dernière valeur de lecture avait la valeur null. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode wasNull est spécifiée par la méthode wasNull de l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
