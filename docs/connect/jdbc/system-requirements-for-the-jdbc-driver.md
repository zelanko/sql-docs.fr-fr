---
title: Configuration système requise pour le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 447792bb-f39b-49b4-9fd0-1ef4154c74ab
caps.latest.revision: 73
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 306c7bcd764ed70f23c51667580fb9f8e79f0e65
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37978721"
---
# <a name="system-requirements-for-the-jdbc-driver"></a>Configuration requise pour le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Pour accéder aux données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] à l’aide du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], vous devez installer les composants suivants sur votre ordinateur :

- [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ([Télécharger](download-microsoft-jdbc-driver-for-sql-server.md))
- Environnement d'exécution Java

## <a name="java-runtime-environment-requirements"></a>Configuration requise pour l'environnement d'exécution Java  
 À compter du Pilote JDBC 6.4 Microsoft pour SQL Server, le Kit JDK (Sun Java SE Development Kit) version 9.0 et l’environnement d’exécution Java (JRE, Java Runtime Environment) version 9.0 sont pris en charge.

 À compter du pilote Microsoft JDBC 4.2 pour SQL Server, Sun Java SE Development Kit (JDK) 8.0 et Java Runtime Environment (JRE) 8.0 sont pris en charge. La prise en charge de l’API de spécification Java Database Connectivity (JDBC) a été étendue pour inclure l’API JDBC 4.1 et 4.2.  
  
 À compter du Pilote JDBC 4.1 Microsoft pour SQL Server, le Kit de développement Java (JDK) version 7.0 et l'environnement d'exécution Java (JRE, Java Runtime Environment) version 7.0 sont pris en charge.  
  
 À partir de [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], la prise en charge de l’API Spec JDBC (Java Database Connectivity) par le pilote JDBC a été étendue pour inclure l’API JDBC 4.0. L'API JDBC 4.0 a été introduit dans le cadre du kit de développement logiciel JDK (Sun Java SE Development Kit) 6.0 et de l'environnement JRE (Java Runtime Environment) 6.0. JDBC 4.0 est un surensemble de l'API JDBC 3.0.  
  
 Quand vous déployez le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] sur les systèmes d’exploitation Windows et UNIX, vous devez utiliser les packages d’installation, respectivement *sqljdbc_\<version>_enu.exe*, et *sqljdbc_\<version>_enu.tar.gz*. Pour plus d’informations sur la façon de déployer le pilote JDBC, consultez [déploiement du pilote JDBC](../../connect/jdbc/deploying-the-jdbc-driver.md) rubrique.  
  
**Microsoft JDBC Driver 6.4 pour SQL Server :**  

  JDBC Driver 6.4 comprend trois bibliothèques de classes JAR dans chaque package d’installation : **mssql-jdbc-6.4.0.jre7.jar**, **mssql-jdbc-6.4.0.jre8.jar**, et **mssql-jdbc-6.4.0.jre9.jar** .

  JDBC Driver 6.4 a été conçu pour être pris en charge par toutes les principales machines virtuelles Java équivalentes à Sun, mais il a été testé uniquement sur Sun JRE 7.0, 8.0 et 9.0.
  
  Le tableau suivant récapitule les versions prises en charge par les trois fichiers JAR fournis avec Microsoft JDBC Drivers 6.4 pour SQL Server :  
  
  |JAR|Compatibilité avec la version de JDBC|Java Version recommandée|Description|  
