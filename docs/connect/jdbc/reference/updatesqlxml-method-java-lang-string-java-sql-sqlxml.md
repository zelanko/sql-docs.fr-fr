---
title: Méthode updateSQLXML (java.lang.String, java.sql.SQLXML) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 60021881-ef83-499b-9977-e20ff23c1312
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 40eb845680bc887f3c28563872a34aa9db627bf5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="updatesqlxml-method-javalangstring-javasqlsqlxml"></a>Méthode updateSQLXML (java.lang.String, java.sql.SQLXML)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une valeur java.sql.SQLXML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateSQLXML(java.lang.String columnLabel,  
                         java.sql.SQLXML xmlObject)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnLabel*  
  
 A **chaîne** qui indique l’étiquette de colonne.  
  
 *xmlObject*  
  
 Un objet SQLXML.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateSQLXML est spécifiée par la méthode updateSQLXML dans l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode updateSQLXML &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md)   
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
