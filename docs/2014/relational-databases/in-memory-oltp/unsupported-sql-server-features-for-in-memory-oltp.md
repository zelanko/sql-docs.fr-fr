---
title: Prise en charge des fonctionnalités de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c39f03a7-e223-4fd7-bd30-142e28f51654
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 660515f10797e1f11fac22c1baf4ed74e9f67c0c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63157241"
---
# <a name="supported-sql-server-features"></a>Fonctionnalités SQL Server prises en charge
  Cette rubrique décrit les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont prises en charge, et celles qui ne le sont pas, avec les objets mémoire optimisés.  
  
## <a name="includessnoversionincludesssnoversion-mdmd-features-supported-for-in-memory-oltp"></a>Fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prises en charge pour l'OLTP en mémoire  
 Les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suivantes sont prises en charge sur une base de données qui contient des objets mémoire optimisés (y compris des groupes de fichiers mémoire optimisés).  
  
 Pour plus d'informations sur les types de données pris en charge, consultez [Supported Data Types](supported-data-types-for-in-memory-oltp.md).  
  
-   Options et opérations prises en charge sur les tables mémoire optimisées. Pour plus d’informations, consultez [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).  
  
-   Options et opérations prises en charge sur les procédures stockées compilées en mode natif. Pour plus d’informations, consultez [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).  
  
-   Capacité à accéder aux tables mémoire optimisées à l'aide du [!INCLUDE[tsql](../../../includes/tsql-md.md)] interprété. Le [!INCLUDE[tsql](../../../includes/tsql-md.md)] interprété fournit la surface d'exposition équivalente pour accéder aux tables qui ne sont pas mémoire optimisées à l'aide de procédures stockées non compilées en mode natif et utilisant [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Pour plus d’informations, consultez [Accès aux tables optimisées en mémoire à l’aide du Transact-SQL interprété](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).  
  
-   Contrôle de version multiple et contrôle d'accès concurrentiel optimiste. Pour plus d’informations, consultez [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md).  
  
-   Opérations de sauvegarde et de restauration d'une base de données qui contient un groupe de fichiers mémoire optimisé. Pour plus d’informations, consultez [Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
-   Affichages catalogue, vues de gestion dynamique et événements étendus pour la prise en charge. Pour plus d’informations, consultez [Vues système, procédures stockées, DMV et types d’attente pour l’OLTP en mémoire](../../database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md).  
  
