---
title: Configurer le routage en lecture seule pour un groupe de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- read-only routing
- Availability Groups [SQL Server], readable secondary replicas
- Availability Groups [SQL Server], read-only routing
- readable secondary replicas
- Availability Groups [SQL Server], client connectivity
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 7bd89ddd-0403-4930-a5eb-3c78718533d4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a129386b5c88939d68f5d7f23a5fe2b4d8ce7cca
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62789531"
---
# <a name="configure-read-only-routing-for-an-availability-group-sql-server"></a>Configurer le routage en lecture seule pour un groupe de disponibilité (SQL Server)
  Pour configurer un groupe de disponibilité AlwaysOn et prendre en charge le routage en lecture seule dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], vous pouvez utiliser [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou PowerShell. Le *routage en lecture seule* fait référence à la capacité de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] d’acheminer les demandes de connexion en lecture seule applicables à un [réplica secondaire lisible](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) AlwaysOn disponible (autrement dit, un réplica configuré pour autoriser des charges de travail en lecture seule quand il s’exécute sous le rôle secondaire). Pour prendre en charge le routage en lecture seule, le groupe de disponibilité doit posséder un [écouteur de groupe de disponibilité](../../listeners-client-connectivity-application-failover.md). Les clients en lecture seule doivent diriger leurs demandes de connexion à cet écouteur, et les chaînes de connexion du client doivent spécifier l'intention d'application « en lecture seule ». Autrement dit, il doit s’agir de *demandes de connexion d’intention de lecture*.  
  
> [!NOTE]
>  Pour plus d’informations sur la configuration d’un réplica secondaire lisible, consultez [Configurer l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md).  
> 
> 
> 
> [!NOTE]
>  La configuration du routage en lecture seule n'est pas prise en charge par [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  

  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   Le groupe de disponibilité doit posséder un écouteur. Pour plus d'informations, consultez [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).  
  
-   Un ou plusieurs réplicas de disponibilité doivent être configurés pour accepter en lecture seule dans le rôle secondaire (autrement dit, pour être [réplicas secondaires lisibles](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)(AlwaysOn % 20Availability % 20Groups\).md)). Pour plus d’informations, consultez [Configurer l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md).  
  
-   Vous devez être connecté à l'instance de serveur qui héberge le réplica principal actuel.  
  
###  <a name="RORReplicaProperties"></a> Quelles sont les propriétés du réplica que vous avez besoin de configurer pour prendre en charge le routage en lecture seule ?  
  
