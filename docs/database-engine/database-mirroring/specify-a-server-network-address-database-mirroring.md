---
title: "Sp&#233;cifier une adresse r&#233;seau de serveur (mise en miroir de bases de donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mise en miroir de base de données [SQL Server], déploiement"
  - "mise en miroir de bases de données [SQL Server], point de terminaison"
  - "points de terminaison [SQL Server], mise en miroir de base de données"
  - "adresses réseau du serveur [SQL Server]"
ms.assetid: a64d4b6b-9016-4f1e-a310-b1df181dd0c6
caps.latest.revision: 60
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 59
---
# Sp&#233;cifier une adresse r&#233;seau de serveur (mise en miroir de bases de donn&#233;es)
  La configuration d'une session de mise en miroir de bases de données requiert une adresse réseau de serveur pour chaque instance de serveur. L'adresse réseau de serveur d'une instance de serveur doit identifier sans ambiguïté l'instance en fournissant une adresse système et le numéro du port sur lequel l'instance est à l'écoute.  
  
 Avant de pouvoir spécifier un port dans une adresse réseau de serveur, le point de terminaison de mise en miroir de bases de données doit exister sur l'instance de serveur. Pour plus d’informations, consultez [Créer un point de terminaison de mise en miroir de bases de données pour l’authentification Windows &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).  
  
 **Dans cette rubrique :**  
  
