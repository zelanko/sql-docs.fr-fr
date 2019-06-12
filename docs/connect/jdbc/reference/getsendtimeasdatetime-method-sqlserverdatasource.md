---
title: Méthode getSendTimeAsDatetime (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 02287122-5dc1-455d-987f-95fd9a69d503
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 36cdeda1cdad226c00449d118f154fd555e7246d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66792085"
---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>Méthode getSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Cette méthode a été ajoutée dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0.  
  
 Retourne le paramètre de la **sendTimeAsDatetime** propriété de connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si les valeurs java.sql.Time sont envoyées au serveur en tant qu’un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **datetime** type. **false** si les valeurs java.sql.Time sont envoyées au serveur en tant qu’un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **temps** type.  
  
## <a name="remarks"></a>Notes  
 Consultez [définissant les propriétés de connexion](../../../connect/jdbc/setting-the-connection-properties.md) pour plus d’informations sur la **sendTimeAsDatetime** propriété de connexion.  
  
 [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) vous permet de définir par programmation la **sendTimeAsDatetime** propriété de connexion.  
  
 Pour plus d’informations, consultez [java.sql.Time configurer comment les valeurs sont envoyées au serveur](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
