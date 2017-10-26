---
title: "Méthode setFetchDirection (SQLServerResultSet) | Documents Microsoft"
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
- SQLServerResultSet.setFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4ee82290-508d-4bff-a5c5-8a56338deef8
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dd6ab9a94acf883ed27cdd79fee886b6c54ca596
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="setfetchdirection-method-sqlserverresultset"></a>Méthode setFetchDirection (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Fournit un Conseil concernant la direction dans laquelle les lignes dans cette [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet est traité.  
  
> [!NOTE]  
>  Cette méthode n’est pas actuellement pris en charge par le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Si vous utilisez cette méthode, le pilote JDBC mémorise le paramètre, mais actuellement il n'intervient pas dessus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setFetchDirection(int direction)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *direction*  
  
 Un **int** qui indique la direction d’extraction suggérée. Il peut s'agir de l'une des valeurs suivantes :  
  
 ResultSet.FETCH_FORWARD  
  
 ResultSet.FETCH_REVERSE  
  
 ResultSet.FETCH_UNKNOWN  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setFetchDirection est spécifiée par la méthode setFetchDirection dans l’interface java.sql.ResultSet.  
  
 La valeur initiale de cette méthode est déterminée par le [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objet qui a produit cet objet SQLServerResultSet. La direction d'extraction peut être modifiée à tout moment.  
  
> [!NOTE]  
>  L'utilisation de cette méthode lorsque le type de curseur est avant uniquement est sans effet.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