-   Objets de gestion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Prise en charge d’objets SMO (SQL Server Management Objects) pour l’OLTP en mémoire](sql-server-management-objects-support-for-in-memory-oltp.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Pour plus d’informations, consultez [Prise en charge de SQL Server Management Studio pour l’OLTP en mémoire](sql-server-management-studio-support-for-in-memory-oltp.md).  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell. Pour plus d'informations, consultez [Présentation de SQL Server PowerShell](https://msdn.microsoft.com/library/cc281954\(SQL.105\).aspx).  
  
-   Importez et exportez des données en bloc à l'aide de l'utilitaire bcp. Pour plus d’informations, consultez [Importer et exporter des données en bloc à l’aide de l’utilitaire bcp &#40;SQL Server&#41;](../import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md).  
  
-   Récupération sur incident.  
  
-   Plusieurs conteneurs dans un groupe de fichiers mémoire optimisé pour stocker des objets de l'OLTP en mémoire et réduire l'objectif de temps de récupération (RTO).  
  
-   Les blocs du journal des transactions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] calculent et valident la somme.  
  
-   Nouvel indicateur de table SNAPSHOT. Pour plus d’informations, consultez [Indicateurs de table &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).  
  
-   Niveau DB COMPAT.  
  
-   Base de données partiellement autonome. L'authentification de la base de données autonome est prise en charge. Toutefois, tous les objets de l'OLTP en mémoire sont marqués comme étant des « relations contenant-contenu essentielles » dans la vue de gestion dynamique dm_db_uncontained_entities.  
  
-   Service Broker, sous certaines conditions. Impossible d'accéder à une file d'attente à partir d'une procédure stockée compilée en mode natif. Impossible d'accéder à une file d'attente dans une base de données distante, dans une transaction qui accède à des tables à mémoire optimisée.  
  
-   Clustering de basculement : Dans le cadre de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AlwaysOn offre, les Instances de Cluster de basculement AlwaysOn exploitent la fonctionnalité de Clustering de basculement Windows Server (WSFC) pour fournir une haute disponibilité locale grâce à la redondance sur le cluster de basculement un niveau d’instance de serveur instance (ICF). Pour plus d’informations, consultez [Instances de cluster de basculement AlwaysOn (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
-   Intégration à AlwaysOn : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit plusieurs options permettant de garantir un haut niveau de disponibilité pour un serveur ou une base de données, y compris AlwaysOn. Pour plus d’informations, consultez [Solutions haute disponibilité &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md).  
  
-   Envoi de journaux : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Envoi de journaux permet d’envoyer automatiquement des sauvegardes de fichier journal à partir d’une base de données primaire sur une instance de serveur principal à un ou plusieurs bases de données secondaires sur des instances distinctes du serveur secondaire. Pour plus d’informations, consultez [À propos de la copie des journaux de transaction &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
-   La réplication transactionnelle vers des tables mémoire optimisées sur les abonnés est prise en charge avec certaines restrictions. Pour plus d’informations, consultez [Abonnés à la réplication de tables optimisées en mémoire](../replication/replication-to-memory-optimized-table-subscribers.md).  
  
-   Gouverneur de ressources : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Gouverneur de ressources est une fonctionnalité que vous pouvez utiliser pour gérer les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la consommation des ressources système et de la charge de travail. Resource Governor vous permet de spécifier des limites sur l'utilisation de la quantité d'UC, d'E/S physiques et de mémoire par les demandes d'application entrantes. Pour plus d'informations, consultez [Managing Memory for In-Memory OLTP](../../database-engine/managing-memory-for-in-memory-oltp.md) et [Resource Governor](../resource-governor/resource-governor.md).  
  
-   OLTP en mémoire est limité au niveau des pages de codes prises en charge pour les colonnes (var)char dans les tables mémoire optimisées et les classements pris en charge utilisés dans des index et des procédures stockées compilées en mode natif. Pour plus d'informations, consultez [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).  
  
-   Prise en charge de BACPAC.  
  
## <a name="includessnoversionincludesssnoversion-mdmd-features-not-supported-for-in-memory-oltp"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fonctionnalités non prises en charge pour l’OLTP en mémoire  
 Les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suivantes ne sont pas prises en charge sur une base de données qui contient des objets à mémoire optimisée (notamment des groupes de fichiers à mémoire optimisée).  
  
|Fonctionnalités non prises en charge|Description de la fonctionnalité|  
|-------------------------|-------------------------|  
|Compression de données pour les tables à mémoire optimisée.|Vous pouvez utiliser la fonctionnalité de compression de données pour compresser les données dans une base de données et réduire la taille de la base de données. Pour plus d'informations, consultez [Data Compression](../data-compression/data-compression.md).|  
|Partitionnement des tables et des index HASH mémoire optimisés.|Les données des tables et des index partitionnés sont divisées en unités qui peuvent être réparties sur plusieurs groupes de fichiers d'une base de données. Pour plus d’informations, consultez [Tables et index partitionnés](../partitions/partitioned-tables-and-indexes.md).|  
|Chiffrement transparent des données (TDE) sur le groupe de fichiers mémoire optimisé d'une base de données.|Le chiffrement transparent des données (TDE, Transparent Data Encryption) effectue le chiffrement et le déchiffrement des E/S en temps réel des fichiers de données et des fichiers journaux. Pour plus d’informations, consultez [Transparent Data Encryption &#40;TDE&#41;](../security/encryption/transparent-data-encryption.md).<br /><br /> Le chiffrement transparent des données (TDE) peut être activé sur une base de données contenant des objets de l'OLTP en mémoire. Les enregistrements de journal de l'OLTP en mémoire sont chiffrés si le chiffrement transparent des données (TDE) est activé. Les fichiers de point de contrôle des tables durables ne sont pas chiffrés, même si le chiffrement transparent des données (TDE) est activé sur la base de données.|  
|Réplication|Les configurations de réplication autres que la réplication transactionnelle vers des tables mémoire optimisées sur les abonnés sont incompatibles avec des tables ou des vues qui référencent des tables mémoire optimisées. Réplication à l’aide de sync_mode = 'database snapshot' n’est pas pris en charge s’il existe un groupe de fichiers mémoire optimisé. Pour plus d’informations, consultez [Abonnés à la réplication de tables optimisées en mémoire](../replication/replication-to-memory-optimized-table-subscribers.md).|  
|MARS (Multiple Active Result Sets)|Multiple Active Result Sets (MARS) n'est pas pris en charge avec les tables mémoire optimisées. Cette erreur peut également indiquer l'utilisation d'un serveur lié. Un serveur lié peut utiliser MARS. Les serveurs liés ne sont pas pris en charge avec les tables mémoire optimisées. À la place, connectez-vous directement au serveur et à la base de données qui héberge les tables mémoire optimisées.|  
|Mise en miroir|La mise en miroir de bases de données est une solution permettant d'accroître la disponibilité d'une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).|  
|Reconstruire le journal|La reconstruction du journal, via un attachement ou ALTER DATABASE, n'est pas prise en charge pour les bases de données avec un groupe de fichiers MEMORY_OPTIMIZED_DATA.|  
|Serveur lié|Pour plus d’informations, consultez [Serveurs liés &#40;moteur de base de données&#41;](../linked-servers/linked-servers-database-engine.md).|  
|Journalisation en bloc|Quel que soit le mode de récupération de la base de données, toutes les opérations sur les tables à mémoire optimisée durables sont toujours entièrement journalisées.|  
|Journalisation minimale|La journalisation minimale n'est pas prise en charge pour les tables à mémoire optimisée. Pour plus d’informations sur la journalisation minimale, consultez [Journal des transactions &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) et [Conditions requises pour une journalisation minimale dans l’importation en bloc](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md).|  
|Suivi des modifications|Le suivi des modifications peut être activé sur une base de données avec des objets de l'OLTP en mémoire. Toutefois, les modifications apportées aux tables à mémoire optimisée ne sont pas suivies.|  
|déclencheurs DDL|Les déclencheurs DDL aux niveaux de la base de données et du serveur ne sont pas pris en charge avec les tables de l'OLTP en mémoire et les procédures stockées compilées en mode natif.|  
|Capture de données modifiées (CDC)|La capture de données modifiées ne doit pas être activée sur une base de données qui possède des objets de l'OLTP en mémoire, car elle empêche certaines opérations telles que DROP.|  
|Relation contenant-contenu de base de données|La relation contenant-contenu de la base de données n'est pas prise en charge dans une base de données contenant des procédures stockées compilées en mode natif et des tables optimisées en mémoire. Pour plus d'informations, consultez [Bases de données autonomes](../databases/contained-databases.md)|  
|Connexions contextuelles|L'accès aux tables optimisées en mémoire à l'aide de la connexion contextuelle depuis des procédures stockées CLR n'est pas pris en charge.|  
|Curseurs|Curseurs de jeu de clés et dynamiques sur les requêtes qui accèdent aux tables à mémoire optimisée. Ces requêtes sont dégradées en requêtes statiques en lecture seule.|  
|TABLESTAMP|TABLESTAMP n'est pas pris en charge. Pour plus d’informations, consultez [FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql).|  
|AUTO_CLOSE|AUTO_CLOSE n'est pas pris en charge. Pour plus d'informations, consultez [Set the AUTO_CLOSE Database Option to OFF](../policy-based-management/set-the-auto-close-database-option-to-off.md).|  
|Instantanés de base de données|Les instantanés de base de données ne sont pas pris en charge. Pour plus d’informations, consultez [Instantanés de base de données &#40;SQL Server&#41;](../databases/database-snapshots-sql-server.md).|  
|DDL transactionnel|La DLL transactionnelle n'est pas prise en charge avec l'OLTP en mémoire.|  
|Notifications d'événements|Les notifications d'événements ne sont pas prises en charge. Pour plus d'informations, consultez [Event Notifications](../service-broker/event-notifications.md).|  
|Mode fibre|Le mode fibre n'est pas pris en charge avec l'OLTP en mémoire.|  
|Gestion basée sur des stratégies (PBM).|Les modes Prévention et Journal uniquement de PBM ne sont pas pris en charge. L'existence de ces stratégies sur le serveur peut empêcher l'exécution des déclencheurs DDL de l'OLTP en mémoire. Les modes À la demande et Selon la planification sont pris en charge.|  
|Déployer/Extraire DACFX|Le déploiement et l'extraction d'infrastructure DAC ne sont pas pris en charge avec l'OLTP en mémoire.|  
  
 À quelques exceptions, les transactions de bases de données croisées ne sont pas prises en charge. Le tableau suivant décrit les cas sont pris en charge, et les restrictions correspondantes. (Voir aussi [Requêtes de bases de données croisées](cross-database-queries.md).)  
  
|Bases de données|Autorisé|Description|  
|---------------|-------------|-----------------|  
|Bases de données utilisateur, model et msdb|Non|Les requêtes et transactions de bases de données croisées ne sont pas prises en charge.<br /><br /> Les requêtes et les transactions qui accèdent aux tables mémoire optimisées ou aux procédures stockées compilées en mode natif ne peuvent pas accéder à d'autres bases de données, à l'exception de la base de données système master (accès en lecture seule) et de tempdb.|  
|Base de données Resource et tempdb|Oui|Il n'y a pas de restrictions appliquées aux transactions de bases de données croisées qui, à part une base de données en mode mono-utilisateur, utilisent uniquement la base de données Resource et tempdb.|  
|master|Lecture seule|La validation des transactions de bases de données croisées qui impliquent l'OLTP en mémoire et la base de données master échoue si ces transactions incluent des écritures dans la base de données master. Les transactions de bases de données croisées qui n'impliquent que des lectures de la base de données master et utilisent uniquement une base de données mono-utilisateur sont autorisées.|  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge d'OLTP en mémoire par SQL Server](sql-server-support-for-in-memory-oltp.md)  
  
  
