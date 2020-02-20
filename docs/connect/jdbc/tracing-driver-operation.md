---
title: Suivre le fonctionnement du pilote | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 723aeae7-6504-4585-ba8b-3525115bea8b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 18bfd63a8cf3255a62b6aef5c4c31573c60e76b0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "69027591"
---
# <a name="tracing-driver-operation"></a>Suivi du fonctionnement du pilote
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge l’utilisation du suivi (ou de la journalisation) pour aider à résoudre les problèmes liés au pilote JDBC dans votre application. Pour permettre l’utilisation du suivi, le pilote JDBC utilise les API de journalisation de java.util.logging, qui offrent un ensemble de classes pour la création d’objets Logger et LogRecord.  
  
> [!NOTE]  
>  Pour le composant natif (sqljdbc_xa.dll) fourni avec le pilote JDBC, le suivi est activé par le système de diagnostic intégré BID (Built-In Diagnostics). Pour obtenir des informations sur le système de diagnostic intégré BID, consultez [Data Access Tracing in SQL Server (Suivi de l’accès aux données dans SQL Server)](https://go.microsoft.com/fwlink/?LinkId=70042).  
  
 Quand vous développez votre application, vous pouvez appeler des objets Logger, qui à leur tour créent des objets LogRecord, lesquels sont ensuite transmis aux objets Handler pour traitement. Les objets Logger et Handler utilisent tous deux des niveaux de journalisation et, éventuellement, des filtres de journalisation pour réguler les LogRecord traités. Une fois les opérations de journalisation terminées, les objets Handler peuvent éventuellement utiliser des objets Formatter pour publier les informations du journal.  
  
 Par défaut, le système java.util.logging écrit sa sortie dans un fichier. Ce fichier journal de sortie doit disposer des autorisations d'écriture dans le contexte dans lequel le pilote JDBC s'exécute.  
  
> [!NOTE]  
>  Pour plus d'informations sur l'utilisation des divers objets de journalisation en relation avec le suivi de programme, consultez la documentation (en anglais) Java Logging APIs sur le site Web de Sun Microsystems.  
  
 Les sections suivantes décrivent les niveaux de journalisation et les catégories qui peuvent être journalisées et fournissent des informations sur la procédure d'activation du suivi dans votre application.  
  
## <a name="logging-levels"></a>Niveaux de journalisation  
 Chaque message de journal créé est associé à un niveau de journalisation. Le niveau de journalisation détermine l’importance du message de journal ; il est défini par la classe **Level** dans java.util.logging. L'activation de la journalisation à un niveau active également la journalisation à tous les niveaux supérieurs. Cette section décrit les niveaux de journalisation à la fois pour les catégories de journalisation publiques et internes. Pour plus d'informations sur les catégories de journalisation, voir la section Catégories de journalisation de cet article.  
  
 Le tableau suivant décrit chacun des niveaux de journalisation disponibles pour les catégories de journalisation publiques.  
  
|Name|Description|  
|----------|-----------------|  
|SEVERE|Indique un échec grave ; il s'agit du niveau de journalisation le plus élevé. Dans le pilote JDBC, ce niveau permet de signaler des erreurs et des exceptions.|  
|WARNING|Indique un problème potentiel.|  
|INFO|Fournit des messages d'information.|  
|CONFIG|Fournit des messages de configuration. Notez que le pilote JDBC ne fournit actuellement aucun message de configuration.|  
|FINE|Fournit des informations de suivi de base, y compris toutes les exceptions levées par les méthodes publiques.|  
|FINER|Fournit des informations de suivi détaillées, y compris tous les points d'entrée et de sortie des méthodes publiques avec les types de données associés pour les paramètres et toutes les propriétés publiques pour les classes publiques. En outre, les paramètres d’entrée, les paramètres de sortie et les méthodes retournent des valeurs, à l’exception des types de valeurs de retour CLOB, BLOB, NCLOB, Reader, \<stream>.|  
|FINEST|Fournit des informations de suivi très détaillées. Il s'agit du niveau de journalisation le plus bas.|  
|OFF|Désactive la journalisation.|  
|ALL|Active la journalisation de tous les messages.|  
  
 Le tableau suivant décrit chacun des niveaux de journalisation disponibles pour les catégories de journalisation internes.  
  
|Name|Description|  
|----------|-----------------|  
|SEVERE|Indique un échec grave ; il s'agit du niveau de journalisation le plus élevé. Dans le pilote JDBC, ce niveau permet de signaler des erreurs et des exceptions.|  
|WARNING|Indique un problème potentiel.|  
|INFO|Fournit des messages d'information.|  
|FINE|Fournit des informations de suivi, y compris la création et la destruction d'objets de base. En outre, toutes les exceptions levées par les méthodes publiques.|  
|FINER|Fournit des informations de suivi détaillées, y compris tous les points d'entrée et de sortie des méthodes publiques avec les types de données associés pour les paramètres et toutes les propriétés publiques pour les classes publiques. En outre, les paramètres d’entrée, les paramètres de sortie et les méthodes retournent des valeurs, à l’exception des types de valeurs de retour CLOB, BLOB, NCLOB, Reader, \<stream>.<br /><br /> Les catégories suivantes de journalisation existaient dans la version 1.2 du pilote JDBC avec le niveau de journalisation FINE : [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md), [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), XA et [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md). À compter de la version 2.0, elles sont mises à niveau vers le niveau FINER.|  
|FINEST|Fournit des informations de suivi très détaillées. Il s'agit du niveau de journalisation le plus bas.<br /><br /> Les catégories suivantes de journalisation existaient dans la version 1.2 du pilote JDBC avec le niveau de journalisation FINEST : TDS.DATA et TDS.TOKEN. À compter de la version 2.0, elles conservent le niveau de journalisation FINEST.|  
|OFF|Désactive la journalisation.|  
|ALL|Active la journalisation de tous les messages.|  
  
## <a name="logging-categories"></a>Catégories de journalisation  
 Quand vous créez un objet Logger, vous devez lui indiquer l’entité nommée ou la catégorie pour laquelle vous souhaitez obtenir des informations de journal. Le pilote JDBC prend en charge les catégories de journalisation publiques suivantes, qui sont toutes définies dans le package du pilote com.microsoft.sqlserver.jdbc.  
  
|Name|Description|  
|----------|-----------------|  
|Connexion|Journalise les messages dans la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Les applications peuvent affecter le niveau de journalisation FINER.|  
|.|Journalise les messages dans la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Les applications peuvent affecter le niveau de journalisation FINER.|  
|DataSource|Journalise les messages dans la classe [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md). Les applications peuvent affecter le niveau de journalisation FINE.|  
|ResultSet|Journalise les messages dans la classe [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md). Les applications peuvent affecter le niveau de journalisation FINER.|  
|Pilote|Journalise les messages dans la classe [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md). Les applications peuvent affecter le niveau de journalisation FINER.|  
  
 À partir de la version 2.0 du pilote JDBC Microsoft, le pilote fournit également le package com.microsoft.sqlserver.jdbc.internals, qui inclut la prise en charge de la journalisation pour les catégories de journalisation internes suivantes.  
  
|Name|Description|  
|----------|-----------------|  
|AuthenticationJNI|Messages des journaux concernant les problèmes liés à l’authentification intégrée Windows (lorsque la propriété de connexion **authenticationScheme** est implicitement ou explicitement définie sur **NativeAuthentication**).<br /><br /> Les applications peuvent affecter le niveau de journalisation FINEST et FINE.|  
|SQLServerConnection|Journalise les messages dans la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Les applications peuvent affecter le niveau de journalisation FINE et FINER.|  
|SQLServerDataSource|Journalise les messages dans les classes [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md), [SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md) et [SQLServerPooledConnection](../../connect/jdbc/reference/sqlserverpooledconnection-class.md).<br /><br /> Les applications peuvent affecter le niveau de journalisation FINER.|  
|InputStream|Journalise les messages concernant les types de données suivants : java.io.InputStream, java.io.Reader et ceux qui ont un spécificateur max, tel que varchar, nvarchar ainsi que les types de données varbinary.<br /><br /> Les applications peuvent affecter le niveau de journalisation FINER.|  
|SQLServerException|Journalise les messages dans la classe [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md). Les applications peuvent affecter le niveau de journalisation FINE.|  
|SQLServerResultSet|Journalise les messages dans la classe [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md). Les applications peuvent affecter le niveau de journalisation FINE, FINER et FINEST.|  
|SQLServerStatement|Journalise les messages dans la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Les applications peuvent affecter le niveau de journalisation FINE, FINER et FINEST.|  
|XA|Journalise les messages relatifs à toutes les transactions XA dans la classe [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md). Les applications peuvent affecter le niveau de journalisation FINE et FINER.|  
|KerbAuthentication|Messages des journaux concernant l’authentification Kerberos de type 4 (lorsque la propriété de connexion **authenticationScheme** est définie sur **JavaKerberos**). L'application peut définir le niveau de journalisation sur FINE ou FINER.|  
|TDS.DATA|Journalise les messages contenant la conversation au niveau du protocole TDS entre le pilote et SQL Server. Le contenu détaillé de chaque paquet TDS envoyé et reçu est journalisé au format ASCII et hexadécimal. Les informations d'identification de connexion (noms d'utilisateur et mots de passe) ne sont pas consignées. Toutes les autres données sont journalisées.<br /><br /> Cette catégorie génère des messages clairs et très détaillés et ne peut être activée que lorsque le niveau de journalisation est défini sur FINEST.|  
|TDS.Channel|Cette catégorie effectue le suivi des actions du canal de communication TCP avec SQL Server. Les messages journalisés incluent l'ouverture et la fermeture de sockets ainsi que les lectures et écritures. Elle effectue également le suivi des messages relatifs à l'établissement d'une connexion SSL (Secure Sockets Layer) à SQL Server.<br /><br /> Cette catégorie peut uniquement être activée en affectant le niveau de journalisation FINE, FINER ou FINEST.|  
|TDS.Writer|Cette catégorie effectue le suivi des écritures dans le canal TDS. À noter que seule la longueur des écritures, et non le contenu, fait l'objet d'un suivi. Cette catégorie effectue également le suivi des problèmes lorsqu'un signal d'avertissement est envoyé au serveur pour annuler l'exécution d'une instruction.<br /><br /> Cette catégorie peut uniquement être activée en affectant le niveau de journalisation FINEST.|  
|TDS.Reader|Cette catégorie effectue le suivi de certaines opérations de lecture à partir du canal TDS au niveau FINEST. Au niveau FINEST, le suivi peut être détaillé. Aux niveaux WARNING et SEVERE, cette catégorie effectue le suivi lorsque le pilote reçoit un protocole TDS non valide de SQL Server avant qu'il ne ferme la connexion.<br /><br /> Cette catégorie peut uniquement être activée en affectant le niveau de journalisation FINER et FINEST.|  
|TDS.Command|Cette catégorie effectue le suivi des transitions d’état de bas niveau et d’autres informations associées à l’exécution de commandes TDS, telles que les exécutions d’instructions [!INCLUDE[tsql](../../includes/tsql-md.md)], les extractions de curseurs ResultSet, les validations, et ainsi de suite.<br /><br /> Cette catégorie peut uniquement être activée en affectant le niveau de journalisation FINEST.|  
|TDS.TOKEN|Cette catégorie ne journalise que les jetons des paquets TDS et est moins claire que la catégorie TDS.DATA. Elle peut uniquement être activée en affectant le niveau de journalisation FINEST.<br /><br /> Au niveau FINEST, cette catégorie effectue le suivi des jetons TDS lors de leur traitement dans la réponse. Au niveau SEVERE, cette catégorie effectue le suivi en cas de jeton TDS non valide.|  
|SQLServerDatabaseMetaData|Journalise les messages dans la classe [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md). Les applications peuvent affecter le niveau de journalisation FINE.|  
|SQLServerResultSetMetaData|Journalise les messages dans la classe [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md). Les applications peuvent affecter le niveau de journalisation FINE.|  
|SQLServerParameterMetaData|Journalise les messages dans la classe [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md). Les applications peuvent affecter le niveau de journalisation FINE.|  
|SQLServerBlob|Journalise les messages dans la classe [SQLServerBlob](../../connect/jdbc/reference/sqlserverblob-class.md). Les applications peuvent affecter le niveau de journalisation FINE.|  
|SQLServerClob|Journalise les messages dans la classe [SQLServerClob](../../connect/jdbc/reference/sqlserverclob-class.md). Les applications peuvent affecter le niveau de journalisation FINE.|  
|SQLServerSQLXML|Journalise les messages dans la classe interne SQLServerSQLXML. Les applications peuvent affecter le niveau de journalisation FINE.|  
|SQLServerDriver|Journalise les messages dans la classe [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md). Les applications peuvent affecter le niveau de journalisation FINE.|  
|SQLServerNClob|Journalise les messages dans la classe [SQLServerNClob](../../connect/jdbc/reference/sqlservernclob-class.md). Les applications peuvent affecter le niveau de journalisation FINE.|  
  
