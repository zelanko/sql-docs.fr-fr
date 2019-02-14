---
title: Configuration système requise pour le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 447792bb-f39b-49b4-9fd0-1ef4154c74ab
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4e2ccc488c7bdac6e6e73863b55760c622a73474
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55736910"
---
# <a name="system-requirements-for-the-jdbc-driver"></a>Configuration requise pour le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Pour accéder aux données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] à l’aide du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], vous devez installer les composants suivants sur votre ordinateur :

- [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ([Télécharger](download-microsoft-jdbc-driver-for-sql-server.md))
- Environnement d'exécution Java

## <a name="java-runtime-environment-requirements"></a>Configuration requise pour l'environnement d'exécution Java  

 À compter de Microsoft JDBC Driver 7.2 pour SQL Server, le Kit JDK (Java Development Kit) version 11.0 et l’environnement JRE (Java Runtime Environment) version 11.0 sont pris en charge.
 
 À compter de Microsoft JDBC Driver 7.0 pour SQL Server, le Kit JDK (Java Development Kit) version 10.0 et l’environnement JRE (Java Runtime Environment) version 10.0 sont pris en charge.

 À compter de Microsoft JDBC Driver 6.4 pour SQL Server, le Kit JDK (Java Development Kit) version 9.0 et l’environnement JRE (Java Runtime Environment) version 9.0 sont pris en charge.

 À compter de Microsoft JDBC Driver 4.2 pour SQL Server, le Kit JDK (Java Development Kit) version 8.0 et l’environnement JRE (Java Runtime Environment) version 8.0 sont pris en charge. La prise en charge de l’API de spécification Java Database Connectivity (JDBC) a été étendue pour inclure l’API JDBC 4.1 et 4.2.
  
 À compter de Microsoft JDBC Driver 4.1 pour SQL Server, le Kit JDK (Java Development Kit) version 7.0 et l’environnement JRE (Java Runtime Environment) version 7.0 sont pris en charge.
  
 À partir de [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], la prise en charge de l’API Spec JDBC (Java Database Connectivity) par le pilote JDBC a été étendue pour inclure l’API JDBC 4.0. L’API JDBC 4.0 a été introduite dans le cadre du kit JDK (Java Development Kit) version 6.0 et de l’environnement JRE (Java Runtime Environment) version 6.0. JDBC 4.0 est un surensemble de l'API JDBC 3.0.
  
 Quand vous déployez le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] sur les systèmes d’exploitation Windows et UNIX, vous devez utiliser les packages d’installation, respectivement *sqljdbc_\<version>_enu.exe*, et *sqljdbc_\<version>_enu.tar.gz*. Pour plus d’informations sur la façon de déployer le pilote JDBC, consultez [déploiement du pilote JDBC](../../connect/jdbc/deploying-the-jdbc-driver.md) rubrique.  

**Microsoft JDBC Driver 7.2 pour SQL Server :**  

  JDBC Driver 7.2 comporte deux bibliothèques de classes JAR dans chaque package d’installation : **mssql-jdbc-7.2.0.jre8.jar** et **mssql-jdbc-7.2.0.jre11.jar**.

  Le 7.2 du pilote JDBC est conçu pour travailler avec et être pris en charge par toutes les principales machines virtuelles de Java, mais il est testé uniquement sur OpenJDK 8.0, OpenJDK 11.0, Azul Zulu JRE 8.0 et Azul Zulu JRE 11.0.
  
  Le tableau suivant récapitule les versions prises en charge par les deux fichiers JAR fournis avec Microsoft JDBC Driver 7.2 pour SQL Server :  
  
  |JAR|Compatibilité avec la version de JDBC|Java Version recommandée|Description|  
