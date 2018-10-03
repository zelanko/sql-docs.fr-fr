---
title: Changer le contexte de cluster HADR de l’instance de serveur (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- Availability replicas [SQL Server], change WSFC cluster context
ms.assetid: ecd99f91-b9a2-4737-994e-507065a12f80
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3309d3754d8d4842ed238a54f0120b54bba1d596
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219179"
---
# <a name="change-the-hadr-cluster-context-of-server-instance-sql-server"></a>Changer le contexte de cluster HADR de l'instance de serveur (SQL Server)
  Cette rubrique explique comment basculer le contexte de cluster HADR d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide de [!INCLUDE[tsql](../../../includes/tsql-md.md)] dans [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] et versions ultérieures. Le *contexte de cluster HADR* détermine le cluster de clustering de basculement Windows Server (WSFC) qui gère les métadonnées pour les réplicas de disponibilité hébergés par l’instance de serveur.  
  
 Basculez le contexte de cluster HADR uniquement pendant une migration entre clusters de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] vers une instance de [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] sur un nouveau cluster WSFC. La migration entre clusters de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prend en charge la mise à niveau vers [!INCLUDE[win8](../../../includes/win8-md.md)] ou [!INCLUDE[win8srv](../../../includes/win8srv-md.md)] avec un temps mort minimal des groupes de disponibilité. Pour plus d'informations, consultez [Migration entre clusters de groupes de disponibilité AlwaysOn pour la mise à niveau du système d'exploitation](http://msdn.microsoft.com/library/jj873730.aspx).  
  

  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
> [!CAUTION]  
>  Basculez le contexte de cluster HADR uniquement lors de la migration entre clusters de déploiements [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] .  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Vous pouvez basculer le contexte de cluster HADR uniquement du cluster WSFC local vers un cluster distant, puis de nouveau du cluster distant vers le cluster local. Vous ne pouvez pas changer de contexte de cluster HADR d'un cluster distant à un autre.  
  
-   Il est possible de basculer le contexte de cluster HADR vers un cluster distant uniquement lorsque l'instance de SQL Server n'héberge pas un réplica de disponibilité.  
  
-   Un environnement de cluster HADR distant peut être basculé vers le cluster local à tout moment. Toutefois, le contexte ne peut pas être rebasculé tant que l'instance de serveur héberge des réplicas de disponibilité.  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   L'instance de serveur sur laquelle vous modifiez le contexte de cluster HADR doit exécuter [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] ou version ultérieure (édition Entreprise ou ultérieure).  
  
-   L'instance de serveur doit être activée pour AlwaysOn. Pour plus d’informations, consultez [Activer et désactiver les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md).  
  
-   Pour pouvoir être basculée du contexte de cluster local vers un cluster à distance, une instance de serveur ne peut pas héberger de réplicas de disponibilité. La vue de catalogue [sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) ne doit retourner aucune ligne.  
  
     S'il existe des réplicas de disponibilité sur l'instance de serveur, avant de modifier le contexte de cluster HADR, vous devez effectuer l'une des opérations suivantes :  
  
    |Rôle de réplica|Action|Lien|  
    |------------------|------------|----------|  
    |Principal|Place le groupe de disponibilité hors connexion.|[Placer un groupe de disponibilité hors connexion &#40;SQL Server&#41;](../../take-an-availability-group-offline-sql-server.md)|  
    |Secondary|Supprimer le réplica de son groupe de disponibilité|[Supprimer un réplica secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)|  
  
-   Avant de pouvoir basculer d'un cluster à distance vers un cluster local, tous les réplicas de validation synchrone doivent être dans l'état SYNCHRONIZED.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Nous vous recommandons de spécifier le nom de domaine complet. Cela est dû au fait que pour rechercher l'adresse IP cible d'un nom court, ALTER SERVER CONFIGURATION utilise la résolution DNS. Dans certaines situations, selon l'ordre de recherche de DNS, l'utilisation d'un nom court peut entraîner quelques confusions. Par exemple, considérez la commande suivante, exécutée sur un nœud dans le domaine `abc` , (`node1.abc.com`). Le cluster de destination attendu est le cluster `CLUS01` dans le domaine `xyz` (`clus01.xyz.com`). Toutefois, le domaine local héberge aussi un cluster nommé `CLUS01` (`clus01.abc.com`).  
  
     Si le nom court du cluster cible, `CLUS01`, a été spécifié, la résolution de noms DNS peut retourner l'adresse IP d'un cluster incorrect, `clus01.abc.com`. Pour éviter une telle confusion, spécifiez le nom complet du cluster cible, comme dans l'exemple suivant :  
  
    ```  
    ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com'  
    ```  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
  
-   **compte de connexion SQL Server**  
  
     Requiert l'autorisation CONTROL SERVER.  
  
-   **Compte de service SQL Server**  
  
     Le compte de service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de l'instance de serveur doit disposer :  
  
    -   des autorisations nécessaires pour ouvrir le cluster WSFC de destination ;  
  
    -   d'un accès en lecture/écriture au cluster WSFC distant.  
  
 
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour modifier le contexte de cluster WSFC d'un réplica de disponibilité**  
  
1.  Connectez-vous à l'instance de qui héberge soit le réplica principal, soit un réplica secondaire du groupe de disponibilité.  
  
2.  Utilisez la clause SET HADR CLUSTER CONTEXT de l’instruction [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) , comme suit :  
  
     ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT **=** { **'*`windows_cluster`*'** | LOCAL}  
  
     où :  
  
     *windows_cluster*  
     Le nom d'objet cluster (CON) d'un cluster WSFC. Vous pouvez spécifier le nom court ou le nom de domaine complet. Nous vous recommandons de spécifier le nom de domaine complet. Pour plus d'informations, consultez [Recommandations](#Recommendations), plus haut dans cette rubrique.  
  
     LOCAL  
     Cluster WSFC local  
  
### <a name="examples"></a>Exemples  
 L'exemple qui suit remplace le contexte de cluster HADR par un autre cluster. Pour identifier le cluster WSFC de destination, `clus01`, l'exemple spécifie le nom d'objet cluster complet, `clus01.xyz.com`.  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com';  
```  
  
 L'exemple qui suit remplace le contexte de cluster HADR par le cluster WSFC local.  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = LOCAL;  
```  
  

  
##  <a name="FollowUp"></a> Suivi : après le basculement du contexte de cluster d'un réplica de disponibilité  
 Le nouveau contexte de cluster HADR prend effet immédiatement, sans redémarrer l'instance de serveur. Le paramètre de contexte de cluster HADR est un paramètre persistant au niveau de l'instance qui demeure inchangé si l'instance de serveur redémarre.  
  
 Confirmez le nouveau contexte de cluster HADR en interrogeant la vue de gestion dynamique [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql) , comme suit :  
  
```  
SELECT cluster_name FROM sys.dm_hadr_cluster  
```  
  
 Cette requête doit retourner le nom du cluster auquel sur lequel vous définissez le contexte de cluster HADR.  
  
 Lorsque le contexte de cluster HADR est basculé vers un nouveau cluster :  
  
-   Les métadonnées sont nettoyées pour tous les réplicas de disponibilité qui sont actuellement hébergés par l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Toutes les bases de données qui ont déjà appartenu à un réplica de disponibilité sont désormais dans un état RESTORING.  
  
 
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Supprimer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](remove-an-availability-group-listener-sql-server.md)  
  
-   [Placer un groupe de disponibilité hors connexion &#40;SQL Server&#41;](../../take-an-availability-group-offline-sql-server.md)  
  
-   [Ajouter un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Supprimer un réplica secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Joindre une base de données secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
 
  
##  <a name="RelatedContent"></a> Contenu associé  
  
-   [Articles techniques SQL Server 2012](http://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)  
  
-   [Blog de l’équipe AlwaysOn SQL Server : Le Blog officiel de SQL Server AlwaysOn Team](http://blogs.msdn.com/b/sqlalwayson/)  
  
  
  
## <a name="see-also"></a>Voir aussi  
 [Groupes de disponibilité AlwaysOn (SQL Server)](always-on-availability-groups-sql-server.md) [Clustering de basculement Windows Server &#40;WSFC&#41; avec SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)  
  
  
