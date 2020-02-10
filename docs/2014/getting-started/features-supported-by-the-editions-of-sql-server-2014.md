---
title: Fonctionnalités prises en charge par les éditions de SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 5da61ff5-12b9-48e6-b3c8-0dacca1751c4
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: caae4212e2182ae6afde29b0fed1aaee4f05645a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70176126"
---
# <a name="features-supported-by-the-editions-of-sql-server-2014"></a>Fonctionnalités prises en charge par les éditions de SQL Server 2014


  Cette rubrique fournit des détails sur les fonctionnalités prises en charge par les différentes éditions de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. 

 > **Remarque :** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est disponible dans une édition d’évaluation pour une période d’évaluation de 180 jours. Pour plus d’informations, consultez le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [de](https://go.microsoft.com/fwlink/?LinkId=190955).  
> 
> **Remarque :** Pour les fonctionnalités prises en charge par les éditions Evaluation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et Developer, consultez l’ensemble des fonctionnalités d’entreprise.  
  
 Pour naviguer jusqu'à la table d'une technologie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , cliquez sur son lien :  
  
 [Limites de l’échelle transversale](#CrossBoxScale)  
  
 [Haute disponibilité](#High_availability)  
  
 [Extensibilité et performance](#Scalability)  
  
 [Sécurité](#Enterprise_security)  
  
 [Réplication](#Replication)  
  
 [Outils de gestion](#Mgmt_Tools)  
  
 [Facilité de gestion de SGBDR](#RDBMS_mgmt)  
  
 [Outils de développement](#Dev_tools)  
  
 [Programmabilité](#Programmability)  
  
 [Integration Services](#SSIS)  
  
 [Integration Services - Adaptateurs avancés](#SSIS_AA)  
  
 [Integration Services - Transformations avancées](#SSIS_AT)  
  
 [Master Data Services](#MDS)  
  
 [entrepôt de données](#Data_warehouse)  
  
 [Analysis Services](#SSAS)  
  
 [Modèle sémantique BI (multidimensionnel)](#BISemModel_multi)  
  
 [Modèle sémantique BI (tabulaire)](#BISemModel_tabular)  
  
 [PowerPivot pour SharePoint](#PowerPivot)  
  
 [Exploration de données](#DataMining)  
  
 [Reporting Services](#Reporting)  
  
 [Clients Business Intelligence](#BIClients)  
  
 [Services spatiaux et de localisation](#Spatial)  
  
 [Services de base de données supplémentaires](#Add_DBServices)  
  
 [Autres composants](#Other_Components)  
  
##  <a name="CrossBoxScale"></a>Limites de l’échelle transversale  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Capacité maximale de calcul utilisée par une instance unique ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] moteur de base de données)<sup>1</sup>|Maximum du système d'exploitation|Limité inférieure à 4 sockets ou 16 noyaux|Limité inférieure à 4 sockets ou 16 noyaux|Limité inférieure à 4 sockets ou 16 noyaux|Limité inférieure à 1 sockets ou 4 noyaux|Limité inférieure à 1 sockets ou 4 noyaux|Limité inférieure à 1 sockets ou 4 noyaux|  
|Capacité maximale de calcul utilisée par une instance unique (Analysis Services, Reporting Services) <sup>1</sup>|Maximum du système d'exploitation|Maximum du système d'exploitation|Limité inférieure à 4 sockets ou 16 noyaux|Limité inférieure à 4 sockets ou 16 noyaux|Limité inférieure à 1 sockets ou 4 noyaux|Limité inférieure à 1 sockets ou 4 noyaux|Limité inférieure à 1 sockets ou 4 noyaux|  
|Mémoire maximale utilisée (par instance du moteur de base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] )|Maximum du système d'exploitation|128 Go|128 Go|64 Go|1 Go|1 Go|1 Go|  
|Mémoire maximale utilisée (par instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)])|Maximum du système d'exploitation|Maximum du système d'exploitation|64 Go|N/A|N/A|N/A|N/A|  
|Mémoire maximale utilisée (par instance de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)])|Maximum du système d'exploitation|Maximum du système d'exploitation|64 Go|64 Go|4 Go|N/A|N/A|  
|Taille maximale de la base de données relationnelle|524 Po|524 Po|524 Po|524 Po|10 Go|10 Go|10 Go|  
  
 <sup>1</sup> Enterprise Edition avec serveur + licences d’accès client (CAL) (non disponibles pour les nouveaux contrats) est limitée à un maximum de 20 cœurs par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance. Il n'existe aucune limite dans le mode de licence Serveur selon le nombre de cœurs. Pour plus d’informations, consultez [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
##  <a name="High_availability"></a>Haute disponibilité  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Prise en charge de Server Core<sup>1</sup>|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Copie des journaux de transactions|Oui|Oui|Oui|Oui||||  
|Mise en miroir de bases de données|Oui|Oui (niveau complet sécurité uniquement)|Oui (niveau complet sécurité uniquement)|Témoin uniquement|Témoin uniquement|Témoin uniquement|Témoin uniquement|  
|Compression de sauvegarde|Oui|Oui|Oui|||||  
|Instantané de base de données|Oui|||||||  
|Instances de cluster de basculement AlwaysOn|Oui (prise en charge de nœud : maximum du système d'exploitation)|Oui (prise en charge de nœud : 2)|Oui (prise en charge de nœud : 2)|||||  
|Groupes de disponibilité AlwaysOn|Oui (jusqu'à 8 réplicas secondaires, notamment 2 réplicas secondaires synchrones)|||||||  
|Directeur de connexion|Oui|||||||  
|Restauration en ligne de pages et de fichiers|Oui|||||||  
|Indexation en ligne|Oui|||||||  
|Modification de schéma en ligne|Oui|||||||  
|Récupération rapide|Oui|||||||  
|Sauvegardes en miroir|Oui|||||||  
|Ajout de mémoire et de l’UC<sup>2</sup>|Oui|||||||  
|Assistant de récupération de base de données|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Sauvegarde chiffrée|Oui|Oui|Oui|||||  
|Sauvegarde intelligente|Oui|Oui|Oui|Non||||  
  
 <sup>1</sup> Pour plus d’informations sur [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] l’installation de sur Server Core, consultez [installer SQL Server 2014 sur Server Core](../database-engine/install-windows/install-sql-server-on-server-core.md).  
  
 <sup>2</sup> Cette fonctionnalité est disponible uniquement pour 64 bits [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
##  <a name="Scalability"></a>Évolutivité et performances  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Prise en charge de plusieurs instances|50|50|50|50|50|50|50|  
|Partitionnement des tables et des index|Oui|||||||  
|Compression des données|Oui|||||||  
|gouverneur de ressources|Oui|||||||  
|Parallélisme de table de partition|Oui|||||||  
|Plusieurs conteneurs Filestream|Oui|||||||  
|Mémoire de pages de grande taille compatible NUMA et allocation de tableau de tampons|Oui|||||||  
|Extension du pool de mémoires tampons <sup>1</sup>|Oui|Oui|Oui|||||  
|Gouvernance des ressources d'E/S|Oui|||||||  
|OLTP en mémoire <sup>1</sup>|Oui|||||||  
|Durabilité différée|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
  
 <sup>1</sup> cette fonctionnalité est disponible uniquement pour 64 bits [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
##  <a name="Enterprise_security"></a> Sécurité  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Audit de base|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Audit de granularité fine|Oui|||||||  
|Chiffrement transparent de base de données|Oui|||||||  
|Gestion de clés extensible|Oui|||||||  
|Rôles définis par l'utilisateur|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Bases de données autonomes|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Chiffrement des sauvegardes|Oui|Oui|Oui|||||  
  
##  <a name="Replication"></a>La  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]suivi des modifications|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Réplication de fusion|Oui|Oui|Oui|Oui (abonné uniquement)|Oui (abonné uniquement)|Oui (abonné uniquement)|Oui (abonné uniquement)|  
|Réplication transactionnelle|Oui|Oui|Oui|Oui (abonné uniquement)|Oui (abonné uniquement)|Oui (abonné uniquement)|Oui (abonné uniquement)|  
|Réplication d'instantané|Oui|Oui|Oui|Oui (abonné uniquement)|Oui (abonné uniquement)|Oui (abonné uniquement)|Oui (abonné uniquement)|  
|Abonnés hétérogènes|Oui|Oui|Oui|||||  
|Publication Oracle|Oui|||||||  
|Réplication transactionnelle d'égal à égal|Oui|||||||  
  
##  <a name="Mgmt_Tools"></a>Outils de gestion  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Objets de gestion SQL (SMO)|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Gestionnaire de configuration SQL|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|SQL CMD (outil d'invite de commandes)|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Management Studio|Oui|Oui|Oui|Oui|Oui|Oui||  
|Distributed Replay - Outil d’administration|Oui|Oui|Oui|Oui|Oui|Oui||  
|Distributed Replay - Client|Oui|Non|Oui|Oui||||  
|Distributed Replay - Contrôleur|Oui (Enterprise prend en charge jusqu'à 16 clients, Developer prend en charge uniquement 1 client)|Non|Oui (prise en charge d'1 client uniquement)|Oui (prise en charge d'1 client uniquement)||||  
|SQL Profiler|Oui|Oui|Oui|Non<sup>2</sup>|Non<sup>2</sup>|Non<sup>2</sup>|Non<sup>2</sup>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Agent|Oui|Oui|Oui|Oui||||  
|Pack d'administration Microsoft System Center Operations Manager|Oui|Oui|Oui|Oui||||  
|Assistant Paramétrage de base de données (DTA)|Oui|Oui|Oui<sup>3</sup>|Oui<sup>3</sup>||||  
|Assistant déployer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] une base de données sur une machine virtuelle Azure|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Fichiers de données dans Azure|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
  
 <sup>2</sup> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Web, [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Tools et [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services peuvent être profilés à l' [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] aide des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] éditions standard et Enterprise.  
  
 <sup>3</sup> paramétrage activé uniquement sur les fonctionnalités d’édition standard.  
  
##  <a name="RDBMS_mgmt"></a>Facilité de gestion de SGBDR  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Instances utilisateur|||||Oui|Oui|Oui|  
|LocalDB|||||Oui|Oui||  
|Connexion administrateur dédiée|Oui|Oui|Oui|Oui|Oui (sous indicateur de trace)|Oui (sous indicateur de trace)|Oui (sous indicateur de trace)|  
|Prise en charge de scripts PowerShell|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Prise en charge de SysPrep<sup>1</sup>|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Prise en charge des opérations de composant d’application de la couche données-extraction, déploiement, mise à niveau, suppression|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Automation de stratégie (vérification selon la planification et sur modification)|Oui|Oui|Oui|Oui||||  
|Collecteur de données de performances|Oui|Oui|Oui|Oui||||  
|Possibilité d'inscription en tant qu'instance managée dans le cadre de la gestion de plusieurs instances|Oui|Oui|Oui|Oui||||  
|Rapports de performances standard|Oui|Oui|Oui|Oui||||  
|Repères de plan et gel de plan relatif|Oui|Oui|Oui|Oui||||  
|Requête directe de vues d'index (à l'aide de l'indicateur NOEXPAND)|Oui|Oui|Oui|Oui||||  
|Maintenance de vue indexée automatique|Oui|Oui|Oui|Oui||||  
|Vues partitionnées distribuées|Oui|Partial. Les vues partitionnées distribuées ne peuvent pas être mises à jour|Partial. Les vues partitionnées distribuées ne peuvent pas être mises à jour|Partial. Les vues partitionnées distribuées ne peuvent pas être mises à jour|Partial. Les vues partitionnées distribuées ne peuvent pas être mises à jour|Partial. Les vues partitionnées distribuées ne peuvent pas être mises à jour|Partial. Les vues partitionnées distribuées ne peuvent pas être mises à jour|  
|Opérations d'index parallèles|Oui|||||||  
|Utilisation automatique de vues indexées par l'optimiseur de requête|Oui|||||||  
|Vérifications de cohérence parallèles|Oui|||||||  
|Point de contrôle de l'utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Oui|||||||  
|Bases de données autonomes|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Extension du pool de mémoires tampons<sup>2</sup>|Oui|Oui|Oui|||||  
  
 <sup>1</sup> pour plus d’informations, consultez [considérations relatives à l’installation de SQL Server à l’aide de Sysprep](../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md).  
  
 <sup>2</sup> cette fonctionnalité est disponible uniquement pour 64 bits [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
##  <a name="Dev_tools"></a>Outils de développement  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[msCoName](../includes/msconame-md.md)]Intégration de Visual Studio|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Intellisense ([!INCLUDE[tsql](../includes/tsql-md.md)] et MDX)|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]|Oui|Oui|Oui|Oui|Oui|||  
|Outils de conception et de modification de requêtes SQL<sup>1</sup>|Oui|Oui|Oui|||||  
|Prise en charge du contrôle de version<sup>1</sup>|Oui|Oui|Oui|||||  
|Outils de modification, de débogage et de conception MDX<sup>1</sup>|Oui|Oui|Oui|||||  
  
 <sup>1</sup> cette fonctionnalité n’est pas disponible pour la version 64 bits de l’édition standard.  
  
##  <a name="Programmability"></a> Programmability  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Intégration du CLR (Common Language Runtime)|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Prise en charge XML native|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Indexation XML|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|FUSIONNer les fonctionnalités de UPSERT &|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|prise en charge de FILESTREAM|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|FileTable|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Types de données de date et d'heure|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Support d'internationalisation|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Recherche sémantique et en texte intégral|Oui|Oui|Oui|Oui|Oui|||  
|Spécification d'une langue dans une requête|Oui|Oui|Oui|Oui|Oui|||  
|Service Broker (messagerie)|Oui|Oui|Oui|Non (client uniquement)|Non (client uniquement)|Non (client uniquement)|Non (client uniquement)|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]terminaison|Oui|Oui|Oui|Oui||||  
  
##  <a name="SSIS"></a> Integration Services  
  
|Fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|-------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Assistant Importation et Exportation|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Connecteurs de source de données intégrés|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Concepteur et exécution SSIS|Oui|Oui|Oui|||||  
|Transformations de base|Oui|Oui|Oui|||||  
|Outils de profilage de données de base|Oui|Oui|Oui|||||  
|Service de capture de données modifiées pour Oracle par Attunity|Oui|||||||  
|Concepteur de capture de données modifiées pour Oracle par Attunity|Oui|||||||  
  
###  <a name="SSIS_AA"></a>Integration Services-adaptateurs avancés  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Destination Oracle de haute performance|Oui|||||||  
|Destination Teradata de haute performance|Oui|||||||  
|Source et destination SAP BW|Oui|||||||  
|Adaptateur de destination d'apprentissage du modèle d'exploration de données|Oui|||||||  
|Adaptateur de destination de traitement de dimension|Oui|||||||  
|Adaptateur de destination de traitement de partition|Oui|||||||  
|Composants de capture de données modifiées par Attunity|Oui|||||||  
|Connecteur pour Open Database Connectivity (ODBC) par Attunity|Oui|||||||  
  
###  <a name="SSIS_AT"></a>Integration Services-transformations avancées  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Recherches de persistance (haute performance)|Oui|||||||  
|Transformation de requête d'exploration de données|Oui|||||||  
|Transformations de recherche floue et de regroupement probable|Oui|||||||  
|Extractions de termes et transformations de recherche|Oui|||||||  
  
##  <a name="MDS"></a>Master Data Services  
  
> [!NOTE]  
>  -   
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] est disponible uniquement sur les éditions 64 bits de Business Intelligence et Enterprise uniquement.  
  
|Fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|-------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]Database|Oui|Oui||||||  
|[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]application Web|Oui|Oui||||||  
  
##  <a name="Data_warehouse"></a>Data Warehouse  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Création de cubes sans une base de données|Oui|Oui|Oui|||||  
|Génération automatique de la mise en lots et du schéma d'entrepôt de données|Oui|Oui|Oui|||||  
|Capture des données modifiées|Oui|||||||  
|Optimisations de requêtes de jointure en étoile|Oui|||||||  
|Configuration en lecture seule évolutive d'Analysis Services|Oui|||||||  
|Traitement des requêtes parallèles sur les tables et les index partitionnés|Oui|||||||  
|Index columnstore optimisés en mémoire xVelocity|Oui|||||||  
|Agrégation globale des traitements|Oui|||||||  
  
##  <a name="SSAS"></a>Analysis Services  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Bases de données partagées évolutives (attacher ou détacher les bases de données, bases de données en lecture seule)|Oui|Oui||||||  
|Sauvegarder/Restaurer, attacher/détacher des bases de données|Oui|Oui|Oui|||||  
|Synchroniser des bases de données|Oui|Oui||||||  
|Haute disponibilité|Oui|Oui|Oui|||||  
|Programmabilité (AMO, ADOMD.Net, OLEDB, XML/A, ASSL)|Oui|Oui|Oui|||||  
  
###  <a name="BISemModel_multi"></a>Modèle sémantique BI (multidimensionnel)  
  
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
  
###  <a name="BISemModel_tabular"></a>Modèle sémantique BI (tabulaire)  
  
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
  
###  <a name="PowerPivot"></a>PowerPivot pour SharePoint  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Intégration de batterie de serveurs SharePoint selon l'architecture de service partagé|Oui|Oui||||||  
|Rapports d’utilisation|Oui|Oui||||||  
|Règles de contrôle d'intégrité|Oui|Oui||||||  
|Galerie PowerPivot|Oui|Oui||||||  
|Actualisation des données PowerPivot|Oui|Oui||||||  
|Flux de données PowerPivot|Oui|Oui||||||  
  
###  <a name="DataMining"></a>Exploration de données  
  
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
  
##  <a name="Reporting"></a>Reporting Services  
  
###  <a name="Reporting_features"></a>Fonctionnalités de Reporting Services  
  
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
  
 <sup>1</sup> Pour plus d’informations sur les sources de données [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]prises en charge dans, consultez [sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
 <sup>2</sup> Requiert [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode SharePoint. Pour plus d’informations, consultez [Reporting Services installation en mode sharepoint &#40;sharepoint 2010 et sharepoint 2013&#41;](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
### <a name="report-server-database-server-edition-requirements"></a>Conditions requises pour l'édition SQL Server de la base de données du serveur de rapports  
 Lors de la création d'une base de données de serveur de rapports, toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne peuvent pas être utilisées pour héberger la base de données. Le tableau suivant répertorie les éditions du [!INCLUDE[ssDE](../includes/ssde-md.md)] que vous pouvez utiliser pour les éditions spécifiques de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
|Pour cette édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services|Utilisez cette édition de l'instance du moteur de base de données pour héberger la base de données|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Entreprise|Éditions Standard, Business Intelligence, Enterprise (locales ou distantes)|  
|Business Intelligence|Éditions Standard, Business Intelligence, Enterprise (locales ou distantes)|  
|standard|Éditions Standard, Enterprise (locales ou distantes)|  
|Web|Web Edition (locale uniquement)|  
|Express with Advanced Services|Express with Advanced Services (local uniquement).|  
|Évaluation|Évaluation|  
  
##  <a name="BIClients"></a>Clients Business Intelligence  
 Les applications logicielles clientes suivantes sont disponibles dans le Centre de téléchargement Microsoft ; elles ont pour but de vous aider à créer des documents décisionnels qui s'exécutent sur une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Lorsque vous hébergez ces documents dans un environnement serveur, utilisez une édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prise en charge pour ce type de document. Le tableau suivant identifie quelle édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contient les fonctionnalités de serveur obligatoires pour héberger les documents créés dans ces applications clientes.  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)]|Oui|Oui|Oui|||||  
|Compléments d'exploration de données pour Excel et Visio 2010|Oui|Oui|Oui|||||  
|[!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)]2010|Oui|Oui||||||  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]|Oui|Oui||||||  
  
> [!NOTE]
>  1.  [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)]est un complément Excel et ne dépend pas de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Toutefois [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] est requis pour partager les classeurs [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] dans SharePoint et y collaborer ; cette fonction est disponible dans le cadre des éditions Enterprise et Business Intelligence de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
> 2.  Le tableau ci-dessus identifie les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requises pour activer ces outils clients ; toutefois, ces fonctionnalités peuvent accéder aux données hébergées sur n'importe quelle édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
##  <a name="Spatial"></a>Services spatiaux et de localisation  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Index spatiaux|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Types de données planaires et géodésiques|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Bibliothèques spatiales avancées|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Importation/exportation de formats de données spatiales standard|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
  
##  <a name="Add_DBServices"></a>Services de base de données supplémentaires  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Assistant Migration|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|Messagerie de base de données|Oui|Oui|Oui|Oui||||  
  
##  <a name="Other_Components"></a>Autres composants  
  
|Nom de la fonctionnalité|Entreprise|Business Intelligence|standard|Web|Express with Advanced Services|Express with Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Data Quality Services|Oui|Oui||||||  
|StreamInsight|StreamInsight Premium Edition|StreamInsight Standard Edition|StreamInsight Standard Edition|StreamInsight Standard Edition||||  
|StreamInsight HA|StreamInsight Premium Edition|||||||  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifications de produit pour SQL Server 2014](../../2014/getting-started/sql-server-2014-product-specifications.md)   
 [Installation pour SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md)   
 [Installation de démarrage rapide de SQL Server 2014](../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)  
  
  
