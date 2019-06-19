---
title: Spécifications des capacités maximales pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- objects [SQL Server]
- number capacity specifications [SQL Server]
- size [SQL Server], capacity specifications
- number of objects
- capacity specifications [SQL Server]
- maximum capacity specifications [SQL Server]
- size [SQL Server]
- replication capacity specifications [SQL Server]
- objects [SQL Server], capacity specifications
- Database Engine [SQL Server], capacity specifications
ms.assetid: 13e95046-0e76-4604-b561-d1a74dd824d7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 49e86c8b47a3a0de48a0138d96cec22d585901c6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62711444"
---
# <a name="maximum-capacity-specifications-for-sql-server"></a>Spécifications des capacités maximales pour SQL Server
  Les tableaux suivants présentent la taille maximale et le nombre maximal des différents objets définis dans les composants [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour naviguer jusqu'à la table d'une technologie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , cliquez sur son lien :  
  
 [Objets du moteur de base de données SQL Server](#Engine)  
  
 [Objets utilitaires SQL Server](#Utility)  
  
 [Objets d'application de la couche Données SQL Server](#DAC)  
  
 [Objets de réplication SQL Server](#Replication)  
  
##  <a name="Engine"></a> [!INCLUDE[ssDE](../includes/ssde-md.md)] Objets  
 Le tableau suivant présente la taille maximale et le nombre maximal des différents objets définis dans les bases de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou référencés dans les instructions [!INCLUDE[tsql](../includes/tsql-md.md)].  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] objet|Tailles maximales/nombres [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (32 bits)|Tailles maximales/nombres maximaux [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (64-bit)|  
|---------------------------------------------------------|------------------------------------------------------------------|------------------------------------------------------------------|  
|Taille du lot<br /><br /> Remarque : La taille des paquets réseau représente la taille des paquets TDS (Tabular Data Stream) utilisés pour la communication entre des applications et le [!INCLUDE[ssDE](../includes/ssde-md.md)]relationnel. La taille par défaut s'élève à 4 Ko ; elle est contrôlée par l'option de configuration Taille du paquet réseau.|65 536 * Taille des paquets réseau|65 536 * Taille des paquets réseau|  
|Octets par colonne de chaîne courte|8,000|8,000|  
|Octets par clause GROUP BY, ORDER BY|8,060|8,060|  
|Octets par clé d’index<br /><br /> Remarque : Le nombre maximal d’octets dans une clé d’index ne peut pas dépasser 900 dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Vous pouvez définir une clé en utilisant des colonnes de longueur variable dont la taille n'excède pas 900, à condition qu'aucune ligne de plus de 900 octets de données ne soit insérée dans ces colonnes. Dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], vous pouvez inclure des colonnes non-clés dans un index non cluster afin d'éviter la taille de clé d'index maximale de 900 octets.|900|900|  
|Octets par clé étrangère|900|900|  
|Octets par clé primaire|900|900|  
|Octets par ligne<br /><br /> Remarque :<br />        [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prend en charge le stockage avec dépassement de ligne, qui permet d’envoyer hors ligne les colonnes de longueur variable. Seule une racine de 24 octets est stockée dans l'enregistrement principal des colonnes de longueur variable envoyées hors ligne ; par conséquent, la limite effective par ligne est supérieure dans les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour plus d'informations, consultez la rubrique « Données de dépassement de ligne de plus de 8 Ko » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|8,060|8,060|  
|Octets par ligne dans les tables optimisées en mémoire<br /><br /> Remarque :<br />        L’OLTP en mémoire de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne prend pas en charge le stockage avec dépassement de ligne. Les colonnes de longueur variable ne sont pas envoyées hors ligne. Cela limite la largeur maximale des colonnes à longueur variable que vous pouvez spécifier dans une table optimisée en mémoire à la taille de ligne maximale. Pour plus d’informations, consultez [Taille de la table et des lignes dans les tables optimisées en mémoire](../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md).|Non pris en charge|8,060|  
|Octets dans le texte source d'une procédure stockée|Taille de lot inférieure ou 250 Mo|Taille de lot inférieure ou 250 Mo|  
|Octets par colonne `varchar(max)`, `varbinary(max)`, `xml`, `text` ou `image`|2^31-1|2^31-1|  
|Caractères par colonne `ntext` ou `nvarchar(max)`|2^30-1|2^30-1|  
|Index cluster par table|1|1|  
|Colonnes dans les clauses GROUP BY, ORDER BY|Limité uniquement par le nombre d'octets|Limité uniquement par le nombre d'octets|  
|Colonnes ou expressions dans une instruction GROUP BY WITH CUBE ou WITH ROLLUP|10|10|  
|Colonnes par clé d’index<br /><br /> Remarque : Si la table contient au moins un index XML, la clé de clustering de la table d’utilisateur est limitée à 15 colonnes, car la colonne XML est ajoutée à la clé de clustering du principal index XML. Dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], vous pouvez inclure des colonnes non-clés dans un index non cluster afin d'éviter la limitation à un maximum de 16 colonnes clés. Pour plus d’informations, consultez [Créer des index avec colonnes incluses](../relational-databases/indexes/create-indexes-with-included-columns.md).|16|16|  
|Colonnes par clé étrangère|16|16|  
|Colonnes par clé primaire|16|16|  
|Colonnes par tableau non large|1,024|1,024|  
|Colonnes par tableau large|30,000|30,000|  
|Colonnes par instruction SELECT|4,096|4,096|  
|Colonnes par instruction INSERT|4096|4096|  
|Connexions par client|Valeur maximale des connexions configurées|Valeur maximale des connexions configurées|  
|Taille de la base de données|524 272 téraoctets|524 272 téraoctets|  
|Bases de données par instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|32,767|32,767|  
|Groupes de fichiers par base de données|32,767|32,767|  
|Groupes de fichiers par base de données pour les données optimisées en mémoire|Non pris en charge|1|  
|Fichiers par base de données|32,767|32,767|  
|Taille de fichier (données)|16 téraoctets|16 téraoctets|  
|Taille de fichier (journal)|2 téraoctets|2 téraoctets|  
|Fichiers de données pour les données optimisées en mémoire par base de données|Non pris en charge|4.096|  
|Fichier delta par fichier de données pour les données optimisées en mémoire|Non pris en charge|1|  
|Références de table de clé étrangère par table<br /><br /> Remarque : Bien qu’une table peut contenir un nombre illimité de contraintes FOREIGN KEY, le maximum recommandé est 253. Selon la configuration matérielle qui héberge [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], la spécification de contraintes FOREIGN KEY supplémentaires peut représenter un coût de traitement élevé pour l'optimiseur de requête.|253|253|  
|Longueur d'identificateur (en caractères)|128|128|  
|Instances par ordinateur|50 instances sur un serveur autonome pour toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].<br /><br /> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prend en charge 25 instances sur un basculement de cluster lorsque vous utilisez un disque de cluster partagé comme l’option stockée installation de cluster [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] partages de fichiers prend en charge 50 instances sur un basculement de cluster si vous choisissez SMB comme option de stockage pour votre installation de cluster Pour plus d’informations, consultez [Hardware and Software Requirements for Installing SQL Server 2014](install/hardware-and-software-requirements-for-installing-sql-server.md).|50 instances sur un serveur autonome.<br /><br /> 25 instances sur un cluster de basculement si vous utilisez un disque de cluster partagé, car l'option stockée pour votre installation de cluster [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prend en charge 50 instances sur un cluster de basculement si vous choisissez les partages SMB comme option de stockage de votre installation de cluster.|  
|Index par table optimisée en mémoire|Non pris en charge|8|  
|Longueur d’une chaîne contenant des instructions SQL (taille du traitement)<br /><br /> Remarque : La taille des paquets réseau représente la taille des paquets TDS (Tabular Data Stream) utilisés pour la communication entre des applications et le [!INCLUDE[ssDE](../includes/ssde-md.md)]relationnel. La taille par défaut s'élève à 4 Ko ; elle est contrôlée par l'option de configuration Taille du paquet réseau.|65 536 * Taille des paquets réseau|65 536 * Taille des paquets réseau|  
|Verrous par connexion|Verrous maximaux par serveur|Verrous maximaux par serveur|  
|Verrous par instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<br /><br /> Remarque : Cette valeur s’applique à l’allocation de verrouillage statique. Les verrous dynamiques sont uniquement limités par la mémoire.|Jusqu'à 2 147 483 647|Limité uniquement par la mémoire|  
|Niveaux d’imbrication des procédures stockées<br /><br /> Remarque : Si une procédure stockée accède à plus de 64 bases de données ou à plus de 2 bases entrelacées, vous recevez un message d’erreur.|32|32|  
|Sous-requêtes imbriquées|32|32|  
|Niveaux de déclencheurs imbriqués|32|32|  
|Index non cluster par table|999|999|  
|Nombre d'expressions distinctes dans la clause GROUP BY lorsque l'un des éléments suivants est présent : CUBE, ROLLUP, GROUPING SETS, WITH CUBE, WITH ROLLUP|32|32|  
|Nombre de jeux de regroupement générés par les opérateurs dans la clause GROUP BY|4,096|4,096|  
|Paramètres par procédure stockée|2,100|2,100|  
|Paramètres par fonction définie par l'utilisateur|2,100|2,100|  
|REFERENCES par table|253|253|  
|Lignes par table|Limité par le stockage disponible|Limité par le stockage disponible|  
|Tables par base de données<br /><br /> Remarque : Les objets de base de données comprennent des tables, des vues, des procédures stockées, des fonctions définies par l’utilisateur, des déclencheurs, des règles, des valeurs par défaut et des contraintes. Au total, le nombre de tous les objets d'une base de données ne peut pas dépasser 2 147 483 647.|Limité par le nombre d'objets dans une base de données|Limité par le nombre d'objets dans une base de données|  
|Partitions par table ou index partitionné|1,000<br /><br /> **\*\* Important \* \***  création d’une table ou un index avec plus de 1 000 partitions est possible sur un système 32 bits, mais n’est pas pris en charge.|15,000|  
|Statistiques sur les colonnes non indexées|30,000|30,000|  
|Tables par instruction SELECT|Limité uniquement par les ressources disponibles|Limité uniquement par les ressources disponibles|  
|Déclencheurs par table<br /><br /> Remarque : Les objets de base de données comprennent des tables, des vues, des procédures stockées, des fonctions définies par l’utilisateur, des déclencheurs, des règles, des valeurs par défaut et des contraintes. Au total, le nombre de tous les objets d'une base de données ne peut pas dépasser 2 147 483 647.|Limité par le nombre d'objets dans une base de données|Limité par le nombre d'objets dans une base de données|  
|Colonnes par instruction UPDATE (tableaux larges)|4096|4096|  
|Connexions utilisateur|32,767|32,767|  
|Index XML|249|249|  
  
##  <a name="Utility"></a> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objets utilitaires  
 Le tableau suivant présente la taille maximale et le nombre maximal des différents objets qui ont été testés dans l'utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objet utilitaire|Tailles maximales/nombres [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (32 bits)|Tailles maximales/nombres maximaux [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (64-bit)|  
|----------------------------------------------|------------------------------------------------------------------|------------------------------------------------------------------|  
|Ordinateurs (ordinateurs physique ou ordinateurs virtuels) par utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|100|100|  
|Instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] par ordinateur|5|5|  
|Nombre total d'instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] par utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|200*|200*|  
|Bases de données utilisateur par instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], notamment les applications de la couche Données|50|50|  
|Nombre total de bases de données utilisateur par utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|1,000|1,000|  
|Groupes de fichiers par base de données|1|1|  
|Fichiers de données par groupe de fichiers|1|1|  
|Fichiers journaux par base de données|1|1|  
|Volumes par ordinateur|3|3|  
  
 \* Le nombre maximal d’instances gérées de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pris en charge par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilitaire peut varier en fonction de la configuration matérielle du serveur. Pour obtenir des informations de prise en main, consultez [Fonctionnalités et tâches de l’utilitaire SQL Server](../relational-databases/manage/sql-server-utility-features-and-tasks.md). Le point de contrôle de l'utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] n'est pas disponible dans toutes les éditions de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
##  <a name="DAC"></a> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objets d’application de la couche Données  
 Le tableau suivant spécifie la taille maximale et le nombre maximum des différents objets testés dans les applications de la couche Données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (DAC).  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Object DAC|Tailles maximales/nombres [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (32 bits)|Tailles maximales/nombres maximaux [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (64-bit)|  
|------------------------------------------|------------------------------------------------------------------|------------------------------------------------------------------|  
|Bases de données par DAC|1|1|  
|Objets par DAC*|Limité par le nombre d'objets dans une base de données ou la mémoire disponible.|Limité par le nombre d'objets dans une base de données ou la mémoire disponible.|  
  
 \* Les types d’objets inclus dans la limite sont des utilisateurs, des tables, des vues, des procédures stockées, des fonctions définies par l’utilisateur, des types de données définis par l’utilisateur, des rôles de base de données, des schémas et des types de table définis par l’utilisateur.  
  
##  <a name="Replication"></a> Objets de réplication  
 Le tableau suivant présente la taille maximale et le nombre maximal des différents objets définis dans Réplication [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objet de réplication|Taille maximale/nombre maximal dans SQL Server (32 bits)|Taille maximale/nombre maximal dans SQL Server (64 bits)|  
|--------------------------------------------------|---------------------------------------------------|---------------------------------------------------|  
|Articles (publication de fusion)|256|256|  
|Articles (publication d'instantané ou transactionnelle)|32,767|32,767|  
|Colonnes dans une table* (publication de fusion)|246|246|  
|Colonnes dans une table** (publication d’instantané ou transactionnelle[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] )|1,000|1,000|  
|Colonnes dans une table** (publication d’instantané ou transactionnelle Oracle)|995|995|  
|Octets pour une colonne utilisée dans un filtre de lignes (publication de fusion)|1,024|1,024|  
|Octets pour une colonne utilisée dans un filtre de lignes (publication d'instantané ou transactionnelle)|8,000|8,000|  
  
 \* Si le suivi de lignes est utilisé pour la détection de conflits (valeur par défaut), la table de base peut inclure 1 024 colonnes au maximum, mais les colonnes doivent être filtrées à partir de l’article afin que 246 colonnes au maximum soient publiées. Si le suivi de colonnes est utilisé, la table de base peut inclure 246 colonnes au maximum.  
  
 ** La table de base peut inclure le nombre maximal de colonnes autorisées dans la base de données de publication (1 024 pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]), mais les colonnes doivent être filtrées à partir de l’article si elles sont plus nombreuses que le maximum spécifié pour le type de publication.  
  
## <a name="see-also"></a>Voir aussi  
 [Matérielle et logicielle requise pour l’installation de SQL Server 2014](install/hardware-and-software-requirements-for-installing-sql-server.md)   
 [Paramètres de l'outil d'analyse de configuration système](../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)   
 [Fonctionnalités et tâches de l’utilitaire SQL Server](../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
