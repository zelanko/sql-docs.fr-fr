---
title: Groupes de disponibilité Always On (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- secondary replicas, see Availability Groups [SQL Server]
- availability [SQL Server]
- AlwaysOn [SQL Server], see Availability Groups [SQL Server]
- Availability Groups [SQL Server]
ms.assetid: aa427606-8422-4656-b205-c9e665ddc8c1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2c05dc72e99d5b897412bdcf8afdd85370dd06b7
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937225"
---
# <a name="always-on-availability-groups-sql-server"></a>Groupes de disponibilité Always On (SQL Server)
  La fonctionnalité [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] est une solution de haute disponibilité et de récupération d'urgence qui fournit une alternative au niveau de l'entreprise à la mise en miroir de bases de données. Introduite dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] optimise la disponibilité d'un ensemble de bases de données utilisateur pour l'entreprise. Un *groupe de disponibilité* prend en charge un environnement de basculement pour un ensemble discret de bases de données utilisateur, appelées *bases de données de disponibilité*, qui basculent ensemble. Un groupe de disponibilité prend en charge un ensemble de bases de données primaires en lecture-écriture et un à huit ensembles de bases de données secondaires correspondantes. Éventuellement, les bases de données secondaires peuvent être rendues disponibles pour l'accès en lecture seule et/ou certaines opérations de sauvegarde.  
  
 Un groupe de disponibilité bascule au niveau d'un réplica de disponibilité. Les basculements ne sont pas dus à des problèmes de base de données, tels qu'une base de données devenant suspecte en raison de la perte d'un fichier de données, de la suppression d'une base de données ou de l'altération d'un journal des transactions.  
  
  
##  <a name="benefits"></a><a name="Benefits"></a> Avantages  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] fournissent un riche ensemble d'options qui améliorent la disponibilité des bases de données et l'utilisation des ressources. Les composants clés sont les suivants :  
  
-   Prend en charge jusqu'à neuf réplicas de disponibilité. Un *réplica de disponibilité* est une instanciation d'un groupe de disponibilité hébergé par une instance spécifique de SQL Server qui conserve une copie locale de chaque base de données de disponibilité appartenant au groupe de disponibilité. Chaque groupe de disponibilité prend en charge un réplica principal et jusqu'à huit réplicas secondaires. Pour plus d’informations, consultez [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
    > [!IMPORTANT]  
    >  Chaque réplica de disponibilité doit résider sur un nœud différent d'un cluster de clustering de basculement Windows Server (WSFC). Pour plus d’informations sur les conditions préalables requises, les restrictions et les recommandations pour les groupes de disponibilité, consultez [conditions préalables requises, restrictions et recommandations pour les groupes de disponibilité Always on. SQL Server ;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
-   Prend en charge d'autres modes de disponibilité, comme suit :  
  
    -   *Mode de validation asynchrone*. Ce mode avec validation asynchrone est une solution de récupération d'urgence qui fonctionne bien lorsque les réplicas de disponibilité sont séparés par des distances considérables.  
  
    -   *Mode de validation synchrone*. Ce mode de disponibilité privilégie la haute disponibilité et la protection des données plutôt que les performances, au prix d'une latence accrue des transactions. Un groupe de disponibilité donné peut prendre en charge jusqu'à trois réplicas de disponibilité avec validation synchrone, y compris le réplica principal actuel.  
  
     Pour plus d’informations, consultez [modes de disponibilité ; Always On des groupes de disponibilité ;](availability-modes-always-on-availability-groups.md).  
  
-   Prend en charge plusieurs formes de basculement de groupe de disponibilité : le basculement automatique, le basculement manuel planifié (généralement appelé simplement « basculement manuel ») et le basculement manuel forcé (généralement appelé simplement « basculement forcé »). Pour plus d’informations, consultez [basculement et modes de basculement. Always On des groupes de disponibilité ;](failover-and-failover-modes-always-on-availability-groups.md).  
  
-   Vous permet de configurer un réplica de disponibilité donné pour prendre en charge l'une des deux fonctions secondaires actives suivantes :  
  
    -   Accès à la connexion en lecture seule, permettant aux connexions en lecture seule au réplica d'accéder à et lire ses bases de données lorsqu'il s'exécute comme réplica secondaire. Pour plus d’informations, consultez [secondaires actifs : réplicas secondaires accessibles en lecture ; Always On les groupes de disponibilité](https://msdn.microsoft.com/library/ff878253.aspx)).  
  
    -   Exécution d'opérations de sauvegarde sur ses bases de données lorsqu'il s'exécute comme réplica secondaire. Pour plus d’informations, consultez secondaires [actifs : sauvegarde sur les réplicas secondaires](https://msdn.microsoft.com/library/ff878253.aspx)).  
  
     L'utilisation de fonctions secondaires actives améliore l'efficacité informatique et réduit les coûts grâce à une meilleure utilisation des ressources du matériel secondaire. En outre, le déchargement des applications de tentative de lecture et des travaux de sauvegarde vers des réplicas secondaires permet d'améliorer les performances au niveau du réplica principal.  
  
