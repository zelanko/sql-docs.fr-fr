---
title: Référence d’API du pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 07/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e4e1ae9d-18a6-41db-8bd2-9cf0eee4cccb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f311458a8fb6b58f22a1ca4c23fa8d1f36dddc51
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773789"
---
# <a name="jdbc-driver-api-reference"></a>Référence de l'API du pilote JDBC

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] fournit une API que vous pouvez utiliser dans du code de programmation Java pour vous connecter à une base de données [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et interagir avec elle.



### <a name="javadocio-website-is-primary"></a>Site Web JavaDoc.io est primaire

La documentation de référence de l’API Microsoft JDBC est hébergée pour votre affichage sur le site Web JavaDoc.io. JavaDoc.io est maintenant notre principal site Web de documentation de référence sur JDBC. Notre documentation de référence JDBC sur JavaDoc.io est disponible via le lien direct suivant :

- [https://javadoc.io/doc/com.microsoft.sqlserver/mssql-jdbc/](https://javadoc.io/doc/com.microsoft.sqlserver/mssql-jdbc/)

JavaDoc.io a notre documentation de référence JDBC depuis la version 6.0.

#### <a name="only-legacy-jdbc-documentation-is-here-on-docs"></a>Uniquement la Documentation JDBC hérité est ici sur Docs

La documentation de référence de l’API JDBC articles ici sur **https://docs.microsoft.com/sql/connect/jdbc/reference/** sont ne sont plus mis à jour lorsque les classes JDBC sont mis à jour pour les nouvelles versions. Toutefois, les articles ici contiennent toutes les références pour les versions JDBC 4.1 et 4.2.

Documentation de version JDBC 6.0 et des versions ultérieures, est également ici. Mais, pour n’importe quelle version 6.0 ou version ultérieure, utilisez le site Web JavaDoc.io.



### <a name="important-notes"></a>Remarques importantes

> [!NOTE]  
>  Pour obtenir des informations conceptuelles sur l’utilisation du pilote JDBC, consultez [vue d’ensemble du pilote JDBC](../../../connect/jdbc/overview-of-the-jdbc-driver.md).  
  
> [!IMPORTANT]  
>  Pour la prise en charge de la compatibilité avec JDBC 4.1 et 4.2, utilisez Microsoft JDBC Driver 4.2 (ou version ultérieure) pour SQL Server. Les versions antérieures 4.1 et 4.0 du pilote Microsoft JDBC ne prennent pas en charge les nouvelles méthodes introduites avec JDBC 4.1 ou 4.2.  
>   
>  Cette section ne comprend pas d'informations sur l'API pour la compatibilité avec JDBC 4.1. Voir [Conformité à JDBC 4.1 pour le pilote JDBC](../../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md).  
>   
>  Cette section ne comprend pas d’informations sur l’API pour la compatibilité avec JDBC 4.2. Voir [Conformité à JDBC 4.2 pour le pilote JDBC](../../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).  
>   
>  Cette section ne comprend pas d’informations sur l’API pour la fonctionnalité de copie en bloc, disponible à partir de Microsoft JDBC Driver 4.2 pour SQL Server. Voir [Utilisation de la copie en bloc avec le pilote JDBC](../../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).  
>   
>  Cette section ne comprend pas d’informations sur l’API pour la fonctionnalité Always Encrypted, disponible à partir de Microsoft JDBC Driver 6.0 pour SQL Server. Voir [Informations de référence sur l’API Always Encrypted pour le pilote JDBC](../../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).  
>   
>  Détails de l’API pour les paramètres Using Table-Valued, disponible à partir de Microsoft JDBC Driver 6.0 pour SQL Server, sont introuvables dans cette section. Voir [Utilisation de paramètres table](../../../connect/jdbc/using-table-valued-parameters.md).  
>   
>  Microsoft JDBC Driver 6.4 Microsoft prend en charge la compilation avec JDK 7.0, 8.0 et 9.0.  
>   
>  Microsoft JDBC Driver 6.2 prend en charge la compilation avec JDK 7.0 et 8.0.  
>   
>  Microsoft JDBC Driver 6.0 et 4.2 prennent en charge la compilation avec JDK 5.0, 6.0, 7.0 et 8.0.  
>   
>  Le Pilote JDBC 4.1 Microsoft prend en charge la compilation avec JDK 5.0, 6.0 et 7.0.  



## <a name="interfaces"></a>Interfaces  
  
|Nom de l'interface|Description|  
|--------------------|-----------------|  
|[ISQLServerCallableStatement, interface](../../../connect/jdbc/reference/isqlservercallablestatement-interface.md)|Permet de spécifier le nom de la procédure stockée à appeler avec les paramètres d'entrée et de sortie.|  
|[ISQLServerConnection, interface](../../../connect/jdbc/reference/isqlserverconnection-interface.md)|Représente une connexion JDBC à une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)|Représente une liste de propriétés propres à la connexion à une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l’aide d’un objet [ISQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
|[ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)|Représente l'implémentation de base de la fonctionnalité d'instruction préparée JDBC.|  
|[ISQLServerResultSet](../../../connect/jdbc/reference/isqlserverresultset-interface.md)|Représente un jeu de résultats JDBC.|  
|[ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)|Représente l'implémentation de base de la fonctionnalité d'instruction JDBC.|
| &nbsp; | &nbsp; |


  
## <a name="classes"></a>Classes  
  
|Nom de la classe|Description|  
|----------------|-----------------|  
|[DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)|Représente un objet de type microsoft.sql.DateTimeOffset.|  
|[SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)|Représente un objet blob.|  
|[SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)|Implémente ISQLServerCallableStatement.|  
|[SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)|Représente un CLOB (Character Large Binary Object).|  
|[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)|Implémente ISQLServerConnectopn.|  
|[SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)|Représente des connexions de bases de données physiques pour les gestionnaires de regroupement de connexions.|  
|[SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)|Représente les métadonnées pour la base de données.|  
|[SQLServerDataSource](../../../connect/jdbc/reference/isqlserverdatasource-interface.md)|Représente une liste de propriétés propres à la connexion à une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l’aide d’un objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
|[SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-class.md)|Représente une fabrique d'objet permettant de matérialiser des sources de données à partir de JNDI (Java Naming and Directory Interface).|  
|[SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-class.md)|Représente le pilote JDBC. Cette classe inclut des méthodes de connexion à une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et d’obtention d’informations sur le pilote JDBC.|  
|[SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)|Représente une exécution incorrecte ou incomplète d'une instruction SQL.|  
|[SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)|Représente un CLOB utilisant le jeu de caractères nationaux.|  
|[SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)|Représente les métadonnées pour les paramètres d'instructions préparées.|  
|[SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)|Représente une connexion de base de données physique dans un regroupement de connexions.|  
|[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)|Implémente ISQLServerPreparedStatement.|  
|[SQLServerResource](../../../connect/jdbc/reference/sqlserverresource-class.md)|Représente une ressource de chaîne d'erreur localisée. Cette classe est réservée à l'usage interne uniquement.|  
|[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)|Implémente ISQLServerResultSet.|  
|[SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)|Représente les métadonnées des colonnes contenues dans un jeu de résultats.|  
|[SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)|Représente le point de contrôle auquel la transaction peut être restaurée.|  
|[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)|Implémente ISQLServerStatement.|  
|[SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)|Représente les connexions JDBC qui peuvent participer à des transactions distribuées (XA).|  
|[SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)|Représente une fabrique d’objets [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) destinée à un usage interne.|  
|[SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)|Représente une XAResource pour la gestion des transactions distribuées XA.|
| &nbsp; | &nbsp; |



## <a name="see-also"></a> Voir aussi  
 [Vue d’ensemble du pilote JDBC](../../../connect/jdbc/overview-of-the-jdbc-driver.md)

