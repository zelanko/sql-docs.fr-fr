---
title: Prise en charge de la haute disponibilité et de la récupération d'urgence par le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 62de4be6-b027-427d-a7e5-352960e42877
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c7035ebdab328abd33c4648754ebaba6b80efb54
ms.sourcegitcommit: 54cfeb36c9caa51ec68fa8f4a1918e305db5e00a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219192"
---
# <a name="jdbc-driver-support-for-high-availability-disaster-recovery"></a>Prise en charge de la haute disponibilité et de la récupération d'urgence par le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Cette rubrique traite de la prise en charge de [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] en ce qui concerne la haute disponibilité et la reprise d’activité -- [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]. Pour plus d'informations sur [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], consultez la documentation en ligne de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] .  
  
 À compter de la version 4.0 du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], il est possible de spécifier l’écouteur du groupe de disponibilité (haute disponibilité et reprise d’activité) depuis la propriété de connexion. Si une application [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] est connectée à une base de données AlwaysOn sur laquelle un basculement est effectué, la connexion d’origine sera interrompue. L’application devra alors établir une nouvelle connexion pour poursuivre la tâche après le basculement. Les [propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md) suivantes ont été ajoutées dans [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] :  
  
-   **multiSubnetFailover**  
  
-   **applicationIntent**
 
Spécifiez multiSubnetFailover=true lors de la connexion à l’écouteur de groupe de disponibilité d’un groupe de disponibilité ou d’une instance de cluster de basculement. Il est à noter que **multiSubnetFailover** a la valeur false par défaut. Utilisez **applicationIntent** pour déclarer le type de charge de travail de l’application. Pour plus d’informations, consultez les sections ci-dessous.
 
À compter de la version 6.0 de Microsoft JDBC Driver pour SQL Server, une nouvelle propriété de connexion **transparentNetworkIPResolution** (TNIR) est ajoutée pour la connexion transparente à des groupes de disponibilité AlwaysOn ou à un serveur auquel plusieurs adresses IP sont associées. Lorsque **transparentNetworkIPResolution** a la valeur true, le pilote tente de se connecter à la première adresse IP disponible. Si la première tentative échoue, le pilote tente de se connecter à toutes les adresses IP en parallèle jusqu’à ce que le délai expire, ignorant toutes les tentatives de connexion en attente lorsque l’une d’elles réussit.   

Remarques :
* transparentNetworkIPResolution a la valeur true par défaut.
* transparentNetworkIPResolution est ignoré si multiSubnetFailover a la valeur true.
* transparentNetworkIPResolution est ignoré si la mise en miroir de bases de données est utilisée.
* transparentNetworkIPResolution est ignoré s’il y a plus de 64 adresses IP.
* Lorsque transparentNetworkIPResolution= a la valeur true, la première tentative de connexion utilise une valeur de délai d’expiration de 500 ms. Les autres tentatives de connexion suivent la même logique qu’avec la fonctionnalité multiSubnetFailover. 

> [!NOTE]
> Si vous utilisez la version 4.2 ou une version antérieure de Microsoft JDBC Driver pour SQL Server et que **multiSubnetFailover** a la valeur false, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] tente de se connecter à la première adresse IP. Si le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ne parvient pas à établir de connexion avec la première adresse IP, la connexion échoue. Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ne tentera pas de se connecter à l’adresse IP suivante qui est associée au serveur. 
> 
> 
> [!NOTE]
>  L'augmentation du délai de connexion et l'implémentation de la logique de tentative de connexion augmente la probabilité qu'une application se connecte à un groupe de disponibilité. En raison du risque d'échec de connexion en cas de basculement d'un groupe de disponibilité, il est également nécessaire d'implémenter la logique de déclenchement de nouvelles tentatives de connexion, afin de multiplier les tentatives jusqu'à ce qu'une connexion soit établie.  
  
 
  
