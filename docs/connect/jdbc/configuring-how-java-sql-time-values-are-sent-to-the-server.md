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
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028234"
---
# <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Configuration du mode d’envoi des valeurs java.sql.Time au serveur
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
  
 Les versions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de antérieures [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] à ne prennent pas en charge le type de données **Time** , donc les applications utilisant Java. Sql. Time stockent généralement les valeurs Java. Sql. Time en tant que types de données **DateTime** ou **smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Si vous souhaitez utiliser les types de données **DateTime** et **smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lorsque vous travaillez avec des valeurs Java. Sql. Time, vous devez définir la propriété de connexion **sendTimeAsDatetime** sur **true**. Si vous souhaitez utiliser le type de données **Time** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] quand vous travaillez avec des valeurs Java. Sql. Time, vous devez affecter la valeur **false**à la propriété de connexion **sendTimeAsDatetime** .  
  
 Notez que quand vous envoyez des valeurs java.sql.Time dans un paramètre dont le type de données peut également stocker la date, les dates par défaut diffèrent selon que la valeur java.sql.Time est envoyée en tant que valeur **datetime** (1/1/1970) ou **time** (1/1/1900). Pour plus d’informations sur les conversions de données lors de l’envoi de données à un serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Utilisation des données de date et d’heure](https://go.microsoft.com/fwlink/?LinkID=145211).  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le pilote JDBC 3,0, **sendTimeAsDatetime** a la valeur true par défaut. Dans une prochaine version, il se peut que la propriété de connexion **sendTimeAsDatetime** soit définie sur false par défaut.  
  
 Pour garantir que votre application continue à fonctionner comme prévu quelle que soit la valeur par défaut de la propriété de connexion **sendTimeAsDatetime**, vous disposez des possibilités suivantes :  
  
-   Utilisez java.sql.Time avec le type de données **time**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Utilisez Java. Sql. Timestamp lorsque vous utilisez les types de données **DateTime**, **smalldatetime**et **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
SendTimeAsDatetime doit avoir la valeur false pour les colonnes chiffrées, car les colonnes chiffrées ne prennent pas en charge la conversion de Time en DateTime. À compter de Microsoft JDBC Driver 6,0 pour SQL Server, la classe SQLServerConnection possède les deux méthodes suivantes pour définir/obtenir la valeur de la propriété sendTimeAsDatetime.

```java
  public boolean getSendTimeAsDatetime()
  public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)
```
  
## <a name="see-also"></a>Voir aussi
 [Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
