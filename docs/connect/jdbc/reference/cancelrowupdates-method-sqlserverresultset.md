---
title: "cancelRowUpdates (méthode) (SQLServerResultSet) | Documents Microsoft"
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
- SQLServerResultSet.cancelRowUpdates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2ecacca4-f7bc-4f5d-886a-da7747fdccae
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3823cc47e56615b29f33f3f37e1178afe0094022
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="cancelrowupdates-method-sqlserverresultset"></a>cancelRowUpdates (méthode) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Annule les mises à jour apportées à la ligne actuelle dans ce [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void cancelRowUpdates()  
```  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode cancelRowUpdates est spécifiée par la méthode cancelRowUpdates dans l’interface java.sql.ResultSet.  
  
 Cette méthode peut être appelée après l’appel à une méthode de mise à jour et avant d’appeler le [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) méthode pour restaurer les mises à jour qui ont été apportées à une ligne. Si aucune mise à jour n’ont été apportées ou updateRow a déjà été appelée, cette méthode n’a aucun effet.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

