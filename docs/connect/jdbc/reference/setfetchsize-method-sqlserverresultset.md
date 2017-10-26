---
title: "setFetchSize (méthode) (SQLServerResultSet) | Documents Microsoft"
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
- SQLServerResultSet.setFetchSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 233bf4f8-4758-42d0-a80b-33e34fa78027
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ed3f37d12253c03ae192b03db27caf4d180e568d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="setfetchsize-method-sqlserverresultset"></a>setFetchSize (méthode) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Fournit un Conseil au concernant le nombre de lignes qui doivent être extraites à partir de la base de données lorsque plusieurs lignes sont nécessaires pour ce au pilote JDBC [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setFetchSize(int rows)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *lignes*  
  
 Un **int** indiquant le nombre de lignes à extraire.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setFetchSize est spécifiée par la méthode setFetchSize de l’interface java.sql.ResultSet.  
  
 Si la taille d'extraction spécifiée est de zéro, le pilote JDBC ignore la valeur et procède à une estimation de ce que devrait être la taille d'extraction. La valeur par défaut est définie par le [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objet qui a créé le jeu de résultats. La taille d'extraction peut être modifiée à tout moment.  
  
 Cette méthode change la taille d'extraction du bloc pour les curseurs côté serveur et prend effet la prochaine fois que le pilote JDBC doit appeler sp_cursorfetch. La définition de la taille d'extraction à zéro permet de restaurer la taille d'extraction par défaut du type de curseur en cours d'utilisation  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

