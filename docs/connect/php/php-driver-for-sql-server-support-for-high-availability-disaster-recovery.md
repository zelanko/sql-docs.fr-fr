---
title: Prise en charge pour la haute disponibilité, récupération d’urgence pour les pilotes Microsoft SQL Server pour PHP | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 73a80821-d345-4fea-b076-f4aabeb4af3e
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb0af342ac2ccbe916fba9edb497e8197b2fe7f5
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784896"
---
# <a name="support-for-high-availability-disaster-recovery"></a>Prise en charge des fonctionnalités de récupération d’urgence/haute disponibilité
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique aborde la prise en charge de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] (ajoutée à la version 3.0) pour la haute disponibilité et la reprise d’activité -- [!INCLUDE[ssHADR](../../includes/sshadr_md.md)].  La prise en charge [!INCLUDE[ssHADR](../../includes/sshadr_md.md)] a été ajoutée dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Pour plus d'informations sur [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], consultez la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Dans la version 3.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], il est possible de spécifier l’écouteur d’un groupe de disponibilité (haute disponibilité et reprise d’activité) depuis la propriété de connexion. Si une application [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] est connectée à une base de données AlwaysOn sur laquelle un basculement est effectué, la connexion d’origine sera interrompue. L’application devra alors établir une nouvelle connexion pour poursuivre la tâche après le basculement.  
  
Si vous ne vous connectez pas à un écouteur du groupe de disponibilité et si plusieurs adresses IP sont associées à un nom d’hôte, [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] effectue une itération de façon séquentielle parmi toutes les adresses IP associées à l’entrée DNS. Cette opération peut prendre du temps si la première adresse IP retournée par le serveur DNS n'est liée à aucune carte d'interface réseau (NIC). Lors de la connexion à un écouteur de groupe de disponibilité, [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] tente d’établir une connexion à toutes les adresses IP en parallèle. Quand une tentative de connexion réussit, le pilote supprime toutes les tentatives de connexion en attente.  
  
> [!NOTE]  
> L'augmentation du délai de connexion et l'implémentation de la logique de tentative de connexion augmente la probabilité qu'une application se connecte à un groupe de disponibilité. En raison du risque d'échec de connexion en cas de basculement d'un groupe de disponibilité, il est également nécessaire d'implémenter la logique de déclenchement de nouvelles tentatives de connexion, afin de multiplier les tentatives jusqu'à ce qu'une connexion soit établie.  
  
## <a name="connecting-with-multisubnetfailover"></a>Connexion à MultiSubnetFailover  
La propriété de connexion **MultiSubnetFailover** indique que l’application est déployée sur un groupe de disponibilité ou une instance de cluster de basculement et que [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] tente de se connecter à la base de données sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] principale en essayant toutes les adresses IP. Quand **MultiSubnetFailover=true** est spécifié dans le cadre d’une connexion, le client retente d’établir une connexion TCP plus rapidement que les intervalles de retransmission TCP par défaut du système d’exploitation. Cela permet une reconnexion plus rapide après le basculement d'un groupe de disponibilité AlwaysOn ou d'une instance de cluster de basculement AlwaysOn et s'applique aux groupes de disponibilité et aux instances de cluster de basculement uniques et à plusieurs sous-réseaux.  
  
Spécifiez toujours **MultiSubnetFailover=True** lors de la connexion à un écouteur du groupe de disponibilité SQL Server 2012 ou à une instance de cluster de basculement SQL Server 2012. **MultiSubnetFailover** permet un basculement plus rapide pour tous les groupes de disponibilité et l’instance de cluster de basculement dans SQL Server 2012, et réduit considérablement le temps de basculement pour les topologies AlwaysOn uniques et de sous-réseaux multiples. Lors d'un basculement de sous-réseaux multiples, le client tente les connexions en parallèle. Lors d’un basculement de sous-réseau, [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] tentera intensément d’établir la connexion TCP.  
  
Pour plus d’informations sur les mots clés de chaîne de connexion dans [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], consultez [Options de connexion](../../connect/php/connection-options.md).  
  
La spécification de **MultiSubnetFailover=true** quand la connexion ne concerne pas un écouteur de groupe de disponibilité ni une instance de cluster de basculement peut avoir un impact négatif sur les performances et n’est pas prise en charge.  
  
Utilisez les indications suivantes pour vous connecter à un serveur d'un groupe de disponibilité :  
  
-   Utilisez la propriété de connexion**MultiSubnetFailover** quand vous vous connectez à un sous-réseau unique ou à des sous-réseaux multiples pour améliorer leurs performances.  
  
