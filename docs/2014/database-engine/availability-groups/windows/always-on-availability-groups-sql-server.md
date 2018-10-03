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
manager: craigg
ms.openlocfilehash: 5e560cae97a647b484bc75936db31434dc08864a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177009"
---
# <a name="always-on-availability-groups-sql-server"></a>Groupes de disponibilité Always On (SQL Server)
  La fonctionnalité [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] est une solution de haute disponibilité et de récupération d'urgence qui fournit une alternative au niveau de l'entreprise à la mise en miroir de bases de données. Introduite dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] optimise la disponibilité d'un ensemble de bases de données utilisateur pour l'entreprise. Un *groupe de disponibilité* prend en charge un environnement de basculement pour un ensemble discret de bases de données utilisateur, appelées *bases de données de disponibilité*, qui basculent de concert. Un groupe de disponibilité prend en charge un ensemble de bases de données primaires en lecture-écriture et un à huit ensembles de bases de données secondaires correspondantes. Éventuellement, les bases de données secondaires peuvent être rendues disponibles pour l'accès en lecture seule et/ou certaines opérations de sauvegarde.  
  
 Un groupe de disponibilité bascule au niveau d'un réplica de disponibilité. Les basculements ne sont pas dus à des problèmes de base de données, tels qu'une base de données devenant suspecte en raison de la perte d'un fichier de données, de la suppression d'une base de données ou de l'altération d'un journal des transactions.  
  
  
##  <a name="Benefits"></a> Avantages  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] fournissent un riche ensemble d'options qui améliorent la disponibilité des bases de données et l'utilisation des ressources. Les composants clés sont les suivants :  
  
-   Prend en charge jusqu'à neuf réplicas de disponibilité. Un *réplica de disponibilité* est une instanciation d'un groupe de disponibilité hébergé par une instance spécifique de SQL Server qui conserve une copie locale de chaque base de données de disponibilité appartenant au groupe de disponibilité. Chaque groupe de disponibilité prend en charge un réplica principal et jusqu'à huit réplicas secondaires. Pour plus d’informations, consultez [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
    > [!IMPORTANT]  
    >  Chaque réplica de disponibilité doit résider sur un nœud différent d'un cluster de clustering de basculement Windows Server (WSFC). Pour plus d’informations sur les conditions préalables, restrictions et recommandations pour les groupes de disponibilité, consultez [prérequis, Restrictions et recommandations pour les groupes de disponibilité AlwaysOn ; SQL Server ; ](prereqs-restrictions-recommendations-always-on-availability.md).  
  
-   Prend en charge d'autres modes de disponibilité, comme suit :  
  
    -   *Mode de validation asynchrone*. Ce mode avec validation asynchrone est une solution de récupération d'urgence qui fonctionne bien lorsque les réplicas de disponibilité sont séparés par des distances considérables.  
  
    -   *Mode de validation synchrone*. Ce mode de disponibilité privilégie la haute disponibilité et la protection des données plutôt que les performances, au prix d'une latence accrue des transactions. Un groupe de disponibilité donné peut prendre en charge jusqu'à trois réplicas de disponibilité avec validation synchrone, y compris le réplica principal actuel.  
  
     Pour plus d’informations, consultez [ Modes de disponibilité ; Toujours sur les groupes de disponibilité ; ](availability-modes-always-on-availability-groups.md).  
  
-   Prend en charge plusieurs formes de basculement de groupe de disponibilité : le basculement automatique, le basculement manuel planifié (généralement appelé simplement « basculement manuel ») et le basculement manuel forcé (généralement appelé simplement « basculement forcé »). Pour plus d’informations, consultez [basculement et Modes de basculement ; Toujours sur les groupes de disponibilité ; ](failover-and-failover-modes-always-on-availability-groups.md).  
  
-   Vous permet de configurer un réplica de disponibilité donné pour prendre en charge l'une des deux fonctions secondaires actives suivantes :  
  
    -   Accès à la connexion en lecture seule, permettant aux connexions en lecture seule au réplica d'accéder à et lire ses bases de données lorsqu'il s'exécute comme réplica secondaire. Pour plus d’informations, consultez [secondaires actifs : réplicas secondaires lisibles ; Groupes de disponibilité Always On](https://msdn.microsoft.com/library/ff878253.aspx)).  
  
    -   Exécution d'opérations de sauvegarde sur ses bases de données lorsqu'il s'exécute comme réplica secondaire. Pour plus d’informations, consultez [secondaires actifs : sauvegarde sur les réplicas secondaires](https://msdn.microsoft.com/library/ff878253.aspx)).  
  
     L'utilisation de fonctions secondaires actives améliore l'efficacité informatique et réduit les coûts grâce à une meilleure utilisation des ressources du matériel secondaire. En outre, le déchargement des applications de tentative de lecture et des travaux de sauvegarde vers des réplicas secondaires permet d'améliorer les performances au niveau du réplica principal.  
  
