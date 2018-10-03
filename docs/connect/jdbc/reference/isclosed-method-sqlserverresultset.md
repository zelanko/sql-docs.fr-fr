---
title: IsClosed, méthode (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6081aa34-fc88-4dd0-9a3f-05e8488219dc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c17ec2b88d5f86d94c918dc1a02d4cc2c5a0fdc4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47736187"
---
# <a name="isclosed-method-sqlserverresultset"></a>Méthode isClosed (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) a été fermé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si ce [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet est fermé, **false** si elle est toujours ouverte.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode isClosed est spécifiée par la méthode isClosed dans l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
