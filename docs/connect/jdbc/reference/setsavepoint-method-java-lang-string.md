---
title: "Méthode setSavepoint (java.lang.String) | Documents Microsoft"
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
apiname: SQLServerConnection.setSavepoint (java.lang.String)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 1cf15ec4-d9d9-4ab3-bfee-2ea43ff609a6
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 985a80b511a87b795a5a8d3cdeb478d451fe4114
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="setsavepoint-method-javalangstring"></a>Méthode setSavepoint (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un point d’enregistrement avec le nom donné dans la transaction actuelle et retourne le nouvel [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) objet qui le représente.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Savepoint setSavepoint(java.lang.String sName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sName*  
  
 A **chaîne** valeur qui contient le nom du point de sauvegarde.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet de point d’enregistrement.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setSavePoint est spécifiée par la méthode setSavePoint dans l’interface java.sql.Connection.  
  
 Le *sName* argument est automatiquement échappé à le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode setSavepoint &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)   
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
