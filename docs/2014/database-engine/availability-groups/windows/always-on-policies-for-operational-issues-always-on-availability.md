---
title: Stratégies Always On pour les problèmes opérationnels avec des groupes de disponibilité (SQL Server) Always On | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], troubleshooting
- Availability Groups [SQL Server], policies
ms.assetid: afa5289c-641a-4c03-8749-44862384ec5f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 815f549cf9ab6dd7fe748c08ae7f32683c9d8551
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62815750"
---
# <a name="always-on-policies-for-operational-issues-with-always-on-availability-groups-sql-server"></a>Stratégies Always On pour les problèmes opérationnels avec des groupes de disponibilité Always On (SQL Server)
  Le modèle d'intégrité [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] évalue un ensemble de stratégies de gestion basées sur des stratégies prédéfinies. Vous pouvez les utiliser pour afficher l'intégrité d'un groupe de disponibilité AlwaysOn et de ses réplicas de disponibilité et bases de données dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 
  
##  <a name="TermsAndDefinitions"></a> Termes et définitions  
 Stratégies prédéfinies AlwaysOn  
 Ensemble de stratégies intégrées qui permettent à un administrateur de base de données de vérifier qu'un groupe de disponibilité et ses réplicas de disponibilité et bases de données sont conformes aux états définis par les stratégies AlwaysOn.  
  
 [Groupes de disponibilité AlwaysOn](always-on-availability-groups-sql-server.md) une solution de haute disponibilité et récupération d’urgence qui fournit une alternative au niveau entreprise pour la mise en miroir de base de données.  
  
 Groupe de disponibilité  
 Conteneur d’un jeu discret de bases de données utilisateur, appelées *bases de données de disponibilité*, qui basculent ensemble.  
  
 réplica de disponibilité  
 Instanciation d'un groupe de disponibilité hébergé par une instance spécifique de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et qui conserve une copie locale de chaque base de données de disponibilité appartenant au groupe de disponibilité. Il existe deux types de réplicas de disponibilité : un seul *réplica principal* et un à quatre *réplicas secondaires*. Les instances de serveur qui hébergent les réplicas de disponibilité pour un groupe de disponibilité donné doivent résider sur différents nœuds d'un même cluster WSFC (Clustering de basculement Windows Server).  
  
 Base de données de disponibilité  
 Base de données qui appartient à un groupe de disponibilité. Pour chaque base de données de disponibilité, le groupe de disponibilité contient une seule copie en lecture-écriture (la *base de données primaire*) et une à quatre copies en lecture seule (les*bases de données secondaires*).  
  
 Tableau de bord AlwaysOn  
 Tableau de bord [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] qui fournit d'un coup d'œil une vue de l'intégrité d'un groupe de disponibilité. Pour plus d'informations, consultez [Tableau de bord AlwaysOn](#Dashboard)plus loin dans cette rubrique.  
  
##  <a name="AlwaysOnPBM"></a> Stratégies prédéfinies et problèmes rencontrés  
 Le tableau suivant récapitule les stratégies définies.  
  
|Nom de stratégie|Problème|Catégorie**<sup>*</sup>**|Facette|  
|-----------------|-----------|------------------------------|-----------|  
|État du cluster WSFC|[Le service de cluster WSFC est hors connexion](wsfc-cluster-service-is-offline.md).|Critique|Instance de SQL Server|  
|État en ligne du groupe de disponibilité|[Le groupe de disponibilité est hors connexion](availability-group-is-offline.md).|Critique|Groupe de disponibilité|  
|Disponibilité du groupe de disponibilité pour le basculement automatique|[Le groupe de disponibilité n’est pas prêt pour le basculement automatique](availability-group-is-not-ready-for-automatic-failover.md).|Critique|Groupe de disponibilité|  
|État de synchronisation des données des réplicas de disponibilité|[Certains réplicas de disponibilité ne synchronisent pas de données](some-availability-replicas-are-not-synchronizing-data.md).|Warning|Groupe de disponibilité|  
|État de synchronisation des données de réplicas synchrones|[Certains réplicas synchrones ne sont pas synchronisés](some-synchronous-replicas-are-not-synchronized.md).|Warning|Groupe de disponibilité|  
|État du rôle des réplicas de disponibilité|[Certains réplicas de disponibilité n’ont pas un rôle sain](some-availability-replicas-do-not-have-a-healthy-role.md).|Warning|Groupe de disponibilité|  
|État de la connexion des réplicas de disponibilité|[Certains réplicas de disponibilité sont déconnectés](some-availability-replicas-are-disconnected.md).|Warning|Groupe de disponibilité|  
|État du rôle du réplica de disponibilité|[Le réplica de disponibilité n’a pas un rôle sain](availability-replica-does-not-have-a-healthy-role.md).|Critique|réplica de disponibilité|  
|État de la connexion du réplica de disponibilité|[Le réplica de disponibilité est déconnecté](availability-replica-is-disconnected.md).|Critique|Réplica de disponibilité|  
|État de jointure du réplica de disponibilité|[Le réplica de disponibilité n’est pas joint](availability-replica-is-not-joined.md).|Warning|Réplica de disponibilité|  
|État de synchronisation des données du réplica de disponibilité|[L’état de synchronisation des données d’une base de données de disponibilité n’est pas sain](data-synchronization-state-of-some-availability-database-is-not-healthy.md).|Warning|Réplica de disponibilité|  
|État de suspension de la base de données de disponibilité|[La base de données de disponibilité est suspendue](availability-database-is-suspended.md).|Warning|Base de données de disponibilité|  
|État de la jointure de la base de données de disponibilité|[La base de données secondaire n’est pas jointe](secondary-database-is-not-joined.md).|Warning|Base de données de disponibilité|  
|État de synchronisation des données de la base de données de disponibilité|[L’état de synchronisation des données de la base de données de disponibilité n’est pas sain](data-synchronization-state-of-availability-database-is-not-healthy.md).|Warning|Base de données de disponibilité|  
  
