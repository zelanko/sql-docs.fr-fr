---
title: "Configuration système requise pour le pilote JDBC | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 447792bb-f39b-49b4-9fd0-1ef4154c74ab
caps.latest.revision: "73"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 910f1725cee29593a8ca5a6fbb17ca7ed1f2c5db
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="system-requirements-for-the-jdbc-driver"></a>Configuration requise pour le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Pour accéder aux données d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] à l’aide de la [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], vous devez disposer des composants suivants sur votre ordinateur :  
  
-   [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]  
  
     Vous pouvez télécharger Microsoft JDBC Driver depuis le lien Microsoft Download Center ci-dessous : 
     * [Microsoft JDBC Driver 6.2 pour SQL Server](http://go.microsoft.com/fwlink/?linkid=852460)
     * [Microsoft JDBC Driver 6.0 pour SQL Server](http://go.microsoft.com/fwlink/?linkid=841535)
     * [Microsoft JDBC Driver 4.2 pour SQL Server](http://go.microsoft.com/fwlink/?linkid=841534) 
     * [Microsoft JDBC Driver 4.1 pour SQL Server](http://go.microsoft.com/fwlink/?linkid=841533) 
     * [Microsoft JDBC Driver 4.0 pour SQL Server](http://go.microsoft.com/fwlink/?linkid=841532)
  
-   Environnement d'exécution Java  
  
## <a name="java-runtime-environment-requirements"></a>Spécifications concernant Java Runtime Environment  
 À compter du pilote Microsoft JDBC 4.2 pour SQL Server, Sun Java SE Development Kit (JDK) 8.0 et Java Runtime Environment (JRE) 8.0 sont pris en charge. La prise en charge de l’API de spécification Java Database Connectivity (JDBC) a été étendue pour inclure l’API JDBC 4.1 et 4.2.  
  
 À compter du Pilote JDBC 4.1 Microsoft pour SQL Server, le Kit de développement Java (JDK) version 7.0 et l'environnement d'exécution Java (JRE, Java Runtime Environment) version 7.0 sont pris en charge.  
  
 En commençant par le [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], la prise en charge du pilote JDBC pour l’API de spécification Java Database Connectivity (JDBC) a été étendu pour inclure l’API JDBC 4.0. L'API JDBC 4.0 a été introduit dans le cadre du kit de développement logiciel JDK (Sun Java SE Development Kit) 6.0 et de l'environnement JRE (Java Runtime Environment) 6.0. JDBC 4.0 est un surensemble de l'API JDBC 3.0.  
  
 Lorsque vous déployez le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] sur les systèmes d’exploitation Windows et UNIX, vous devez utiliser les packages d’installation, *sqljdbc_\<version > _enu.exe* et *sqljdbc_\<version > _ ENU.tar.gz*, respectivement. Pour plus d’informations sur la façon de déployer le pilote JDBC, consultez [déploiement du pilote JDBC](../../connect/jdbc/deploying-the-jdbc-driver.md) rubrique.  
  
**Microsoft JDBC Driver 6.2 pour SQL Server :**  
  
  Le 6.2 du pilote JDBC comprend deux bibliothèques de classes JAR dans chaque package d’installation : **mssql-jdbc-6.2.1.jre7.jar**, et **mssql-jdbc-6.2.1.jre8.jar**. 
  
 Le 6.2 du pilote JDBC est conçu pour fonctionner avec et être pris en charge par tous les principaux Sun machines virtuelles Java équivalentes, mais il est testé uniquement sur Sun JRE 5.0, 6.0, 7.0 et 8.0. 
  
 Voici un résumé de prise en charge dans les deux fichiers JAR inclus avec les pilotes Microsoft JDBC 6.0 et 4.2 pour SQL Server :  
  
|JAR|Compatibilité avec la version de JDBC|Java Version recommandée| Description|  
|---------|-----------------------------|----------------------|-----------------|   
|MSSQL-jdbc-6.2.1.jre7.jar|4.1|7|Nécessite Java Runtime Environment (JRE) 7.0. L’utilisation de JRE 6.0 ou version antérieure lève une exception.<br /><br /> Nouvelles fonctionnalités de 6.2 incluent : authentification Azure AD pour Linux, méthode Principal/mot de passe pour Kerberos, la détection automatique du domaine dans le SPN pour l’authentification entre domaines, la délégation contrainte Kerberos, de délai de requête, de délai d’attente du Socket et préparées handle d’instruction réutilisation. |  
|MSSQL-jdbc-6.2.1.jre8.jar|4.2|8|Nécessite Java Runtime Environment (JRE) 8.0. L’utilisation de JRE 7.0 ou version antérieure lève une exception.<br /><br /> Nouvelles fonctionnalités de 6.2 incluent : authentification Azure AD pour Linux, méthode Principal/mot de passe pour Kerberos, la détection automatique du domaine dans le SPN pour l’authentification entre domaines, la délégation contrainte Kerberos, de délai de requête, de délai d’attente du Socket et préparées réutilisation de handle d’instruction|    

  Le 6.2 du pilote JDBC est également disponible sur le référentiel Central de Maven et peuvent ajoutés à un projet Maven en ajoutant le code suivant dans le POM. XML 
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.2.1.jre8</version>
</dependency>
```    

 **Microsoft JDBC Driver 6.0 et 4.2 pour SQL Server :**  
  
  Les pilotes JDBC 6.0 et 4.2 incluent deux bibliothèques de classes JAR dans chaque package d’installation : **sqljdbc41.jar**, et **sqljdbc42.jar**. 
  
 Les pilotes JDBC 6.0 et 4.2 sont conçus pour fonctionner avec et être pris en charge par tous les principaux Sun machines virtuelles Java équivalentes, mais est testé uniquement sur Sun JRE 5.0, 6.0, 7.0 et 8.0. 
  
 Voici un résumé de prise en charge dans les deux fichiers JAR inclus avec les pilotes Microsoft JDBC 6.0 et 4.2 pour SQL Server :  
  
|JAR|Compatibilité avec la version de JDBC|Java Version recommandée| Description|  
|---------|-----------------------------|----------------------|-----------------|   
|sqljdbc41.jar|4.1|7|Nécessite Java Runtime Environment (JRE) 7.0. L’utilisation de JRE 6.0 ou version antérieure lève une exception.<br /><br /> Parmi les nouvelles fonctionnalités des packages 6.0 & 4.2 figurent la copie en bloc et la conformité JDBC 4.1.<br /><br /> En outre, les nouvelles fonctionnalités dans le package 6.0 incluent : préparation des connexions transparentes aux groupes de disponibilité AlwaysOn, amélioration de la récupération des métadonnées de paramètre pour Always Encrypted, les paramètres de la table, Azure Active Directory Authentication, les requêtes et le nom de domaine internationaux (IDN)|  
|sqljdbc42.jar|4.2|8|Nécessite Java Runtime Environment (JRE) 8.0. L’utilisation de JRE 7.0 ou version antérieure lève une exception.<br /><br /> Parmi les nouvelles fonctionnalités des packages 6.0 & 4.2 figurent la copie en bloc, la conformité JDBC 4.2 et la conformité JDBC 4.1.<br /><br /> En outre, les nouvelles fonctionnalités dans le package 6.0 incluent : préparation des connexions transparentes aux groupes de disponibilité AlwaysOn, amélioration de la récupération des métadonnées de paramètre pour Always Encrypted, les paramètres de la table, Azure Active Directory Authentication, les requêtes et le nom de domaine internationaux (IDN)|  
  
 **Microsoft JDBC Driver 4.1 pour SQL Server :**  
  
 Le pilote JDBC 4.1 inclut une bibliothèque de classes JAR dans chaque package d’installation : **sqljdbc41.jar**.  
    
|JAR| Description|  
|---------|-----------------|  
|sqljdbc41.jar|**sqljdbc41.jar** bibliothèque de classes fournit la prise en charge de l’API JDBC 4.0. Elle inclut toutes les fonctionnalités du pilote JDBC 4.0, ainsi que les méthodes de l’API JDBC 4.0. JDBC 4.1 n'est pas pris en charge (il lève une exception « SQLFeatureNotSupportedException »).<br /><br /> **sqljdbc41.jar** bibliothèque de classes requiert un 7.0 Java Runtime Environment (JRE). À l’aide de **sqljdbc41.jar** sur JRE 6.0 et 5.0 lève une exception.<br /><br /> 
  
 Notez que le pilote JDBC est conçu pour être pris en charge par toutes les principales machines virtuelles Java équivalentes de Sun ; toutefois, il est testé sur Sun JRE 5.0, 6.0 et 7.0.  
  
 Voici un résumé de prise en charge fournie par le fichier JAR inclus avec Microsoft JDBC Driver 4.1 pour SQL Server.  
  
|JAR|Version JDBC|JRE (exécution possible)|JDK (compilation possible)|  
|---------|------------------|---------------------|-------------------------|   
|sqljdbc41.jar|4|7|7 6 5|  
  
 **Microsoft JDBC Driver 4.0 pour SQL Server :**  
  
 Pour prendre en charge de la compatibilité descendante et des scénarios possibles de mise à niveau, le pilote JDBC comprend deux bibliothèques de classes JAR dans chaque package d’installation : **sqljdbc.jar** et **sqljdbc4.jar**.  
  
|JAR| Description|  
|---------|-----------------|  
|sqljdbc.jar|**sqljdbc.jar** bibliothèque de classes fournit la prise en charge JDBC 3.0.<br /><br /> **sqljdbc.jar** bibliothèque de classes requiert un environnement d’exécution Java (JRE) version 5.0. À l’aide de **sqljdbc.jar** dans JRE 6.0 ou JRE 7.0 lève une exception lors de la connexion à une base de données.<br /><br /> **Remarque :** du pilote JDBC ne prend pas en charge JRE 1.4. Vous devez mettre à niveau JRE 1.4 vers JRE 5.0, JRE 6.0 ou JRE 7.0 lors de l'utilisation du pilote JDBC. Dans certains cas, vous devrez peut-être recompiler votre application, car elle risque de ne pas être compatible avec l'API JDK 5.0 ou l'API JDK 6.0. Pour plus d'informations, consultez la documentation disponible sur le site web de Sun Microsystems.<br /><br /> [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]ne prend pas en charge JDK 7.|  
|sqljdbc4.jar|**sqljdbc4.jar** bibliothèque de classes fournit la prise en charge de l’API JDBC 4.0. Elle inclut toutes les fonctionnalités de la **sqljdbc.jar** , ainsi que les nouvelles méthodes de l’API JDBC 4.0.<br /><br /> **sqljdbc4.jar** bibliothèque de classes requiert un environnement d’exécution Java (JRE) version 6.0 ou 7.0. À l’aide de **sqljdbc4.jar** sur JRE 5.0 lève une exception.<br /><br /> **Remarque :** utiliser **sqljdbc4.jar** lorsque votre application doit exécuter sur JRE 6.0 ou 7.0, même si votre application n’utilise pas de fonctionnalités de l’API JDBC 4.0.|  
  
 Notez que le pilote JDBC est conçu pour être pris en charge par toutes les principales machines virtuelles Java équivalentes de Sun ; toutefois, il est testé sur Sun JRE 5.0, 6.0 et 7.0.  
  
## <a name="sql-server-requirements"></a>Configuration SQL Server requise  
 Le pilote JDBC prend en charge les connexions à la base de données SQL Azure et SQL Server. Pour les pilotes Microsoft JDBC 4.2 et 4.1 pour SQL Server, la prise en charge commence avec SQL Server 2008. Pour le pilote Microsoft JDBC 4.0 pour SQL Server, la prise en charge commence avec SQL Server 2005.  
  
## <a name="operating-system-requirements"></a>Système d'exploitation requis  
 Le pilote JDBC est conçu pour fonctionner sur tout système d'exploitation prenant en charge l'utilisation d'une machine virtuelle Java (JVM). Toutefois, seuls les systèmes d'exploitation Sun Solaris, SUSE Linux et Windows ont été testés officiellement.  
  
## <a name="supported-languages"></a>Langues prises en charge  
 Le pilote JDBC prend en charge tous les [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] classements de colonne. Pour plus d’informations sur les classements pris en charge par le pilote JDBC, consultez [fonctionnalités internationales du pilote JDBC](../../connect/jdbc/international-features-of-the-jdbc-driver.md).  
  
 Pour plus d’informations sur les classements, consultez la rubrique « Classements » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
