---
title: Méthode getClientInfo () | Documents Microsoft
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
ms.assetid: b06a5ced-b760-4c78-b17e-854ce95a1a5c
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 78dbe04742c12f5fb4c37b5184fcc91a81aad4fc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="getclientinfo-method-"></a>Méthode getClientInfo ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une liste contenant le nom et la valeur actuelle de chaque propriété d'informations client prise en charge par le pilote JDBC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.util.Properties getClientInfo()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet de propriétés qui contient le nom et la valeur actuelle de chacune des propriétés d’informations client prises en charge par le pilote.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getClientInfo est spécifiée par la méthode getClientInfo dans l’interface java.sql.Connection.  
  
 Le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ne prend pas en charge toutes les propriétés d’informations client. Par conséquent, cette méthode retourne un objet de propriétés vide.  
  
 De même, les applications peuvent utiliser le [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) méthode de la [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) classe pour récupérer une liste des propriétés d’informations du client qui prend en charge par le pilote. Le [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) méthode retourne un jeu de résultats vide.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getClientInfo &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