> [!IMPORTANT]  
>  **<sup>*</sup>**  Pour les stratégies AlwaysOn, les noms de catégorie sont utilisés comme identificateurs. Modifier le nom d'une catégorie AlwaysOn compromettrait sa fonctionnalité d'évaluation de l'intégrité. Par conséquent, ne modifiez pas les noms des catégories AlwaysOn.  
  
##  <a name="Dashboard"></a> Tableau de bord AlwaysOn  
 Le tableau de bord AlwaysOn fournit d'un coup d'œil une vue de l'intégrité d'un groupe de disponibilité. Il inclut les fonctionnalités suivantes :  
  
-   Vous permet de visualiser facilement les détails d'un groupe de disponibilité donné, ses réplicas de disponibilité et de ses bases de données.  
  
-   Affiche des indications visuelles des états clés pour aider les administrateurs de bases de données à prendre rapidement des décisions opérationnelles.  
  
-   Fournit des points de lancement pour résoudre des scénarios.  
  
-   Pour un problème opérationnel donné, remplit la boîte de dialogue **Résultat d'évaluation de stratégie** avec les informations relatives aux violations spécifiques de la stratégie de contrôle d'intégrité AlwaysOn et avec des liens d'aide pour y rémédier.  
  
-   Fournit une visionneuse d'événements d'intégrité étendus pour afficher les événements précédents liés à des problèmes spécifiques à AlwaysOn.  
  
-   Si le basculement sur le groupe de disponibilité est une solution possible à un problème, fournit un point de lancement pour les liens[Assistant Basculer le groupe de disponibilité](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md). Cet Assistant guide l'administrateur de base de données dans le processus manuel de basculement.  
  
##  <a name="ExtendHealthModel"></a> Extension du modèle d’intégrité AlwaysOn  
 L'extension du modèle d'intégrité [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] consiste à créer vos propres stratégies définies par l'utilisateur et à les placer dans certaines catégories en fonction du type d'objet surveillé.  Après que vous avez modifié quelques paramètres, le tableau de bord AlwaysOn évalue automatiquement vos propres stratégies définies par l'utilisateur, ainsi que les stratégies prédéfinies AlwaysOn.  
  
 Une stratégie définie par l'utilisateur peut utiliser les facettes PBM disponibles, notamment celles utilisées par les stratégies prédéfinies AlwaysOn (consultez [Stratégies prédéfinies et problèmes rencontrés](#AlwaysOnPBM), précédemment dans cette rubrique). La facette serveur fournit les propriétés suivantes pour la surveillance de l'intégrité [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] :  (`IsHadrEnabled` et `HadrManagerStatus`). La facette serveur fournit également les propriétés des stratégies suivantes pour la surveillance de la configuration du cluster WSFC : `ClusterQuorumType` et `ClusterQuorumState`.  
  
 Pour plus d'informations, consultez [Modèle d'intégrité AlwaysOn Partie 2 - Extension du modèle d'intégrité](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx) (blog de l'équipe de SQL Server AlwaysOn).  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Utiliser les stratégies AlwaysOn pour afficher l’intégrité d’un groupe de disponibilité &#40;SQL Server&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
-   [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [Récupération d’urgence WSFC par le quorum forcé &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-disaster-recovery-through-forced-quorum-sql-server.md)  
  
-   [Forcer un cluster WSFC à démarrer sans quorum](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md)  
  
-   [Effectuer un basculement manuel forcé d’un groupe de disponibilité &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Résoudre une opération d’ajout de fichier ayant échoué &#40;groupes de disponibilité AlwaysOn&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> Contenu associé  
  
-   [La modèle d’intégrité AlwaysOn partie 1--Architecture du modèle d’intégrité](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx)  
  
-   [La modèle d’intégrité AlwaysOn partie 2--Extending the Health Model](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx)  
  
-   [Guide de Solutions Microsoft SQL Server AlwaysOn pour une haute disponibilité et récupération d’urgence](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a>Voir aussi  
 [Groupes de disponibilité AlwaysOn (SQL Server)](always-on-availability-groups-sql-server.md)   
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Administration d’un groupe de disponibilité &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md)   
 [Surveillance des groupes de disponibilité &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)  
  
  