|---------|-----------------------------|----------------------|-----------------|   
|mssql-jdbc-7.2.0.jre8.jar|4.2|8|Nécessite Java Runtime Environment (JRE) 8.0. À l’aide de JRE 7.0 ou inférieure lève une exception.<br /><br /> Nouvelles fonctionnalités dans 7.2 : Prise en charge de JDK 11, l’authentification Active Directory Managed Service Identity (MSI), prise en charge OSGi, SQLServerError APIs. |    
|mssql-jdbc-7.2.0.jre11.jar|4.3|10|Nécessite un environnement JRE (Java Runtime Environment) 11.0. À l’aide de JRE 10.0 ou inférieur lève une exception.<br /><br /> Nouvelles fonctionnalités dans 7.2 : Prise en charge de JDK 11, l’authentification Active Directory Managed Service Identity (MSI), prise en charge OSGi, SQLServerError APIs. |    


  Le 7.2 du pilote JDBC est également disponible sur le référentiel Central Maven et peuvent être ajoutés à un projet Maven en ajoutant le code suivant dans le fichier POM. XML :  
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.2.0.jre11</version>
</dependency>
```
 
**Microsoft JDBC Driver 7.0 pour SQL Server :**  

  JDBC Driver 7.0 comporte deux bibliothèques de classes JAR dans chaque package d’installation : **mssql-jdbc-7.0.0.jre8.jar** et **mssql-jdbc-7.0.0.jre10.jar**.

  JDBC Driver 7.0 est conçu pour fonctionner avec toutes les principales machines virtuelles Java et être pris en charge par celles-ci. Toutefois, il est testé uniquement sur OpenJDK 8.0 et 10.0.
  
  Le tableau suivant récapitule les versions prises en charge par les deux fichiers JAR fournis avec Microsoft JDBC Drivers 7.0 pour SQL Server :  
  
  |JAR|Compatibilité avec la version de JDBC|Java Version recommandée|Description|  
|---------|-----------------------------|----------------------|-----------------|   
|mssql-jdbc-7.0.0.jre8.jar|4.2|8|Nécessite Java Runtime Environment (JRE) 8.0. À l’aide de JRE 7.0 ou inférieure lève une exception.<br /><br /> Nouvelles fonctionnalités dans 7.0 : Prise en charge de JDK 10, niveau de conformité de mise à jour par défaut pour les spécifications de JDBC 4.2, prise en charge des types de données spatiales, propriété de connexion cancelQueryTimeout, méthodes de demande de limite, useBulkCopyForBatchInsert de propriété de connexion, données de découverte et Classification plus d’informations, extension de la fonctionnalité UTF-8 et prise en charge CityHash. |    
|mssql-jdbc-7.0.0.jre10.jar|4.3|10|Nécessite Java Runtime Environment (JRE) 10.0. À l’aide de JRE 9.0 ou inférieur lève une exception.<br /><br /> Nouvelles fonctionnalités dans 7.0 : Prise en charge de JDK 10, niveau de conformité de mise à jour par défaut pour les spécifications de JDBC 4.2, prise en charge des types de données spatiales, propriété de connexion cancelQueryTimeout, méthodes de demande de limite, useBulkCopyForBatchInsert de propriété de connexion, données de découverte et Classification plus d’informations, extension de la fonctionnalité UTF-8 et prise en charge CityHash. |    


  Le 7.0 du pilote JDBC est également disponible sur le référentiel Central Maven et peuvent être ajoutés à un projet Maven en ajoutant le code suivant dans le fichier POM. XML :  
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.0.0.jre10</version>
</dependency>
```
  
**Microsoft JDBC Driver 6.4 pour SQL Server :**  

  JDBC Driver 6.4 comporte trois bibliothèques de classes JAR dans chaque package d’installation : **mssql-jdbc-6.4.0.jre7.jar**, **mssql-jdbc-6.4.0.jre8.jar** et **mssql-jdbc-6.4.0.jre9.jar**.

  JDBC Driver 6.4 est conçu pour fonctionner avec toutes les principales machines virtuelles Java et être pris en charge par celles-ci. Toutefois, il est testé uniquement sur OpenJDK 7.0, 8.0 et 9.0.
  
  Le tableau suivant récapitule les versions prises en charge par les trois fichiers JAR fournis avec Microsoft JDBC Drivers 6.4 pour SQL Server :  
  
  |JAR|Compatibilité avec la version de JDBC|Java Version recommandée|Description|  
