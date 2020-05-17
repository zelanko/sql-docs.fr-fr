---
title: Configuration du mode d'envoi des valeurs java.sql.Time au serveur | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 07eb00dd-621a-46f9-a5a5-8cab4d6058b5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8fe6969d51834d0798a530b9cc9926af1b27fec2
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "69028234"
---
# <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Configuration du mode d’envoi des valeurs java.sql.Time au serveur
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Si vous utilisez un objet java.sql.Time ou le type JDBC java.sql.Types.TIME pour définir un paramètre, vous pouvez configurer si la valeur java.sql.Time est envoyée au serveur sous le type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **time** ou **datetime**.  
  
 Ce scénario s'applique lors de l'utilisation de l'une des méthodes suivantes :  
  
-   [SQLServerCallableStatement.registerOutParameter(int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int.md)  
  
-   [SQLServerCallableStatement.registerOutParameter(int, int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int-int.md)  
  
-   [SQLServerCallableStatement.setTime](../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setTime](../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)  
  
-   [SQLServerCallableStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)  
  
 Vous pouvez configurer comment la valeur java.sql.Time est envoyée avec la propriété de connexion **sendTimeAsDatetime**. Pour plus d’informations, consultez [Définition des propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Vous pouvez modifier par programmation la valeur de la propriété de connexion **sendTimeAsDatetime** avec [SQLServerDataSource.setSendTimeAsDatetime](../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] ne prennent pas en charge le type de données **time**. Par conséquent, les applications utilisant java.sql.Time stockent généralement les valeurs java.sql.Time sous le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime** ou **smalldatetime**.  
  
 Si vous voulez utiliser les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime** et **smalldatetime** avec des valeurs java.sql.Time, vous devez définir la propriété de connexion **sendTimeAsDatetime** sur **true**. Si vous voulez utiliser le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **time** avec des valeurs java.sql.Time, vous devez définir la propriété de connexion **sendTimeAsDatetime** sur **false**.  
  
 Notez que quand vous envoyez des valeurs java.sql.Time dans un paramètre dont le type de données peut également stocker la date, les dates par défaut diffèrent selon que la valeur java.sql.Time est envoyée en tant que valeur **datetime** (1/1/1970) ou **time** (1/1/1900). Pour plus d’informations sur les conversions de données lors de l’envoi de données à un serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Utilisation des données de date et d’heure](https://go.microsoft.com/fwlink/?LinkID=145211).  
  
 Dans la version 3.0 de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] JDBC Driver, **sendTimeAsDatetime** a la valeur true par défaut. Dans une prochaine version, il se peut que la propriété de connexion **sendTimeAsDatetime** soit définie sur false par défaut.  
  
 Pour garantir que votre application continue à fonctionner comme prévu quelle que soit la valeur par défaut de la propriété de connexion **sendTimeAsDatetime**, vous disposez des possibilités suivantes :  
  
-   Utilisez java.sql.Time avec le type de données **time**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Utilisez java.sql.Timestamp avec les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime**, **smalldatetime** et **datetime2**.  
  
SendTimeAsDatetime doit avoir la valeur false pour les colonnes chiffrées, car celles-ci ne prennent pas en charge la conversion de time en datetime. À compter de la version 6.0 de Microsoft JDBC Driver pour SQL Server, la classe SQLServerConnection possède les deux méthodes suivantes pour définir/obtenir la valeur de la propriété sendTimeAsDatetime.

```java
  public boolean getSendTimeAsDatetime()
  public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)
```
  
## <a name="see-also"></a>Voir aussi
 [Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
