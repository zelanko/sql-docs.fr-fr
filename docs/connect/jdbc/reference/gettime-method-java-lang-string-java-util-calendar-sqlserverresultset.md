---
title: "Méthode getTime (java.lang.String, java.util.Calendar) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerResultSet.getTime (java.lang.String, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 13b51f77-cec9-45fc-862e-3d2bb2d718d7
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e11256953955a44528d681424c2719a74f684730
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="gettime-method-javalangstring-javautilcalendar-sqlserverresultset"></a>Méthode getTime (java.lang.String, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du nom de colonne désigné dans la ligne actuelle de ce [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet comme un objet java.sql.Time dans le langage de programmation, à l’aide de l’objet de calendrier donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Time getTime(java.lang.String colName,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nom de colonne*  
  
 A **chaîne** qui contient le nom de colonne.  
  
 *licences d’accès client*  
  
 Un objet de calendrier.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet de l’heure.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getTime est spécifiée par la méthode getTime dans l’interface java.sql.ResultSet.  
  
 Cette méthode retourne une partie de l’heure valide d’un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] type de données datetime ou smalldatetime, avec la partie de date définie sur la date de référence Java de 1970/01/01 dans le fuseau horaire du calendrier fourni.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getTime &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/gettime-method-sqlserverresultset.md)   
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

