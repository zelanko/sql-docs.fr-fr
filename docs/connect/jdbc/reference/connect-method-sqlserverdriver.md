---
title: Méthode Connect (SQLServerDriver) | Documents Microsoft
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
ms.topic: conceptual
apiname:
- SQLServerDriver.connect
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 43813a4c-1cc7-4659-ba27-f1786f1371eb
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 82b43287889bd213f223ac11312715441a904456
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="connect-method-sqlserverdriver"></a>Méthode connect (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Établit une connexion à la base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Connection connect(java.lang.String Url,  
                                   java.util.Properties suppliedProperties)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *URL*  
  
 A **chaîne** valeur qui contient l’URL qui est utilisé pour se connecter à la base de données.  
  
 *suppliedProperties*  
  
 Ensemble de paires de valeurs de chaîne utilisé comme arguments de connexion.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet de connexion.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode de connexion est spécifiée par la méthode de connexion dans l’interface java.sql.Driver.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [Membres de SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver, classe](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
