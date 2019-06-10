---
title: Connexion à SQL Server avec le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 94bcfbe3-f00e-4774-bda8-bb7577518fec
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2ceb6d9f5fca9a0ab6281b3caa4b95ceef5bc0b9
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66789360"
---
# <a name="connecting-to-sql-server-with-the-jdbc-driver"></a>Connexion à SQL Server à l'aide du pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Une des principales choses à faire avec [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] est d’établir une connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Toute l’interaction avec la base de données se fait via l’objet [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) et, comme le pilote JDBC a une architecture plate, pratiquement tout le comportement intéressant concerne l’objet SQLServerConnection.  
  
 Si un serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écoute seulement sur un port IPv6, définissez la propriété système java.net.preferIPv6Addresses pour utiliser IPv6 à la place de IPv4 pour la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
```java
System.setProperty("java.net.preferIPv6Addresses", "true");  
```  
  
 Les rubriques de cette section décrivent créer et utiliser une connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Création de l’URL de connexion](../../connect/jdbc/building-the-connection-url.md)|Décrit comment créer une URL de connexion pour se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Décrit également la connexion à des instances nommées d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Définition des propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md)|Décrit les différentes propriétés de connexion et la façon de les utiliser pour se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Définition des propriétés de la source de données](../../connect/jdbc/setting-the-data-source-properties.md)|Explique comment utiliser les sources de données dans un environnement Java EE (Java Platform, Enterprise Edition).|  
|[Utilisation d’une connexion](../../connect/jdbc/working-with-a-connection.md)|Décrit les différentes méthodes permettant de créer une instance d’une connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Utilisation d’un regroupement de connexions](../../connect/jdbc/using-connection-pooling.md)|Décrit la manière dont le pilote JDBC prend en charge l'utilisation d'un regroupement de connexions.|  
|[Utilisation de la mise en miroir de bases de données &#40;JDBC&#41;](../../connect/jdbc/using-database-mirroring-jdbc.md)|Décrit la manière dont le pilote JDBC prend en charge l'utilisation d'une mise en miroir de bases de données.|  
|[Prise en charge de la haute disponibilité et de la récupération d’urgence par le pilote JDBC](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)|Explique comment développer une application qui se connecte à un groupe de disponibilité AlwaysOn.|  
|[Utilisation de l’authentification intégrée Kerberos pour se connecter à SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)|Aborde l’implémentation Java pour les applications se connectant à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec l’authentification intégrée Kerberos.|  
|[Connexion à une base de données Azure SQL Database](../../connect/jdbc/connecting-to-an-azure-sql-database.md)|Aborde les problèmes de connectivité des bases de données installées sur SQL Azure.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
