---
title: "Fonctionnalit&#233;s prises en charge par les &#233;ditions de SQL Server 2016 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
keywords: 
  - "édition sql"
ms.assetid: 5da61ff5-12b9-48e6-b3c8-0dacca1751c4
caps.latest.revision: 175
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
---
# Fonctionnalit&#233;s prises en charge par les &#233;ditions de SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Cette rubrique fournit des détails sur les fonctionnalités prises en charge par les différentes éditions de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 La version d’évaluation de SQL Server est disponible pendant une période d’évaluation de 180 jours.  
  
 Pour obtenir les notes de publication les plus récentes et des informations sur les nouveautés, consultez les rubriques suivantes :
- [Notes de publication de SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
- [Nouveautés de SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)

    
 **Essayer SQL Server 2016**    
    
 > [![Télécharger à partir du Centre d’évaluation](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Télécharger SQL Server 2016 à partir du Centre d’évaluation](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
> ![Petite machine virtuelle Azure](../analysis-services/media/azure-virtual-machine-small.png) **[Faites tourner une machine virtuelle sur laquelle SQL Server 2016 est déjà installé](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)**    
    
  
 Pour les fonctionnalités prises en charge par les éditions Evaluation Edition et Developer Edition, consultez SQL Server Enterprise Edition.  
  
##  <a name="a-namecross-boxscalelimitsa-scale-limits"></a><a name="Cross-BoxScaleLimits"></a> Limites d’échelle  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|
|Capacité maximale de calcul utilisée par une instance unique - [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]<sup>1</sup>|Maximum du système d'exploitation|Limité à moins de 4 sockets ou 24 cœurs|Limité à moins de 4 sockets ou 16 cœurs|Limité à moins de 1 socket ou 4 cœurs|Limité à moins de 1 socket ou 4 cœurs| 
|Capacité maximale de calcul utilisée par une instance unique - [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|Maximum du système d'exploitation|Limité à moins de 4 sockets ou 24 cœurs|Limité à moins de 4 sockets ou 16 cœurs|Limité à moins de 1 socket ou 4 cœurs|Limité à moins de 1 socket ou 4 cœurs|  
|Mémoire maximale du pool de mémoires tampons par instance du [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|Maximum du système d’exploitation|128 Go|64 Go|1410 Mo|1410 Mo|
|Mémoire maximale du cache de segments columnstore par instance du [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|Mémoire illimitée| 32 Go<sup>2</sup>| 16 Go<sup>2</sup>| 352 Mo<sup>2</sup>| 352 Mo<sup>2</sup>|  
|Taille maximale des données optimisées en mémoire par base de données dans le [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|Mémoire illimitée| 32 Go<sup>2</sup>| 16 Go<sup>2</sup>| 352 Mo<sup>2</sup>| 352 Mo<sup>2</sup>|  
|Mémoire maximale utilisée par instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|Maximum du système d’exploitation|Tabulaire : 16 Go<br /><br /> MOLAP : 64 Go|Néant|Néant|Néant|  
|Mémoire maximale utilisée par instance de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|Maximum du système d’exploitation|64 Go|64 Go|4 Go|Néant|
|Taille maximale de la base de données relationnelle|524 Po|524 Po|524 Po|10 GB|10 GB|  
  
 1. L’édition Enterprise avec serveur + licences d’accès client (CAL) (non disponibles pour les nouveaux contrats) est limitée à un maximum de 20 cœurs par instance SQL Server. Il n'existe aucune limite dans le mode de licence Serveur selon le nombre de cœurs. Pour plus d’informations, voir [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
<sup>2</sup> S’applique à [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1. 

##  <a name="a-namerdbmshaa-rdbms-high-availability"></a><a name="RDBMSHA"></a> Haute disponibilité SGBDR  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Prise en charge de Server Core <sup>1</sup>|Oui|Oui|Oui|Oui|Oui|  
|Copie des journaux de transaction|Oui|Oui|Oui|Non|Non|  
|Mise en miroir de bases de données|Oui|Oui<br /><br /> Sécurité complète uniquement|Témoin uniquement|Témoin uniquement|Témoin uniquement| 
|Compression de sauvegarde|Oui|Oui|Non|Non|Non| 
|Instantané de base de données|Oui|Oui <sup>3</sup>|Oui <sup>3</sup>|Oui <sup>3</sup>|Oui <sup>3</sup>|
|Instances de cluster de basculement Always On|Oui<br /><br /> Le nombre de nœuds correspond au maximum du système d’exploitation|Oui<br /><br /> Prise en charge de 2 nœuds|Non|Non|Non|  
|Groupes de disponibilité Always On|Oui<br /><br /> Jusqu’à 8 réplicas secondaires, notamment 2 réplicas secondaires synchrones|Non|Non|Non|Non|
|Groupes de disponibilité de base <sup>2</sup>|Non|Oui<br /><br /> Prise en charge de 2 nœuds|Non|Non|Non|
|Directeur de connexion|Oui|Non|Non|Non|Non|
|Restauration en ligne de pages et de fichiers|Oui|Non|Non|Non|Non|
|Indexation en ligne|Oui|Non|Non|Non|Non|
|Modification de schéma en ligne|Oui|Non|Non|Non|Non|
|Récupération rapide|Oui|Non|Non|Non|Non|
|Sauvegardes en miroir|Oui|Non|Non|Non|Non|
|Ajout de mémoire et de processeur à chaud|Oui|Non|Non|Non|Non|
|Assistant de récupération de base de données|Oui|Oui|Oui|Oui|Oui|
|Sauvegarde chiffrée|Oui|Oui|Non|Non|Non|
|Sauvegarde hybride vers Windows Azure (sauvegarde vers une URL)|Oui|Oui|Non|Non|Non|  
  
 <sup>1</sup> Pour plus d’informations sur l’installation de SQL Server 2016 sur Server Core, consultez [Installer SQL Server 2016 sur Server Core](../database-engine/install-windows/install-sql-server-2016-on-server-core.md). 

<sup>2</sup> Pour plus d’informations sur les groupes de disponibilité de base, consultez [Groupes de disponibilité de base](../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md).  

<sup>3</sup> S’applique à [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1.
  
##  <a name="a-namerdbmsspa-rdbms-scalability-and-performance"></a><a name="RDBMSSP"></a> Extensibilité et performances SGBDR  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Columnstore <sup>1</sup>|Oui|Oui <sup>2</sup>|Oui <sup>2</sup>|Oui<sup>2</sup>|Oui<sup>2</sup>|  
|OLTP en mémoire <sup>1</sup>|Oui|Oui <sup>2</sup>|Oui <sup>2</sup>|Oui <sup>2</sup>, <sup>3</sup>|Oui <sup>2</sup>|
|Stretch Database|Oui|Oui|Oui|Oui|Oui|
|Mémoire principale persistante|Oui|Oui|Oui|Oui|Oui|
|Prise en charge de plusieurs instances|50|50|50|50|50|
|Partitionnement des tables et des index|Oui|Oui <sup>2</sup>|Oui <sup>2</sup>|Oui <sup>2</sup>|Oui <sup>2</sup>|  
|Compression des données|Oui|Oui <sup>2</sup>|Oui <sup>2</sup>|Oui <sup>2</sup>|Oui <sup>2</sup>|
|Resource Governor|Oui|Non|Non|Non|Non|  
|Parallélisme de tableau partitionné|Oui|Non|Non|Non|Non|
|Plusieurs conteneurs Filestream|Oui|Oui <sup>2</sup>|Oui <sup>2</sup>|Oui <sup>2</sup>|Oui <sup>2</sup>|
|Mémoire de pages de grande taille compatible NUMA et allocation de tableau de tampons|Oui|Non|Non|Non|Non|
|Extension du pool de mémoires tampons|Oui|Oui|Non|Non|Non|
|Gouvernance des ressources d'E/S|Oui|Non|Non|Non|Non|  
|Durabilité différée|Oui|Oui|Oui|Oui|Oui|

<sup>1</sup> La taille des données OLTP en mémoire et le cache de segments columnstore sont limités à la quantité de mémoire spécifiée par l’édition dans la section Limites d’échelle. Le Nombre maximal de degrés de parallélisme est limité. Le nombre de degrés de parallélisme maximal pour la création d’un index est limité à 2 pour l’Édition Standard et à 1 pour les éditions Web et Express. Cela fait référence aux index columnstore créés sur les tables basées sur des disques et les tables optimisées en mémoire.

<sup>2</sup> S’applique à [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1. 

<sup>3</sup> Cette fonctionnalité n’est pas incluse dans l’option d’installation LocalDB.
##  <a name="a-namerdbmssa-rdbms-security"></a><a name="RDBMSS"></a> Sécurité SGBDR  
  
|Fonctionnalité|Enterprise|Standard|Web|Express|Express with Advanced Services|  
|-------------|----------------|--------------|---------|-------------|------------------------------------| 
|Sécurité au niveau des lignes|Oui|Oui|Oui <sup>1</sup>|Oui <sup>1</sup>|Oui <sup>1</sup>|  
|Always Encrypted|Oui|Oui <sup>1</sup>|Oui <sup>1</sup>|Oui <sup>1</sup>|Oui <sup>1</sup>| 
|Masquage dynamique des données|Oui|Oui|Oui <sup>1</sup>|Oui <sup>1</sup>|Oui <sup>1</sup>|   
|Audit de base|Oui|Oui|Oui|Oui|Oui| 
|Audit de granularité fine|Oui|Oui <sup>1</sup>|Oui <sup>1</sup>|Oui <sup>1</sup>|Oui <sup>1</sup>| 
|Chiffrement transparent de base de données|Oui|Non|Non|Non|Non|   
|Gestion de clés extensible|Oui|Non|Non|Non|Non| 
|Rôles définis par l’utilisateur|Oui|Oui|Oui|Oui|Oui| 
|Bases de données à relation contenant-contenu|Oui|Oui|Oui|Oui|Oui| 
|Chiffrement des sauvegardes|Oui|Oui|Non|Non|Non|  

<sup>1</sup> S’applique à [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1.  
##  <a name="a-namereplicationa-replication"></a><a name="Replication"></a> Réplication  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Abonnés hétérogènes|Oui|Oui|Non|Non|Non|  
|Réplication de fusion|Oui|Oui|Oui (abonné uniquement)|Oui (abonné uniquement)|Oui (abonné uniquement)|   
|Publication Oracle|Oui|Non|Non|Non|Non| 
|Réplication transactionnelle d’égal à égal|Oui|Non|Non|Non|Non|   
|Réplication d'instantané|Oui|Oui|Oui (abonné uniquement)|Oui (abonné uniquement)|Oui (abonné uniquement)|   
|Suivi des modifications SQL Server|Oui|Oui|Oui|Oui|Oui| 
|Réplication transactionnelle|Oui|Oui|Oui (abonné uniquement)|Oui (abonné uniquement)|Oui (abonné uniquement)|   
|Réplication transactionnelle vers Azure|Oui|Oui|Oui|Non|Non|   
|Abonnement pouvant être mis à jour à la réplication transactionnelle|Oui|Non|Non|Non|Non|  
  
##  <a name="a-namessmsa-management-tools"></a><a name="SSMS"></a> Outils d’administration  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Objets de gestion SQL (SMO)|Oui|Oui|Oui|Oui|Oui|  
|Gestionnaire de configuration SQL|Oui|Oui|Oui|Oui|Oui|   
|SQL CMD (outil d'invite de commandes)|Oui|Oui|Oui|Oui|Oui|      
|Distributed Replay - Outil d’administration|Oui|Oui|Oui|Oui|Non|  
|Distribute Replay - Client|Oui|Oui|Oui|Non|Non|  
|Distributed Replay - Contrôleur|Oui (jusqu’à 16 clients)|Oui (1 client)|Oui (1 client)|Non|Non|   
|SQL Profiler|Oui|Oui|Non <sup>1</sup>|Non <sup>1</sup>|Non <sup>1</sup>|  
|Agent SQL Server|Oui|Oui|Oui|Non|Non| 
|Pack d'administration Microsoft System Center Operations Manager|Oui|Oui|Oui|Non|Non|  
|Assistant Paramétrage de base de données (DTA)|Oui|Oui <sup>2</sup>|Oui <sup>2</sup>|Non|Non|      
  
 <sup>1</sup> SQL Server Web, SQL Server Express, SQL Server Express with Tools et SQL Server Express with Advanced Services peuvent être profilés à l’aide de SQL Server Standard et SQL Server Enterprise.  
  
 <sup>2</sup> Paramétrage activé uniquement sur les fonctionnalités de l’édition Standard  
  
##  <a name="a-namerdbmsma-rdbms-manageability"></a><a name="RDBMSM"></a> Gestion de SGBDR  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Instances utilisateur|Non|Non|Non|Oui|Oui| 
|LocalDB|Non|Non|Non|Oui|Non| 
|Connexion administrateur dédiée|Oui|Oui|Oui|Oui avec indicateur de trace|Oui avec indicateur de trace|   
|Prise en charge de scripts PowerShell|Oui|Oui|Oui|Oui|Oui| 
|Prise en charge de SysPrep <sup>1</sup>|Oui|Oui|Oui|Oui|Oui| 
|Prise en charge des opérations de composant d’application de la couche Données (DAC): extraction, déploiement, mise à niveau, suppression|Oui|Oui|Oui|Oui|Oui| 
|Automation de stratégie (vérification selon la planification et sur modification)|Oui|Oui|Oui|Non|Non|   
|Collecteur de données de performances|Oui|Oui|Oui|Non|Non| 
|Possibilité d’inscription en tant qu’instance managée dans le cadre de la gestion de plusieurs instances|Oui|Oui|Oui|Non|Non|   
|Rapports de performances standard|Oui|Oui|Oui|Non|Non| 
|Repères de plan et gel de plan relatif|Oui|Oui|Oui|Non|Non|   
|Requête directe de vues d'index (à l'aide de l'indicateur NOEXPAND)|Oui|Oui|Oui|Oui|Oui| 
|Maintenance des vues indexées automatique|Oui|Oui|Oui|Non|Non| 
|Vues partitionnées distribuées|Oui|Non|Non|Non|Non| 
|Opérations d'index parallèles|Oui|Non|Non|Non|Non|  
|Utilisation automatique de vues indexées par l'optimiseur de requête|Oui|Non|Non|Non|Non| 
|Vérifications de cohérence parallèles|Oui|Non|Non|Non|Non| 
|Point de contrôle de l’utilitaire SQL Server|Oui|Non|Non|Non|Non|    
|Extension du pool de mémoires tampons|Oui|Oui|Non|Non|Non| 
  
 <sup>1</sup> Pour plus d’informations, consultez [Considérations relatives à l’installation de SQL Server à l’aide de SysPrep](../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md).  
 
<sup>2</sup> S’applique à [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1. 
  
##  <a name="a-namedevtoolsa-development-tools"></a><a name="DevTools"></a> Outils de développement  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Intégration de Microsoft Visual Studio|Oui|Oui|Oui|Oui|Oui| 
|Intellisense (Transact-SQL et MDX)|Oui|Oui|Oui|Oui|Oui| 
|Outils de données SQL Server (SSDT)|Oui|Oui|Oui|Oui|Non|    
|Outils de conception, de modification et de débogage MDX|Oui|Oui|Non|Non|Non|   
  
##  <a name="a-nameprogrammabilitya-programmability"></a><a name="Programmability"></a> Programmabilité  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Intégration R de base|Oui|Oui|Oui|Oui|Non|   
|Intégration R avancée|Oui|Non|Non|Non|Non| 
|R Server (Standalone)|Oui|Non|Non|Non|Non|   
|Nœud de calcul Polybase|Oui|Oui <sup>1</sup>|Oui <sup>1</sup>, <sup>2</sup>|Oui <sup>1</sup>, <sup>2</sup>|Oui <sup>1</sup>, <sup>2</sup>| 
|Nœud principal Polybase|Oui|Non|Non|Non|Non| 
|JSON|Oui|Oui|Oui|Oui|Oui|   
|Magasin de requêtes|Oui|Oui|Oui|Oui|Oui|   
|Temporal|Oui|Oui|Oui|Oui|Oui|   
|Intégration du CLR (Common Language Runtime)|Oui|Oui|Oui|Oui|Oui|   
|Prise en charge XML native|Oui|Oui|Oui|Oui|Oui| 
|Indexation XML|Oui|Oui|Oui|Oui|Oui| 
|Fonctions MERGE & UPSERT|Oui|Oui|Oui|Oui|Oui|   
|prise en charge de FILESTREAM|Oui|Oui|Oui|Oui|Oui| 
|FileTable|Oui|Oui|Oui|Oui|Oui| 
|Types de données de date et d'heure|Oui|Oui|Oui|Oui|Oui|  
|Support d'internationalisation|Oui|Oui|Oui|Oui|Oui| 
|Recherche sémantique et en texte intégral|Oui|Oui|Oui|Oui|Non| 
|Spécification d'une langue dans une requête|Oui|Oui|Oui|Oui|Non|   
|Service Broker (messagerie)|Oui|Oui|Non (client uniquement)|Non (client uniquement)|Non (client uniquement)|   
|Transact-SQL, points de terminaison|Oui|Oui|Oui|Non|Non| 

<sup>1</sup> La montée en puissance parallèle avec plusieurs nœuds de calcul nécessite un nœud principal.

<sup>2</sup> S’applique à [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1.
  
## <a name="a-nameisa-integration-services"></a><a name="IS"></a> Integration Services

Pour plus d’informations sur les fonctionnalités Integration Services (SSIS) prises en charge par les éditions de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], consultez [Fonctionnalités Integration Services prises en charge par les éditions de SQL Server 2016](Integration%20Services%20Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).

##  <a name="a-namemdsa-master-data-services"></a><a name="MDS"></a> Master Data Services  
 Pour plus d’informations sur les fonctionnalités [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] et Data Quality Services prises en charge par les éditions de [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], consultez [Master Data Services and Data Quality Services Features Supported by the Editions of SQL Server 2016](../master-data-services/master data services and data quality services features support.md) (Fonctionnalités Master Data Services et Data Quality Services prises en charge par les éditions de SQL Server 2016). 

  
##  <a name="a-namedwa-data-warehouse"></a><a name="DW"></a> Data Warehouse  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Création de cubes sans une base de données|Oui|Oui|Non|Non|Non |   
|Génération automatique de la mise en lots et du schéma d'entrepôt de données|Oui|Oui|Non|Non|Non| 
|Capture des données modifiées|Oui|Oui <sup>1</sup>|Oui <sup>1</sup>|Non|Non| 
|Optimisations de requêtes de jointure en étoile|Oui|Non|Non|Non|Non| 
|Configuration en lecture seule évolutive d'Analysis Services|Oui|Non|Non|Non|Non| 
|Traitement des requêtes parallèles sur les tables et les index partitionnés|Oui|Non|Non|Non|Non|   
|Agrégation globale des traitements|Oui|Non|Non|Non|Non| 

<sup>1</sup> S’applique à [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] SP1.  
##  <a name="a-namessasa-analysis-services"></a><a name="SSAS"></a> Analysis Services  
  
Pour plus d’informations sur les fonctionnalités Analysis Services prises en charge par les éditions de [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], consultez [Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md) (Fonctionnalités Analysis Services prises en charge par les éditions de SQL Server 2016). 
  
##  <a name="a-namebimda-bi-semantic-model-multi-dimensional"></a><a name="BIMD"></a> Modèle sémantique BI (multidimensionnel)  
  
Pour plus d’informations sur les fonctionnalités Analysis Services prises en charge par les éditions de [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], consultez [Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md) (Fonctionnalités Analysis Services prises en charge par les éditions de SQL Server 2016).
   
##  <a name="a-namebita-bi-semantic-model-tabular"></a><a name="BIT"></a> Modèle sémantique BI (tabulaire)  
  
Pour plus d’informations sur les fonctionnalités Analysis Services prises en charge par les éditions de [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], consultez [Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md) (Fonctionnalités Analysis Services prises en charge par les éditions de SQL Server 2016).
  
##  <a name="a-nameppspa-power-pivot-for-sharepoint"></a><a name="PPSP"></a> Power Pivot pour SharePoint  
  
Pour plus d’informations sur les fonctionnalités Power Pivot pour SharePoint prises en charge par les éditions de [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], consultez [Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md) (Fonctionnalités Analysis Services prises en charge par les éditions de SQL Server 2016).
  
##  <a name="a-namedma-data-mining"></a><a name="DM"></a> Exploration de données  
  
Pour plus d’informations sur les fonctionnalités d’exploration de données prises en charge par les éditions de [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], consultez [Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md) (Fonctionnalités Analysis Services prises en charge par les éditions de SQL Server 2016).
  
##  <a name="a-namessrsa-reporting-services"></a><a name="SSRS"></a> Reporting Services  
  
Pour plus d’informations sur les fonctionnalités Reporting Services prises en charge par les éditions de [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], consultez [Reporting Services Features Supported by the Editions of SQL Server 2016](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md) (Fonctionnalités Reporting Services prises en charge par les éditions de SQL Server 2016).

##  <a name="a-namebica-business-intelligence-clients"></a><a name="BIC"></a> Clients Business Intelligence  

Pour plus d’informations sur les fonctionnalités de client Business Intelligence prises en charge par les éditions de [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], consultez [Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md) (Fonctionnalités Analysis Services prises en charge par les éditions de SQL Server 2016) ou [Reporting Services Features Supported by the Editions of SQL Server 2016](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md) (Fonctionnalités Reporting Services prises en charge par les éditions de SQL Server 2016).
  
##  <a name="a-nameslsa-spatial-and-location-services"></a><a name="SLS"></a> Services d’emplacement et spatiaux  
  
|Nom de la fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|
|Index spatiaux|Oui|Oui|Oui|Oui|Oui|   
|Types de données planaires et géodésiques|Oui|Oui|Oui|Oui|Oui| 
|Bibliothèques spatiales avancées|Oui|Oui|Oui|Oui|Oui|   
|Importation/exportation de formats de données spatiales standard|Oui|Oui|Oui|Oui|Oui|   
  
##  <a name="a-nameadsa-additional-database-services"></a><a name="ADS"></a> Services de base de données supplémentaires  
  
|Nom de la fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------| 
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Assistant Migration|Oui|Oui|Oui|Oui|Oui|   
|Messagerie de base de données|Oui|Oui|Oui|Non|Non| 
  
##  <a name="a-nameothera-other-components"></a><a name="Other"></a> Autres composants  
  
|Nom de la fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------|  
|StreamInsight|StreamInsight Premium Edition|StreamInsight Standard Edition|StreamInsight Standard Edition|Non|Non| 
|StreamInsight HA|StreamInsight Premium Edition|Non|Non|Non|Non|   
  
> [![Télécharger SSMS](../analysis-services/media/download.png)](https://msdn.microsoft.com/library/mt238290.aspx) **[Télécharger la dernière version de SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx)**    
  
## <a name="see-also"></a>Voir aussi  
 [Spécifications de produit pour SQL Server 2016](../Topic/Product%20Specifications%20for%20SQL%20Server%202016.md)   
 [Installation de SQL Server 2016](../database-engine/install-windows/installation-for-sql-server-2016.md)  
  
  