-   Pour vous connecter à un groupe de disponibilité, spécifiez l'écouteur du groupe de disponibilité en tant que serveur dans votre chaîne de connexion.  
  
-   La connexion à une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurée avec plus de 64 adresses IP provoque un échec de connexion.  
  
-   Le comportement d’une application qui utilise la propriété de connexion **MultiSubnetFailover** peut ne pas être affecté en fonction du type d’authentification : authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], authentification Kerberos ou authentification Windows.  
  
-   Augmentez la valeur de **loginTimeout** pour tenir compte du temps de basculement et réduire les nouvelles tentatives de connexion de l’application.  
  
-   Les transactions distribuées ne sont pas prises en charge.  
  
Si le routage en lecture seule n'est pas appliqué, la connexion à un emplacement de réplica secondaire dans un groupe de disponibilité échoue dans les situations suivantes :  
  
- Si l'emplacement du réplica secondaire n'est pas configuré pour accepter des connexions.  
  
- Si une application utilise **ApplicationIntent=ReadWrite**(voir ci-dessous) et si l’emplacement de réplica secondaire est configuré pour un accès en lecture seule.  
  
Une connexion échoue si un réplica principal est configuré pour rejeter des charges de travail en lecture seule et si la chaîne de connexion contient **ApplicationIntent=ReadOnly**.  

## <a name="transparent-network-ip-resolution-tnir"></a>Résolution d’adresses IP réseau transparente

Résolution de IP transparent réseau (TNIR) est une révision de la fonctionnalité MultiSubnetFailover existante. Elle affecte la séquence de connexion du pilote lors de la première résolu l’adresse IP du nom d’hôte ne répond pas et il y a plusieurs adresses IP associée avec le nom d’hôte. Avec MultiSubnetFailover, ils fournissent les séquences de quatre connexions suivantes : 

- TNIR activé & MultiSubnetFailover désactivé : une adresse IP est tentée, suivie de toutes les adresses IP en parallèle
- TNIR activé & MultiSubnetFailover activé : toutes les adresses IP sont tentées en parallèle
- Désactivé TNIR & MultiSubnetFailover désactivé : toutes les adresses IP sont tentées une après l’autre
- Désactivé TNIR & MultiSubnetFailover activé : toutes les adresses IP sont tentées en parallèle

TNIR est activé par défaut, et MultiSubnetFailover est désactivée par défaut.

Il s’agit d’un exemple d’activation TNIR et MultiSubnetFailover, utilisez le pilote PDO_SQLSRV :

```
<?php
$serverName = "yourservername";
$username = "yourusername";
$password = "yourpassword";
$connectionString = "sqlsrv:Server=$serverName; TransparentNetworkIPResolution=Enabled; MultiSubnetFailover=yes";
try {
    $conn = new PDO($connectionString, $username, $password, array(PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION));
    // your code 
    // more of your code
    // when done, close the connection
    unset($conn);
} catch(PDOException $e) {
    print_r($e->errorInfo);
}
?>
```

## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Mise à niveau pour utiliser des clusters de sous-réseaux multiples à partir de la mise en miroir de bases de données  
Une erreur de connexion se produit si les mots clés de connexion **MultiSubnetFailover** et **Failover_Partner** sont présents dans la chaîne de connexion. Une erreur se produit également si **MultiSubnetFailover** est utilisé et si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne une réponse de partenaire de basculement qui indique qu’il fait partie d’une paire de mise en miroir de bases de données.  
  
Si vous mettez à niveau une application [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] qui utilise actuellement la mise en miroir de bases de données vers un scénario de sous-réseaux multiples, vous devez supprimer la propriété de connexion **Failover_Partner** et la remplacer par **MultiSubnetFailover** avec la valeur **Oui** et remplacer le nom du serveur dans la chaîne de connexion par un écouteur du groupe de disponibilité. Si une chaîne de connexion utilise **Failover_Partner** et **MultiSubnetFailover=true**, le pilote génère une erreur. Toutefois, si une chaîne de connexion utilise **Failover_Partner** et **MultiSubnetFailover=false** (ou **ApplicationIntent=ReadWrite**), l’application utilise la mise en miroir de bases de données.  
  
Le pilote retournera une erreur si la mise en miroir de bases de données est utilisée sur la base de données principale au sein du groupe de disponibilité, et si **MultiSubnetFailover=true** est utilisé dans la chaîne de connexion qui établit une connexion à une base de données principale au lieu d’un écouteur de groupe de disponibilité.  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="see-also"></a> Voir aussi  
[Connexion au serveur](../../connect/php/connecting-to-the-server.md)  
  
