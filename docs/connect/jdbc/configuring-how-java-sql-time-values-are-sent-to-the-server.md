---
title: Configuration du mode d’envoi des valeurs java.sql.Time au serveur | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 07eb00dd-621a-46f9-a5a5-8cab4d6058b5
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 49925570b878bc442e10ab89e3eb9ef6694232d5
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797517"
---
# <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Configuration du mode d'envoi des valeurs java.sql.Time au serveur
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Si vous utilisez un objet java.sql.Time ou le type JDBC java.sql.Types.TIME pour définir un paramètre, vous pouvez configurer la façon dont la valeur java.sql.Time est envoyée au serveur : en tant que type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **time** ou **datetime**.  
  
 Ce scénario s'applique lors de l'utilisation de l'une des méthodes suivantes :  
  
-   [SQLServerCallableStatement.registerOutParameter(int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int.md)  
  
-   [SQLServerCallableStatement.registerOutParameter(int, int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int-int.md)  
  
-   [SQLServerCallableStatement.setTime](../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setTime](../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)  
  
-   [SQLServerCallableStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)  
  
 Vous pouvez configurer comment la valeur java.sql.Time est envoyée avec la propriété de connexion **sendTimeAsDatetime**. Pour plus d’informations, consultez [Définition des propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Vous pouvez modifier par programmation la valeur de la propriété de connexion **sendTimeAsDatetime** avec [SQLServerDataSource.setSendTimeAsDatetime](../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieure à [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] ne prennent en charge la **temps** en tant que type de données, pour les applications utilisant java.sql.Time stockent généralement java.sql.Time valeurs **datetime** ou **smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données.  
  
 Si vous souhaitez utiliser le **datetime** et **smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données lorsque vous travaillez avec des valeurs java.sql.Time, vous devez définir le **sendTimeAsDatetime** propriété de connexion **true**. Si vous souhaitez utiliser le **temps** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données fonctionne avec des valeurs java.sql.Time, vous devez définir le **sendTimeAsDatetime** propriété de connexion **false**.  
  
 Notez que quand vous envoyez des valeurs java.sql.Time dans un paramètre dont le type de données peut également stocker la date, les dates par défaut diffèrent selon que la valeur java.sql.Time est envoyée en tant que valeur **datetime** (1/1/1970) ou **time** (1/1/1900). Pour plus d’informations sur les conversions de données lors de l’envoi de données à un serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Utilisation des données de date et d’heure](https://go.microsoft.com/fwlink/?LinkID=145211).  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 3.0 du pilote JDBC, **sendTimeAsDatetime** a la valeur true par défaut. Dans une prochaine version, il se peut que la propriété de connexion **sendTimeAsDatetime** soit définie sur false par défaut.  
  
 Pour garantir que votre application continue à fonctionner comme prévu quelle que soit la valeur par défaut de la propriété de connexion **sendTimeAsDatetime**, vous disposez des possibilités suivantes :  
  
-   Utilisez java.sql.Time avec le type de données **time**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Utilisez java.sql.Timestamp lorsque vous travaillez avec le **datetime**, **smalldatetime**, et **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données.  
  
SendTimeAsDatetime doit avoir la valeur false pour les colonnes chiffrées comme des colonnes chiffrées ne prennent pas en charge la conversion à partir de l’heure en date/heure. À compter du pilote Microsoft JDBC 6.0 pour SQL Server, la classe SQLServerConnection a deux méthodes suivantes à la valeur de la propriété sendTimeAsDatetime de set/get.

```java
  public boolean getSendTimeAsDatetime()
  public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)
```
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