|---------|-----------------------------|----------------------|-----------------|   
|mssql-jdbc-6.4.0.jre7.jar|4.1|7|Nécessite Java Runtime Environment (JRE) 7.0. À l’aide de JRE 6.0 ou inférieure lève une exception.<br /><br /> Nouvelles fonctionnalités dans 6.4 incluent : L’authentification Azure AD pour Linux, Principal/mot de passe de Kerberos, la détection automatique du domaine dans le SPN pour l’authentification entre domaines, la délégation contrainte Kerberos, délai de requête, délai d’expiration de Socket et descripteur d’instruction préparée à réutiliser. |  
|mssql-jdbc-6.4.0.jre8.jar|4.2|8|Nécessite Java Runtime Environment (JRE) 8.0. À l’aide de JRE 7.0 ou inférieure lève une exception.<br /><br /> Nouvelles fonctionnalités dans 6.4 incluent : L’authentification Azure AD pour Linux, Principal/mot de passe de Kerberos, la détection automatique du domaine dans le SPN pour l’authentification entre domaines, la délégation contrainte Kerberos, délai de requête, délai d’expiration de Socket et descripteur d’instruction préparée à réutiliser. |    
|mssql-jdbc-6.4.0.jre9.jar|4.3|9|Nécessite Java Runtime Environment (JRE) 9.0. À l’aide de JRE 8.0 ou inférieur lève une exception.<br /><br /> Nouvelles fonctionnalités dans 6.4 incluent : L’authentification Azure AD pour Linux, Principal/mot de passe de Kerberos, la détection automatique du domaine dans le SPN pour l’authentification entre domaines, la délégation contrainte Kerberos, délai de requête, délai d’expiration de Socket et descripteur d’instruction préparée à réutiliser. |

JDBC Driver 6.4 est également disponible sur le référentiel Central Maven et peuvent être ajoutés à un projet Maven en ajoutant le code suivant dans le fichier POM. XML 

 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.4.0.jre9</version>
</dependency>
```

**Microsoft JDBC Driver 6.2 pour SQL Server :**  
  
  JDBC Driver 6.2 inclut deux bibliothèques de classes JAR dans chaque package d’installation : **mssql-jdbc-6.2.2.jre7.jar** et **mssql-jdbc-6.2.2.jre8.jar**. 
  
 JDBC Driver 6.2 est conçu pour fonctionner avec toutes les principales machines virtuelles Java et être pris en charge par celles-ci. Toutefois, il est testé uniquement sur Sun JRE 5.0, 6.0, 7.0 et 8.0.
  
 Le tableau suivant récapitule les versions prises en charge par les deux fichiers JAR fournis avec Microsoft JDBC Drivers 6.0 et 4.2 pour SQL Server :  
  
|JAR|Compatibilité avec la version de JDBC|Java Version recommandée|Description|  
|---------|-----------------------------|----------------------|-----------------|
|mssql-jdbc-6.2.2.jre7.jar|4.1|7|Nécessite Java Runtime Environment (JRE) 7.0. À l’aide de JRE 6.0 ou inférieure lève une exception.<br /><br /> Nouvelles fonctionnalités dans 6.2 : L’authentification Azure AD pour Linux, Principal/mot de passe de Kerberos, la détection automatique du domaine dans le SPN pour l’authentification entre domaines, la délégation contrainte Kerberos, délai de requête, délai d’expiration de Socket et descripteur d’instruction préparée à réutiliser. |  
|mssql-jdbc-6.2.3.jre8.jar|4.2|8|Nécessite Java Runtime Environment (JRE) 8.0. À l’aide de JRE 7.0 ou inférieure lève une exception.<br /><br /> Nouvelles fonctionnalités dans 6.2 : L’authentification Azure AD pour Linux, Principal/mot de passe de Kerberos, la détection automatique du domaine dans le SPN pour l’authentification entre domaines, la délégation contrainte Kerberos, délai de requête, délai d’expiration de Socket et descripteur d’instruction préparée réutiliser|    

  JDBC Driver 6.2 est également disponible sur le référentiel Central Maven et peuvent être ajoutés à un projet Maven en ajoutant le code suivant dans le fichier POM. XML 
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.2.2.jre8</version>
</dependency>
```    

 **Microsoft JDBC Driver 6.0 et 4.2 pour SQL Server :**  
  
  Les pilotes JDBC 6.0 et 4.2 incluent deux bibliothèques de classes JAR dans chaque package d’installation : **sqljdbc41.jar**, et **sqljdbc42.jar**. 
  
 Les pilotes JDBC Driver 6.0 et 4.2 sont conçus pour fonctionner avec toutes les principales machines virtuelles Java et être pris en charge par celles-ci. Toutefois, il est testé uniquement sur Sun JRE 5.0, 6.0, 7.0 et 8.0.
  
 Le tableau suivant récapitule les versions prises en charge par les deux fichiers JAR fournis avec Microsoft JDBC Drivers 6.0 et 4.2 pour SQL Server :  
  