-   Prend en charge un écouteur de groupe de disponibilité pour chaque groupe de disponibilité. Un *écouteur de groupe de disponibilité* est un nom de serveur auquel les clients peuvent se connecter afin d'accéder à une base de données dans un réplica principal ou secondaire d'un groupe de disponibilité AlwaysOn. Les écouteurs de groupe de disponibilité dirigent les connexions entrantes vers un réplica principal ou un réplica secondaire en lecture seule. L'écouteur fournit un basculement d'application rapide après le basculement d'un groupe de disponibilité. Pour plus d’informations, consultez [écouteurs de groupe de disponibilité, connectivité client et basculement d’application. SQL Server ;](../../listeners-client-connectivity-application-failover.md).  
  
-   Prend en charge une stratégie de basculement flexible pour un contrôle optimisé du basculement de cluster de disponibilité. Pour plus d’informations, consultez [basculement et modes de basculement. Always On des groupes de disponibilité ;](failover-and-failover-modes-always-on-availability-groups.md).  
  
-   Prend en charge la réparation de page automatique pour éviter les pages endommagées. Pour plus d’informations, consultez [réparation de page automatique &#40;pour les groupes de disponibilité et la mise en miroir de bases de données ;](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md).  
  
-   Prend en charge le chiffrement et la compression, qui fournissent un transport sécurisé et efficace.  
  
-   Fournit un jeu intégré d'outils pour simplifier le déploiement et la gestion de groupes de disponibilité, notamment :  
  
    -   [!INCLUDE[tsql](../../../includes/tsql-md.md)] pour créer et gérer les groupes de disponibilité. Pour plus d’informations, consultez [vue d’ensemble des instructions Transact-SQL pour Always on groupe de disponibilité ; SQL Server ;](transact-sql-statements-for-always-on-availability-groups.md).  
  
    -   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] , comme suit :  
  
        -   L' [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] crée et configure un groupe de disponibilité. Dans certains environnements, cet Assistant peut également préparer automatiquement les bases de données secondaires et démarrer la synchronisation de données pour chacune d'elles. Pour plus d’informations, consultez [utiliser la boîte de dialogue Nouveau groupe de disponibilité ; SQL Server Management Studio ;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md).  
  
        -   L'[!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] ajoute une ou plusieurs bases de données primaires à un groupe de disponibilité existant. Dans certains environnements, cet Assistant peut également préparer automatiquement les bases de données secondaires et démarrer la synchronisation de données pour chacune d'elles. Pour plus d’informations, consultez [Utiliser l’Assistant Ajouter une base de données au groupe de disponibilité (SQL Server)](availability-group-add-database-to-group-wizard.md).  
  
        -   L' [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] ajoute un ou plusieurs réplicas secondaires à un groupe de disponibilité existant. Dans certains environnements, cet Assistant peut également préparer automatiquement les bases de données secondaires et démarrer la synchronisation de données pour chacune d'elles. Pour plus d’informations, consultez [utiliser l’Assistant Ajouter un réplica au groupe de disponibilité ; SQL Server Management Studio ;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md).  
  
        -   L'[!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)] démarre un basculement manuel sur un groupe de disponibilité. En fonction de la configuration et de l'état du réplica secondaire que vous spécifiez comme cible de basculement, l'Assistant peut effectuer un basculement manuel planifié ou forcé. Pour plus d’informations, consultez [utiliser l’Assistant basculer le groupe de disponibilité ; SQL Server Management Studio ;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md).  
  
    -   Le [!INCLUDE[ssAoDash](../../../includes/ssaodash-md.md)] surveille les groupes de disponibilité, les réplicas de disponibilité et les bases de données de disponibilité AlwaysOn et évalue les résultats des stratégies AlwaysOn. Pour plus d’informations, consultez [utiliser le tableau de bord AlwaysOn ; SQL Server Management Studio ;](use-the-always-on-dashboard-sql-server-management-studio.md).  
  
    -   Le volet Détails de l'Explorateur d'objets affiche des informations de base à propos des groupes de disponibilité existants. Pour plus d’informations, consultez [utiliser les détails de l’Explorateur d’objets pour surveiller le groupe de disponibilité. SQL Server Management Studio ;](use-object-explorer-details-to-monitor-availability-groups.md).  
  
    -   Applets de commande PowerShell. Pour plus d’informations, consultez [vue d’ensemble des applets de commande PowerShell pour les groupes de disponibilité Always on. SQL Server ;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md).  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a>Termes et définitions  
 Groupe de disponibilité  
 Conteneur d’un ensemble de bases de données ( *bases de données de disponibilité*) qui basculent ensemble.  
  
 Base de données de disponibilité  
 Base de données qui appartient à un groupe de disponibilité. Pour chaque base de données de disponibilité, le groupe de disponibilité conserve une seule copie en lecture-écriture (la *base de données primaire*) et une à huit copies en lecture seule (les*bases de données secondaires*).  
  
 base de données primaire  
 Copie en lecture-écriture d'une base de données de disponibilité.  
  
 base de données secondaire  
 Copie en lecture seule d'une base de données de disponibilité.  
  
 réplica de disponibilité  
 Instanciation d'un groupe de disponibilité hébergé par une instance spécifique de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et qui conserve une copie locale de chaque base de données de disponibilité appartenant au groupe de disponibilité. Il existe deux types de réplicas de disponibilité : un seul *réplica principal* et un à huit *réplicas secondaires*.  
  
 réplica principal  
 Réplica de disponibilité qui rend les bases de données primaires disponibles pour les connexions en lecture-écriture à partir des clients et envoie également des enregistrements du journal des transactions pour chaque base de données primaire à chaque réplica secondaire.  
  
 réplica secondaire  
 Réplica de disponibilité qui conserve une copie secondaire de chaque base de données de disponibilité, et sert de cible potentielle d'un basculement du groupe de disponibilité. Éventuellement, un réplica secondaire peut prendre en charge l'accès en lecture seule et la création de sauvegardes sur des bases de données secondaires.  
  
 écouteur de groupe de disponibilité  
 Nom du serveur auquel les clients peuvent se connecter afin d’accéder à une base de données dans un réplica principal ou secondaire d’un groupe de disponibilité Always On. Les écouteurs de groupe de disponibilité dirigent les connexions entrantes vers un réplica principal ou un réplica secondaire en lecture seule.  
  
