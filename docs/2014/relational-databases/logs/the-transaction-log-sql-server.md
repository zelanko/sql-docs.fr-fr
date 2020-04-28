---
title: Journal des transactions (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 01/04/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- transaction logs [SQL Server], about
- databases [SQL Server], transaction logs
- logs [SQL Server], transaction logs
ms.assetid: d7be5ac5-4c8e-4d0a-b114-939eb97dac4d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1b4a175ad850ccbb0711a0997c3658cf01497686
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "79289407"
---
# <a name="the-transaction-log-sql-server"></a>Journal des transactions (SQL Server)
  Chaque base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a un journal des transactions qui enregistre toutes les transactions et les modifications apportées par chacune d’entre elles. Le journal des transactions doit être vidé régulièrement pour éviter qu'il ne soit saturé. Toutefois, certains facteurs peuvent retarder la troncation du journal. Par conséquent, il est important de surveiller la taille du journal. Certaines opérations peuvent faire l'objet d'une journalisation minimale afin de réduire leur impact sur la taille des journaux de transactions.  
  
 Le journal des transactions est un composant essentiel de la base de données et, en cas de défaillance du système, vous pouvez en avoir besoin pour rétablir la cohérence de la base de données. Le journal des transactions ne doit jamais être supprimé ni déplacé, à moins d'en avoir pleinement compris les conséquences.  
  
> [!NOTE]  
>  Différents points de contrôle créent des points de référence connus et fiables à partir desquels vous pouvez commencer à appliquer les journaux des transactions lors de la récupération d'une base de données. Pour plus d’informations, consultez [Points de contrôle de base de données &#40;SQL Server&#41;](database-checkpoints-sql-server.md).  
  
 **Dans cette rubrique :**  
  
-   [Avantages : opérations prises en charge par le journal des transactions](#Benefits)  
  
-   [Troncation du journal des transactions](#Truncation)  
  
-   [Facteurs pouvant retarder la troncation du journal](#FactorsThatDelayTruncation)  
  
-   [Opérations pouvant être journalisées au minimum](#MinimallyLogged)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="benefits-operations-supported-by-the-transaction-log"></a><a name="Benefits"></a>Avantages : opérations prises en charge par le journal des transactions  
 Le journal des transactions prend en charge les opérations suivantes :  
  
-   Récupération des transactions individuelles  
  
-   Récupération de toutes les transactions incomplètes au démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Restauration par progression d'une base de données, d'un fichier, d'un groupe de fichiers ou d'une page jusqu'au point de défaillance  
  
-   Prise en charge de la réplication transactionnelle  
  
-   Prise en charge de la haute disponibilité et de solutions de récupération d'urgence : [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], mise en miroir de bases de données et copie des journaux de transaction.  
  
##  <a name="transaction-log-truncation"></a><a name="Truncation"></a>Troncation du journal des transactions  
 La troncation du journal libère de l'espace dans le fichier journal pour que le journal des transactions puisse le réutiliser. La troncation du journal est essentielle pour empêcher que le journal se remplisse. Elle supprime les fichiers journaux virtuels inactifs du journal des transactions logique d'une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ce qui libère de l'espace dans le journal logique de façon à ce qu'il soit réutilisé par le journal des transactions physique. Si un journal des transactions n'était jamais tronqué, il finirait par occuper tout l'espace disque alloué à ses fichiers journaux physiques.  
  
 Pour éviter ce problème, à moins que la troncation du journal ne soit retardée pour une raison quelconque, la troncation se produit automatiquement après les événements suivants :  
  
-   En mode de récupération simple, après un point de contrôle.  
  
-   En mode de récupération complète ou de récupération utilisant les journaux de transactions, si un point de contrôle s'est produit depuis la sauvegarde précédente, la troncation se produit après une sauvegarde de fichier journal (sauf s'il s'agit d'une sauvegarde de copie uniquement).  
  
 Pour plus d'informations, consultez [Facteurs pouvant retarder la troncation du journal](#FactorsThatDelayTruncation), plus loin dans cette rubrique.  
  
> [!NOTE]  
>  La troncation du journal ne réduit pas la taille du fichier journal physique. Pour réduire la taille physique d'un fichier journal physique, vous devez réduire le fichier journal. Pour plus d'informations sur la réduction de la taille du fichier journal physique, consultez [Gérer la taille du fichier journal des transactions](manage-the-size-of-the-transaction-log-file.md).  
  
##  <a name="factors-that-can-delay-log-truncation"></a><a name="FactorsThatDelayTruncation"></a>Facteurs pouvant retarder la troncation du journal  
 Lorsque les enregistrements de journal restent actifs longtemps, la troncation du journal des transactions est retardée, et le journal des transactions risque de se remplir entièrement.  
  
> [!IMPORTANT]  
>  Pour plus d’informations sur la façon de répondre à un journal des transactions saturé, consultez [Résoudre les problèmes liés à un journal des transactions saturé&#40;Erreur SQL Server 9002&#41;](troubleshoot-a-full-transaction-log-sql-server-error-9002.md).  
  
 La troncation du journal peut être retardée pour différents motifs. Le cas échéant, vous pouvez rechercher les raisons qui empêchent de tronquer le journal en interrogeant les colonnes **log_reuse_wait** et **log_reuse_wait_desc** de l’affichage catalogue [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) . Le tableau suivant décrit les valeurs possibles de ces colonnes.  
  
|Valeur log_reuse_wait|Valeur log_reuse_wait_desc|Description|  
|----------------------------|----------------------------------|-----------------|  
|0|NOTHING|Il existe actuellement un ou plusieurs fichiers journaux virtuels réutilisables.|  
|1|CHECKPOINT|Aucun point de contrôle n'est apparu depuis la dernière troncation du journal ou le début du journal n'est pas encore allé au-delà d'un fichier journal virtuel. (Tous les modes de récupération)<br /><br /> Il s'agit d'une raison courante de retarder la troncation du journal. Pour plus d’informations, consultez [Points de contrôle de base de données &#40;SQL Server&#41;](database-checkpoints-sql-server.md).|  
|2|LOG_BACKUP|Une sauvegarde du journal est requise avant que le journal des transactions puisse être tronqué. (Mode de récupération complète ou mode de récupération utilisant les journaux de transactions uniquement)<br /><br /> Lorsque la sauvegarde de journal suivante est terminée, l'espace du journal peut devenir réutilisable.|  
|3|ACTIVE_BACKUP_OR_RESTORE|Une sauvegarde de données ou une restauration est en cours (tous les modes de récupération).<br /><br /> Si une sauvegarde des données empêche la troncation du journal, l'annulation de l'opération de sauvegarde peut résoudre le problème immédiat.|  
|4|ACTIVE_TRANSACTION|Une transaction est active (tous les modes de récupération).<br /><br /> Une transaction longue peut exister au démarrage de la sauvegarde du fichier journal. Dans ce cas, libérer l'espace peut requérir une autre sauvegarde du fichier journal. Notez qu’une transaction de longue durée empêche la troncation du journal dans tous les modes de récupération, y compris le mode de récupération simple, dans lequel le journal des transactions est généralement tronqué sur chaque point de contrôle automatique.<br /><br /> Une transaction est différée. Une *transaction différée* est en fait une transaction active dont la restauration est bloquée à cause d'une ressource indisponible. Pour plus d’informations sur les causes des transactions différées et la manière de les faire sortir de l’état différé, consultez [Transactions différées &#40;SQL Server&#41;](../backup-restore/deferred-transactions-sql-server.md). <br /><br />Les transactions à long terme peuvent également remplir le journal des transactions de tempdb. La base de données tempdb est implicitement utilisée par les transactions utilisateur pour les objets internes tels que les tables de travail pour le tri, les fichiers de travail pour le hachage, les tables de travail de curseur et la gestion de version de ligne. Même si la transaction utilisateur comprend uniquement des données de lecture (requêtes SELECT), des objets internes peuvent être créés et utilisés sous des transactions utilisateur. Ensuite, le journal des transactions tempdb peut être rempli.|  
|5|DATABASE_MIRRORING|La mise en miroir de bases de données est interrompue ou, en mode haute performance, la base de données miroir se trouve derrière la base de données principale de manière significative. (Mode de récupération complète uniquement)<br /><br /> Pour plus d’informations, consultez [Mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).|  
|6|RÉPLICATION|Durant les réplications transactionnelles, les transactions liées aux publications ne sont pas encore remises à la base de données de distribution. (Mode de récupération complète uniquement)<br /><br /> Pour plus d'informations sur la réplication transactionnelle, consultez [SQL Server Replication](../../relational-databases/replication/sql-server-replication.md).|  
|7|DATABASE_SNAPSHOT_CREATION|Un instantané de base de données est créé. (Tous les modes de récupération)<br /><br /> Il s'agit d'une raison courante et habituellement brève du retard de la troncation du journal.|  
|8|LOG_SCAN|Une analyse du journal se produit. (Tous les modes de récupération)<br /><br /> Il s'agit d'une raison courante et habituellement brève du retard de la troncation du journal.|  
|9|AVAILABILITY_REPLICA|Un réplica secondaire d'un groupe de disponibilité applique les enregistrements du journal des transactions de cette base de données à une base de données secondaire associée. (Mode de récupération complète)<br /><br /> Pour plus d’informations, consultez [vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).|  
|10|-|Usage interne uniquement|  
|11|-|Usage interne uniquement|  
|12|-|Usage interne uniquement|  
|13|OLDEST_PAGE|Si une base de données est configurée pour utiliser des points de contrôle indirects, la page la plus ancienne dans la base de données peut être plus ancienne que le LSN du point de contrôle. Dans ce cas, la page la plus ancienne peut retarder la troncation du journal. (Tous les modes de récupération)<br /><br /> Pour plus d’informations sur les points de contrôle indirects, consultez [Points de contrôle de base de données &#40;SQL Server&#41;](database-checkpoints-sql-server.md).|  
|14|OTHER_TRANSIENT|Cette valeur n'est pas utilisée actuellement.|  
|16|XTP_CHECKPOINT|Quand une base de données possède un groupe de fichiers à mémoire optimisée, aucune troncation du journal des transactions ne peut avoir lieu avant le déclenchement du point de contrôle automatique [!INCLUDE[hek_2](../../includes/hek-2-md.md)] (ce qui se produit chaque fois que le journal croît de 512 Mo).<br /><br /> Remarque : pour tronquer le journal des transactions avant la taille de 512 Mo, déclenchez la commande Checkpoint manuellement sur la base de données en question.|  
  
##  <a name="operations-that-can-be-minimally-logged"></a><a name="MinimallyLogged"></a>Opérations pouvant être journalisées au minimum  
 La*journalisation minimale* implique de ne journaliser que les informations obligatoires pour pouvoir récupérer la transaction sans prendre en charge la récupération jusqu’à une date et heure. Cette rubrique identifie les opérations qui sont journalisées au minimum en mode de récupération utilisant les journaux de transactions (ainsi qu'en mode de récupération simple, sauf lorsqu'une sauvegarde est en cours).  
  
> [!NOTE]  
>  La journalisation minimale n'est pas prise en charge pour les tables à mémoire optimisée.  
  
> [!NOTE]  
>  En mode de récupération complète, toutes les opérations en bloc sont entièrement journalisées. Cependant, vous pouvez minimiser la journalisation d'un ensemble d'opérations en bloc en faisant temporairement passer la base de données en mode de récupération utilisant les journaux de transactions pour les opérations en bloc. La journalisation minimale est plus efficace que la journalisation complète et réduit la possibilité pour une opération en bloc de grande envergure d'occuper l'espace disponible du journal des transactions pendant une transaction en bloc. En revanche, si la base de données est endommagée ou perdue lors de la journalisation minimale, vous ne pouvez pas récupérer la base de données jusqu'au point de défaillance.  
  
 Les opérations suivantes, qui sont entièrement journalisées en mode de récupération complète, font l'objet d'une journalisation minimale en modes simple et de récupération utilisant les journaux de transactions :  
  
-   Opérations d’importation en bloc ([bcp](../../tools/bcp-utility.md), [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql)et [INSERT... SELECT](/sql/t-sql/statements/insert-transact-sql)). Pour plus d'informations sur les conditions dans lesquelles la journalisation d'une importation en bloc dans une table est minimale, consultez [Prerequisites for Minimal Logging in Bulk Import](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
    > [!NOTE]  
    >  Lorsque la réplication transactionnelle est activée, les opérations BULK INSERT sont entièrement journalisées, même dans le mode de récupération utilisant les journaux de transactions.  
  
-   Opérations SELECT [into](/sql/t-sql/queries/select-into-clause-transact-sql) .  
  
    > [!NOTE]  
    >  Lorsque la réplication transactionnelle est activée, les opérations SELECT INTO sont entièrement journalisées, même dans le mode de récupération utilisant les journaux de transactions.  
  
-   Mises à jour partielles vers des types de données de valeur élevée, en incluant la clause .WRITE dans l'instruction [UPDATE](/sql/t-sql/queries/update-transact-sql) lors de l'insertion ou de l'ajout de nouvelles données. Notez que la journalisation minimale n'est pas utilisée quand des valeurs existantes sont mises à jour. Pour plus d’informations sur les types de données de valeur élevée, consultez [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
-   [Instructions WRITETEXT](/sql/t-sql/queries/writetext-transact-sql) et [UPDATETEXT](/sql/t-sql/queries/updatetext-transact-sql) lors de l’insertion ou de l’ajout de `text`nouvelles `ntext`données dans `image` les colonnes de type de données, et. Notez que la journalisation minimale n'est pas utilisée quand des valeurs existantes sont mises à jour.  
  
    > [!NOTE]  
    >  L'emploi des instructions WRITETEXT et UPDATETEXT est déconseillé, c'est pourquoi vous devez éviter de les utiliser dans les nouvelles applications.  
  
-   Si la base de données est en mode simple ou de récupération utilisant les journaux de transactions, certaines opérations DDL avec index sont journalisées au minimum qu'elles soient exécutées hors connexion ou en ligne. Les opérations journalisées minimales impliquant les index sont les suivantes :  
  
    -   Opérations[CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) (vues indexées comprises).  
  
    -   Opérations[ALTER INDEX](/sql/t-sql/statements/alter-index-transact-sql) REBUILD ou DBCC DBREINDEX.  
  
        > [!NOTE]  
        >  L'emploi de l'instruction DBCC DBREINDEX est déconseillé, c'est pourquoi vous devez l'éviter dans les nouvelles applications.  
  
    -   Reconstruction d'un nouveau segment de mémoire DROP INDEX (le cas échéant).  
  
        > [!NOTE]  
        >   La désallocation de pages d'index au cours d'une opération [DROP INDEX](/sql/t-sql/statements/drop-index-transact-sql) est toujours entièrement journalisée.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
 `Managing the transaction log`  
  
-   [Gérer la taille du fichier journal des transactions](manage-the-size-of-the-transaction-log-file.md)  
  
-   [Résoudre les problèmes liés à un journal des transactions saturé &#40;erreur SQL Server 9002&#41;](troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
 **Sauvegarde du journal des transactions (mode de récupération complète)**  
  
-   [Sauvegarder un journal des transactions &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md)  
  
 **Restauration du journal des transactions (mode de récupération complète)**  
  
-  [Restaurer une sauvegarde du journal des transactions](../backup-restore/restore-a-transaction-log-backup-sql-server.md)   
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler la durabilité des transactions](control-transaction-durability.md)   
 [Conditions préalables à la journalisation minimale dans l’importation en bloc](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md)   
 [Sauvegarder et restaurer des bases de données SQL Server](../backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Points de contrôle de base de données &#40;SQL Server&#41;](database-checkpoints-sql-server.md)   
 [Afficher ou modifier les propriétés d’une base de données](../databases/view-or-change-the-properties-of-a-database.md)   
 [Modes de récupération &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md)  
  
  
