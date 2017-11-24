---
title: "Méthode Rollback () | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerConnection.rollback ()
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 7adb6772-4047-4d8e-931d-b3d20eec44b5
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 384d2cac20f8764daa7cbcee2803f56f9a79a625
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="rollback-method-"></a>Méthode rollback ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Annule toutes les modifications effectuées dans la transaction actuelle et libère tous les verrous de base de données actuellement maintenus par cet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void rollback()  
```  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode de restauration est spécifiée par la méthode de restauration dans l’interface java.sql.Connection.  
  
 Cette méthode doit être utilisée uniquement lorsque le mode de validation automatique a été désactivé.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode Rollback &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)   
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