|---------|-----------------------------|----------------------|-----------------|   
|mssql-jdbc-6.4.0.jre7.jar|4.1|7|Nécessite Java Runtime Environment (JRE) 7.0. À l’aide de JRE 6.0 ou inférieure lève une exception.<br /><br /> Les nouvelles fonctionnalités dans 6.4 incluent : l’authentification Azure AD pour Linux, méthode Principal/mot de passe pour Kerberos, la détection automatique du domaine dans le SPN pour l’authentification entre domaines, la délégation contrainte Kerberos, délai de requête, délai d’expiration de Socket et préparées handle d’instruction réutiliser. |  
|mssql-jdbc-6.4.0.jre8.jar|4.2|8|Nécessite Java Runtime Environment (JRE) 8.0. À l’aide de JRE 7.0 ou inférieure lève une exception.<br /><br /> Les nouvelles fonctionnalités dans 6.4 incluent : l’authentification Azure AD pour Linux, méthode Principal/mot de passe pour Kerberos, la détection automatique du domaine dans le SPN pour l’authentification entre domaines, la délégation contrainte Kerberos, délai de requête, délai d’expiration de Socket et préparées handle d’instruction réutiliser. |    
|mssql-jdbc-6.4.0.jre9.jar|4.3|9|Nécessite Java Runtime Environment (JRE) 9.0. À l’aide de JRE 8.0 ou inférieur lève une exception.<br /><br /> Les nouvelles fonctionnalités dans 6.4 incluent : l’authentification Azure AD pour Linux, méthode Principal/mot de passe pour Kerberos, la détection automatique du domaine dans le SPN pour l’authentification entre domaines, la délégation contrainte Kerberos, délai de requête, délai d’expiration de Socket et préparées handle d’instruction réutiliser. |    


  JDBC Driver 6.4 est également disponible sur le référentiel Central Maven et peuvent être ajoutés à un projet Maven en ajoutant le code suivant dans le fichier POM. XML 
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.4.0.jre9</version>
</dependency>
```    
**Microsoft JDBC Driver 6.2 pour SQL Server :**  
  
  JDBC Driver 6.2 comprend deux bibliothèques de classes JAR dans chaque package d’installation : **mssql-jdbc-6.2.1.jre7.jar**, et **mssql-jdbc-6.2.1.jre8.jar**. 
  
 JDBC Driver 6.2 a été conçu pour être pris en charge par toutes les principales machines virtuelles Java équivalentes à Sun, mais il a été testé uniquement sur Sun JRE 5.0, 6.0, 7.0 et 8.0. 
  
 Le tableau suivant récapitule les versions prises en charge par les deux fichiers JAR fournis avec Microsoft JDBC Drivers 6.0 et 4.2 pour SQL Server :  
  
|JAR|Compatibilité avec la version de JDBC|Java Version recommandée|Description|  
|---------|-----------------------------|----------------------|-----------------|   
|MSSQL-jdbc-6.2.1.jre7.jar|4.1|7|Nécessite Java Runtime Environment (JRE) 7.0. À l’aide de JRE 6.0 ou inférieure lève une exception.<br /><br /> Les nouvelles fonctionnalités dans 6.2 incluent : l’authentification Azure AD pour Linux, méthode Principal/mot de passe pour Kerberos, la détection automatique du domaine dans le SPN pour l’authentification entre domaines, la délégation contrainte Kerberos, délai de requête, délai d’expiration de Socket et préparées handle d’instruction réutiliser. |  
|MSSQL-jdbc-6.2.1.jre8.jar|4.2|8|Nécessite Java Runtime Environment (JRE) 8.0. À l’aide de JRE 7.0 ou inférieure lève une exception.<br /><br /> Les nouvelles fonctionnalités dans 6.2 incluent : l’authentification Azure AD pour Linux, méthode Principal/mot de passe pour Kerberos, la détection automatique du domaine dans le SPN pour l’authentification entre domaines, la délégation contrainte Kerberos, délai de requête, délai d’expiration de Socket et préparées réutilisation de handle d’instruction|    

  JDBC Driver 6.2 est également disponible sur le référentiel Central Maven et peuvent être ajoutés à un projet Maven en ajoutant le code suivant dans le fichier POM. XML 
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.2.1.jre8</version>
</dependency>
```    

 **Microsoft JDBC Driver 6.0 et 4.2 pour SQL Server :**  
  
  Les pilotes JDBC 6.0 et 4.2 incluent deux bibliothèques de classes JAR dans chaque package d’installation : **sqljdbc41.jar**, et **sqljdbc42.jar**. 
  
 Les pilotes JDBC 6.0 et 4.2 ont été conçus pour être pris en charge par toutes les principales machines virtuelles Java équivalentes à Sun, mais il a été testé uniquement sur Sun JRE 5.0, 6.0, 7.0 et 8.0. 
  
 Le tableau suivant récapitule les versions prises en charge par les deux fichiers JAR fournis avec Microsoft JDBC Drivers 6.0 et 4.2 pour SQL Server :  
  
