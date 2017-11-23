---
title: "Méthode setWorkstationID (SQLServerDataSource) | Documents Microsoft"
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
apiname: SQLServerDataSource.setWorkstationID
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: c1093615-90bf-4918-9f05-8abd765ffb03
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bd2d1ad16dd1ff622c7d8f4f8394df08bdfd3f6a
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="setworkstationid-method-sqlserverdatasource"></a>Méthode setWorkstationID (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom du client de nom de l’ordinateur qui est utilisé pour se connecter à la source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setWorkstationID(java.lang.String workstationID)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *workstationID*  
  
 A **chaîne** qui contient le nom de l’ordinateur client.  
  
## <a name="remarks"></a>Notes  
 Le workstationID est le nom de l'ordinateur client ou du poste de travail. Si la propriété workstationID n’est pas définie, la valeur par défaut est construite en appelant la méthode de InetAddress.getLocalHost().getHostName(). Si getHostName retourne une valeur vide, la méthode getHostAddress().toString() est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
