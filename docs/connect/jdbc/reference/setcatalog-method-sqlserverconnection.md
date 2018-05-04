---
title: Méthode setCatalog (SQLServerConnection) | Documents Microsoft
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
- SQLServerConnection.setCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 553c0603-c07d-436a-86eb-3ba6b51bd696
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c500a74ee2b87487e9596ac372deb2ed5021b325
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="setcatalog-method-sqlserverconnection"></a>Méthode setCatalog (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom de catalogue donné pour sélectionner un sous-espace de ce [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) base de données de l’objet dans lequel travailler.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setCatalog(java.lang.String catalog)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *catalog*  
  
 A **chaîne** qui contient le nom du catalogue.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setCatalog est spécifiée par la méthode setCatalog dans l’interface java.sql.Connection.  
  
 Le *catalogue* argument est échappé à le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] automatiquement. À l’aide de cette méthode définit la propriété de catalogue pour l’objet de connexion. La propriété n'est pas définie implicitement de quelque autre façon.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
