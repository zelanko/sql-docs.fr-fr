---
title: "Méthode getClientInfo (java.lang.String) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8e632c4-d6cc-4c5e-b6ad-873579343b19
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e0f92e5db61ef0b778e293ea61b25ad61956986a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getclientinfo-method-javalangstring"></a>Méthode getClientInfo (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur de la propriété d'informations client spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getClientInfo (java.lang.String name)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nom*  
  
 Chaîne qui contient le nom de la propriété d’informations client à récupérer.  
  
## <a name="return-value"></a>Valeur retournée  
 Chaîne qui contient la valeur de la propriété d’informations client.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getClientInfo est spécifiée par la méthode getClientInfo dans l’interface java.sql.Connection.  
  
 Le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ne prend pas en charge toutes les propriétés d’informations client. Par conséquent, cette méthode retourne **null**.  
  
 De même, les applications peuvent utiliser le [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) méthode de la [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) classe pour récupérer une liste des propriétés d’informations du client qui prend en charge par le pilote. Le [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) méthode retourne un jeu de résultats vide.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getClientInfo &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

