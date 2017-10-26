---
title: "getFetchDirection (méthode) (SQLServerResultSet) | Documents Microsoft"
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
- SQLServerResultSet.getFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5ab385c2-e18c-4b75-ac2d-2402af5c52a5
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2667676b22af4c4f25b8adfb4bb0565dd2e6abf9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getfetchdirection-method-sqlserverresultset"></a>getFetchDirection (méthode) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la direction d’extraction pour cette [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getFetchDirection()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique la direction d’extraction actuel.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getFetchDirection est spécifiée par la méthode getFetchDirection dans l’interface java.sql.ResultSet.  
  
 Cette méthode retourne FETCH_FORWARD pour les curseurs avant uniquement, le dernier paramètre défini par un appel à la [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverresultset.md) méthode pour d’autres types de curseur et elle retourne FETCH_UNKNOWN ces types de curseur si la méthode setFetchDirection n’a jamais été appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