-   [Syntaxe d'une adresse réseau de serveur](#Syntax)  
  
-   [Recherche du nom de domaine complet](#FindFqDn)  
  
-   [Exemples](#Examples)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="Syntax"></a> Syntaxe d'une adresse réseau de serveur  
 La syntaxe d'une adresse réseau de serveur est de la forme :  
  
 TCP**://***<adresse_système>***:***\<port>*  
  
 où  
  
-   *<adresse_système>* est une chaîne qui identifie sans ambiguïté le système informatique de destination. En règle générale, l'adresse de serveur est un nom système (si les systèmes sont dans le même domaine), un nom de domaine complet ou une adresse IP :  
  
    -   Si les systèmes sont dans le même domaine, vous pouvez utiliser le nom du système informatique ; par exemple, `SYSTEM46`.  
  
    -   Pour pouvoir utiliser une adresse IP, elle doit être unique dans votre environnement. Nous vous recommandons d'utiliser une adresse IP seulement si elle est statique. L'adresse IP peut être une adresse IP Version 4 (IPv4) ou IP Version 6 (IPv6). Une adresse IPv6 doit être placée entre crochets, par exemple : **[***<adresse_IPv6>***]**.  
  
         Pour connaître l'adresse IP d'un système, à l'invite de commandes Windows, entrez la commande **ipconfig** .  
  
    -   L'utilisation du nom de domaine complet garantit un fonctionnement correct. Il s'agit d'une chaîne d'adresse définie localement qui présente des formes différentes dans des emplacements différents. Souvent, mais pas systématiquement, un nom de domaine complet correspond à un nom composé qui inclut le nom de l'ordinateur et une série de segments de domaine séparés par des points, de la forme :  
  
         *nom_ordinateur* **.** *segment_domaine*[...**.***segment_domaine*]  
  
         où *nom_ordinateur* correspond au nom réseau de l’ordinateur qui exécute l’instance de serveur et *segment_domaine*[...**.***segment_domaine*] représente les autres informations de domaine du serveur ; par exemple : `localinfo.corp.Adventure-Works.com`.  
  
         Le contenu et le nombre de segments de domaine sont déterminés au sein de la société ou de l'organisation. Si vous ne connaissez pas le nom de domaine complet de votre serveur, contactez votre administrateur système.  
  
        > [!NOTE]  
        >  Pour plus d'informations sur la recherche d'un nom de domaine complet, consultez « Recherche du nom de domaine complet » plus loin dans cette rubrique.  
  
-   *\<port>* est le numéro de port utilisé par le point de terminaison de mise en miroir de l’instance de serveur partenaire. Pour plus d’informations sur la spécification d’un point de terminaison, consultez [Créer un point de terminaison de mise en miroir de bases de données pour l’authentification Windows &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).  
  
     Un point de terminaison de mise en miroir de bases de données peut utiliser tout port disponible sur le système informatique. Chaque numéro de port sur un système d'ordinateur doit être associé à un seul point de terminaison, et chaque point de terminaison est associé à une seule instance de serveur ; ainsi, différentes instances de serveurs sur le même serveur écoutent sur différents points de terminaison dotés de différents ports. Par conséquent, le port que vous spécifiez dans l'adresse réseau du serveur lorsque vous configurez une session de mise en miroir de bases de données dirigera systématiquement la session vers l'instance de serveur dont le point de terminaison est associé à ce port.  
  
     Dans l'adresse réseau d'une instance de serveur, seul le numéro de port associé à son point de terminaison de mise en miroir permet de différencier cette instance des autres instances sur l'ordinateur. L'illustration suivante présente les adresses réseau de deux instances de serveurs sur un même ordinateur. L'instance par défaut utilise le port `7022` et l'instance nommée utilise le port `7033`. Les adresses réseau de serveur de ces deux instances de serveur sont, respectivement : `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` et `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`. Notez que l'adresse ne contient pas le nom de l'instance du serveur.  
  
     ![Adresses de réseau serveur d'une instance par défaut](../../database-engine/availability-groups/windows/media/dbm-2-instances-ports-1-system.gif "Adresses de réseau serveur d'une instance par défaut")  
  
     Pour identifier le port actuellement associé au point de terminaison de mise en miroir de bases de données d'une instance de serveur, utilisez l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante :  
  
    ```  
    SELECT type_desc, port FROM sys.tcp_endpoints  
    ```  
  
     Recherchez la ligne dont la valeur **type_desc** est « DATABASE_MIRRORING » et utilisez le numéro de port correspondant.  
  
### Exemples  
  
#### A. Utilisation d'un nom système  
 L'adresse réseau de serveur suivante spécifie un nom système, `SYSTEM46`, et un port, `7022`.  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://SYSTEM46:7022';  
```  
  
#### B. Utilisation d'un nom de domaine complet  
 L'adresse réseau de serveur suivante spécifie un nom de domaine complet, `DBSERVER8.manufacturing.Adventure-Works.com`, et un port, `7024`.  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://DBSERVER8.manufacturing.Adventure-Works.com:7024';  
```  
  
#### C. Utilisation d'une adresse IPv4  
 L'adresse réseau de serveur suivante spécifie une adresse IPv4, `10.193.9.134`, et un port, `7023`.  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://10.193.9.134:7023';  
```  
  
#### D. Utilisation d'une adresse IPv6  
 L'adresse réseau de serveur suivante contient une adresse IPv6, `2001:4898:23:1002:20f:1fff:feff:b3a3`, et un port, `7022`.  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://[2001:4898:23:1002:20f:1fff:feff:b3a3]:7022';  
```  
  
## Recherche du nom de domaine complet  
 Pour rechercher le nom de domaine complet d'un système, à l'invite de commandes Windows de ce système, entrez :  
  
 **IPCONFIG /ALL**  
  
 Pour former le nom de domaine complet, concaténez les valeurs de *<nom_hôte>* et *<Suffixe_DNS_principal>* de la manière suivante :  
  
 *<nom_hôte>* **.** *<Suffixe_DNS_principal>*  
  
 Par exemple, la configuration IP  
  
 `Host Name  .  .  .  .  .  .  : MYSERVER`  
  
 `Primary Dns Suffix  .  .  .  : mydomain.Adventure-Works.com`  
  
 équivaut au nom de domaine complet suivant :  
  
 `MYSERVER.mydomain.Adventure-Works.com`  
  
##  <a name="Examples"></a> Exemples  
 L'exemple suivant montre l'adresse réseau de serveur d'une instance de serveur sur un système informatique nommé `REMOTESYSTEM3` dans un autre domaine. Les informations du domaine sont `NORTHWEST.ADVENTURE-WORKS.COM`et le port du point de terminaison de mise en miroir de bases de données est `7025`. Étant donné ces exemples de composants, l'adresse réseau du serveur est la suivante :  
  
 `TCP://REMOTESYSTEM3.NORTHWEST.ADVENTURE-WORKS.COM:7025`  
  
 L'exemple suivant montre l'adresse réseau de serveur d'une instance de serveur sur un système informatique nommé `DBSERVER1`. Ce système se trouve dans le domaine local et il est identifié sans ambiguïté par son nom système. Le port du point de terminaison de mise en miroir de bases de données est `7022`.  
  
 `TCP://DBSERVER1:7022`  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Créer un point de terminaison de mise en miroir de bases de données pour l’authentification Windows &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
## Voir aussi  
 [Mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Point de terminaison de mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  