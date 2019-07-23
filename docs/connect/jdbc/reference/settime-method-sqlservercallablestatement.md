---
title: Méthode setTime (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setTime
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 04ea83b2-db5e-4b46-b016-9e496363827e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 81205764a663930ab2d555c0f231448c6cae4099
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972458"
---
# <a name="settime-method-sqlservercallablestatement"></a>Méthode setTime (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné sur la valeur d’heure donnée.  
  
 À [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] partir du pilote JDBC 3,0, le comportement de cette méthode est modifié par la propriété de connexion **sendTimeAsDatetime** (en[définissant les propriétés de connexion](../../../connect/jdbc/setting-the-connection-properties.md)) et [SQLServerDataSource. setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Pour plus d’informations, consultez [configuration de la façon dont les valeurs Java. Sql. Time sont envoyées au serveur](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="overload-list"></a>Liste de surcharge  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|[setTime (java.lang.String, java.sql.Time)](../../../connect/jdbc/reference/settime-method-java-lang-string-java-sql-time.md)|Définit le paramètre désigné sur la valeur d’heure donnée.|  
|[setTime (java.lang.String, java.sql.Time, java.util.Calendar)](../../../connect/jdbc/reference/settime-method-java-lang-string-java-sql-time-java-util-calendar.md)|Définit le paramètre désigné selon les valeurs d'heure et de calendrier spécifiées.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerCallableStatement, méthodes](../../../connect/jdbc/reference/sqlservercallablestatement-methods.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