-   Prend en charge un écouteur de groupe de disponibilité pour chaque groupe de disponibilité. Un *écouteur de groupe de disponibilité* est un nom de serveur auquel les clients peuvent se connecter afin d'accéder à une base de données dans un réplica principal ou secondaire d'un groupe de disponibilité AlwaysOn. Les écouteurs de groupe de disponibilité dirigent les connexions entrantes vers un réplica principal ou un réplica secondaire en lecture seule. L'écouteur fournit un basculement d'application rapide après le basculement d'un groupe de disponibilité. Pour plus d’informations, consultez [écouteurs de groupe de disponibilité, connectivité Client et basculement d’Application ; SQL Server ; ](../../listeners-client-connectivity-application-failover.md).  
  
-   Prend en charge une stratégie de basculement flexible pour un contrôle optimisé du basculement de cluster de disponibilité. Pour plus d’informations, consultez [basculement et Modes de basculement ; Toujours sur les groupes de disponibilité ; ](failover-and-failover-modes-always-on-availability-groups.md).  
  
-   Prend en charge la réparation de page automatique pour éviter les pages endommagées. Pour plus d’informations, consultez [réparation de Page automatique &#40;pour les groupes de disponibilité et de la base de données mise en miroir ;](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md).  
  
-   Prend en charge le chiffrement et la compression, qui fournissent un transport sécurisé et efficace.  
  
-   Fournit un jeu intégré d'outils pour simplifier le déploiement et la gestion de groupes de disponibilité, notamment :  
  
    -   [!INCLUDE[tsql](../../../includes/tsql-md.md)] pour créer et gérer les groupes de disponibilité. Pour plus d’informations, consultez [vue d’ensemble d’instructions Transact-SQL pour le groupe de disponibilité AlwaysOn ; SQL Server ; ](transact-sql-statements-for-always-on-availability-groups.md).  
  
    -   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] , comme suit :  
  
        -   L' [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] crée et configure un groupe de disponibilité. Dans certains environnements, cet Assistant peut également préparer automatiquement les bases de données secondaires et démarrer la synchronisation de données pour chacune d'elles. Pour plus d’informations, consultez [utiliser la nouvelle boîte de dialogue groupe de disponibilité ; SQL Server Management Studio ; ](use-the-new-availability-group-dialog-box-sql-server-management-studio.md).  
  
        -   L'[!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] ajoute une ou plusieurs bases de données primaires à un groupe de disponibilité existant. Dans certains environnements, cet Assistant peut également préparer automatiquement les bases de données secondaires et démarrer la synchronisation de données pour chacune d'elles. Pour plus d’informations, consultez [Utiliser l’Assistant Ajouter une base de données au groupe de disponibilité (SQL Server)](availability-group-add-database-to-group-wizard.md).  
  
        -   L' [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] ajoute un ou plusieurs réplicas secondaires à un groupe de disponibilité existant. Dans certains environnements, cet Assistant peut également préparer automatiquement les bases de données secondaires et démarrer la synchronisation de données pour chacune d'elles. Pour plus d’informations, consultez [utiliser Ajouter un réplica à l’Assistant groupe de disponibilité ; SQL Server Management Studio ; ](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md).  
  
        -   L'[!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)] démarre un basculement manuel sur un groupe de disponibilité. En fonction de la configuration et de l'état du réplica secondaire que vous spécifiez comme cible de basculement, l'Assistant peut effectuer un basculement manuel planifié ou forcé. Pour plus d’informations, consultez [utiliser l’Assistant basculer le disponibilité groupe ; SQL Server Management Studio ; ](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md).  
  
    -   Le [!INCLUDE[ssAoDash](../../../includes/ssaodash-md.md)] surveille les groupes de disponibilité, les réplicas de disponibilité et les bases de données de disponibilité AlwaysOn et évalue les résultats des stratégies AlwaysOn. Pour plus d’informations, consultez [utiliser le tableau de bord AlwaysOn ; SQL Server Management Studio ; ](use-the-always-on-dashboard-sql-server-management-studio.md).  
  
    -   Le volet Détails de l'Explorateur d'objets affiche des informations de base à propos des groupes de disponibilité existants. Pour plus d’informations, consultez [utiliser les détails de l’Explorateur d’objets pour le groupe de disponibilité du moniteur ; SQL Server Management Studio ; ](use-object-explorer-details-to-monitor-availability-groups.md).  
  
    -   Applets de commande PowerShell. Pour plus d’informations, consultez [vue d’ensemble des applets de commande PowerShell pour les groupes de disponibilité AlwaysOn ; SQL Server ; ](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md).  
  
