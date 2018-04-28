---
title: Méthode getPropertyInfo (SQLServerDriver) | Documents Microsoft
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
- SQLServerDriver.getPropertyInfo
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b5eaad8a-31ef-44ac-af11-d5caa13ac3e2
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 011176c3cb96320832bc9a4c0d64894082ff2c3b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="getpropertyinfo-method-sqlserverdriver"></a>Méthode getPropertyInfo (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Utilisée pour découvrir les propriétés requises pour la connexion à une base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.DriverPropertyInfo[] getPropertyInfo(java.lang.String Url,  
                                                     java.util.Properties Info)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *URL*  
  
 A **chaîne** valeur qui contient l’URL qui est utilisé pour se connecter à la base de données.  
  
 *Info*  
  
 Liste de paires de valeurs de propriété, Null à la première utilisation.  
  
## <a name="return-value"></a>Valeur retournée  
 Tableau d’objets de DriverPropertyInfo.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getPropertyInfo est spécifiée par la méthode getPropertyInfo dans l’interface java.sql.Driver.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [Membres de SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver, classe](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
