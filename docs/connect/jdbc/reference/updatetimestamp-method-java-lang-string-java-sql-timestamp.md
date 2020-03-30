---
title: updateTimestamp, méthode (java.lang.String, java.sql.Timestamp) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateTimestamp (java.lang.String, java.sql.Timestamp)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6d468357-bf73-484c-9a30-3671e399cf26
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 59d23bf2536806135b2ec5068c2478e30b4353a1
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67998148"
---
# <a name="updatetimestamp-method-javalangstring-javasqltimestamp"></a>Méthode updateTimestamp (java.lang.String, java.sql.Timestamp)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une valeur d'horodateur en fonction du nom de colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateTimestamp(java.lang.String columnName,  
                            java.sql.Timestamp x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnName*  
  
 Valeur **String** qui contient le nom de la colonne.  
  
 *x*  
  
 Valeur d’horodateur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateTimestamp est spécifiée par la méthode updateTimestamp de l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [updateTimestamp, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatetimestamp-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
