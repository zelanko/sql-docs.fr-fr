---
title: setObject, méthode (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setObject
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 93a2b22c-82b4-48c7-a428-369ebe98a372
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f63a7e5d6b4f533edccc110b4a059a36eaab05c7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635003"
---
# <a name="setobject-method-sqlserverpreparedstatement"></a>setObject, méthode (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit la valeur du paramètre désigné à l'aide de l'objet spécifique.  
  
 À partir de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 3.0 du pilote JDBC, le comportement de cette méthode est modifié par le **sendTimeAsDatetime** propriété de connexion ([définissant les propriétés de connexion](../../../connect/jdbc/setting-the-connection-properties.md)) et [ SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Pour plus d’informations, consultez [java.sql.Time configurer comment les valeurs sont envoyées au serveur](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="overload-list"></a>Liste de surcharge  
  
|Nom   |Description|  
|----------|-----------------|  
|[setObject (int, java.lang.Object)](../../../connect/jdbc/reference/setobject-method-int-java-lang-object.md)|Définit la valeur du paramètre désigné à l'aide de l'objet spécifique.|  
|[setObject (int, java.lang.Object, int)](../../../connect/jdbc/reference/setobject-method-int-java-lang-object-int.md)|Définit la valeur du paramètre désigné à l'aide de l'objet et du type de cible donnés.|  
|[setObject (int, java.lang.Object, int, int)](../../../connect/jdbc/reference/setobject-method-int-java-lang-object-int-int.md)|Définit la valeur du paramètre désigné à l'aide de l'objet , du type de cible et de l'échelle donnés.|  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
