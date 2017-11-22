---
title: "Méthode getSendTimeAsDatetime (SQLServerDataSource) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02287122-5dc1-455d-987f-95fd9a69d503
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f784b25fe9390d98d32ab31e6f3f837e30aa746b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>Méthode getSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Cette méthode a été ajoutée dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] version 3.0 du pilote JDBC.  
  
 Retourne le paramètre de la **sendTimeAsDatetime** propriété de connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si les valeurs java.sql.Time être envoyées au serveur en tant qu’un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime** type. **false** si les valeurs java.sql.Time être envoyées au serveur en tant qu’un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **temps** type.  
  
## <a name="remarks"></a>Notes  
 Consultez [définissant les propriétés de connexion](../../../connect/jdbc/setting-the-connection-properties.md) pour plus d’informations sur la **sendTimeAsDatetime** propriété de connexion.  
  
 [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) vous permet de définir par programme le **sendTimeAsDatetime** propriété de connexion.  
  
 Pour plus d’informations, consultez [java.sql.Time configurer comment les valeurs sont envoyées au serveur](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