## <a name="connecting-with-multisubnetfailover"></a>Connexion à multiSubnetFailover  
 Spécifiez toujours **multiSubnetFailover=true** lors de la connexion à l’écouteur de groupe de disponibilité d’un groupe de disponibilité [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ou d’une instance de cluster de basculement [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. **multiSubnetFailover** permet un basculement plus rapide pour tous les groupes de disponibilité et les instances de cluster de basculement dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], et réduit considérablement le temps de basculement pour les topologies AlwaysOn uniques et de plusieurs sous-réseaux. Lors d'un basculement de sous-réseaux multiples, le client tente les connexions en parallèle. Lors d’un basculement de sous-réseau, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] tentera intensément d’établir la connexion TCP.  
  
 La propriété de connexion **multiSubnetFailover** indique que l’application est déployée sur un groupe de disponibilité ou une instance de cluster de basculement, et que [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] tente de se connecter à la base de données sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] principale en essayant toutes les adresses IP. Quand **MultiSubnetFailover=true** est spécifié dans le cadre d’une connexion, le client retente d’établir une connexion TCP plus rapidement que les intervalles de retransmission TCP par défaut du système d’exploitation. Cela permet une reconnexion plus rapide après le basculement d'un groupe de disponibilité AlwaysOn ou d'une instance de cluster de basculement AlwaysOn et s'applique aux groupes de disponibilité et aux instances de cluster de basculement uniques et à plusieurs sous-réseaux.  
  
 Pour plus d’informations sur les mots clés de chaîne de connexion dans [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], consultez [Définir les propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).  
  
 La spécification de **multiSubnetFailover=true** quand la connexion ne concerne pas un écouteur de groupe de disponibilité ni une instance de cluster de basculement peut avoir un impact négatif sur les performances et n’est pas prise en charge.  
  
 Si le gestionnaire de sécurité n'est pas installé, la machine virtuelle Java met en cache les adresses IP virtuelles pour une durée définie par défaut par votre implémentation JDK et les propriétés Java networkaddress.cache.ttl et networkaddress.cache.negative.ttl. Si le gestionnaire de sécurité JDK est installé, la machine virtuelle Java mettra en cache les adresses IP virtuelles et n'actualisera pas le cache par défaut. Vous devez définir la durée de vie (TTL, time-to-live – networkaddress.cache.ttl) sur un jour pour le cache de la machine virtuelle Java. Si vous ne modifiez pas la valeur par défaut en attribuant une valeur égale à un jour (environ), l'ancienne valeur ne sera pas supprimée définitivement du cache de la machine virtuelle Java lorsqu'une adresse IP virtuelle sera ajoutée ou mise à jour. Pour plus d’informations sur networkaddress.cache.ttl et networkaddress.cache.negative.ttl, consultez [https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html](https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html).  
  
 Utilisez les instructions suivantes pour la connexion à un serveur dans un groupe de disponibilité ou dans une instance de cluster de basculement :  
  
-   Le pilote génèrera une erreur si la propriété de connexion **instanceName** est utilisée dans la même chaîne de connexion que la propriété de connexion **multiSubnetFailover**. Cela révèle que SQL Browser n'est pas utilisé dans un groupe de disponibilité. Toutefois, si la propriété de connexion **portNumber** est également spécifiée, le pilote ignorera **instanceName** et utilisera **portNumber**.  
  
-   Utilisez la propriété de connexion**multiSubnetFailover** quand vous vous connectez à un seul sous-réseau ou à des sous-réseaux multiples pour améliorer leurs performances.  
  
-   Pour vous connecter à un groupe de disponibilité, spécifiez l'écouteur du groupe de disponibilité en tant que serveur dans votre chaîne de connexion. Par exemple, jdbc:sqlserver://VNN1.  
  
-   La connexion à une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurée avec plus de 64 adresses IP provoque un échec de connexion.  
  
-   Le comportement d'une application qui utilise la propriété de connexion **multiSubnetFailover** n'est pas affecté par le type d'authentification : l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l’authentification Kerberos ou l’authentification Windows.  
  
