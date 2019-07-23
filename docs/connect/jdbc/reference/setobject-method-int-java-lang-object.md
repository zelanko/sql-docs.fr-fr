---
title: setObject, méthode (int, java.lang.Object) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setObject (int, java.lang.Object)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 61f19faa-3006-4a1c-974c-55951e3b3000
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e4ab210a30080472a777d151695a04ec49ff1041
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973380"
---
# <a name="setobject-method-int-javalangobject"></a>Méthode setObject (int, java.lang.Object)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit la valeur du paramètre désigné à l'aide de l'objet spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setObject(int index,  
                            java.lang.Object obj)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 **Entier** qui indique le numéro du paramètre.  
  
 *obj*  
  
 Objet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setObject est spécifiée par la méthode setObject de l’interface java.sql.PreparedStatement.  
  
 Avant d’appeler cette méthode setObject, l’application peut définir le paramètre spécifié avec une des méthodes suivantes :  
  
-   Les méthodes set\<Type> de la classe SQLServerPreparedStatement ou de la classe SQLServerCallableStatement  
  
-   Les méthodes setNull de la classe SQLServerPreparedStatement ou de la classe SQLServerCallableStatement  
  
-   Méthode [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) de la classe SQLServerCallableStatement  
  
 Dans ce cas, le type du paramètre est défini automatiquement. Si l’application appelle cette méthode setObject avec une valeur obj définie sur Null, le pilote suppose que le type du paramètre correspond à celui défini par la méthode appelée précédemment.  
  
 Si la valeur de obj est Null et qu’aucune information de type ne peut être déterminée pour ce paramètre, cette méthode setObject convertit le paramètre spécifié en type CHAR avant de l’envoyer à la base de données.  
  
 À [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] partir du pilote JDBC 3,0, le comportement de cette méthode est modifié par la propriété de connexion **sendTimeAsDatetime** (en[définissant les propriétés de connexion](../../../connect/jdbc/setting-the-connection-properties.md)) et [SQLServerDataSource. setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Pour plus d’informations, consultez [configuration de la façon dont les valeurs Java. Sql. Time sont envoyées au serveur](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [setObject, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
