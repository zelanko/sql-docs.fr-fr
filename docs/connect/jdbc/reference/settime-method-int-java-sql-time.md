---
title: Méthode setTime (int, java.sql.Time) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setTime (int, java.sql.Time)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1e3878dc-42fe-4fac-8fe3-22a7bd70c6da
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7004f57f0516263ee70d8f9723536dc7d5ad9904
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67972552"
---
# <a name="settime-method-int-javasqltime"></a>Méthode setTime (int, java.sql.Time)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné sur la valeur d’heure donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setTime(int n,  
                          java.sql.Time x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *n*  
  
 **int** indiquant le numéro du paramètre.  
  
 *x*  
  
 Un objet Time.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setTime est spécifiée par la méthode setTime dans l’interface java.sql.PreparedStatement.  
  
 À partir de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0, le comportement de cette méthode est modifié par la propriété de connexion **sendTimeAsDatetime** ([Définir les propriétés de connexion](../../../connect/jdbc/setting-the-connection-properties.md)) et par [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Pour plus d’informations, consultez [Configurer le mode d’envoi des valeurs java.sql.Time au serveur](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [setTime, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
