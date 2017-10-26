---
title: "Méthode setSendTimeAsDatetime (SQLServerDataSource) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 705a0494-b5e2-43db-940a-1b8cec550cdb
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f6a576e4cb3ef155092a1244bbf9e7c2fcaaadd5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="setsendtimeasdatetime-method-sqlserverdatasource"></a>Méthode setSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Cette méthode a été ajoutée dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] version 3.0 du pilote JDBC.  
  
 Modifie le paramètre de la **sendTimeAsDatetime** propriété de connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setSendTimeAsDatetime(boolean sendTimeAsDateTime)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sendTimeAsDateTime*  
  
 Valeur booléenne. Lorsque la valeur est true, provoque des valeurs java.sql.Time à envoyer au serveur en tant que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime** types. Si la valeur est false, provoque des valeurs java.sql.Time à envoyer au serveur en tant que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **temps** types.  
  
## <a name="remarks"></a>Notes  
 [SQLServerDataSource.getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md) retourne le paramètre de la **sendTimeAsDatetime** propriété de connexion.  
  
 Pour plus d’informations sur la **sendTimeAsDatetime** propriété de connexion, consultez [définissant les propriétés de connexion](../../../connect/jdbc/setting-the-connection-properties.md).  
  
 Pour plus d’informations, consultez [java.sql.Time configurer comment les valeurs sont envoyées au serveur](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

