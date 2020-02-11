---
title: Utiliser le tableau de bord AlwaysOn (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
- Availability Groups [SQL Server], dashboard
ms.assetid: c9ba2589-139e-42bc-99e1-94546717c64d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c4402cd9e7c02b598c47a851c8318e7c840bfbc3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62788726"
---
# <a name="use-the-alwayson-dashboard-sql-server-management-studio"></a>Utiliser le tableau de bord AlwaysOn (SQL Server Management Studio)
  Les administrateurs de base de données utilisent le tableau de bord AlwaysOn pour afficher l'intégrité d'un groupe de disponibilité AlwaysOn et de ses réplicas de disponibilité et bases de données dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Parmi les utilisations courantes du tableau de bord AlwaysOn, citons :  
  
-   Choix d'un réplica pour un basculement manuel.  
  
-   Estimation de la perte de données en cas de basculement forcé.  
  
-   Évaluation des performances de synchronisation des données.  
  
-   Évaluation de l'impact sur les performances d'un réplica secondaire avec validation synchrone  
  
 Le tableau de bord AlwaysOn fournit les états principaux et les indicateurs de performance du groupe de disponibilité et vous permet ainsi de prendre facilement des décisions opérationnelles en matière de haute disponibilité sur la base des types d'informations suivants.  
  
-   État de restauration de réplica  
  
-   Mode et état de synchronisation  
  
-   Estimer la perte de données  
  
-   Durée estimée de récupération (rattrapage de la phase de restauration par progression)  
  
-   Détails du réplica de base de données  
  
-   Mode et état de synchronisation  
  
-   Durée de restauration du journal  
  
 
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a>Conditions préalables  
 Vous devez être connecté à l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (instance de serveur) qui héberge soit le réplica principal, soit un réplica secondaire d'un groupe de disponibilité.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert les autorisations CONNECT, VIEW SERVER STATE et VIEW ANY DEFINITION.  
  
##  <a name="SSMSProcedure"></a>Pour démarrer le tableau de bord AlwaysOn  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur laquelle vous souhaitez exécuter le tableau de bord AlwaysOn.  
  
2.  Développez le nœud **Haute disponibilité AlwaysOn** , cliquez avec le bouton droit sur le nœud **Groupes de disponibilité** , puis sélectionnez **Afficher le tableau de bord**.  
  
###  <a name="DashboardOptions"></a>Pour modifier les options du tableau de bord AlwaysOn  
 Vous pouvez utiliser la boîte de dialogue [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]Options** de ** pour configurer le comportement du tableau de bord [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn en ce qui concerne l’actualisation automatique et l’activation d’une stratégie AlwaysOn définie automatiquement.  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Pour actualiser automatiquement le tableau de bord, dans la boîte de dialogue **Options** , sélectionnez **Activer l'actualisation automatique**, entrez l'intervalle d'actualisation en secondes, puis entrez le nombre de fois où vous souhaitez réessayer la connexion.  
  
3.  Pour activer une stratégie définie par l'utilisateur, sélectionnez **Activer la stratégie AlwaysOn définie par l'utilisateur**.  
  
##  <a name="AvGroupsView"></a>Résumé du groupe de disponibilité  
 L'écran de groupe de disponibilité affiche une ligne de résumé pour chaque groupe de disponibilité pour lequel l'instance de serveur connectée héberge un réplica. Ce volet inclut les colonnes suivantes.  
  
 **Nom du groupe de disponibilité**  
 Nom d'un groupe de disponibilité pour lequel l'instance de serveur connectée héberge un réplica.  
  
 **Instance principale**  
 Nom de l'instance de serveur qui héberge le réplica principal du groupe de disponibilité.  
  
 **Mode de basculement**  
 Affiche le mode de basculement pour lequel le réplica est configuré. Les valeurs possibles pour le mode de basculement sont les suivantes :  
  
-   **Automatique**. Indique qu'un ou plusieurs réplicas se trouvent en mode de basculement automatique.  
  
-   **Manuel**. Indique qu'aucun réplica n'est en mode de basculement automatique.  
  
 **Problèmes**  
 Cliquez sur le lien **Problèmes** pour ouvrir la documentation de dépannage relative à un problème donné. Pour obtenir la liste de tous les problèmes de stratégie AlwaysOn, consultez [stratégies AlwaysOn pour les problèmes opérationnels avec groupes de disponibilité AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
> [!TIP]  
>  Cliquez sur les en-têtes de colonne pour trier les informations de groupe de disponibilité selon le nom du groupe de disponibilité, l'instance principale, le mode de basculement ou le problème.  
  
##  <a name="AvGroupDetails"></a>Détails du groupe de disponibilité  
 Les informations détaillées suivantes sont affichées pour le groupe de disponibilité que vous sélectionnez dans l'écran récapitulatif :  
  
 **État du groupe de disponibilité**  
 Affiche l'état d'intégrité du groupe de disponibilité.  
  
 **Instance principale**  
 Nom de l'instance de serveur qui héberge le réplica principal du groupe de disponibilité.  
  
 **Mode de basculement**  
 Affiche le mode de basculement pour lequel le réplica est configuré. Les valeurs possibles pour le mode de basculement sont les suivantes :  
  
-   **Automatique**. Indique qu'un ou plusieurs réplicas se trouvent en mode de basculement automatique.  
  
-   **Manuel**. Indique qu'aucun réplica n'est en mode de basculement automatique.  
  
 **État du cluster**  
 Nom et état du cluster dans lequel l'instance du serveur connecté et du groupe de disponibilité est un nœud membre.  
  
##  <a name="AvReplicaDetails"></a>Détails du réplica de disponibilité  
 Le volet **Réplica de disponibilité** affiche les colonnes suivantes :  
  
 **Nom**  
 Nom de l'instance du serveur qui héberge le réplica de disponibilité. Cette colonne est affichée par défaut.  
  
 **Actif**  
 Indique le rôle actuel du réplica de disponibilité, à savoir **Principal** ou **Secondaire**. Pour plus d’informations sur les rôles des [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consultez [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md). Cette colonne est affichée par défaut.  
  
 **Mode de basculement**  
 Affiche le mode de basculement pour lequel le réplica est configuré. Les valeurs possibles pour le mode de basculement sont les suivantes :  
  
-   **Automatique**. Indique qu'un ou plusieurs réplicas se trouvent en mode de basculement automatique.  
  
-   **Manuel**. Indique qu'aucun réplica n'est en mode de basculement automatique.  
  
 **État de synchronisation**  
 Indique si un réplica secondaire est actuellement synchronisé avec le réplica principal. Cette colonne est affichée par défaut. Les valeurs possibles sont les suivantes :  
  
-   **Non synchronisé**. Une ou plusieurs bases de données du réplica ne sont pas synchronisées ou n'ont pas encore été jointes au groupe de disponibilité.  
  
-   **Synchronisation**en cours. Une ou plusieurs bases de données du réplica sont synchronisées.  
  
-   **Synchronisé**. Toutes les bases de données du réplica secondaire sont synchronisées avec les base de données primaires correspondantes sur le réplica principal actuel, le cas échéant, ou sur le dernier réplica principal.  
  
    > [!NOTE]  
    >  En mode de performances, la base de données n'est jamais dans l'état synchronisé.  
  
-   **Valeur null**. État inconnu. Cette valeur se produit lorsque l'instance de serveur locale ne peut pas communiquer avec le cluster de basculement WSFC (le nœud local ne fait pas partie du quorum WSFC).  
  
 **Problèmes**  
 Énonce le nom du problème. Cette valeur est affichée par défaut. Pour obtenir la liste de tous les problèmes de stratégie AlwaysOn, consultez [stratégies AlwaysOn pour les problèmes opérationnels avec groupes de disponibilité AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
 **Mode de disponibilité**  
 Indique la propriété de réplica que vous définissez séparément pour chaque réplica de disponibilité. Cette valeur est masquée par défaut. Les valeurs possibles sont les suivantes :  
  
-   **Asynchrone**. Le réplica secondaire n'est jamais synchronisé avec le réplica principal.  
  
-   **Synchrone**. Lors du rattrapage du retard par rapport à la base de données primaire, une base de données secondaire entre dans cet état, mais reste en retard tant que la synchronisation des données se poursuit pour la base de données.  
  
 **Mode de connexion principal**  
 Indique le mode utilisé pour se connecter au réplica principal.  Cette valeur est masquée par défaut.  
  
 **Mode de connexion secondaire**  
 Indique le mode utilisé pour se connecter au réplica secondaire.  Cette valeur est masquée par défaut.  
  
 **État de la connexion**  
 Indique si un réplica secondaire est actuellement connecté au réplica principal. Cette colonne est masquée par défaut. Les valeurs possibles sont les suivantes :  
  
-   **Déconnecté**. Pour un réplica de disponibilité distant, indique qu'il est déconnecté du réplica de disponibilité local. La réponse du réplica local à l'état déconnecté dépend de son rôle, comme suit :  
  
    -   Sur le réplica principal, si un réplica secondaire est déconnecté, les bases de données secondaires sont marquées comme **Non synchronisé** sur le réplica principal, et le réplica principal attend que le réplica secondaire se reconnecte.  
  
    -   Une fois la déconnexion détectée, le réplica secondaire tente de se reconnecter au réplica principal.  
  
-   **Connecté**. Réplica de disponibilité distant qui est actuellement connecté au réplica local.  
  
 **État de fonctionnement**  
 Indique l'état opérationnel actuel du réplica secondaire. Cette valeur est masquée par défaut. Les valeurs possibles sont les suivantes :  
  
 **0**. basculement en attente  
  
 **1**. en attente  
  
 **2**. en ligne  
  
 **3**. hors connexion  
  
 **4**. échec  
  
 **5**. échec, pas de quorum  
  
 **Valeur null**. Le réplica n'est pas local  
  
 **N ° de la dernière erreur de connexion**  
 Numéro de la dernière erreur de connexion.  Cette valeur est masquée par défaut.  
  
 **Description de la dernière erreur de connexion**  
 Description de la dernière erreur de connexion.  Cette valeur est masquée par défaut.  
  
 **Horodateur de la dernière erreur de connexion**  
 Horodateur de la dernière erreur de connexion. Cette valeur est masquée par défaut.  
  
> [!NOTE]  
>  Pour plus d’informations sur les compteurs de performances pour les réplicas de disponibilité, consultez [SQL Server, réplica de disponibilité](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).  
  
##  <a name="AvDbDetails"></a>Pour regrouper les informations de groupe de disponibilité  
 Pour regrouper les informations, cliquez sur **Regrouper par**, puis sélectionnez l'une des commandes suivantes :  
  
-   **Réplicas de disponibilité**  
  
-   **Bases de données de disponibilité**  
  
-   **État de synchronisation**  
  
-   **Disponibilité du basculement**  
  
-   **Problèmes**  
  
 Le volet qui affiche les informations regroupées comporte les colonnes suivantes :  
  
 **Nom**  
 Nom de la base de données de disponibilité. Cette valeur est affichée par défaut.  
  
 **Réplica**  
 Nom de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui héberge le réplica de disponibilité. Cette valeur est affichée par défaut.  
  
 **État de synchronisation**  
 Indique si la base de données de disponibilité est actuellement synchronisée avec le réplica principal. Cette valeur est affichée par défaut. Les états de synchronisation possibles sont les suivants :  
  
-   **Non synchronisé**.  
  
    -   Pour le rôle principal, indique que la base de données n'est pas prête à synchroniser son journal des transactions avec les bases de données secondaires correspondantes.  
  
    -   Pour une base de données secondaire, indique que la base de données n'a pas commencé la synchronisation du journal en raison d'un problème de connexion, est suspendue, ou passe par des états de transition pendant le démarrage ou lors d'un changement de rôle.  
  
-   **Synchronisation**en cours.  
  
     Sur un réplica principal :  
  
    -   Pour une base de données primaire, indique que cette base de données est prête à recevoir une demande d'analyse d'une base de données secondaire.  
  
    -   Sur un réplica secondaire, indique qu'il existe un déplacement des données actif pour cette base de données secondaire.  
  
     Sur un réplica secondaire, indique qu'il existe un déplacement des données actif pour ce réplica.  
  
-   **Synchronisé**.  
  
     Pour une base de données primaire, indique qu'au moins une base de données secondaire est synchronisée.  
  
     Pour une base de données secondaire, indique que la base de données est synchronisée avec la base de données primaire correspondante.  
  
-   **Rétablissement**.  
  
     Indique la phase dans le processus de restauration lorsqu'une base de données secondaire obtient activement les pages de la base de données primaire.  
  
    > [!CAUTION]  
    >  Lorsqu'une base de données est dans l'état REVERTING, forcer le basculement vers le réplica secondaire peut laisser cette base de données dans un état dans lequel elle ne peut pas être démarrée.  
  
-   **Initialisation en cours**.  
  
     Indique la phase de restauration lorsque le journal des transactions requis pour qu'une base de données secondaire rattrape le retard du numéro séquentiel de restauration dans le journal est livré et renforcé sur un réplica secondaire.  
  
    > [!CAUTION]  
    >  Lorsqu'une base de données est dans l'état INITIALIZING, forcer le basculement vers le réplica secondaire laisse toujours cette base de données dans un état dans lequel elle ne peut pas être démarrée.  
  
 **Disponibilité du basculement**  
 Indique le réplica de disponibilité qui peut basculer avec ou sans perte possible de données. Cette colonne est affichée par défaut. Les valeurs possibles sont les suivantes :  
  
-   **Perte de données**  
  
-   **Aucune perte de données**  
  
 **Problèmes**  
 Énonce le nom du problème. Cette colonne est affichée par défaut. Les valeurs possibles sont les suivantes :  
  
-   **Avertissements**. Cliquez pour afficher les problèmes d'avertissements et de seuils.  
  
-   **Critique**. Cliquez pour afficher les problèmes critiques.  
  
 Pour obtenir la liste de tous les problèmes de stratégie AlwaysOn, consultez [stratégies AlwaysOn pour les problèmes opérationnels avec groupes de disponibilité AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
 **Suspendu**  
 Indique si la base de données est à l’état **Suspendu** ou si elle a été **reprise**. Cette valeur est masquée par défaut.  
  
 **Motif de suspension**  
 Indique le motif de l'état suspendu. Cette valeur est masquée par défaut.  
  
 **Estimer la perte de données (secondes)**  
 Indique la différence de temps du dernier enregistrement des journaux de transactions dans le réplica principal et le réplica secondaire. Si le réplica principal échoue, tous les enregistrements du journal des transactions se trouvant dans cette fenêtre temporelle seront perdus. Cette valeur est masquée par défaut.  
  
 **Durée estimée de récupération (secondes)**  
 Indique la durée (en secondes) nécessaire pour rétablir le temps de rattrapage. Le *temps de rattrapage* correspond au temps nécessaire pour que le réplica secondaire rattrape le réplica principal. Cette valeur est masquée par défaut.  
  
 **Performances de synchronisation (secondes)**  
 Indique le temps (en secondes) nécessaire pour effectuer la synchronisation entre le réplica principal et le réplica secondaire. Cette valeur est masquée par défaut.  
  
 **Taille de la file d'attente d'envoi du journal (Ko)**  
 Indique la quantité d'enregistrements de journal dans les fichiers journaux de la base de données primaire qui n'ont pas été envoyés au réplica secondaire. Cette valeur est masquée par défaut.  
  
 **Débit d'envoi du journal (Ko/s)**  
 Indique le débit, en Ko par seconde, auquel les enregistrements de journal sont envoyés au réplica secondaire. Cette valeur est masquée par défaut.  
  
 **Taille de la file d’attente de restauration par progression (Ko)**  
 Indique la quantité d'enregistrements du journal dans les fichiers journaux du réplica secondaire qui n'ont pas encore été restaurés. Cette valeur est masquée par défaut.  
  
 **Taux de restauration par progression (Ko/s)**  
 Indique le débit, en Ko par seconde, auquel les enregistrements de journal sont restaurés. Cette valeur est masquée par défaut.  
  
 **Taux d’envoi FileStream (Ko/s)**  
 Indique le débit de FileStream, en Ko par seconde, auquel les transactions sont envoyées au réplica. Cette valeur est masquée par défaut.  
  
 **LSN de fin du journal**  
 Indique le numéro séquentiel dans le journal (LSN) réel qui correspond au dernier enregistrement du journal dans le cache du journal sur les réplicas principal et secondaire. Cette valeur est masquée par défaut.  
  
 **LSN de récupération**  
 Indique la fin du journal des transactions avant que le réplica n'écrive de nouveaux enregistrements de journal après la récupération ou le basculement sur le réplica principal. Cette valeur est masquée par défaut.  
  
 **LSN de troncation**  
 Indique la valeur minimale de troncation du journal du réplica principal. Cette valeur est masquée par défaut.  
  
 **LSN de la dernière validation**  
 Indique le numéro séquentiel dans le journal réel correspondant au dernier enregistrement de validation dans le journal des transactions. Cette valeur est masquée par défaut.  
  
 **Heure de la dernière validation**  
 Indique l'heure correspondant au dernier enregistrement de validation. Cette valeur est masquée par défaut.  
  
 **LSN du dernier envoi**  
 Indique le point jusqu'auquel tous les blocs de journal ont été envoyés par le réplica principal. Cette valeur est masquée par défaut.  
  
 **Heure du dernier envoi**  
 Indique l'heure à laquelle le dernier bloc du journal a été envoyé. Cette valeur est masquée par défaut.  
  
 **LSN de dernière réception**  
 Indique le point jusqu'auquel tous les blocs de journal ont été reçus par le réplica secondaire qui héberge la base de données secondaire. Cette valeur est masquée par défaut.  
  
 **Heure de la dernière réception**  
 Indique l'heure à laquelle l'identificateur de bloc de journal du dernier message reçu a été lu sur le réplica secondaire. Cette valeur est masquée par défaut.  
  
 **LSN de dernière sécurisation renforcée**  
 Indique le point jusqu'auquel tous les enregistrements de journal ont été vidés sur le disque du réplica secondaire. Cette valeur est masquée par défaut.  
  
 **Heure de la dernière sécurisation renforcée**  
 Indique l'heure à laquelle l'identificateur de bloc de journal a été reçu pour le LSN de dernière sécurisation renforcée sur le réplica secondaire. Cette valeur est masquée par défaut.  
  
 **LSN de la dernière opération de restauration**  
 Indique le numéro séquentiel réel dans l'enregistrement du journal qui a été reconstruit pour la dernière fois sur le réplica secondaire. Cette valeur est masquée par défaut.  
  
 **Heure de la dernière restauration**  
 Indique l'heure à laquelle le dernier enregistrement du journal a été restauré sur la base de données secondaire. Cette valeur est masquée par défaut.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Utilisez les stratégies AlwaysOn pour afficher l’intégrité d’un groupe de disponibilité &#40;SQL Server&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [sys. dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)   
 [Surveillance des groupes de disponibilité &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)  
  
  
