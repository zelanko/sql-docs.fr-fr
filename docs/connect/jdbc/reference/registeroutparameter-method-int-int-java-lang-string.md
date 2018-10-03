---
title: registerOutParameter, méthode (int, int, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter (int, int, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3eb5c384-6751-4d50-be23-0c2ccc35593c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e661a6ed2dbc3f6503ca566ea8052edde735e415
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47804827"
---
# <a name="registeroutparameter-method-int-int-javalangstring"></a>Méthode registerOutParameter (int, int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Inscrit le paramètre OUT dans la position ordinale spécifiée en fonction du type JDBC et du nom du type donnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void registerOutParameter(int index,  
                                 int sqlType,  
                                 java.lang.String typeName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 Un **int** qui indique la position ordinale du paramètre.  
  
 *sqlType*  
  
 Code de type JDBC comme défini dans java.sql.Types.  
  
 *typeName*  
  
 Un **chaîne** qui contient le nom complet du type SQL.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode registerOutParameter est spécifiée par la méthode registerOutParameter dans l’interface java.sql.CallableStatement.  
  
 À partir de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 3.0 du pilote JDBC, lorsque *sqlType* est de type java.sql.Types.TIME, le comportement de cette méthode est modifié par le **sendTimeAsDatetime** propriété de connexion ([Définissant les propriétés de connexion](../../../connect/jdbc/setting-the-connection-properties.md)) et [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Pour plus d’informations, consultez [java.sql.Time configurer comment les valeurs sont envoyées au serveur](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a> Voir aussi  
 [registerOutParameter, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
