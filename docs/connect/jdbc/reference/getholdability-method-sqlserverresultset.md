---
title: "Méthode getHoldability (SQLServerResultSet) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4508d90f-c3c4-4eac-8001-fb0b93b66734
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ae5a5d40381cd6b7939e7e67b5950e3d0e3644d3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getholdability-method-sqlserverresultset"></a>Méthode getHoldability (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la fonctionnalité de ce [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getHoldability()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** valeur contenant l’un des niveaux de fonctionnalité suivants :  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getHoldability est spécifiée par la méthode getHoldability dans l’interface java.sql.ResultSet.  
  
 Pour définir la fonction holdability du jeu de résultats, les applications peuvent utiliser le [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md) méthode de la [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) classe. Après le [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md) méthode est appelée et l’objet d’instruction et de son objet de jeu de résultats sont créés et l’instruction est exécutée, l’application peut avoir besoin modifier la fonctionnalité à nouveau.  
  
 Pour les curseurs côté serveur, lors d'une connexion à SQL Server 2005 ou version ultérieure, la définition de la fonctionnalité de mise en attente affecte uniquement la fonctionnalité des nouveaux jeux de résultats qui doivent être créés sur cette connexion. Toutefois, avec SQL Server 2000, la définition de la fonctionnalité de mise en attente affecte la fonctionnalité de mise en attente des jeux de résultats existants et des nouveaux jeux de résultats qui doivent être créés sur cette connexion.  
  
 Lorsque la fonctionnalité est réinitialisée et que la méthode getHoldability est appelée sur objet de jeu de résultats créé précédemment, la valeur retournée par cette méthode peut être différente de celui de la valeur de la mise en attente retournée par les méthodes suivantes : Statement.getResultSetHoldability , Connection.getHoldability ou DatabaseMetaData.getResultSetHoldability.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

