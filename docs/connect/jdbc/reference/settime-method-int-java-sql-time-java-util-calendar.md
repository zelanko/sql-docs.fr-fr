---
title: setTime, méthode (int, java.sql.Time, java.util.Calendar) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setTime (int, java.sql.Time, java.lang.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 79ff6eef-6ad7-4e33-95be-c2d552c65546
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c6388ea031c6cbd5c492b5af03bd37a091592868
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972557"
---
# <a name="settime-method-int-javasqltime-javautilcalendar"></a>Méthode setTime (int, java.sql.Time, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon les valeurs d'heure et de calendrier spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setTime(int n,  
                          java.sql.Time x,  
                          java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *n*  
  
 **Entier** qui indique le numéro du paramètre.  
  
 *x*  
  
 Objet d’heure.  
  
 *cal*  
  
 Objet de calendrier.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setTime est spécifiée par la méthode setTime dans l’interface java.sql.PreparedStatement.  
  
 À [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] partir du pilote JDBC 3,0, le comportement de cette méthode est modifié par la propriété de connexion **sendTimeAsDatetime** (en[définissant les propriétés de connexion](../../../connect/jdbc/setting-the-connection-properties.md)) et [SQLServerDataSource. setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Pour plus d’informations, consultez [configuration de la façon dont les valeurs Java. Sql. Time sont envoyées au serveur](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [setTime, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
