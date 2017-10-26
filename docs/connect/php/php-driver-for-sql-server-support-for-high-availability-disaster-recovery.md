---
title: Pilote PHP pour SQL Server High Availability, Disaster Recovery | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73a80821-d345-4fea-b076-f4aabeb4af3e
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 24b65a4c4572638cff243bcf46e49a30453f0550
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="php-driver-for-sql-server-support-for-high-availability-disaster-recovery"></a>Prise en charge de la récupération d’urgence et la haute disponibilité par le pilote SQL Server pour PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique traite [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] prise en charge (ajouté dans la version 3.0) pour la récupération d’urgence haute disponibilité-- [!INCLUDE[ssHADR](../../includes/sshadr_md.md)].  La prise en charge [!INCLUDE[ssHADR](../../includes/sshadr_md.md)] a été ajoutée dans [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]. Pour plus d'informations sur [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], consultez la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
Dans la version 3.0 de la [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], vous pouvez spécifier l’écouteur du groupe de disponibilité d’une (haute disponibilité, récupération d’urgence) le groupe de disponibilité (AG) dans la propriété de connexion. Si un [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] application est connectée à une base de données AlwaysOn qui bascule, la connexion d’origine est rompue et l’application doit ouvrir une nouvelle connexion pour continuer à fonctionner après le basculement.  
  
Si vous ne vous connectez pas à un écouteur de groupe de disponibilité, et si plusieurs adresses IP sont associées à un nom d’hôte, le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] toutes les adresses IP associées entrée DNS s’itérer séquentiellement. Cette opération peut prendre du temps si la première adresse IP retournée par le serveur DNS n'est liée à aucune carte d'interface réseau (NIC). Lorsque vous vous connectez à un écouteur de groupe de disponibilité, le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] tente d’établir des connexions à toutes les adresses IP en parallèle et si une tentative de connexion réussit, le pilote ignore toutes les tentatives de connexion en attente.  
  
> [!NOTE]  
> L'augmentation du délai de connexion et l'implémentation de la logique de tentative de connexion augmente la probabilité qu'une application se connecte à un groupe de disponibilité. En raison du risque d'échec de connexion en cas de basculement d'un groupe de disponibilité, il est également nécessaire d'implémenter la logique de déclenchement de nouvelles tentatives de connexion, afin de multiplier les tentatives jusqu'à ce qu'une connexion soit établie.  
  
## <a name="connecting-with-multisubnetfailover"></a>Connexion à MultiSubnetFailover  
Le **MultiSubnetFailover** propriété de connexion indique que l’application est déployée dans un groupe de disponibilité ou Instance de Cluster de basculement et que le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] essaient de se connecter à la base de données sur le serveur principal [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] traite de l’instance en essayant de se connecter à tous les l’adresse IP. Lorsque **MultiSubnetFailover = true** est spécifié pour une connexion, le client tente de tentatives de connexion TCP plus rapidement que les intervalles de retransmission TCP par défaut du système d’exploitation. Cela permet une reconnexion plus rapide après le basculement d'un groupe de disponibilité AlwaysOn ou d'une instance de cluster de basculement AlwaysOn et s'applique aux groupes de disponibilité et aux instances de cluster de basculement uniques et à plusieurs sous-réseaux.  
  
Spécifiez toujours **MultiSubnetFailover = True** lors de la connexion à un écouteur de groupe de disponibilité de SQL Server 2012 ou une Instance de Cluster de basculement SQL Server 2012. **MultiSubnetFailover** permet un basculement plus rapide pour tous les groupes de disponibilité et l’instance de cluster de basculement dans SQL Server 2012, et réduit considérablement le temps de basculement pour les topologies AlwaysOn uniques et de sous-réseaux multiples. Lors d'un basculement de sous-réseaux multiples, le client tente les connexions en parallèle. Lors d’un basculement de sous-réseau, le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] sera intensément d’établir la connexion TCP.  
  
Pour plus d’informations sur les mots clés de chaîne de connexion dans [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], consultez [Options de connexion](../../connect/php/connection-options.md).  
  
Spécification de **MultiSubnetFailover = true** lorsque la connexion à un élément autre qu’un écouteur du groupe de disponibilité ou d’une Instance de Cluster de basculement peut provoquer une diminution des performances et n’est pas pris en charge.  
  
Utilisez les indications suivantes pour vous connecter à un serveur d'un groupe de disponibilité :  
  
-   Utilisez la propriété de connexion**MultiSubnetFailover** quand vous vous connectez à un sous-réseau unique ou à des sous-réseaux multiples pour améliorer leurs performances.  
  
-   Pour vous connecter à un groupe de disponibilité, spécifiez l'écouteur du groupe de disponibilité en tant que serveur dans votre chaîne de connexion.  
  
-   La connexion à une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] configurée avec plus de 64 adresses IP provoque un échec de connexion.  
  
