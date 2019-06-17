---
title: registeroutparameter, méthode (int, int, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter (int, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d902d4e0-881f-4182-814c-0ede9a8da7fd
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: df9265a677d9e44c2d8834d3c45525b7af80142a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802107"
---
# <a name="registeroutparameter-method-int-int-int"></a>Méthode registerOutParameter (int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Inscrit le paramètre OUT dans la position ordinale spécifiée en fonction du type et de l'échelle JDBC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void registerOutParameter(int index,  
                                 int sqlType,  
                                 int scale)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 Un **int** qui indique la position ordinale du paramètre.  
  
 *sqlType*  
  
 Code de type JDBC comme défini dans java.sql.Types.  
  
 *scale*  
  
 **int** indiquant le nombre de chiffres à placer à droite du séparateur décimal.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode registerOutParameter est spécifiée par la méthode registerOutParameter dans l’interface java.sql.CallableStatement.  
  
 À partir de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 3.0 du pilote JDBC, lorsque *sqlType* est de type java.sql.Types.TIME, le comportement de cette méthode est modifié par le **sendTimeAsDatetime** propriété de connexion ([Définissant les propriétés de connexion](../../../connect/jdbc/setting-the-connection-properties.md)) et [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Pour plus d’informations, consultez [java.sql.Time configurer comment les valeurs sont envoyées au serveur](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [registerOutParameter, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
