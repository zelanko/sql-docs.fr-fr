---
title: "Méthode updateBlob (java.lang.String, java.sql.Blob) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerResultSet.updateBlob (java.lang.String, java.sql.Blob)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: fdd47885-c7ec-4599-a645-ad0e082586f4
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3623da3ecc17e31e79cdfb13afa9cd5a1a853af4
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="updateblob-method-javalangstring-javasqlblob"></a>Méthode updateBlob (java.lang.String, java.sql.Blob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une valeur java.sql.Blob.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateBlob(java.lang.String columnName,  
                       java.sql.Blob x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnName*  
  
 A **chaîne** qui contient le nom de colonne.  
  
 *x*  
  
 Un objet Blob.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateBlob est spécifiée par la méthode updateBlob dans l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode updateBlob &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)   
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
