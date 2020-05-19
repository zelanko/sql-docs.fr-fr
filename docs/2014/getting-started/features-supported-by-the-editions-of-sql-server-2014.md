---
title: Fonctionnalités prises en charge par les éditions de SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 5da61ff5-12b9-48e6-b3c8-0dacca1751c4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 118fe59e76f23089ce56371ea4ba981bb4ab1f7f
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706961"
---
# <a name="features-supported-by-the-editions-of-sql-server-2014"></a>Fonctionnalités prises en charge par les éditions de SQL Server 2014


  Cette rubrique fournit des détails sur les fonctionnalités prises en charge par les différentes éditions de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. 

 > **Remarque :** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est disponible dans une édition d’évaluation pour une période d’évaluation de 180 jours. Pour plus d’informations, consultez le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [de](https://go.microsoft.com/fwlink/?LinkId=190955).  
> 
> **Remarque :** Pour les fonctionnalités prises en charge par les éditions Evaluation et Developer, consultez l' [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ensemble des fonctionnalités d’entreprise.  
  
 Pour naviguer jusqu'à la table d'une technologie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , cliquez sur son lien :  
  
 [Limites d'échelle des solutions croisées](#CrossBoxScale)  
  
 [Haute disponibilité](#High_availability)  
  
 [Évolutivité et performances](#Scalability)  
  
 [Security](#Enterprise_security)  
  
 [Réplication](#Replication)  
  
 [Outils de gestion](#Mgmt_Tools)  
  
 [Facilité de gestion de SGBDR](#RDBMS_mgmt)  
  
 [Outils de développement](#Dev_tools)  
  
 [Programmabilité](#Programmability)  
  
 [Services d’intégration](#SSIS)  
  
 [Integration Services - Adaptateurs avancés](#SSIS_AA)  
  
 [Integration Services - Transformations avancées](#SSIS_AT)  
  
 [Master Data Services](#MDS)  
  
 [Data Warehouse](#Data_warehouse)  
  
 [Analysis Services](#SSAS)  
  
 [Modèle sémantique BI (multidimensionnel)](#BISemModel_multi)  
  
 [Modèle sémantique BI (tabulaire)](#BISemModel_tabular)  
  
 [PowerPivot pour SharePoint](#PowerPivot)  
  
 [Exploration de données](#DataMining)  
  
 [Reporting Services](#Reporting)  
  
 [Clients Business Intelligence](#BIClients)  
  
 [Services spatiaux et de localisation](#Spatial)  
  
 [Services de base de données supplémentaires](#Add_DBServices)  
  
 [Autres composants](#Other_Components)  
  
##  <a name="cross-box-scale-limits"></a><a name="CrossBoxScale"></a>Limites de l’échelle transversale  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Capacité maximale de calcul utilisée par une instance unique ( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] moteur de base de données)<sup>1</sup>|Maximum du système d'exploitation|Limité inférieure à 4 sockets ou 16 noyaux|Limité inférieure à 4 sockets ou 16 noyaux|Limité inférieure à 4 sockets ou 16 noyaux|Limité inférieure à 1 sockets ou 4 noyaux|Limité inférieure à 1 sockets ou 4 noyaux|Limité inférieure à 1 sockets ou 4 noyaux|  
|Capacité maximale de calcul utilisée par une instance unique (Analysis Services, Reporting Services) <sup>1</sup>|Maximum du système d'exploitation|Maximum du système d'exploitation|Limité inférieure à 4 sockets ou 16 noyaux|Limité inférieure à 4 sockets ou 16 noyaux|Limité inférieure à 1 sockets ou 4 noyaux|Limité inférieure à 1 sockets ou 4 noyaux|Limité inférieure à 1 sockets ou 4 noyaux|  
|Mémoire maximale utilisée (par instance du moteur de base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] )|Maximum du système d'exploitation|128 Go|128 Go|64 Go|1 Go|1 Go|1 Go|  
|Mémoire maximale utilisée (par instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)])|Maximum du système d'exploitation|Maximum du système d'exploitation|64 Go|N/A|N/A|N/A|N/A|  
|Mémoire maximale utilisée (par instance de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)])|Maximum du système d'exploitation|Maximum du système d'exploitation|64 Go|64 Go|4 Go|N/A|N/A|  
|Taille maximale de la base de données relationnelle|524 Po|524 Po|524 Po|524 Po|10 Go|10 Go|10 Go|  
  
 <sup>1</sup> Enterprise Edition avec serveur + licences d’accès client (CAL) (non disponibles pour les nouveaux contrats) est limitée à un maximum de 20 cœurs par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance. Il n'existe aucune limite dans le mode de licence Serveur selon le nombre de cœurs. Pour plus d’informations, voir [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
##  <a name="high-availability"></a><a name="High_availability"></a>Haute disponibilité  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Prise en charge de Server Core<sup>1</sup>|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Copie des journaux de transactions|Yes|Yes|Yes|Yes||||  
|Mise en miroir de bases de données|Yes|Oui (niveau complet sécurité uniquement)|Oui (niveau complet sécurité uniquement)|Témoin uniquement|Témoin uniquement|Témoin uniquement|Témoin uniquement|  
|Compression de sauvegarde|Yes|Yes|Yes|||||  
|Instantané de base de données|Yes|||||||  
|Instances de cluster de basculement AlwaysOn|Oui (prise en charge de nœud : maximum du système d'exploitation)|Oui (prise en charge de nœud : 2)|Oui (prise en charge de nœud : 2)|||||  
|Groupes de disponibilité AlwaysOn|Oui (jusqu'à 8 réplicas secondaires, notamment 2 réplicas secondaires synchrones)|||||||  
|Directeur de connexion|Yes|||||||  
|Restauration en ligne de pages et de fichiers|Yes|||||||  
|Indexation en ligne|Yes|||||||  
|Modification de schéma en ligne|Yes|||||||  
|Récupération rapide|Yes|||||||  
|Sauvegardes en miroir|Yes|||||||  
|Ajout de mémoire et de l’UC<sup>2</sup>|Yes|||||||  
|Assistant de récupération de base de données|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Sauvegarde chiffrée|Yes|Yes|Yes|||||  
|Sauvegarde intelligente|Yes|Yes|Yes|Non||||  
  
 <sup>1</sup> Pour plus d’informations sur l’installation [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] de sur Server Core, consultez [installer SQL Server 2014 sur Server Core](../database-engine/install-windows/install-sql-server-on-server-core.md).  
  
 <sup>2</sup> Cette fonctionnalité est disponible uniquement pour 64 bits [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
##  <a name="scalability-and-performance"></a><a name="Scalability"></a>Évolutivité et performances  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Prise en charge de plusieurs instances|50|50|50|50|50|50|50|  
|Partitionnement des tables et des index|Yes|||||||  
|Compression des données|Oui|||||||  
|gouverneur de ressources|Oui|||||||  
|Parallélisme de table de partition|Yes|||||||  
|Plusieurs conteneurs Filestream|Yes|||||||  
|Mémoire de pages de grande taille compatible NUMA et allocation de tableau de tampons|Yes|||||||  
|Extension du pool de mémoires tampons <sup>1</sup>|Yes|Yes|Yes|||||  
|Gouvernance des ressources d'E/S|Yes|||||||  
|OLTP en mémoire <sup>1</sup>|Yes|||||||  
|Durabilité différée|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
  
 <sup>1</sup> cette fonctionnalité est disponible uniquement pour 64 bits [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
##  <a name="security"></a><a name="Enterprise_security"></a> Sécurité  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Audit de base|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Audit de granularité fine|Yes|||||||  
|Chiffrement transparent de base de données|Oui|||||||  
|Gestion de clés extensible|Yes|||||||  
|Rôles définis par l'utilisateur|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Bases de données autonomes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Chiffrement des sauvegardes|Yes|Yes|Oui|||||  
  
##  <a name="replication"></a>Réplication<a name="Replication"></a>  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Suivi des modifications [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Réplication de fusion|Yes|Yes|Yes|Oui (abonné uniquement)|Oui (abonné uniquement)|Oui (abonné uniquement)|Oui (abonné uniquement)|  
|Réplication transactionnelle|Yes|Yes|Yes|Oui (abonné uniquement)|Oui (abonné uniquement)|Oui (abonné uniquement)|Oui (abonné uniquement)|  
|Réplication d'instantané|Yes|Yes|Yes|Oui (abonné uniquement)|Oui (abonné uniquement)|Oui (abonné uniquement)|Oui (abonné uniquement)|  
|Abonnés hétérogènes|Yes|Yes|Yes|||||  
|Publication Oracle|Yes|||||||  
|Réplication transactionnelle d'égal à égal|Yes|||||||  
  
##  <a name="management-tools"></a><a name="Mgmt_Tools"></a>Outils de gestion  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Objets de gestion SQL (SMO)|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Gestionnaire de configuration SQL|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|SQL CMD (outil d'invite de commandes)|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Studio|Yes|Yes|Yes|Yes|Yes|Yes||  
|Distributed Replay - Outil d’administration|Yes|Yes|Yes|Yes|Yes|Yes||  
|Distributed Replay - Client|Oui|Non|Oui|Yes||||  
|Distributed Replay - Contrôleur|Oui (Enterprise prend en charge jusqu'à 16 clients, Developer prend en charge uniquement 1 client)|No|Oui (prise en charge d'1 client uniquement)|Oui (prise en charge d'1 client uniquement)||||  
|SQL Profiler|Yes|Yes|Yes|Non <sup>2</sup>|Non <sup>2</sup>|Non <sup>2</sup>|Non <sup>2</sup>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent|Yes|Yes|Yes|Yes||||  
|Pack d'administration Microsoft System Center Operations Manager|Yes|Yes|Yes|Yes||||  
|Assistant Paramétrage de base de données (DTA)|Yes|Yes|Oui<sup>3</sup>|Oui<sup>3</sup>||||  
|Assistant déployer une [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] base de données sur une machine virtuelle Azure|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Fichiers de données dans Azure|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
  
 <sup>2</sup> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Web, [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] , [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Tools et [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services peuvent être profilés à l’aide des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] éditions standard et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise.  
  
 <sup>3</sup> paramétrage activé uniquement sur les fonctionnalités d’édition standard.  
  
##  <a name="rdbms-manageability"></a><a name="RDBMS_mgmt"></a>Facilité de gestion de SGBDR  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Instances utilisateur|||||Yes|Yes|Yes|  
|LocalDB|||||Yes|Yes||  
|Connexion administrateur dédiée|Yes|Yes|Yes|Yes|Oui (sous indicateur de trace)|Oui (sous indicateur de trace)|Oui (sous indicateur de trace)|  
|Prise en charge de scripts PowerShell|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Prise en charge de SysPrep<sup>1</sup>|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Prise en charge des opérations de composant d’application de la couche données-extraction, déploiement, mise à niveau, suppression|Yes|Yes|Yes|Yes|Yes|Yes|Oui|  
|Automation de stratégie (vérification selon la planification et sur modification)|Yes|Yes|Yes|Yes||||  
|Collecteur de données de performances|Yes|Yes|Yes|Yes||||  
|Possibilité d'inscription en tant qu'instance managée dans le cadre de la gestion de plusieurs instances|Yes|Yes|Yes|Yes||||  
|Rapports de performances standard|Yes|Yes|Yes|Yes||||  
|Repères de plan et gel de plan relatif|Yes|Yes|Yes|Yes||||  
|Requête directe de vues d'index (à l'aide de l'indicateur NOEXPAND)|Yes|Yes|Yes|Yes||||  
|Maintenance de vue indexée automatique|Yes|Yes|Yes|Yes||||  
|Vues partitionnées distribuées|Oui|Partial. Les vues partitionnées distribuées ne peuvent pas être mises à jour|Partial. Les vues partitionnées distribuées ne peuvent pas être mises à jour|Partial. Les vues partitionnées distribuées ne peuvent pas être mises à jour|Partial. Les vues partitionnées distribuées ne peuvent pas être mises à jour|Partial. Les vues partitionnées distribuées ne peuvent pas être mises à jour|Partial. Les vues partitionnées distribuées ne peuvent pas être mises à jour|  
|Opérations d'index parallèles|Yes|||||||  
|Utilisation automatique de vues indexées par l'optimiseur de requête|Yes|||||||  
|Vérifications de cohérence parallèles|Yes|||||||  
|Point de contrôle de l'utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Yes|||||||  
|Bases de données autonomes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Extension du pool de mémoires tampons<sup>2</sup>|Yes|Yes|Yes|||||  
  
 <sup>1</sup> pour plus d’informations, consultez [considérations relatives à l’installation de SQL Server à l’aide de Sysprep](../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md).  
  
 <sup>2</sup> cette fonctionnalité est disponible uniquement pour 64 bits [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
##  <a name="development-tools"></a><a name="Dev_tools"></a>Outils de développement  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Intégration à [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Intellisense ([!INCLUDE[tsql](../includes/tsql-md.md)] et MDX)|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]|Yes|Yes|Yes|Yes|Yes|||  
|Outils de conception et de modification de requêtes SQL<sup>1</sup>|Yes|Yes|Yes|||||  
|Prise en charge du contrôle de version<sup>1</sup>|Yes|Yes|Yes|||||  
|Outils de modification, de débogage et de conception MDX<sup>1</sup>|Yes|Yes|Yes|||||  
  
 <sup>1</sup> cette fonctionnalité n’est pas disponible pour la version 64 bits de l’édition standard.  
  
##  <a name="programmability"></a><a name="Programmability"></a> Programmability  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Intégration du CLR (Common Language Runtime)|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Prise en charge XML native|Yes|Yes|Yes|Yes|Yes|Yes|Oui|  
|Indexation XML|Oui|Yes|Yes|Yes|Yes|Yes|Yes|  
|FUSIONNer les fonctionnalités de UPSERT &|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|prise en charge de FILESTREAM|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|FileTable|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Types de données de date et d'heure|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Support d'internationalisation|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Recherche sémantique et en texte intégral|Yes|Yes|Yes|Yes|Yes|||  
|Spécification d'une langue dans une requête|Yes|Yes|Yes|Yes|Yes|||  
|Service Broker (messagerie)|Oui|Yes|Oui|Non (client uniquement)|Non (client uniquement)|Non (client uniquement)|Non (client uniquement)|  
|Points de terminaison [!INCLUDE[tsql](../includes/tsql-md.md)]|Yes|Yes|Yes|Yes||||  
  
##  <a name="integration-services"></a><a name="SSIS"></a> Integration Services  
  
|Fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|-------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Assistant Importation et Exportation|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Connecteurs de source de données intégrés|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Concepteur et exécution SSIS|Yes|Yes|Yes|||||  
|Transformations de base|Yes|Yes|Yes|||||  
|Outils de profilage de données de base|Yes|Yes|Yes|||||  
|Service de capture de données modifiées pour Oracle par Attunity|Yes|||||||  
|Concepteur de capture de données modifiées pour Oracle par Attunity|Yes|||||||  
  
###  <a name="integration-services---advanced-adapters"></a><a name="SSIS_AA"></a>Integration Services-adaptateurs avancés  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Destination Oracle de haute performance|Yes|||||||  
|Destination Teradata de haute performance|Yes|||||||  
|Source et destination SAP BW|Yes|||||||  
|Adaptateur de destination d'apprentissage du modèle d'exploration de données|Yes|||||||  
|Adaptateur de destination de traitement de dimension|Yes|||||||  
|Adaptateur de destination de traitement de partition|Yes|||||||  
|Composants de capture de données modifiées par Attunity|Yes|||||||  
|Connecteur pour Open Database Connectivity (ODBC) par Attunity|Yes|||||||  
  
###  <a name="integration-services---advanced-transforms"></a><a name="SSIS_AT"></a>Integration Services-transformations avancées  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Recherches de persistance (haute performance)|Yes|||||||  
|Transformation de requête d'exploration de données|Yes|||||||  
|Transformations de recherche floue et de regroupement probable|Yes|||||||  
|Extractions de termes et transformations de recherche|Yes|||||||  
  
##  <a name="master-data-services"></a><a name="MDS"></a>Master Data Services  
  
> [!NOTE]  
>  -   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] est disponible uniquement sur les éditions 64 bits de Business Intelligence et Enterprise uniquement.  
  
|Fonctionnalité|Enterprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|-------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] base de données|Oui|Oui||||||  
|Application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]|Oui|Oui||||||  
  
##  <a name="data-warehouse"></a><a name="Data_warehouse"></a>Data Warehouse  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Création de cubes sans une base de données|Oui|Oui|Oui|||||  
|Génération automatique de la mise en lots et du schéma d'entrepôt de données|Oui|Oui|Oui|||||  
|Capture des données modifiées|Yes|||||||  
|Optimisations de requêtes de jointure en étoile|Yes|||||||  
|Configuration en lecture seule évolutive d'Analysis Services|Yes|||||||  
|Traitement des requêtes parallèles sur les tables et les index partitionnés|Yes|||||||  
|Index columnstore optimisés en mémoire xVelocity|Yes|||||||  
|Agrégation globale des traitements|Yes|||||||  
  
##  <a name="analysis-services"></a><a name="SSAS"></a>Analysis Services  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Bases de données partagées évolutives (attacher ou détacher les bases de données, bases de données en lecture seule)|Oui|Oui||||||  
|Sauvegarder/Restaurer, attacher/détacher des bases de données|Oui|Oui|Oui|||||  
|Synchroniser des bases de données|Oui|Oui||||||  
|Haute disponibilité|Oui|Oui|Oui|||||  
|Programmabilité (AMO, ADOMD.Net, OLEDB, XML/A, ASSL)|Oui|Oui|Oui|||||  
  
###  <a name="bi-semantic-model-multidimensional"></a><a name="BISemModel_multi"></a>Modèle sémantique BI (multidimensionnel)  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Mesures semi-additives|Oui|Oui|Non<sup>1</sup>|||||  
|Hierarchies|Oui|Oui|Oui|||||  
|Indicateurs de performance clés|Oui|Oui|Oui|||||  
|perspectives|Oui|Oui||||||  
|Actions|Oui|Oui|Oui|||||  
|Intelligence comptable|Oui|Oui|Oui|||||  
|Time Intelligence|Oui|Oui|Oui|||||  
|Cumuls personnalisés|Oui|Oui|Oui|||||  
|Cube d'écriture différée|Oui|Oui|Oui|||||  
|Dimensions d'écriture différée|Oui|Oui||||||  
|Cellules d'écriture différée|Oui|Oui|Oui|||||  
|Extraction|Oui|Oui|Oui|||||  
|Types de hiérarchies avancées (hiérarchies parent-enfant et déséquilibrées)|Oui|Oui|Oui|||||  
|Dimensions avancées (dimensions de référence, plusieurs-à-plusieurs)|Oui|Oui|Oui|||||  
|Dimensions et mesures liées|Oui|Oui||||||  
|Translations|Oui|Oui|Oui|||||  
|Agrégations|Oui|Oui|Oui|||||  
|Partitions multiples|Oui|Oui|Oui, jusqu'à 3|||||  
|Mise en cache proactive|Oui|Oui||||||  
|Assemblys personnalisés (procédures stockées)|Oui|Oui|Oui|||||  
|Requêtes et scripts MDX|Oui|Oui|Oui|||||  
|Requêtes DAX|Oui|Oui||||||  
|Modèle de sécurité basé sur les rôles|Oui|Oui|Oui|||||  
|Sécurité au niveau de la dimension et de la cellule|Oui|Oui|Oui|||||  
|Stockage évolutif de chaîne|Oui|Oui|Oui|||||  
|Modes de stockage MOLAP, ROLAP, HOLAP|Oui|Oui|Oui|||||  
|Transport XML binaire et compressé|Oui|Oui|Oui|||||  
|Traitement de type envoi de données (push)|Oui|Oui||||||  
|Écriture différée directe|Oui|Oui||||||  
|Expressions de mesure|Oui|Oui||||||  
  
 <sup>1</sup> La mesure semi-additive LastChild est prise en charge dans l’édition standard, mais les autres mesures semi-additives, telles que None, FirstChild, FirstNonEmpty, LastNonEmpty, AverageOfChildren et ByAccount, ne le sont pas. Les mesures additives, telles que Sum, Count, Min, Max, et les mesures non additives (DistinctCount) sont prises en charge dans toutes les éditions.  
  
###  <a name="bi-semantic-model-tabular"></a><a name="BISemModel_tabular"></a>Modèle sémantique BI (tabulaire)  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Hierarchies|Oui|Oui||||||  
|Indicateurs de performance clés|Oui|Oui||||||  
|perspectives|Oui|Oui||||||  
|Translations|Oui|Oui||||||  
|Calculs DAX, requêtes DAX, requêtes MDX|Oui|Oui||||||  
|Sécurité de niveau ligne|Oui|Oui||||||  
|Partitions|Oui|Oui||||||  
|Modes de stockage In-Memory et DirectQuery (tabulaires uniquement)|Oui|Oui||||||  
  
###  <a name="powerpivot-for-sharepoint"></a><a name="PowerPivot"></a> PowerPivot pour SharePoint  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Intégration de batterie de serveurs SharePoint selon l'architecture de service partagé|Oui|Oui||||||  
|Rapports d’utilisation|Oui|Oui||||||  
|Règles de contrôle d'intégrité|Oui|Oui||||||  
|Galerie PowerPivot|Oui|Oui||||||  
|Actualisation des données PowerPivot|Oui|Oui||||||  
|Flux de données PowerPivot|Oui|Oui||||||  
  
###  <a name="data-mining"></a><a name="DataMining"></a>Exploration de données  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Algorithmes standard|Oui|Oui|Oui|||||  
|Outils d'exploration de données (Assistants, éditeurs, générateurs de requêtes)|Oui|Oui|Oui|||||  
|validation croisée|Oui|Oui||||||  
|Modèles sur les sous-ensembles filtrés de données de structure d'exploration de données|Oui|Oui||||||  
|Série chronologique : fusion personnalisée entre les méthodes ARTXP et ARIMA|Oui|Oui||||||  
|Série chronologique : prédiction avec les nouvelles données|Oui|Oui||||||  
|Requêtes d'exploration de données simultanées illimitées|Oui|Oui||||||  
|Configuration avancée & options de paramétrage pour les algorithmes d’exploration de données|Oui|Oui||||||  
|Prise en charge des algorithmes de plug-in|Oui|Oui||||||  
|Traitement de modèle parallèle|Oui|Oui||||||  
|Série chronologique : prédiction inter-série|Oui|Oui||||||  
|Attributs illimités pour les règles d'association|Oui|Oui||||||  
|Prédiction de séquence|Oui|Oui||||||  
|Plusieurs cibles de prédiction pour naïve Bayes, réseau neuronal et régression logistique|Oui|Oui||||||  
  
##  <a name="reporting-services"></a><a name="Reporting"></a>Reporting Services  
  
###  <a name="reporting-services-features"></a><a name="Reporting_features"></a>Fonctionnalités de Reporting Services  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Édition [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prise en charge pour la base de données du catalogue|Standard ou supérieur|Standard ou supérieur|Standard ou supérieur|Web|Express|||  
|Sources de données prises en charge par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Toutes les éditions   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Toutes les éditions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Toutes les éditions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Web|Express|||  
|Serveur de rapports|Oui|Oui|Oui|Oui|Oui|||  
|Concepteur de rapports|Oui|Oui|Oui|Oui|Oui|||  
|Gestionnaire de rapports|Oui|Oui|Oui|Oui|Oui|||  
|Sécurité basée sur les rôles|Oui|Oui|Oui|Oui|Oui|||  
|Exportation Word et prise en charge de texte enrichi|Oui|Oui|Oui|Oui|Oui|||  
|Jauges et graphiques améliorés|Oui|Oui|Oui|Oui|Oui|||  
|Exporter vers Excel, PDF et images|Oui|Oui|Oui|Oui|Oui|||  
|Authentification personnalisée|Oui|Oui|Oui|Oui|Oui|||  
|Rapport en tant que flux de données|Oui|Oui|Oui|Oui|Oui|||  
|Prise en charge des modèles|Oui|Oui|Oui|Oui||||  
|Créer des rôles personnalisés pour la sécurité basée sur les rôles|Oui|Oui|Oui|||||  
|Sécurité de l'élément de modèle|Oui|Oui|Oui|||||  
|Rapport généré interactif infini|Oui|Oui|Oui|||||  
|Bibliothèque de composants partagés|Oui|Oui|Oui|||||  
|Abonnements et planifications par partage de fichiers et messagerie électronique|Oui|Oui|Oui|||||  
|Historique de rapport, exécution d'instantanés et mise en cache|Oui|Oui|Oui|||||  
|Intégration SharePoint|Oui|Oui|Oui|||||  
|Prise en charge de sources de données distantes et non-SQL<sup>1</sup>|Oui|Oui|Oui|||||  
|Source de données, remise et rendu, extensibilité RDCE|Oui|Oui|Oui|||||  
|Abonnement aux rapports pilotés par les données|Oui|Oui||||||  
|Déploiement avec montée en puissance parallèle (batteries de serveurs Web)|Oui|Oui||||||  
|Alerte<sup>2</sup>|Oui|Oui||||||  
|[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)]<sup>2</sup>|Oui|Oui||||||  
  
 <sup>1</sup> Pour plus d’informations sur les sources de données prises en charge dans [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] , consultez [sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
 <sup>2</sup> Requiert [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode SharePoint. Pour plus d’informations, consultez [Reporting Services installation en mode sharepoint &#40;sharepoint 2010 et sharepoint 2013&#41;](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
### <a name="report-server-database-server-edition-requirements"></a>Conditions requises pour l'édition SQL Server de la base de données du serveur de rapports  
 Lors de la création d'une base de données de serveur de rapports, toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne peuvent pas être utilisées pour héberger la base de données. Le tableau suivant répertorie les éditions du [!INCLUDE[ssDE](../includes/ssde-md.md)] que vous pouvez utiliser pour les éditions spécifiques de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
|Pour cette édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services|Utilisez cette édition de l'instance du moteur de base de données pour héberger la base de données|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Enterprise|Éditions Standard, Business Intelligence, Enterprise (locales ou distantes)|  
|Business Intelligence|Éditions Standard, Business Intelligence, Enterprise (locales ou distantes)|  
|standard|Éditions Standard, Enterprise (locales ou distantes)|  
|Web|Web Edition (locale uniquement)|  
|Express with Advanced Services|Express with Advanced Services (local uniquement).|  
|Évaluation|Évaluation|  
  
##  <a name="business-intelligence-clients"></a><a name="BIClients"></a>Clients Business Intelligence  
 Les applications logicielles clientes suivantes sont disponibles dans le Centre de téléchargement Microsoft ; elles ont pour but de vous aider à créer des documents décisionnels qui s'exécutent sur une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Lorsque vous hébergez ces documents dans un environnement serveur, utilisez une édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prise en charge pour ce type de document. Le tableau suivant identifie quelle édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contient les fonctionnalités de serveur obligatoires pour héberger les documents créés dans ces applications clientes.  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)]|Yes|Yes|Yes|||||  
|Compléments d'exploration de données pour Excel et Visio 2010|Yes|Yes|Yes|||||  
|[!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] 2010|Yes|Yes||||||  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]|Yes|Yes||||||  
  
> [!NOTE]
>  1.  [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)]est un complément Excel et ne dépend pas de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Toutefois [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] est requis pour partager les classeurs [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] dans SharePoint et y collaborer ; cette fonction est disponible dans le cadre des éditions Enterprise et Business Intelligence de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
> 2.  Le tableau ci-dessus identifie les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requises pour activer ces outils clients ; toutefois, ces fonctionnalités peuvent accéder aux données hébergées sur n'importe quelle édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
##  <a name="spatial-and-location-services"></a><a name="Spatial"></a>Services spatiaux et de localisation  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Index spatiaux|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Types de données planaires et géodésiques|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Bibliothèques spatiales avancées|Yes|Yes|Yes|Yes|Yes|Yes|Oui|  
|Importation/exportation de formats de données spatiales standard|Oui|Yes|Yes|Yes|Yes|Yes|Yes|  
  
##  <a name="additional-database-services"></a><a name="Add_DBServices"></a>Services de base de données supplémentaires  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Assistant Migration|Yes|Yes|Yes|Yes|Yes|Yes|Yes|  
|Messagerie de base de données|Yes|Yes|Yes|Yes||||  
  
##  <a name="other-components"></a><a name="Other_Components"></a>Autres composants  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Data Quality Services|Oui|Oui||||||  
|StreamInsight|StreamInsight Premium Edition|StreamInsight Standard Edition|StreamInsight Standard Edition|StreamInsight Standard Edition||||  
|StreamInsight HA|StreamInsight Premium Edition|||||||  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifications de produit pour SQL Server 2014](../../2014/getting-started/sql-server-2014-product-specifications.md)   
 [Installation pour SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md)   
 [Installation de démarrage rapide de SQL Server 2014](../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)  
  
  
