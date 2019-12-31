---
title: Composants de Data Warehouse parallèles
description: Cet article explique le logiciel de l’appliance et les composants logiciels non-Appliance d’Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 5e609585e464cb52b996f45c7d8c57aaffcd79fe
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400933"
---
# <a name="parallel-data-warehouse-components---analytics-platform-system"></a>Composants de Data Warehouse parallèles-système de plateforme d’analyse
Cet article explique le logiciel de l’appliance et les composants logiciels non-Appliance d’Analytics Platform System.  
  
<!-- MISSING LINKS

To learn more about Analytics Platform System, see:  
  
-   [Analytics Platform System architecture](architecture-overview.md)  
  
-   [Distributed and Replicated Tables &#40;SQL Server PDW&#41;](../sqlpdw/distributed-and-replicated-tables-sql-server-pdw.md)  
  
-   [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  
  
-   [Clustered Columnstore Indexes &#40;SQL Server PDW&#41;](../sqlpdw/clustered-columnstore-indexes-sql-server-pdw.md)  
  
-   [Query Process &#40;SQL Server PDW&#41;](../sqlpdw/query-process-sql-server-pdw.md)  
  
-   [Minimum and Maximum Values &#40;SQL Server PDW&#41;](../sqlpdw/minimum-and-maximum-values-sql-server-pdw.md)  

-->
   
  
![Logiciel Data Warehouse parallèles](media/parallel-data-warehouse-software.png "Logiciel Data Warehouse parallèles")  
  
## <a name="sec1"></a>Logiciel d’appliance-traitement des requêtes et stockage des données utilisateur  
  
### <a name="control-node"></a>nœud de contrôle  
Moteur MPP  
Le moteur MPP est le cerveau du système de traitement massivement parallèle (MPP). Il effectue les opérations suivantes :  
  
-   Crée des plans de requête parallèles et coordonne l’exécution des requêtes parallèles sur les nœuds de calcul.  
  
-   Stocke et coordonne les métadonnées et les données de configuration pour toutes les bases de données.  
  
-   Gère SQL Server PDW l’authentification et l’autorisation de base de données.  
  
-   Effectue le suivi de l’état du matériel et des logiciels.  
  
### <a name="data-movement-service-dms"></a>Service de déplacement des données (DMS)  
Le service de déplacement des données (DMS) fait partie du « sauce secrète » des PDW. Il effectue les opérations suivantes :  
  
-   Transfère les données vers et depuis les nœuds de SQL Server PDW.  
  
-   Traite les opérations de requête qui nécessitent le transfert de données entre les nœuds.  
  
-   Améliore les performances des requêtes en optimisant les vitesses de transfert des données.  
  
### <a name="admin-console"></a>Console Administration  
La console d’administration est une application Web qui présente les informations relatives à l’État, à l’intégrité et aux performances de l’appliance.  
  
### <a name="configuration-manager"></a>Gestionnaire de configuration  
Le Configuration Manager (dwconfig. exe) est l’outil utilisé par les administrateurs d’appliance pour configurer Analytics Platform System.  
  
### <a name="control-node-databases"></a>Bases de données de nœuds de contrôle  
SQL Server gère toutes les bases de données sur le nœud de contrôle.  
  
-   La base de données Shell gère les métadonnées de toutes les bases de données utilisateur distribuées.  
  
-   TempDB contient les métadonnées de toutes les tables temporaires de l’utilisateur sur l’ensemble de l’appliance.  
  
-   Master est la table principale pour SQL Server sur le nœud de contrôle.  
  
### <a name="compute-node"></a>Nœud de calcul  
Les nœuds de calcul sont des unités de stockage et de traitement de données parallèles. Ils disposent d’un stockage en attachement direct et utilisent SQL Server pour gérer les données utilisateur.  
  
### <a name="data-movement-service-dms"></a>Service de déplacement des données (DMS)  
Le service de déplacement des données (DMS) s’exécute sur chaque nœud de calcul pour effectuer les opérations suivantes :  
  
-   Dans le cadre du traitement des requêtes parallèles, DMS transfère les données vers et à partir d’autres nœuds d’ordinateur et du nœud de contrôle.  
  
-   DMS, exécuté sur chaque nœud de calcul, reçoit les chargements de données en parallèle. Les données sont chargées en parallèle directement à partir du serveur de chargement vers les nœuds de calcul.  
  
-   DMS transfère les données de chaque nœud de calcul directement au serveur de sauvegarde.  
  
-   À l’aide de Polybase, DMS transfère des données vers et à partir d’un cluster Hadoop ou d’Azure Storage Blob externe.  
  
### <a name="compute-node-databases"></a>Bases de données de nœud de calcul 
Chaque nœud de calcul exécute une instance de SQL Server pour traiter les requêtes et gérer les données utilisateur.  
  
## <a name="appliance-fabric"></a>Infrastructure d’appliances  
La structure d’appliances fournit le système d’exploitation, les services et l’infrastructure réseau de l’appliance.  
  
### <a name="domain-controller"></a>Contrôleur de domaine  
Services de domaine Active Directory (AD)  
Analytics Platform System effectue l’authentification parmi les nœuds système de la plateforme d’analyse et gère l’authentification des SQL Server PDW les connexions d’authentification Windows.  
  
Service DNS  
Windows Domain Name Service (DNS) résout les noms de domaine en adresses IP pour l’appliance Analytics Platform System.  
  
### <a name="windows-deployment-service"></a>Service de déploiement Windows  
Le service de déploiement Windows (WDS) déploie le système d’exploitation Windows Server sur l’appliance. Elle est déployée sur chaque ordinateur hôte et machine virtuelle sur l’ensemble de l’appliance.  
  
Le service DHCP crée des adresses IP afin que les hôtes au sein du domaine de l’appliance puissent joindre le réseau de l’appliance sans disposer d’une adresse IP préconfigurée.  
  
### <a name="virtual-machine-manager"></a>Virtual Machine Manager  
Analytics Platform System utilise la virtualisation pour obtenir une haute disponibilité. Le Virtual Machine Manager héberge System Center pour déployer le système d’exploitation sur les hôtes physiques.  
  
Windows Server Update Services (WSUS) pour appliquer ou supprimer des mises à jour Windows sur tous les ordinateurs hôtes et machines virtuelles.  
  
### <a name="windows-server"></a>Windows Server  
Tous les ordinateurs hôtes et les ordinateurs virtuels de l’appliance exécutent le système d’exploitation Windows Server.  
  
### <a name="failover-clustering"></a>Clustering de basculement  
Le clustering de basculement Windows permet de redémarrer les processus sur un hôte passif en cas de défaillance d’un ordinateur hôte.  
  
### <a name="storage-spaces"></a>Espaces de stockage  
Les espaces de stockage Windows gèrent les données utilisateur en tant que pool de stockage pour un petit groupe de nœuds de calcul. En cas de défaillance d’un nœud de calcul, les données sont toujours accessibles via un autre nœud de calcul dans le groupe.  
  
### <a name="hyper-v"></a>Hyper-V  
Microsoft Hyper-V Server fournit une solution de virtualisation simple et fiable. Analytics Platform System utilise des virtualisations pour équilibrer les ressources du processeur et fournir une haute disponibilité pour les nœuds PDW et les composants d’infrastructure d’appareil.  
  
## <a name="sec2"></a>Données non relationnelles
La technologie Polybase intègre des données SQL Server PDW avec des données Hadoop externes. Les données Hadoop peuvent être stockées sur l’une de ces sources de données Hadoop :  
  
-   Distribution Hadoop Hortonworks  
  
-   Distribution Cloudera de Hadoop  
  
-   Données HDInsight stockées sur Azure Storage Blob  
  
## <a name="query-tools"></a>Outils de requête   
  
Les requêtes sont écrites avec\-Transact SQL modifié pour s’adapter à la nature MPP des requêtes. Toutes les requêtes sont envoyées au nœud de contrôle, qui génère un plan de requête parallèle pour exécuter la requête sur les nœuds de calcul.  
  
### <a name="sql-server-data-tools-ssdt"></a>Outils SQL Server Data Tools (SSDT)  
SQL Server Data Tools s’exécute dans Visual Studio et est notre outil GUI recommandé pour soumettre des requêtes à SQL Server PDW. Elle est similaire à SQL Server Management Studio en vous permettant de naviguer dans un Explorateur d’objets.  
  
Si vous ne disposez pas de Visual Studio, vous pouvez télécharger gratuitement les outils dont vous avez besoin. 
<!-- MISSING LINKS
For more information, see [Install SQL Server database tooling  for Visual Studio &#40;SQL Server PDW&#41;](../sqlpdw/install-sql-server-database-tooling-for-visual-studio-sql-server-pdw.md).  
-->
  
### <a name="sqlcmd-command-line-query-tool"></a>Outil de requête de ligne de commande sqlcmd  
sqlcmd est l’outil de ligne de commande SQL Server pour l'\-exécution d’instructions Transact SQL et de commandes système. Il fonctionne avec SQL Server PDW et est notre outil de ligne de commande recommandé pour l’interrogation des SQL Server PDW. Avec sqlcmd, vous pouvez exécuter\-des instructions Transact SQL de manière interactive à partir de la ligne de commande, d’un fichier de commandes ou de Windows PowerShell.  
  
<!-- MISSING LINKS

If you don't have SQL Server, you can download this as a standalone package. For more information, see [Install sqlcmd Command-Line Client &#40;SQL Server PDW&#41;](../sqlpdw/install-sqlcmd-command-line-client-sql-server-pdw.md) 
--> 
  
### <a name="integration-services"></a>Integration Services  
Vous pouvez utiliser Integration Services pour interroger des SQL Server PDW. 

<!-- MISSING LINKS
For more information, see [Connect With SQL Server Integration Services for Querying &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-integration-services-for-querying-sql-server-pdw.md). 

--> 
  
### <a name="linked-server"></a>Serveur lié  
En utilisant une connexion de serveur lié SQL Server, vous pouvez utiliser SQL Server pour envoyer\-des instructions Transact SQL à SQL Server PDW. 
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Linked Server &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-linked-server-sql-server-pdw.md). 
--> 
  
## <a name="business-intelligence-tools"></a>Outils décisionnels
  
### <a name="analysis-services"></a>Analysis Services  
SQL Server PDW est une source de données valide pour les bases de données Analysis Services et les modèles PowerPivot Excel. À l’aide du fournisseur OLE DB, vous pouvez configurer un cube Analysis Services pour utiliser le stockage de traitement analytique en ligne (MOLAP) multidimensionnel ou de traitement OLAP relationnel (ROLAP).  
  
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Analysis Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-analysis-services-sql-server-pdw.md).  

-->
  
### <a name="report-builder"></a>Générateur de rapports  
Vous pouvez utiliser SQL Server PDW comme source de données SQL Server pour les rapports que vous développez pour Reporting Services à l’aide de SQL Server Générateur de rapports. Vous pouvez également utiliser SQL Server PDW comme source de SQL Server pour les modèles de rapport. En utilisant Gestionnaire de rapports ou l’API du serveur de rapports, vous pouvez générer un modèle à partir d’une base de données SQL Server PDW.  
  
<!-- MISSING LINKS

For more information, see [Connect With SQL Server Report Builder &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-report-builder-sql-server-pdw.md) and [Connect With SQL Server Reporting Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-reporting-services-sql-server-pdw.md). 

--> 
  
### <a name="power-pivot-for-excel"></a>Power Pivot pour Excel  
Vous pouvez vous connecter à SQL Server PDW avec PowerPivot pour Excel, un téléchargement gratuit qui étend considérablement les fonctionnalités d’analyse des données d’Excel.  
  
<!-- MISSING LINKS

For more information, see [Connect With PowerPivot for Excel &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-powerpivot-for-excel-sql-server-pdw.md).  

-->
  
## <a name="loading-tools"></a>Chargement d’outils 
  
### <a name="integration-services"></a>Integration Services  
Installez des adaptateurs de destination PDW qui vous permettent d’utiliser les services SQL ServerIntegration pour charger des données dans SQL Server PDW.  

<!-- MISSING LINKS
For more information, see [Install Integration Services Destination Adapters &#40;SQL Server PDW&#41;](../sqlpdw/install-integration-services-destination-adapters-sql-server-pdw.md). 
--> 
  
### <a name="dwloader-command-line-loader"></a>Chargeur de ligne de commande dwloader  
dwloader est un outil de chargement de ligne de commande qui charge les données en parallèle de votre serveur de chargement vers les nœuds de calcul SQL Server PDW. 

<!-- MISSING LINKS
For more information, see [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](../sqlpdw/install-dwloader-command-line-loader-sql-server-pdw.md)  
-->
  
### <a name="polybase-for-hadoop-integration"></a>Polybase pour l’intégration de Hadoop  
Avec la technologie Polybase, vous pouvez charger des données non relationnelles à partir d’un cluster Hadoop dans une table relationnelle dans SQL Server PDW. Les données Hadoop peuvent se trouver dans un cluster Hadoop externe ou dans un Azure Storage Blob.  

<!-- MISSING LINKS
For more information, see [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md).
-->  
  
## <a name="database-backup-and-restore"></a>Sauvegarde et restauration de base de données  
SQL Server PDW utilise les commandes de sauvegarde et de restauration de base de données Transact-SQL pour sauvegarder et restaurer des bases de données utilisateur, en parallèle, vers et à partir d’un serveur de sauvegarde. SQL Server PDW écrit la sauvegarde dans un répertoire dans un partage de fichiers Windows, puis restaure les données à partir d’un partage de fichiers Windows.  
  
Pour plus d’informations, consultez la rubrique [planification de la sauvegarde et du chargement du matériel](backup-and-loading-hardware.md) , et [vue d’ensemble de la sauvegarde et de la restauration](backup-and-restore-overview.md)  
  
## <a name="remote-table-copy"></a>Copie de table distante  
La fonctionnalité de copie de table distante vous permet de copier des tables de SQL Server PDW bases de données vers des bases de données SMP à distance (sans Appliance) SQL Server. Cela permet d’activer les scénarios Hub et spoke pour SQL Server PDW.  
  
<!-- MISSING LINKS

For more information, see [Remote Table Copy &#40;SQL Server PDW&#41;](../sqlpdw/remote-table-copy-sql-server-pdw.md).  

-->
  
## <a name="monitoring"></a>Surveillance  
Analytics Platform System offre plusieurs moyens de surveiller l’activité de l’appliance.  
  
### <a name="admin-console"></a>Console Administration  
La console d’administration vous permet d’afficher l’état actuel de l’intégrité de l’appliance. Cela s’exécute en tant qu’application Web sur le nœud de contrôle et est accessible via HTTPS.  
  
Pour plus d’informations, consultez [surveiller l’appliance à l’aide de la console d’administration &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  

### <a name="system-views"></a>Vues système  
La console d’administration est basée sur les requêtes de vue système. Vous pouvez interroger les vues système individuellement pour obtenir les informations spécifiques dont vous avez besoin.  

Pour plus d’informations, consultez [surveiller l’appliance à l’aide des vues système &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md) 
  
### <a name="system-center-operations-manager"></a>System Center Operations Manager  
Il existe des packs d’administration System Center Operations Manager (SCOM) pour SQL Server PDW. 

Pour configurer l’appliance pour SCOM, consultez [surveiller l’appliance à l’aide de System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