|JAR|Compatibilité avec la version de JDBC|Java Version recommandée|Description|  
|---------|-----------------------------|----------------------|-----------------|   
|sqljdbc41.jar|4.1|7|Nécessite Java Runtime Environment (JRE) 7.0. À l’aide de JRE 6.0 ou inférieure lève une exception.<br /><br /> Parmi les nouvelles fonctionnalités des packages 6.0 & 4.2 figurent la copie en bloc et la conformité JDBC 4.1.<br /><br /> En outre, les nouvelles fonctionnalités dans le package 6.0 incluent : préparation des connexions transparentes aux groupes de disponibilité AlwaysOn, amélioration de la récupération des métadonnées de paramètre pour Always Encrypted, les paramètres de la table, authentification Azure Active Directory, requêtes et du nom de domaine international (IDN)|  
|sqljdbc42.jar|4.2|8|Nécessite Java Runtime Environment (JRE) 8.0. À l’aide de JRE 7.0 ou inférieure lève une exception.<br /><br /> Parmi les nouvelles fonctionnalités des packages 6.0 & 4.2 figurent la copie en bloc, la conformité JDBC 4.2 et la conformité JDBC 4.1.<br /><br /> En outre, les nouvelles fonctionnalités dans le package 6.0 incluent : préparation des connexions transparentes aux groupes de disponibilité AlwaysOn, amélioration de la récupération des métadonnées de paramètre pour Always Encrypted, les paramètres de la table, authentification Azure Active Directory, requêtes et du nom de domaine international (IDN)|  
  
 **Microsoft JDBC Driver 4.1 pour SQL Server :**  
  
 Le pilote JDBC 4.1 inclut une bibliothèque de classes JAR dans chaque package d’installation : **sqljdbc41.jar**.  
    
|JAR|Description|  
|---------|-----------------|  
|sqljdbc41.jar|La bibliothèque de classes **sqljdbc41.jar** prend en charge l’API JDBC 4.0. Elle comprend toutes les fonctionnalités du pilote JDBC 4.0, ainsi que les méthodes de l’API JDBC 4.0. JDBC 4.1 n’est pas pris en charge (il lève une exception « SQLFeatureNotSupportedException »).<br /><br /> La bibliothèque de classes **sqljdbc41.jar** nécessite la version 7.0 de l’environnement d’exécution Java (JRE, Java Runtime Environment). À l’aide de **sqljdbc41.jar** sur JRE 6.0 et 5.0 lève une exception.<br /><br /> 
  
 Le pilote JDBC est conçu pour fonctionner et être pris en charge par toutes les principales machines virtuelles Java équivalentes de Sun. Toutefois, il est testé sur Sun JRE 5.0, 6.0 et 7.0.  
  
 Le tableau suivant récapitule les versions prises en charge par le fichier JAR fourni avec Microsoft JDBC Driver 4.1 pour SQL Server.  
  
|JAR|Version JDBC|JRE (exécution possible)|JDK (compilation possible)|  
|---------|------------------|---------------------|-------------------------|   
|sqljdbc41.jar|4|7|7 6 5|  
  
## <a name="sql-server-requirements"></a>Configuration SQL Server requise  
 Le pilote JDBC prend en charge les connexions à Azure SQL Database et à SQL Server. Pour les pilotes Microsoft JDBC 4.2 et 4.1 pour SQL Server, la prise en charge commence avec SQL Server 2008.
  
## <a name="operating-system-requirements"></a>Système d'exploitation requis  
 Le pilote JDBC est conçu pour fonctionner sur tout système d'exploitation prenant en charge l'utilisation d'une machine virtuelle Java (JVM). Toutefois, seuls les systèmes d'exploitation Sun Solaris, SUSE Linux et Windows ont été testés officiellement.  
  
## <a name="supported-languages"></a>Langues prises en charge  
 Le pilote JDBC prend en charge tous les classements de colonnes [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Pour plus d’informations sur les classements pris en charge par le pilote JDBC, consultez [fonctionnalités internationales du pilote JDBC](../../connect/jdbc/international-features-of-the-jdbc-driver.md).  
  
 Pour plus d’informations sur les classements, consultez la rubrique « Utilisation des classements » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="see-also"></a> Voir aussi  
 [Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