-   Pour chaque réplica secondaire lisible qui doit prendre en charge le routage en lecture seule, vous devez spécifier une *URL de routage en lecture seule*. Cette URL est effective uniquement lorsque le réplica local s'exécute sous le rôle secondaire. L'URL de routage en lecture seule doit être spécifiée par réplica, si nécessaire. Chaque URL de routage en lecture seule est utilisée pour acheminer les demandes de connexion d'intention de lecture vers un réplica secondaire lisible spécifique. En général, à chaque réplica secondaire lisible est affecté une URL de routage en lecture seule.  
  
     Pour plus d’informations sur le calcul de l’URL de routage en lecture seule pour un réplica de disponibilité, consultez [Calcul de l’URL de routage en lecture seule pour AlwaysOn](https://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-alwayson.aspx).  
  
-   Pour chaque réplica de disponibilité qui doit prendre en charge le routage en lecture seule lorsqu'il est le réplica principal, vous devez spécifier une *liste de routage en lecture seule*. Une liste de routage en lecture seule donnée est effective uniquement lorsque le réplica local s'exécute sous le rôle principal. Cette liste doit être spécifiée par réplica, si nécessaire. En général, chaque liste de routage en lecture seule contient toutes les URL de routage en lecture seule, avec l'URL du réplica local à la fin de la liste.  
  
    > [!NOTE]  
    >  Les demandes de connexion d'intention de lecture sont acheminées vers le premier secondaire lisible disponible dans la liste de routage en lecture seule du réplica principal actuel. Il n'existe aucun équilibrage de charge.  
  
> [!NOTE]  
>  Pour plus d’informations sur les écouteurs de groupe de disponibilité et sur le routage en lecture seule, consultez [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
  
|Tâche|Autorisations|  
|----------|-----------------|  
|Pour configurer des réplicas lors de la création d'un groupe de disponibilité|Requiert le rôle serveur fixe **sysadmin** et l’autorisation de serveur CREATE AVAILABILITY GROUP, l’autorisation ALTER ANY AVAILABILITY GROUP ou l’autorisation CONTROL SERVER.|  
|Pour modifier un réplica de disponibilité :|Requiert l'autorisation ALTER AVAILABILITY GROUP sur le groupe de disponibilité, l'autorisation CONTROL AVAILABILITY GROUP, l'autorisation ALTER ANY AVAILABILITY GROUP ou l'autorisation CONTROL SERVER.|  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour configurer le routage en lecture seule**  
  
> [!NOTE]  
>  Pour obtenir un exemple de code, consultez [Exemple (Transact-SQL)](#TsqlExample), plus loin dans cette section.  
  
1.  Connectez-vous à l'instance de serveur qui héberge le réplica principal.  
  
2.  Si vous spécifiez un réplica pour un nouveau groupe de disponibilité, utilisez l'instruction [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] . Si vous ajoutez ou modifiez un réplica pour un groupe de disponibilité existant, utilisez l'instruction [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] .  
  
    -   Pour configurer le routage en lecture seule pour le rôle secondaire, dans la clause ADD REPLICA ou MODIFY REPLICA WITH, spécifiez l'option SECONDARY_ROLE, comme suit :  
  
         SECONDARY_ROLE **(** READ_ONLY_ROUTING_URL **='** TCP **:// *`system-address`* : *`port`* »)**  
  
         Les paramètres de l'URL de routage en lecture sont les suivants :  
  
         *system-address*  
         Chaîne, telle qu'un nom de système, un nom de domaine complet ou une adresse IP, qui identifie de manière unique l'ordinateur de destination.  
  
         *port*  
         Numéro de port utilisé par le moteur de base de données de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
         Par exemple :   `SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433')`  
  
         Dans une clause MODIFY REPLICA, ALLOW_CONNECTIONS est facultatif si le réplica est déjà configuré pour autoriser les connexions en lecture seule.  
  
         Pour plus d'informations, consultez [Calcul de l'URL de routage en lecture seule pour AlwaysOn](https://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-alwayson.aspx).  
  
    -   Pour configurer le routage en lecture seule pour le rôle principal, dans la clause ADD REPLICA ou MODIFY REPLICA WITH, spécifiez l'option PRIMARY_ROLE, comme suit :  
  
         PRIMARY_ROLE **(** READ_ONLY_ROUTING_LIST **= (' *`server`* '** [ **,** ... *n* ] **))**  
  
         où *server* indique une instance de serveur qui héberge un réplica secondaire en lecture seule dans le groupe de disponibilité.  
  
         Par exemple :   `PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('Server1','Server2'))`  
  
        > [!NOTE]  
        >  Vous devez définir le routage en lecture seule avant de configurer la liste de routage en lecture seule.  
  
###  <a name="TsqlExample"></a> Exemple (Transact-SQL)  
 L'exemple suivant modifie deux réplicas de disponibilité d'un groupe de disponibilité existant, `AG1` pour prendre en charge le routage en lecture seule si un de ces réplicas détient actuellement le rôle principal. Pour identifier les instances de serveur qui hébergent le réplica de disponibilité, cet exemple spécifie les noms d’instance `COMPUTER01` et `COMPUTER02`.  
  
```  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER02.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER02','COMPUTER01')));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER01','COMPUTER02')));  
GO  
  
```  
  
##  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
 **Pour configurer le routage en lecture seule**  
  
> [!NOTE]  
>  Pour obtenir un exemple de code, consultez [Exemple (PowerShell)](#PSExample), plus loin dans cette section.  
  
1.  Définissez la valeur par défaut (`cd`) sur l'instance de serveur qui héberge le réplica principal.  
  
2.  Lorsque vous ajoutez un réplica de disponibilité à un groupe de disponibilité, utilisez l'applet de commande `New-SqlAvailabilityReplica`. Lorsque vous modifiez un réplica de disponibilité existant, utilisez l'applet de commande `Set-SqlAvailabilityReplica`. Les paramètres pertinents sont les suivants :  
  
    -   Pour configurer le routage en lecture seule pour le rôle secondaire, spécifiez la **ReadonlyRoutingConnectionUrl » *`url`* »** paramètre.  
  
         où *url* est le nom de domaine complet (FQDN) de la connectivité et le port à utiliser lors de l’acheminement vers le réplica pour les connexions en lecture seule. Par exemple :  `-ReadonlyRoutingConnectionUrl "TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024"`  
  
         Pour plus d'informations, consultez [Calcul de l'URL de routage en lecture seule pour AlwaysOn](https://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-alwayson.aspx).  
  
    -   Pour configurer l’accès à la connexion pour le rôle principal, spécifiez **ReadonlyRoutingList » *`server`* »** [ **,** ... *n* ], où *server* identifie une instance de serveur qui héberge un réplica secondaire en lecture seule dans le groupe de disponibilité. Par exemple :  `-ReadOnlyRoutingList "SecondaryServer","PrimaryServer"`  
  
        > [!NOTE]  
        >  Vous devez définir l'URL de routage en lecture seule d'un réplica avant de configurer sa liste de routage en lecture seule.  
  
    > [!NOTE]  
    >  Pour afficher la syntaxe d'une applet de commande, utilisez l'applet de commande `Get-Help` dans l'environnement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Pour configurer et utiliser le fournisseur SQL Server PowerShell**  
  
-   [Fournisseur SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
###  <a name="PSExample"></a> Exemple (PowerShell)  
 L'exemple suivant configure le réplica principal et un réplica secondaire dans un groupe de disponibilité pour le routage en lecture seule. D'abord, l'exemple affecte une URL de routage en lecture seule à chaque réplica. Il définit ensuite la liste de routage en lecture seule sur le réplica principal. Les connexions avec la propriété « ReadOnly » définie dans la chaîne de connexion sont redirigées vers le réplica secondaire. Si ce réplica secondaire n'est pas accessible en lecture (comme déterminé par le paramètre `ConnectionModeInSecondaryRole`), la connexion sera renvoyée vers le réplica principal.  
  
```  
Set-Location SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MyAg  
$primaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"  
$secondaryReplica = Get-Item "AvailabilityReplicas\SecondaryServer"  
  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://PrimaryServer.domain.com:1433" -InputObject $primaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://SecondaryServer.domain.com:1433" -InputObject $secondaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingList "SecondaryServer","PrimaryServer" -InputObject $primaryReplica  
```  
  
##  <a name="FollowUp"></a> Suivi : Après la configuration du routage en lecture seule  
 Une fois le réplica principal actuel et les réplicas secondaires lisibles configurés pour prendre en charge le routage en lecture seule dans les deux rôles, les réplicas secondaires lisibles peuvent recevoir des demandes de connexion d'intention de lecture des clients qui se connectent via l'écouteur du groupe de disponibilité.  
  
> [!TIP]  
>  Lorsque vous utilisez le [utilitaire bcp](../../../tools/bcp-utility.md) ou [utilitaire sqlcmd](../../../tools/sqlcmd-utility.md), vous pouvez spécifier un accès en lecture seule à n’importe quel réplica secondaire qui est activé pour l’accès en lecture seule en spécifiant le `-K ReadOnly` basculer.  
  
###  <a name="ConnStringReqsRecs"></a> Exigences et recommandations pour les chaînes de connexion clientes  
 Pour qu'une application cliente utilise le routage en lecture seule, sa chaîne de connexion doit respecter les conditions suivantes :  
  
-   Utiliser le protocole TCP.  
  
-   Définir l'attribut/propriété d'intention de l'application en lecture seule.  
  
-   Référencer l'écouteur d'un groupe de disponibilité qui est configuré pour prendre en charge le routage en lecture seule.  
  
-   Référencer une base de données dans ce groupe de disponibilité.  
  
 En outre, nous recommandons que les chaînes de connexion autorisent le basculement de sous-réseaux multiples, ce qui permet de prendre en charge un thread client parallèle pour chaque réplica sur chaque sous-réseau. Cela réduit le temps de reconnexion du client après un basculement.  
  
 La syntaxe d'une chaîne de connexion dépend du fournisseur SQL Server utilisé par l'application. L'exemple de chaîne de connexion suivant pour le fournisseur de données .NET Framework Data Provider 4.0.2 pour SQL Server illustre les parties d'une chaîne de connexion requises et recommandées pour utiliser le routage en lecture seule.  
  
```  
Server=tcp:MyAgListener,1433;Database=Db1;IntegratedSecurity=SSPI;ApplicationIntent=ReadOnly;MultiSubnetFailover=True  
```  
  
 Pour plus d’informations sur l’intention de l’application en lecture seule et le routage en lecture seule, consultez [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).  
  
### <a name="if-read-only-routing-is-not-working-correctly"></a>Si le routage en lecture seule ne fonctionne pas correctement  
 Pour plus d’informations sur la résolution des problèmes liés à la configuration du routage en lecture seule, consultez [Le routage en lecture seule ne fonctionne pas correctement](troubleshoot-always-on-availability-groups-configuration-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Pour consulter les configurations de routage en lecture seule**  
  
-   [sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
  
-   [sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) (colonne **read_only_routing_url**)  
  
 **Pour configurer l'accès à la connexion du client**  
  
-   [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Configurer l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
 **Pour utiliser les chaînes de connexion dans des applications**  
  
-   [Prise en charge des fonctionnalités de récupération d'urgence, haute disponibilité par SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [Utilisation de mots clés de chaîne de connexion avec SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
##  <a name="RelatedContent"></a> Contenu associé  
  
-   **Blogs :**  
  
     [Calcul de read_only_routing_url pour AlwaysOn](https://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-alwayson.aspx)  
  
     [Blogs de l’équipe AlwaysOn SQL Server : Blog officiel de SQL Server AlwaysOn Team](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Blogs des ingénieurs du Service clientèle et du Support technique de SQL Server](https://blogs.msdn.com/b/psssql/)  
  
-   **Livres blancs :**  
  
     [Livres blancs de Microsoft pour SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Livres blancs de l'équipe de consultants clients de SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Secondaires actifs : Réplicas secondaires lisibles (groupes de disponibilité AlwaysOn)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)   
 [À propos de l’accès de la connexion client aux réplicas de disponibilité &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md)   
 [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)  
  
  