> [!NOTE]  
>  Pour plus d’informations, consultez [vue d’ensemble des groupes de disponibilité AlwaysOn ; SQL Server ;](overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="interoperability-and-coexistence-with-other-database-engine-features"></a><a name="Interoperability"></a>Interopérabilité et coexistence avec d’autres fonctionnalités de Moteur de base de données  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] peuvent être utilisés avec les fonctionnalités ou les composants [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]suivants :  
  
-   [À propos de la capture de données modifiées ; SQL Server ;](../../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
-   [À propos de Change Tracking ; SQL Server ;](../../../relational-databases/track-changes/about-change-tracking-sql-server.md)  
  
-   [Bases de données à relation contenant-contenu](../../../relational-databases/databases/contained-databases.md)  
  
-   [Chiffrement de base de données](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
-   [Instantanés de base de données](database-snapshots-with-always-on-availability-groups-sql-server.md)  
  
-   [FILESTREAM](../../../relational-databases/blob/filestream-sql-server.md)  
  
-   [FileTable](../../../relational-databases/blob/filetables-sql-server.md)  
  
-   [Copie des journaux de transaction](../../log-shipping/about-log-shipping-sql-server.md)  
  
-   [Magasin d'objets blob distants (RBS)](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
-   [Réplication](../../install-windows/install-sql-server-replication.md)  
  
-   [Service Broker](../../configure-windows/sql-server-service-broker.md)  
  
-   [SQL Server Agent](../../../ssms/agent/sql-server-agent.md)  
  
-   [Reporting Services](reporting-services-with-always-on-availability-groups-sql-server.md)  
  
> [!WARNING]  
>  Pour plus d’informations sur les restrictions et les limitations relatives à l’utilisation d’autres fonctionnalités avec [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , consultez [Always on des groupes de disponibilité : interopérabilité ; SQL Server ;](always-on-availability-groups-interoperability-sql-server.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
  
-   [Prise en main avec les groupes de disponibilité Always On ; SQL Server ;](getting-started-with-always-on-availability-groups-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Contenu associé  
  
-   **Blogs :**  
  
     [Blogs de l’équipe de SQL Server Always On : le blog officiel de l’équipe SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Blogs des ingénieurs du Service clientèle et du Support technique de SQL Server](https://blogs.msdn.com/b/psssql/)  
  
-   **Vidéos :**  
  
     [Microsoft SQL Server, nom de code « Denali », série Always On, Partie 1 : Introducing the Next Generation High Availability Solution](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302) (vidéo de présentation de la solution haute disponibilité de la génération suivante)  
  
     [Microsoft SQL Server nom de code « Denali » Always On série, partie 2 : génération d’une solution haute disponibilité stratégique à l’aide d’AlwaysOn](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Livres blancs :**  
  
     [Guide de solutions Microsoft SQL Server Always On pour la haute disponibilité et la récupération d’urgence](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On ; SQL Server ;](overview-of-always-on-availability-groups-sql-server.md)   
 [Conditions préalables requises, restrictions et recommandations pour groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Configuration d’une instance de serveur pour les groupes de disponibilité Always On ; SQL Server ;](always-on-availability-groups-sql-server.md)   
 [Création et configuration des groupes de disponibilité ; SQL Server ;](creation-and-configuration-of-availability-groups-sql-server.md)   
 [Administration d’un groupe de disponibilité ; SQL Server ;](administration-of-an-availability-group-sql-server.md)   
 [Surveillance des groupes de disponibilité &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [Vue d’ensemble des instructions Transact-SQL pour les groupes de disponibilité Always On ; SQL Server ;](transact-sql-statements-for-always-on-availability-groups.md)   
 [Vue d’ensemble des applets de commande PowerShell pour groupes de disponibilité AlwaysOn ; SQL Server ;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
