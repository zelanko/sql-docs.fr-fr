---
title: Méthode getClientInfo () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b06a5ced-b760-4c78-b17e-854ce95a1a5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a89f2afa50b0ee1b83e72c05bf675d49dac662ca
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47757767"
---
# <a name="getclientinfo-method-"></a>Méthode getClientInfo ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une liste contenant le nom et la valeur actuelle de chaque propriété d'informations client prise en charge par le pilote JDBC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.util.Properties getClientInfo()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Objet Properties contenant le nom et la valeur actuelle de chaque propriété d’informations client prise en charge par le pilote.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getClientInfo est spécifiée par la méthode getClientInfo dans l’interface java.sql.Connection.  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ne prend en charge aucune propriété d’informations client. Par conséquent, cette méthode retourne un objet de propriétés vide.  
  
 De façon similaire, les applications peuvent utiliser la méthode [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) de la classe [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) pour récupérer la liste des propriétés d’informations client prises en charge par le pilote. La méthode [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) retourne un jeu de résultats vide.  
  
## <a name="see-also"></a> Voir aussi  
 [getClientInfo, méthode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
