---
title: Méthode getString (java.lang.String) (SQLServerResultSet) | Documents Microsoft
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
ms.topic: article
apiname:
- SQLServerResultSet.getString (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8a98c8a8-61d0-40c9-9335-25a87b732dc3
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 07f6a17c49143fcb0ca6cffd2656ce200bedf2e1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="getstring-method-javalangstring-sqlserverresultset"></a>Méthode getString (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du nom de colonne désigné dans la ligne actuelle de ce [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) de l’objet en un **chaîne** dans le langage de programmation Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getString(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnName*  
  
 A **chaîne** qui contient le nom de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 A **chaîne** valeur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getString est spécifiée par la méthode getString dans l’interface java.sql.ResultSet.  
  
 Toutes les colonnes dans SQL Server peuvent être retournées en tant que chaîne. Cela signifie qu’un **chaîne** la représentation sous forme de tous les types de nombres et de caractères et une représentation sous forme de chaîne hexadécimale des colonnes binaires telles que binary, varbinary, varbinary (max), image, timestamp et uniqueidentifier, peuvent être retourné.  
  
 Les types sensibles à l'emplacement, tels que money, smallmoney, datetime, smalldatetime, float, real, decimal et numeric, retourneront le format canonique toString() pour la valeur sous-jacente du type.  
  
 Les types définis par l’utilisateur sont retournés au format hexadécimal **chaîne** valeurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getString &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)   
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
