---
title: Parallèle des composants de l’entrepôt de données - Analytique Platform System | Microsoft Docs
description: Cet article explique le logiciel de l’appliance et les composants non-appliance logicielle du système de plateforme d’Analytique.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: aaf90124cc7877b633a997a2c4f170057b965028
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62639881"
---
# <a name="parallel-data-warehouse-components---analytics-platform-system"></a>Composants de l’entrepôt de données - Analytique Platform System en parallèle
Cet article explique le logiciel de l’appliance et les composants non-appliance logicielle du système de plateforme d’Analytique.  
  
<!-- MISSING LINKS

To learn more about Analytics Platform System, see:  
  
-   [Analytics Platform System architecture](architecture-overview.md)  
  
-   [Distributed and Replicated Tables &#40;SQL Server PDW&#41;](../sqlpdw/distributed-and-replicated-tables-sql-server-pdw.md)  
  
-   [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  
  
-   [Clustered Columnstore Indexes &#40;SQL Server PDW&#41;](../sqlpdw/clustered-columnstore-indexes-sql-server-pdw.md)  
  
-   [Query Process &#40;SQL Server PDW&#41;](../sqlpdw/query-process-sql-server-pdw.md)  
  
-   [Minimum and Maximum Values &#40;SQL Server PDW&#41;](../sqlpdw/minimum-and-maximum-values-sql-server-pdw.md)  

-->
   
  
![Logiciel de l’entrepôt de données en parallèle](media/parallel-data-warehouse-software.png "logiciel de Parallel Data Warehouse")  
  
## <a name="sec1"></a>Logiciel d’application - requête de traitement et stockage des données utilisateur  
  
### <a name="control-node"></a>Nœud de contrôle  
Moteur MPP  
Le moteur MPP est le cerveau du système de traitement massivement parallèle (MPP). Elle effectue les opérations suivantes :  
  
-   Crée des plans de requête parallèles et coordonne l’exécution de requêtes parallèles sur les nœuds de calcul.  
  
-   Stocke et coordonne les données de configuration et de métadonnées pour toutes les bases de données.  
  
-   Gère l’autorisation et l’authentification de base de données SQL Server PDW.  
  
-   Effectue le suivi d’état du matériel et logiciel.  
  
### <a name="data-movement-service-dms"></a>Service de déplacement de données (DMS)  
Service de déplacement des données (DMS) fait partie de le « ingrédient secret » de PDW. Elle effectue les opérations suivantes :  
  
-   Transfère les données vers et depuis les nœuds de SQL Server PDW.  
  
-   Processus des opérations nécessitant le transfert de données entre les nœuds de requête.  
  
-   Améliore les performances des requêtes en optimisant les vitesses de transfert de données.  
  
### <a name="admin-console"></a>Console Administration  
La Console d’administration est une application web qui présente l’état de l’appliance, intégrité et informations sur les performances.  
  
### <a name="configuration-manager"></a>Gestionnaire de configuration  
Le Gestionnaire de Configuration (dwconfig.exe), est l’outil que les administrateurs de matériel utilisent pour configurer le système de plateforme d’Analytique.  
  
### <a name="control-node-databases"></a>Bases de données de nœud contrôle  
SQL Server gère toutes les bases de données sur le nœud de contrôle.  
  
-   La base de données Shell gère les métadonnées pour toutes les bases de données utilisateur distribuée.  
  
-   TempDB contient les métadonnées pour toutes les tables temporaires utilisateur sur l’appliance.  
  
-   Maître est la table principale pour SQL Server sur le nœud de contrôle.  
  
### <a name="compute-node"></a>Nœud de calcul  
Les nœuds de calcul sont des unités de stockage et de traitement parallèle des données. Ils ont le stockage en attachement direct et que vous utilisent SQL Server pour gérer les données utilisateur.  
  
### <a name="data-movement-service-dms"></a>Service de déplacement de données (DMS)  
Service de déplacement des données (DMS) s’exécute sur chaque nœud de calcul pour effectuer les opérations suivantes :  
  
-   Dans le cadre du traitement de requêtes parallèles, DMS transférer des données vers et depuis d’autres nœuds de l’ordinateur et le nœud de contrôle.  
  
-   DMS, en cours d’exécution sur chaque nœud de calcul, reçoit les chargements de données en parallèle. Chargement des données en parallèle directement depuis le serveur de chargement pour les nœuds de calcul  
  
-   DMS transfère les données à partir de chaque nœud de calcul directement sur le serveur de sauvegarde.  
  
-   À l’aide de PolyBase, DMS transfère les données vers et depuis un cluster Hadoop externe ou le stockage Blob Azure.  
  
### <a name="compute-node-databases"></a>Bases de données de nœud de calcul 
Chaque nœud de calcul s’exécute une instance de SQL Server pour traiter les requêtes et de gérer les données utilisateur.  
  
## <a name="appliance-fabric"></a>Appliance Fabric  
L’infrastructure de l’appliance fournit le système d’exploitation, services et l’infrastructure de réseau pour l’appliance.  
  
### <a name="domain-controller"></a>Contrôleur de domaine  
Active Directory (AD) Domain Services (DS)  
Analytique Platform System effectue l’authentification entre les nœuds d’Analytique Platform System et gère l’authentification des connexions d’authentification Windows de SQL Server PDW.  
  
Service DNS  
Windows Service DNS (Domain Name) résout les noms de domaine en adresses IP pour l’appliance Analytique Platform System.  
  
### <a name="windows-deployment-service"></a>Service de déploiement Windows  
Service de déploiement Windows (WDS) déploie le système d’exploitation Windows Server sur l’appliance. Il est déployé sur chaque hôte et la machine virtuelle sur l’appliance.  
  
Le service DHCP crée des adresses IP afin que les hôtes au sein du domaine de l’appliance peuvent joindre le réseau de l’appliance sans avoir une adresse IP préconfigurée.  
  
### <a name="virtual-machine-manager"></a>Virtual Machine Manager  
Analytique Platform System utilise la virtualisation pour atteindre une haute disponibilité. Le Virtual Machine Manager héberge System Center pour déployer le système d’exploitation sur les hôtes physiques.  
  
Windows Server Update Services (WSUS) pour appliquer ou supprimer des mises à jour de Windows sur l’ensemble des hôtes et des machines virtuelles.  
  
### <a name="windows-server"></a>Windows Server  
Tous les hôtes et des machines virtuelles dans l’appliance exécutent le système d’exploitation Windows Server.  
  
### <a name="failover-clustering"></a>Clustering de basculement  
Le Clustering de basculement Windows fournit la possibilité de redémarrer les processus sur un ordinateur hôte passif dans le cas où un hôte échoue.  
  
### <a name="storage-spaces"></a>Espaces de stockage  
Espaces de stockage Windows gère les données de l’utilisateur en tant qu’un pool de stockage pour un petit groupe de nœuds de calcul. Si un nœud de calcul échoue, les données sont toujours accessibles via un autre nœud de calcul dans le groupe.  
  
### <a name="hyper-v"></a>Hyper-V  
Microsoft Hyper-V Server fournit une solution de virtualisation fiable et simple. Analytique Platform System utilise la virtualisation pour équilibrer les ressources processeur et offre une haute disponibilité pour les nœuds PDW appliance composants d’infrastructure.  
  
## <a name="sec2"></a>Données non relationnelles
La technologie PolyBase intègre les données de SQL Server PDW avec des données Hadoop externes. Les données de Hadoop peuvent être stockées sur une de ces sources de données Hadoop :  
  
-   Distribution Hadoop de Hortonworks  
  
-   Distribution de Cloudera Hadoop  
  
-   HDInsight les données stockées sur le stockage Blob Azure  
  
## <a name="query-tools"></a>Outils de requête   
  
Les requêtes sont écrites avec Transact\-SQL modifiés selon la nature MPP des requêtes. Toutes les requêtes sont envoyées au nœud de contrôle, ce qui génère un plan de requête parallèle pour exécuter la requête entre les nœuds de calcul.  
  
### <a name="sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT)  
SQL Server Data Tools exécute à l’intérieur de Visual Studio, notre outil GUI recommandé pour l’envoi de requêtes SQL Server PDW. Il est similaire à SQL Server Management Studio en vous permettant de naviguer dans un Explorateur d’objets.  
  
Si vous ne disposez pas de Visual Studio, vous pouvez télécharger les outils dont vous avez besoin gratuitement. 
<!-- MISSING LINKS
For more information, see [Install SQL Server database tooling  for Visual Studio &#40;SQL Server PDW&#41;](../sqlpdw/install-sql-server-database-tooling-for-visual-studio-sql-server-pdw.md).  
-->
  
### <a name="sqlcmd-command-line-query-tool"></a>Outil de requête de ligne de commande de SQLCMD  
SQLCMD est l’outil de ligne de commande de SQL Server pour l’exécution Transact\-SQL instructions et des commandes du système. Il fonctionne avec SQL Server PDW et notre outil de ligne de commande recommandée pour l’interrogation de SQL Server PDW. Avec sqlcmd, vous pouvez exécuter Transact\-instructions SQL interactivement à partir de la ligne de commande, comme un fichier de commandes, ou à partir de Windows PowerShell.  
  
<!-- MISSING LINKS

If you don't have SQL Server, you can download this as a standalone package. For more information, see [Install sqlcmd Command-Line Client &#40;SQL Server PDW&#41;](../sqlpdw/install-sqlcmd-command-line-client-sql-server-pdw.md) 
--> 
  
### <a name="integration-services"></a>Integration Services  
Vous pouvez utiliser les Services d’intégration à la requête SQL Server PDW. 

<!-- MISSING LINKS
For more information, see [Connect With SQL Server Integration Services for Querying &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-integration-services-for-querying-sql-server-pdw.md). 

--> 
  
### <a name="linked-server"></a>Serveur lié  
En utilisant une connexion de serveur lié SQL Server, vous pouvez utiliser SQL Server pour envoyer Transact\-des instructions SQL pour SQL Server PDW. 
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Linked Server &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-linked-server-sql-server-pdw.md). 
--> 
  
## <a name="business-intelligence-tools"></a>Outils d’analyse décisionnelle
  
### <a name="analysis-services"></a>Analysis Services  
SQL Server PDW est une source de données valide pour les modèles de PowerPivot pour Excel et les bases de données Analysis Services. Utilisez le fournisseur OLE DB, vous pouvez configurer un cube Analysis Services pour utiliser le traitement analytique en ligne multidimensionnel (MOLAP) ou stockage de traitement analytique en ligne relationnel (ROLAP).  
  
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Analysis Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-analysis-services-sql-server-pdw.md).  

-->
  
### <a name="report-builder"></a>Générateur de rapports  
Vous pouvez utiliser SQL Server PDW comme une source de données SQL Server pour les rapports que vous développez pour Reporting Services à l’aide du Générateur de rapports SQL Server. Vous pouvez également utiliser SQL Server PDW en tant que SQL Server source pour les modèles de rapport. En utilisant le Gestionnaire de rapports ou l’API du serveur de rapports, vous pouvez générer un modèle à partir d’une base de données SQL Server PDW.  
  
<!-- MISSING LINKS

For more information, see [Connect With SQL Server Report Builder &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-report-builder-sql-server-pdw.md) and [Connect With SQL Server Reporting Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-reporting-services-sql-server-pdw.md). 

--> 
  
### <a name="power-pivot-for-excel"></a>Power Pivot pour Excel  
Vous pouvez vous connecter à SQL Server PDW avec PowerPivot pour Excel, un téléchargement gratuit qui étend les fonctionnalités d’analyse de données d’Excel de manière significative.  
  
<!-- MISSING LINKS

For more information, see [Connect With PowerPivot for Excel &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-powerpivot-for-excel-sql-server-pdw.md).  

-->
  
## <a name="loading-tools"></a>Outils de chargement 
  
### <a name="integration-services"></a>Integration Services  
Installez les adaptateurs de destination PDW spécifiques qui vous permettent d’utiliser des Services de ServerIntegration SQL pour charger des données dans SQL Server PDW.  

<!-- MISSING LINKS
For more information, see [Install Integration Services Destination Adapters &#40;SQL Server PDW&#41;](../sqlpdw/install-integration-services-destination-adapters-sql-server-pdw.md). 
--> 
  
### <a name="dwloader-command-line-loader"></a>dwloader du chargeur de ligne de commande  
dwloader est un outil de ligne de commande de chargement qui charge des données en parallèle à partir de votre serveur de chargement pour les nœuds de calcul de SQL Server PDW. 

<!-- MISSING LINKS
For more information, see [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](../sqlpdw/install-dwloader-command-line-loader-sql-server-pdw.md)  
-->
  
### <a name="polybase-for-hadoop-integration"></a>PolyBase pour l’intégration de Hadoop  
Avec la technologie PolyBase, vous pouvez charger des données non relationnelles à partir d’un Hadoop Cluster dans une table relationnelle dans SQL Server PDW. Les données de Hadoop peuvent être situées dans un Hadoop Cluster externe ou dans un objet Blob de stockage Azure.  

<!-- MISSING LINKS
For more information, see [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md).
-->  
  
## <a name="database-backup-and-restore"></a>Sauvegarde de base de données et restauration  
SQL Server PDW utilise la sauvegarde de base de données Transact-SQL et restaurer les commandes de sauvegarde et de restauration des bases de données utilisateur, en parallèle, vers et depuis un serveur de sauvegarde. SQL Server PDW écrit la sauvegarde dans un répertoire dans un partage de fichiers Windows et même restaure ensuite les données à partir d’un partage de fichiers Windows.  
  
Pour plus d’informations, consultez [planifier pour la sauvegarde et de chargement de matériel](backup-and-loading-hardware.md) et [sauvegarde et restaurer une vue d’ensemble](backup-and-restore-overview.md)  
  
## <a name="remote-table-copy"></a>Copie de la Table distante  
La fonctionnalité de copie de la Table à distance vous permet de copier des tables de bases de données SQL Server PDW aux bases de données de SQL Server SMP (non-appliance) à distance. Cela permet des scénarios de hub- and -spoke pour SQL Server PDW.  
  
<!-- MISSING LINKS

For more information, see [Remote Table Copy &#40;SQL Server PDW&#41;](../sqlpdw/remote-table-copy-sql-server-pdw.md).  

-->
  
## <a name="monitoring"></a>Surveillance  
Analytique Platform System a plusieurs façons de surveiller l’activité de l’appliance  
  
### <a name="admin-console"></a>Console Administration  
La Console d’administration permet d’afficher l’état actuel sur l’intégrité de l’appliance. Il s’exécute comme une application web sur le nœud de contrôle et est accessible via le protocole https.  
  
Pour plus d’informations, consultez [surveiller l’Appliance à l’aide de la Console d’administration &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  

### <a name="system-views"></a>Vues système  
La Console d’administration est basée sur les requêtes de vue système. Vous pouvez interroger les vues système individuellement afin d’obtenir la partie spécifique des informations dont vous avez besoin.  

Pour plus d’informations, consultez [surveiller l’Appliance par à l’aide des vues système &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-system-views.md) 
  
### <a name="system-center-operations-manager"></a>System Center Operations Manager  
Il existe des packs d’administration de System Center Operations Manager (SCOM) pour SQL Server PDW. 

Pour configurer l’appliance pour SCOM, consultez [surveiller l’Appliance à l’aide de System Center Operations Manager &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