-   Augmentez la valeur de **loginTimeout** pour tenir compte du temps de basculement et réduire les nouvelles tentatives de connexion de l’application.  
  
-   Les transactions distribuées ne sont pas prises en charge.  
  
 Si le routage en lecture seule n'est pas appliqué, la connexion à un emplacement de réplica secondaire dans un groupe de disponibilité échoue dans les situations suivantes :  
  
1.  Si l'emplacement du réplica secondaire n'est pas configuré pour accepter des connexions.  
  
2.  Si une application utilise **applicationIntent=ReadWrite**(voir ci-dessous) et si l’emplacement de réplica secondaire est configuré pour un accès en lecture seule.  
  
 Une connexion échoue si un réplica principal est configuré pour rejeter des charges de travail en lecture seule et si la chaîne de connexion contient **ApplicationIntent=ReadOnly**.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Mise à niveau pour utiliser des clusters de sous-réseaux multiples à partir de la mise en miroir de bases de données  
 Si vous mettez à niveau une application [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] qui utilise actuellement la mise en miroir de bases de données pour un scénario de sous-réseaux multiples, vous devez supprimer la propriété de connexion **failoverPartner** et la remplacer par **multiSubnetFailover** définie sur **true** et remplacer le nom du serveur dans la chaîne de connexion par un écouteur du groupe de disponibilité. Si une chaîne de connexion utilise **failoverPartner** et **multiSubnetFailover=true**, le pilote génère une erreur. Cependant, si une chaîne de connexion utilise **failoverPartner** et **multiSubnetFailover=false** (ou **ApplicationIntent=ReadWrite**), l’application utilise la mise en miroir de bases de données.  
  
 Le pilote retournera une erreur si la mise en miroir de bases de données est utilisée sur la base de données principale au sein du groupe de disponibilité, et si **multiSubnetFailover=true** est utilisé dans la chaîne de connexion qui établit une connexion à une base de données principale au lieu d’un écouteur de groupe de disponibilité.  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="new-methods-supporting-multisubnetfailover-and-applicationintent"></a>Nouvelles méthodes prenant en charge multiSubnetFailover et applicationIntent  
 Les méthodes suivantes permettent d’accéder programmatiquement aux mots clés de chaîne de connexion **multiSubnetFailover**, **applicationIntent** et **transparentNetworkIPResolution** :  
  
-   [SQLServerDataSource.getApplicationIntent](../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setApplicationIntent](../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.getMultiSubnetFailover](../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setMultiSubnetFailover](../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [SQLServerDriver.getPropertyInfo](../../connect/jdbc/reference/getpropertyinfo-method-sqlserverdriver.md)  

-   SQLServerDataSource.setTransparentNetworkIPResolution

-   SQLServerDataSource.getTransparentNetworkIPResolution
  
 Les méthodes **getMultiSubnetFailover**, **setMultiSubnetFailover**, **getApplicationIntent**, **setApplicationIntent**, **getTransparentNetworkIPResolution** et **setTransparentNetworkIPResolution** sont également ajoutées à [SQLServerDataSource Class](../../connect/jdbc/reference/sqlserverdatasource-class.md), à [SQLServerConnectionPoolDataSource Class](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md) et à [SQLServerXADataSource Class](../../connect/jdbc/reference/sqlserverxadatasource-class.md).  
  
## <a name="tlsssl-certificate-validation"></a>Validation du certificat TLS/SSL  
 Un groupe de disponibilité se compose de plusieurs serveurs physiques. [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] prend désormais en charge **Autre nom du sujet** dans les certificats TLS/SSL de manière à permettre l’association de plusieurs hôtes à un même certificat. Pour plus d’informations sur le protocole TLS, consultez [Comprendre la prise en charge du chiffrement](../../connect/jdbc/understanding-ssl-support.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion à SQL Server avec le pilote JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)   
 [Définition des propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md)  
  
  