|JAR|Compatibilité avec la version de JDBC|Java Version recommandée|Description|  
|---------|-----------------------------|----------------------|-----------------|   
|sqljdbc41.jar|4.1|7|Nécessite Java Runtime Environment (JRE) 7.0. À l’aide de JRE 6.0 ou inférieure lève une exception.<br /><br /> Nouvelles fonctionnalités des packages 6.0 & 4.2 incluent : JDBC 4.1 copie en bloc et conformité<br /><br /> En outre, nouvelles fonctionnalités dans le package 6.0 : Always Encrypted, les paramètres table, authentification Azure Active Directory, connexions transparentes aux groupes de disponibilité AlwaysOn, amélioration de la récupération des métadonnées de paramètre pour les requêtes préparées et le nom de domaine international (IDN)|  
|sqljdbc42.jar|4.2|8|Nécessite Java Runtime Environment (JRE) 8.0. À l’aide de JRE 7.0 ou inférieure lève une exception.<br /><br /> Nouvelles fonctionnalités des packages 6.0 & 4.2 incluent : JDBC 4.1 conformité, JDBC 4.2, copie et la conformité en bloc<br /><br /> En outre, nouvelles fonctionnalités dans le package 6.0 : Always Encrypted, les paramètres table, authentification Azure Active Directory, connexions transparentes aux groupes de disponibilité AlwaysOn, amélioration de la récupération des métadonnées de paramètre pour les requêtes préparées et le nom de domaine international (IDN)|  
  
 **Microsoft JDBC Driver 4.1 pour SQL Server :**  
  
 Le pilote JDBC 4.1 inclut une bibliothèque de classes JAR dans chaque package d’installation : **sqljdbc41.jar**.  
    
|JAR|Description|  
|---------|-----------------|  
|sqljdbc41.jar|La bibliothèque de classes **sqljdbc41.jar** prend en charge l’API JDBC 4.0. Elle comprend toutes les fonctionnalités du pilote JDBC 4.0, ainsi que les méthodes de l’API JDBC 4.0. JDBC 4.1 n’est pas pris en charge (il lève une exception « SQLFeatureNotSupportedException »).<br /><br /> La bibliothèque de classes **sqljdbc41.jar** nécessite la version 7.0 de l’environnement d’exécution Java (JRE, Java Runtime Environment). À l’aide de **sqljdbc41.jar** sur JRE 6.0 et 5.0 lève une exception.<br /><br /> 
  
 Le pilote JDBC est conçu pour fonctionner avec toutes les principales machines virtuelles Java et être pris en charge par celles-ci. Toutefois, il est testé sur Sun JRE 5.0, 6.0 et 7.0.
  
 Le tableau suivant récapitule les versions prises en charge par le fichier JAR fourni avec Microsoft JDBC Driver 4.1 pour SQL Server.  
  
|JAR|Version JDBC|JRE (exécution possible)|JDK (compilation possible)|  
|---------|------------------|---------------------|-------------------------|   
|sqljdbc41.jar|4|7|7 6 5|  
  
## <a name="sql-server-requirements"></a>Configuration SQL Server requise  
 Le pilote JDBC prend en charge les connexions à Azure SQL Database et à SQL Server. Pour les pilotes Microsoft JDBC 4.2 et 4.1 pour SQL Server, la prise en charge commence avec SQL Server 2008.
  
## <a name="operating-system-requirements"></a>Système d'exploitation requis  
 Le pilote JDBC est conçu pour fonctionner sur tout système d'exploitation prenant en charge l'utilisation d'une machine virtuelle Java (JVM). Toutefois, seuls les systèmes d'exploitation Sun Solaris, SUSE Linux et Windows ont été testés officiellement.  
  
## <a name="supported-languages"></a>Langues prises en charge  
 Le pilote JDBC prend en charge tous les classements de colonnes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur les classements pris en charge par le pilote JDBC, consultez [fonctionnalités internationales du pilote JDBC](../../connect/jdbc/international-features-of-the-jdbc-driver.md).  
  
 Pour plus d’informations sur les classements, consultez la rubrique « Utilisation des classements » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a> Voir aussi  
 [Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