##  <a name="TermsAndDefinitions"></a> Termes et définitions  
 groupe de disponibilité  
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
>  Pour plus d’informations, consultez [vue d’ensemble de groupes de disponibilité AlwaysOn ; SQL Server ; ](overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="Interoperability"></a> Interopérabilité et coexistence avec d'autres fonctionnalités de moteur de base de données  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] peuvent être utilisés avec les fonctionnalités ou les composants [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]suivants :  
  
-   [À propos de la Capture de données modifiées ; SQL Server ;](../../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
-   [Sur le suivi des modifications ; SQL Server ;](../../../relational-databases/track-changes/about-change-tracking-sql-server.md)  
  
-   [Bases de données autonomes](../../../relational-databases/databases/contained-databases.md)  
  
-   [Chiffrement de base de données](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
-   [Instantanés de base de données](database-snapshots-with-always-on-availability-groups-sql-server.md)  
  
-   [FILESTREAM](../../../relational-databases/blob/filestream-sql-server.md)  
  
-   [FileTable](../../../relational-databases/blob/filetables-sql-server.md)  
  
-   [Envoi des journaux de transaction](../../log-shipping/about-log-shipping-sql-server.md)  
  
-   [Magasin d'objets blob distants (RBS)](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
-   [Réplication](../../install-windows/install-sql-server-replication.md)  
  
-   [Service Broker](../../configure-windows/sql-server-service-broker.md)  
  
-   [SQL Server Agent](../../../ssms/agent/sql-server-agent.md)  
  
-   [Reporting Services](reporting-services-with-always-on-availability-groups-sql-server.md)  
  
> [!WARNING]  
>  Pour plus d’informations sur les restrictions et limitations d’utilisation d’autres fonctionnalités avec [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consultez [groupes de disponibilité AlwaysOn : interopérabilité ; SQL Server ; ](always-on-availability-groups-interoperability-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Prise en main toujours sur les groupes de disponibilité ; SQL Server ;](getting-started-with-always-on-availability-groups-sql-server.md)  
  
##  <a name="RelatedContent"></a> Contenu associé  
  
-   **Blogs :**  
  
     [SQL Server Always On Blogs de l’équipe : Officiel SQL Server AlwaysOn Blog de l’équipe](http://blogs.msdn.com/b/sqlalwayson/)  
  
     [Blogs des ingénieurs du Service clientèle et du Support technique de SQL Server](http://blogs.msdn.com/b/psssql/)  
  
-   **Vidéos :**  
  
     [Microsoft SQL Server Code-Named "Denali" Always On Series,Part 1: Introducing the Next Generation High Availability Solution (Présentation de la solution haute disponibilité de nouvelle génération)](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server nom de code « Denali » Always On Series, Part 2 : Création d’une Solution de haute disponibilité critique à l’aide d’AlwaysOn](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Livres blancs :**  
  
     [Microsoft SQL Server Always On Solutions Guide for High Availability and Disaster Recovery (Guide de solutions Microsoft SQL Server Always On pour la haute disponibilité et la récupération d’urgence)](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité ; Always On SQL Server ;](overview-of-always-on-availability-groups-sql-server.md)   
 [Conditions préalables, Restrictions et recommandations pour les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Configuration d’une Instance de serveur pour toujours sur les groupes de disponibilité ; SQL Server ;](always-on-availability-groups-sql-server.md)   
 [Création et Configuration des groupes de disponibilité ; SQL Server ;](creation-and-configuration-of-availability-groups-sql-server.md)   
 [Administration d’un groupe de disponibilité ; SQL Server ;](administration-of-an-availability-group-sql-server.md)   
 [Surveillance des groupes de disponibilité &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [Vue d’ensemble des instructions Transact-SQL pour les groupes de disponibilité ; Always On SQL Server ;](transact-sql-statements-for-always-on-availability-groups.md)   
 [Vue d’ensemble des applets de commande PowerShell pour les groupes de disponibilité AlwaysOn ; SQL Server ;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
  
