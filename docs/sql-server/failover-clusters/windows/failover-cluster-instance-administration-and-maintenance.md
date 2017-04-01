---
title: "Administration et maintenance de l&#39;instance de cluster de basculement | Microsoft Docs"
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
  - "comptes utilisateur [SQL Server], clustering de basculement"
  - "clusters [SQL Server], maintenance"
  - "nœuds [clustering de basculement]"
  - "clustering de basculement [SQL Server], maintenance"
  - "ajout de nœuds"
  - "serveurs virtuels [SQL Server], suppression de nœuds"
  - "instance cluster de SQL Server"
  - "nœuds [clustering de basculement], suppression"
  - "nœuds [clustering de basculement], ajout"
  - "comptes de services [SQL Server]"
  - "suppression de nœuds"
  - "serveurs virtuels [SQL Server], ajout de nœuds"
ms.assetid: 2d5c63e9-8061-45c3-94db-8dd3100b8a91
caps.latest.revision: 35
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 35
---
# Administration et maintenance de l&#39;instance de cluster de basculement
  Les tâches de maintenance telles que l’ajout ou la suppression de nœuds dans une instance de cluster de basculement Always On existante sont accomplies à l’aide du programme d’installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. D'autres tâches d'administration telles que la modification d'une ressource d'adresse IP et la récupération de certains scénarios FCI sont accomplies à l'aide du composant logiciel enfichable Gestionnaire du cluster de basculement, qui est le composant logiciel enfichable de gestion du service de clustering de basculement Windows Server (WSFC).  
  
## Conservation d'une instance de cluster de basculement  
 Après avoir installé une FCI, vous pouvez la changer ou la réparer au moyen du programme d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Par exemple, vous pouvez ajouter des nœuds supplémentaires à une FCI, exécuter une FCI comme une instance indépendante, ou supprimer un nœud d'une configuration de FCI.  
  
### Ajout d'un nœud à une instance cluster de basculement existante  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] permet de maintenir une FCI existante. Si vous choisissez cette option, vous pouvez ajouter d’autres nœuds à votre FCI en exécutant le programme d’installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur l’ordinateur que vous souhaitez ajouter à la FCI. Pour plus d’informations, consultez [Créer un cluster de basculement SQL Server &#40;Setup&#41;](../../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md) et [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
### Suppression d'un nœud dans une instance cluster de basculement existante  
 Vous pouvez supprimer un nœud d'une FCI en exécutant le programme d'installation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur l'ordinateur que vous souhaitez supprimer de la FCI. Chaque nœud dans une FCI est considéré comme un homologue sans dépendances sur d'autres nœuds de la FCI, et vous pouvez supprimer n'importe quel nœud. Il n'est pas nécessaire qu'un nœud endommagé soit disponible pour le supprimer : la suppression ne désinstalle aucun binaire [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] du nœud indisponible. Un nœud supprimé peut être ajouté à nouveau à une FCI à tout moment. Pour plus d’informations, consultez [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
### Modification des comptes de service  
 Vous ne devez pas modifier les mots de passe des comptes de service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lorsqu'un nœud de FCI est arrêté ou hors ligne. Si vous êtes amené à le faire, vous devrez redéfinir le mot de passe à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lorsque tous les nœuds seront de nouveau en ligne.  
  
 Si le compte de service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] n'est pas un administrateur de votre cluster, il n'est pas possible de supprimer les partages administratifs sur les nœuds du cluster. Les partages administratifs doivent être disponibles dans un cluster pour que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fonctionne.  
  
> [!IMPORTANT]  
>  N'utilisez pas le même compte pour le compte du service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et pour le compte de service WSFC. Si le mot de passe du compte de service WSFC change, votre installation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] échouera.  
  
 Sur [!INCLUDE[nextref_longhorn](../../../includes/nextref-longhorn-md.md)], des SID de service sont utilisés pour les comptes de service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Configurer les comptes de service Windows et les autorisations](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## Administration d'une instance de cluster de basculement  
  
|Description de la tâche|Lien de rubrique|  
|----------------------|----------------|  
|Explique comment ajouter des dépendances à une ressource [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|[Ajouter des dépendances à une ressource SQL Server](../../../sql-server/failover-clusters/windows/add-dependencies-to-a-sql-server-resource.md)|  
|Kerberos est un protocole d'authentification de réseau conçu pour fournir une authentification renforcée pour applications client/serveur. Kerberos fournit une base d'interopérabilité et permet d'améliorer la sécurité de l'authentification réseau à l'échelle de l'entreprise. Vous pouvez utiliser l’authentification Kerberos avec des instances autonomes de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou avec des instances de cluster de basculement Always On.|[Inscrire un nom de principal du service pour les connexions Kerberos](../../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).|  
|Fournit des liens vers un contenu qui explique comment activer l'authentification Kerberos||  
|Décrit la procédure utilisée pour effectuer une récupération suite à échec d'un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|[Récupérer à partir d'une défaillance d'instance de cluster de basculement](../../../sql-server/failover-clusters/windows/recover-from-failover-cluster-instance-failure.md)|  
|Décrit la procédure utilisée pour modifier la ressource d'adresse IP d'une instance de cluster de basculement de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|[Modifier l'adresse IP d'une instance de cluster de basculement](../../../sql-server/failover-clusters/windows/change-the-ip-address-of-a-failover-cluster-instance.md)|  
  
## Voir aussi  
 [Configurer les paramètres de propriété HealthCheckTimeout](../../../sql-server/failover-clusters/windows/configure-healthchecktimeout-property-settings.md)   
 [Configurer les paramètres de propriété FailureConditionLevel](../../../sql-server/failover-clusters/windows/configure-failureconditionlevel-property-settings.md)   
 [Afficher et lire le journal de diagnostic de l'instance de cluster de basculement](../../../sql-server/failover-clusters/windows/view-and-read-failover-cluster-instance-diagnostics-log.md)  
  
  