## <a name="enabling-tracing-programmatically"></a>Activation du suivi par programmation  
 Vous pouvez activer le suivi par programmation en créant un objet Logger et en indiquant la catégorie à journaliser. Par exemple, le code suivant montre comment activer la journalisation pour les instructions SQL :  
  
```java
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc.Statement");  
logger.setLevel(Level.FINER);  
```  
  
 Pour désactiver la journalisation dans le code, utilisez ce qui suit :  
  
```java
logger.setLevel(Level.OFF);  
```  
  
 Pour journaliser toutes les catégories disponibles, utilisez ce qui suit :  
  
```java
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc");  
logger.setLevel(Level.FINE);  
```  
  
 Pour désactiver la journalisation d'une catégorie spécifique, utilisez ce qui suit :  
  
```java
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc.Statement");  
logger.setLevel(Level.OFF);  
```  
  
## <a name="enabling-tracing-by-using-the-loggingproperties-file"></a>Activation du suivi à l'aide du fichier logging.properties  
 Vous pouvez également activer le suivi à l’aide du fichier `logging.properties` qui se trouve dans le répertoire `lib` d’installation de Java Runtime Environment (JRE). Ce fichier permet de définir les valeurs par défaut des fonctionnalités de journalisation et de gestion utilisées lorsque le suivi est activé.  
  
 L’exemple suivant présente les paramètres pouvant être définis dans les fichiers `logging.properties` :  
  
```  
# Specify the handler, the handlers will be installed during VM startup.  
handlers= java.util.logging.FileHandler  
  
# Default global logging level.  
.level= OFF  
  
# default file output is in user's home directory.  
java.util.logging.FileHandler.pattern = %h/java%u.log  
java.util.logging.FileHandler.limit = 5000000  
java.util.logging.FileHandler.count = 20  
java.util.logging.FileHandler.formatter = java.util.logging.SimpleFormatter  
java.util.logging.FileHandler.level = FINEST  
  
# Facility specific properties.  
com.microsoft.sqlserver.jdbc.level=FINEST  
  
```  
  
> [!NOTE]  
>  Vous pouvez définir les propriétés dans le fichier `logging.properties` à l’aide de l’objet LogManager figurant dans java.util.logging.  
  
## <a name="see-also"></a>Voir aussi  
 [Diagnostic de problèmes avec le pilote JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