-   Le comportement d’une application qui utilise la propriété de connexion **MultiSubnetFailover** peut ne pas être affecté en fonction du type d’authentification : authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], authentification Kerberos ou authentification Windows.  
  
-   Augmentez la valeur de **loginTimeout** pour tenir compte des temps de basculement et de réduire le nombre de tentatives de connexion application.  
  
-   Les transactions distribuées ne sont pas prises en charge.  
  
Si le routage en lecture seule n'est pas appliqué, la connexion à un emplacement de réplica secondaire dans un groupe de disponibilité échoue dans les situations suivantes :  
  
1.  Si l'emplacement du réplica secondaire n'est pas configuré pour accepter des connexions.  
  
2.  Si une application utilise **ApplicationIntent=ReadWrite**(voir ci-dessous) et si l’emplacement de réplica secondaire est configuré pour un accès en lecture seule.  
  
Une connexion échoue si un réplica principal est configuré pour rejeter des charges de travail en lecture seule et si la chaîne de connexion contient **ApplicationIntent=ReadOnly**.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Mise à niveau pour utiliser des clusters de sous-réseaux multiples à partir de la mise en miroir de bases de données  
Une erreur de connexion se produit si les mots clés de connexion **MultiSubnetFailover** et **Failover_Partner** sont présents dans la chaîne de connexion. Une erreur se produit également si **MultiSubnetFailover** est utilisé et si [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] retourne une réponse de partenaire de basculement qui indique qu’il fait partie d’une paire de mise en miroir de bases de données.  
  
Si vous mettez à niveau un [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] application qui utilise actuellement la mise en miroir de base de données à un scénario de sous-réseaux multiples, vous devez supprimer la **Failover_Partner** propriété de connexion et remplacez-la par **MultiSubnetFailover ** la valeur **Oui** et remplacez le nom du serveur dans la chaîne de connexion avec un écouteur de groupe de disponibilité. Si une chaîne de connexion utilise **Failover_Partner** et **MultiSubnetFailover = true**, le pilote génère une erreur. Toutefois, si une chaîne de connexion utilise **Failover_Partner** et **MultiSubnetFailover = false** (ou **ApplicationIntent = ReadWrite**), l’application utilise la base de données mise en miroir.  
  
Le pilote retournera une erreur si la mise en miroir de base de données est utilisée sur la base de données primaire dans le groupe de disponibilité et si **MultiSubnetFailover = true** est utilisé dans la chaîne de connexion qui se connecte à une base de données principale au lieu d’un groupe de disponibilité écouteur.  
  
## <a name="specifying-application-intent"></a>Spécification de l'intention d'application  
Quand **ApplicationIntent=ReadOnly**, le client demande une charge de travail en lecture lors de la connexion à une base de données prenant en charge AlwaysOn. Le serveur applique l'intention au moment de la connexion et pendant une instruction de base de données USE mais uniquement sur une base de données prenant en charge AlwaysOn.  
  
Le mot clé **ApplicationIntent** ne fonctionne pas avec les bases de données en lecture seule existantes.  
  
Une base de données peut autoriser ou interdire les charges de travail en lecture sur la base de données AlwaysOn ciblée. (Utilisez la clause **ALLOW_CONNECTIONS** des instructions **PRIMARY_ROLE** et **SECONDARY_ROLE**[!INCLUDE[tsql](../../includes/tsql_md.md)].)  
  
Le mot clé **ApplicationIntent** est utilisé pour activer le routage en lecture seule.  
  
## <a name="read-only-routing"></a>Routage en lecture seule  
Le routage en lecture seule est une fonctionnalité qui peut garantir la disponibilité d'un réplica en lecture seule d'une base de données. Pour activer le routage en lecture seule :  
  
1.  Vous devez vous connecter à un écouteur du groupe de disponibilité Always On.  
  
2.  Dans la chaîne de connexion, le mot clé **ApplicationIntent** doit avoir la valeur **ReadOnly**.  
  
3.  Le groupe de disponibilité doit être configuré par l'administrateur de base de données pour activer le routage en lecture seule.  
  
Il est possible que plusieurs connexions utilisant le routage en lecture seule ne se connectent pas toutes au même réplica en lecture seule. Les modifications apportées à la synchronisation de base de données ou à la configuration du routage du serveur peuvent entraîner des connexions clientes à différents réplicas en lecture seule. Pour vérifier que toutes les demandes en lecture seule se connectent au même réplica en lecture seule, ne transmettez pas d’écouteur du groupe de disponibilité au mot clé de chaîne de connexion **Server**. Au lieu de cela, spécifiez le nom de l'instance en lecture seule.  
  
Le routage en lecture seule peut prendre plus de temps que la connexion au réplica primaire car le routage en lecture seule se connecte d'abord au réplica primaire, puis recherche le meilleur réplica secondaire lisible disponible. Pour cette raison, vous devez augmenter le délai de connexion.  
  
## <a name="see-also"></a>Voir aussi  
[Connexion au serveur](../../connect/php/connecting-to-the-server.md)  
  

