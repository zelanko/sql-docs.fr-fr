---
title: Utilisation d’une connexion JDBC
description: Des exemples des différents modes de connexion à une base de données SQL Server à l'aide de la classe SQLServerConnection du pilote Microsoft JDBC pour SQL Server.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cf8ee392-8a10-40a3-ae32-31c7b1efdd04
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1253c2ec5822fef83d6da71279752202f2d93ebd
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81631949"
---
# <a name="working-with-a-connection"></a>Utilisation d'une connexion

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Les sections suivantes proposent des exemples des différents modes de connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de la classe [SQLServerConnection](reference/sqlserverconnection-class.md) du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].

> [!NOTE]  
> Si vous rencontrez des problèmes de connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais du pilote JDBC, consultez [Résolution des problèmes de connectivité](troubleshooting-connectivity.md) pour obtenir des suggestions de solutions.

## <a name="creating-a-connection-by-using-the-drivermanager-class"></a>Création d'une connexion via la classe DriverManager

La façon la plus simple de créer une connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consiste à charger le pilote JDBC et à appeler la méthode getConnection de la classe DriverManager, comme suit :

```java
Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = DriverManager.getConnection(connectionUrl);  
```

Cette technique crée une connexion de base de données via le premier pilote disponible dans la liste des pilotes capables de se connecter avec succès à l'URL donnée.

> [!NOTE]  
> Lors de l’utilisation de la bibliothèque de classes sqljdbc4.jar, les applications n’ont pas besoin d’inscrire ni de charger explicitement le pilote à l’aide de la méthode Class.forName. Lorsque la méthode getConnection de la classe DriverManager est appelée, un pilote correspondant est localisé parmi l’ensemble des pilotes JDBC inscrits. Pour plus d'informations, consultez Utilisation du pilote JDBC.

## <a name="creating-a-connection-by-using-the-sqlserverdriver-class"></a>Création d'une connexion via la classe SQLServerDriver

Si vous devez spécifier un pilote en particulier dans la liste des pilotes pour DriverManager, vous pouvez créer une connexion de base de données à l’aide de la méthode [connect](reference/connect-method-sqlserverdriver.md) de la classe [SQLServerDriver](reference/sqlserverdriver-class.md), comme suit :

```java
Driver d = (Driver) Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver").newInstance();  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = d.connect(connectionUrl, new Properties());  
```

## <a name="creating-a-connection-by-using-the-sqlserverdatasource-class"></a>Création d'une connexion via la classe SQLServerDataSource

Si vous devez établir une connexion à l’aide de la classe [SQLServerDataSource](reference/sqlserverdatasource-class.md), vous pouvez utiliser les différentes méthodes setter de la classe avant d’appeler la méthode [getConnection](reference/getconnection-method.md), comme suit :

```java
SQLServerDataSource ds = new SQLServerDataSource();  
ds.setUser("MyUserName");  
ds.setPassword("*****");  
ds.setServerName("localhost");  
ds.setPortNumber(1433);
ds.setDatabaseName("AdventureWorks");  
Connection con = ds.getConnection();  
```

## <a name="creating-a-connection-that-targets-a-specific-data-source"></a>Création d'une connexion visant une source de données spécifique

Si vous devez créer une connexion de base de données qui vise une source de données spécifique, plusieurs approches s'offrent à vous. Chacune d'elles dépend des propriétés définies à l'aide de l'URL de connexion.

Pour établir une connexion à l'instance par défaut sur un serveur distant, utilisez l’exemple qui suit :

```java
String url = "jdbc:sqlserver://MyServer;integratedSecurity=true;"
```

Pour établir une connexion à un port spécifique sur un serveur, utilisez l’exemple qui suit :

```java
String url = "jdbc:sqlserver://MyServer:1533;integratedSecurity=true;"
```

Pour établir une connexion à une instance nommée sur un serveur, utilisez l’exemple qui suit :

```java
String url = "jdbc:sqlserver://209.196.43.19;instanceName=INSTANCE1;integratedSecurity=true;"
```

Pour établir une connexion à une base de données spécifique sur un serveur, utilisez l’exemple qui suit :

```java
String url = "jdbc:sqlserver://172.31.255.255;database=AdventureWorks;integratedSecurity=true;"
```

Pour plus d'exemples d'URL de connexion plus, consultez [Création de l'URL de connexion](building-the-connection-url.md).

## <a name="creating-a-connection-with-a-custom-login-timeout"></a>Création d'une connexion avec un délai de connexion personnalisé

Si vous devez vous adapter à la charge du serveur ou au trafic réseau, vous pouvez établir une connexion ayant une valeur de délai de connexion spécifique, exprimée en secondes, comme l’exemple qui suit :

```java
String url = "jdbc:sqlserver://MyServer;loginTimeout=90;integratedSecurity=true;"
```

## <a name="create-a-connection-with-application-level-identity"></a>Création d'une connexion avec une identité au niveau de l'application

Si vous devez utiliser la journalisation et la définition de profils, vous devez identifier votre connexion comme provenant d'une application spécifique, comme l’exemple qui suit :

```java
String url = "jdbc:sqlserver://MyServer;applicationName=MYAPP.EXE;integratedSecurity=true;"
```

## <a name="closing-a-connection"></a>Fermeture d'une connexion

Vous pouvez explicitement fermer une connexion de base de données en appelant la méthode [close](reference/close-method-sqlserverconnection.md) de la classe SQLServerConnection, comme suit :

```java
con.close();
```

Cela libère les ressources de base de données utilisées par l’objet SQLServerConnection ou retourne la connexion au regroupement de connexions dans les scénarios regroupés.

> [!NOTE]  
> L’appel de la méthode close entraîne également l’annulation des transactions en attente.

## <a name="see-also"></a>Voir aussi

[Connexion à SQL Server avec le pilote JDBC](connecting-to-sql-server-with-the-jdbc-driver.md)
