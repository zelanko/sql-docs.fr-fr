---
title: Méthode getClientInfo (java.lang.String) | Documents Microsoft
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
ms.assetid: e8e632c4-d6cc-4c5e-b6ad-873579343b19
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 92c177cb4bdf77be75cc05da832be8787436de5e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
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
 [Méthode getClientInfo &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
