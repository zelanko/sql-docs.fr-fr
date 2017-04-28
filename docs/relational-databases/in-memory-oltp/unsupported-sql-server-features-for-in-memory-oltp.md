---
title: "Fonctionnalités SQL Server non prises en charge pour l’OLTP en mémoire | Microsoft Docs"
ms.custom: 
ms.date: 10/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c39f03a7-e223-4fd7-bd30-142e28f51654
caps.latest.revision: 55
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e1b1d4a26616fe83a241267bc87b9e799d883e26
ms.lasthandoff: 04/11/2017

---
# <a name="unsupported-sql-server-features-for-in-memory-oltp"></a>Fonctionnalités SQL Server non prises en charge pour l’OLTP en mémoire
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Cette rubrique décrit les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui ne sont pas prises en charge pour une utilisation avec les objets optimisés en mémoire.  
  
## <a name="includessnoversionincludesssnoversion-mdmd-features-not-supported-for-in-memory-oltp"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fonctionnalités non prises en charge pour l’OLTP en mémoire  
 Les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suivantes ne sont pas prises en charge sur une base de données qui contient des objets optimisés en mémoire (notamment des groupes de fichiers optimisés en mémoire).  
  
|Fonctionnalités non prises en charge|Description de la fonctionnalité|  
|-------------------------|-------------------------|  
|Compression de données pour les tables optimisées en mémoire.|Vous pouvez utiliser la fonctionnalité de compression de données pour compresser les données dans une base de données et réduire la taille de la base de données. Pour plus d’informations, consultez [Data Compression](../../relational-databases/data-compression/data-compression.md).|  
|Partitionnement des tables et des index HASH optimisés en mémoire, ainsi que des index non cluster.|Les données des tables et des index partitionnés sont divisées en unités qui peuvent être réparties sur plusieurs groupes de fichiers d'une base de données. Pour plus d’informations, consultez [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md).|  
|Réplication|Les configurations de réplication autres que la réplication transactionnelle vers des tables optimisées en mémoire sur les abonnés sont incompatibles avec des tables ou des vues qui référencent des tables optimisées en mémoire. La réplication à l'aide de sync_mode=’database snapshot’ n'est pas prise en charge s'il existe un groupe de fichiers optimisé en mémoire. Pour plus d’informations, consultez [Abonnés à la réplication de tables optimisées en mémoire](../../relational-databases/replication/replication-to-memory-optimized-table-subscribers.md).|  
|Mise en miroir|La mise en miroir de base de données n’est pas prise en charge pour les bases de données avec un groupe de fichiers MEMORY_OPTIMIZED_DATA. Pour plus d’informations sur la mise en miroir, consultez [Mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).|  
|Reconstruire le journal|La reconstruction du journal, via un attachement ou ALTER DATABASE, n’est pas prise en charge pour les bases de données avec un groupe de fichiers MEMORY_OPTIMIZED_DATA.|  
|Serveur lié|Vous ne peut pas accéder à des serveurs liés dans la même requête ou transaction en tant que tables optimisées en mémoire. Pour plus d’informations, consultez [Serveurs liés &#40;moteur de base de données&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md).|  
|Journalisation en bloc|Quel que soit le mode de récupération de la base de données, toutes les opérations sur les tables optimisées en mémoire durables sont toujours entièrement journalisées.|  
|Journalisation minimale|La journalisation minimale n'est pas prise en charge pour les tables optimisées en mémoire. Pour plus d’informations sur la journalisation minimale, consultez [Journal des transactions &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md) et [Conditions requises pour une journalisation minimale dans l’importation en bloc](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).|  
|Suivi des modifications|Le suivi des modifications peut être activé sur une base de données avec des objets de l'OLTP en mémoire. Toutefois, les modifications apportées aux tables optimisées en mémoire ne sont pas suivies.|  
|déclencheurs DDL|Les déclencheurs DDL aux niveaux de la base de données et du serveur ne sont pas pris en charge avec les tables de l’OLTP en mémoire et les modules compilés en mode natif.|  
|Capture de données modifiées (CDC)|La capture de données modifiées ne peut pas être utilisée avec une base de données qui contient des tables optimisées en mémoire, car elle utilise un déclencheur DDL pour exécuter une opération DROP TABLE en arrière-plan.|  
|Mode fibre|Le mode fibre n’est pas pris en charge avec les tables optimisées en mémoire :<br /><br /> Si le mode fibre est activé, vous ne pouvez pas créer de bases de données avec des groupes de fichiers optimisés en mémoire ni ajouter de tels groupes aux bases de données existantes.<br /><br /> Vous pouvez activer le mode fibre s'il existe déjà des bases de données avec des groupes de fichiers optimisés en mémoire. Cependant, l'activation du mode fibre nécessite un redémarrage du serveur. Dans cette situation, les bases de données avec des groupes de fichiers optimisés en mémoire ne pourraient pas être récupérées et vous verriez un message d'erreur vous suggérant de désactiver le mode fibre afin de pouvoir utiliser ces bases de données.<br /><br /> L'attachement et la restauration de bases de données avec des groupes de fichiers optimisés en mémoire échouent si le mode fibre est activé. Les bases de données seront marquées comme suspectes.<br /><br /> <br /><br /> Pour plus d’informations, consultez [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).|  
|Limitation de Service Broker|Impossible d'accéder à une file d'attente à partir d'une procédure stockée compilée en mode natif.<br /><br /> Impossible d'accéder à une file d'attente dans une base de données distante, dans une transaction qui accède à des tables optimisées en mémoire.|  
|Réplication sur les abonnés|La réplication transactionnelle vers des tables optimisées en mémoire sur les abonnés est prise en charge, mais avec certaines restrictions. Pour plus d’informations, consultez [Abonnés à la réplication de tables optimisées en mémoire](../../relational-databases/replication/replication-to-memory-optimized-table-subscribers.md).|  
  
 À quelques exceptions, les transactions de bases de données croisées ne sont pas prises en charge. Le tableau suivant décrit les cas sont pris en charge, et les restrictions correspondantes. (Voir aussi [Requêtes de bases de données croisées](../../relational-databases/in-memory-oltp/cross-database-queries.md).)  
  
|Bases de données|Autorisé|Description|  
|---------------|-------------|-----------------|  
|Bases de données utilisateur, model et msdb.|Non|Les requêtes et transactions de bases de données croisées ne sont pas prises en charge.<br /><br /> Les requêtes et les transactions qui accèdent aux tables optimisées en mémoire ou aux procédures stockées compilées en mode natif ne peuvent pas accéder à d'autres bases de données, à l'exception de la base de données système master (accès en lecture seule) et de tempdb.|  
|Base de données Resource, tempdb|Oui|Il n'y a pas de restrictions appliquées aux transactions de bases de données croisées qui, à part une base de données en mode mono-utilisateur, utilisent uniquement la base de données Resource et tempdb.|  
|master|Lecture seule|La validation des transactions de bases de données croisées qui impliquent l'OLTP en mémoire et la base de données master échoue si ces transactions incluent des écritures dans la base de données master. Les transactions de bases de données croisées qui n'impliquent que des lectures de la base de données master et utilisent uniquement une base de données mono-utilisateur sont autorisées.|  
  
## <a name="scenarios-not-supported"></a>Scénarios non pris en charge.  
  
-   Le type de relation contenant-contenu de la base de donnée([bases de données à relation contenant-contenu](../../relational-databases/databases/contained-databases.md)) n’est pas pris en charge avec l’OLTP en mémoire. L'authentification de la base de données à relation contenant-contenu est prise en charge. Toutefois, tous les objets de l'OLTP en mémoire sont marqués comme étant des « relations contenant-contenu essentielles » dans la vue de gestion dynamique dm_db_uncontained_entities.  
  
-   Accès aux tables optimisées en mémoire à l'aide de la connexion contextuelle depuis des procédures stockées CLR.  
  
-   Curseurs de jeu de clés et dynamiques sur les requêtes qui accèdent aux tables optimisées en mémoire. Ces curseurs sont dégradés en statique et en lecture seule.  
  
-   L’utilisation de **MERGE INTO***cible* quand *cible* est une table optimisée en mémoire. **MERGE USING***source* est pris en charge pour les tables optimisées en mémoire.  
  
-   Le type de données ROWVERSION (TIMESTAMP) n’est pas pris en charge. Pour plus d’informations, consultez [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md).  
  
-   La fermeture automatique n’est pas prise en charge par les bases de données avec un groupe de fichiers MEMORY_OPTIMIZED_DATA.  
  
-   Les instantanés de base de données ne sont pas pris en charge par les bases de données avec un groupe de fichiers MEMORY_OPTIMIZED_DATA.  
  
-   DDL transactionnel. Les opérations CREATE/ALTER/DROP des objets OLTP en mémoire ne sont pas prises en charge dans les transactions utilisateur.  
  
-   Notification d'événements  
  
-   Gestion basée sur des stratégies (PBM). Les modes Prévention et Journal uniquement de PBM ne sont pas pris en charge. L'existence de ces stratégies sur le serveur peut empêcher l'exécution des déclencheurs DDL de l'OLTP en mémoire. Les modes À la demande et Selon la planification sont pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge d'OLTP en mémoire par SQL Server](../../relational-databases/in-memory-oltp/sql-server-support-for-in-memory-oltp.md)  
  
  

