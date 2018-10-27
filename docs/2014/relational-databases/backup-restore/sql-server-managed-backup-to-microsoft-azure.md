---
title: SQL Server sauvegarde managée sur Windows Azure | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: afa01165-39e0-4efe-ac0e-664edb8599fd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: af11bb2283db0561c176fb543ff21c3c04f676d3
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100250"
---
# <a name="sql-server-managed--backup-to-windows-azure"></a>Gestion de sauvegarde de SQL Server vers Microsoft Azure
  La [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] gère et automatise les sauvegardes SQL Server dans le service de stockage d'objets blob Windows Azure. La stratégie de sauvegarde utilisée par la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] est basée sur la période de rétention et la charge de travail transactionnelle sur la base de données. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] prend en charge la restauration limitée dans le temps pour la période de rétention spécifiée.   
La [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] peut être activée au niveau de la base de données ou au niveau de l'instance pour gérer toutes les bases de données sur l'instance de SQL Server. SQL Server peut s'exécuter dans un environnement local ou hébergé, tel qu'une machine virtuelle Windows Azure. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] est recommandée pour SQL Server s’exécutant sur des Machines virtuelles Windows Azure.  
  
## <a name="benefits-of-automating-sql-server-backup-using-includesssmartbackupincludesss-smartbackup-mdmd"></a>Avantages de l'automatisation de la sauvegarde SQL Server à l'aide de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]  
  
-   Actuellement, l'automatisation des sauvegardes pour plusieurs bases de données requiert le développement d'une stratégie de sauvegarde, l'écriture d'un code personnalisé et la planification des sauvegardes. La [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] exige uniquement que vous indiquiez les paramètres de période de rétention et l'emplacement de stockage. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] planifie, exécute et administre les sauvegardes.  
  
     La [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] peut être configurée au niveau de la base de données, ou avec les paramètres par défaut d'une instance de SQL Server. Automatisation à l’aide de sauvegarde [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] présente les avantages suivants :  
  
    -   En définissant les valeurs par défaut au niveau de l'instance, vous pouvez appliquer les paramètres de la stratégie à n'importe quelle base de données créée par la suite, supprimer le risque d'avoir de nouvelles bases de données non sauvegardées et de perte de données.  
  
    -   L'option d'activation de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] et la configuration de la période de rétention au niveau de la base de données vous permettent de remplacer le jeu de paramètres par défaut au niveau de l'instance. Vous pouvez ainsi avoir un contrôle plus granulaire sur la récupération d'une base de données spécifique.  
  
-   Avec la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], vous n'avez pas besoin de spécifier le type ou la fréquence des sauvegardes pour une base de données.  Vous spécifiez la période de rétention et [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] détermine le type et la fréquence des sauvegardes pour une base de données stocke les sauvegardes sur le service de stockage d’objets Blob Windows Azure. Pour plus d’informations sur l’ensemble de critères qui [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] utilise pour créer la stratégie de sauvegarde, consultez le [composants et Concepts](#Concepts) dans cette rubrique.  
  
-   Lorsque l'utilisation du chiffrement est configurée, vous disposez d'une protection supplémentaire pour les données de sauvegarde. Pour plus d’informations, consultez [chiffrement de sauvegarde](backup-encryption.md)  
  
 Pour plus d’informations sur les avantages de l’utilisation du stockage d’objets Blob Windows Azure pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sauvegardes, consultez [SQL Server Backup and Restore with Windows Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
## <a name="terms-and-definitions"></a>Termes et définitions  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]  
 Une fonctionnalité SQL Server qui automatise la sauvegarde de bases de données et administre les sauvegardes en fonction de la période de rétention.  
  
 Période de rétention  
 La période de rétention est utilisée par la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour déterminer les fichiers de sauvegarde qui doivent être retenus dans le stockage pour restaurer une base de données à un point précis dans le temps au cours d'une période spécifiée.  Les valeurs prises en charge s'échelonnent sur une plage de 1 à 30 jours.  
  
 Séquence de journaux de transactions consécutifs  
 Une séquence continue de sauvegardes de journaux s'appelle une séquence de journaux de transactions consécutifs. Une séquence de journaux de transactions consécutifs commence par une sauvegarde complète de la base de données.  
  
##  <a name="Concepts"></a> Configuration requise, Concepts et composants  
  
  
###  <a name="Security"></a> Permissions  
 Transact-SQL est l'interface principale utilisée pour configurer et surveiller la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. En règle générale, pour exécuter la configuration de procédures stockées, **db_backupoperator** rôle de base de données avec **ALTER ANY CREDENTIAL** autorisations, et `EXECUTE` autorisations sur **sp_delete_ backuphistory** procédure stockée n’est requise.  Les procédures stockées et les fonctions utilisées pour passer en revue les informations nécessitent généralement des autorisations `Execute` sur la procédure stockée et `Select` sur la fonction, respectivement.  
  
###  <a name="Prereqs"></a> Conditions préalables  
 **Configuration requise :**  
  
 **Service de stockage Windows Azure** est utilisé par [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour stocker les fichiers de sauvegarde.    Les concepts, la structure et la configuration requise pour créer un compte de stockage Windows Azure est expliqué en détail dans le [Introduction aux Concepts et composants de la clé](sql-server-backup-to-url.md#intorkeyconcepts) section de la **SQL Server Backup to URL** rubrique.  
  
 **Informations d’identification SQL** est utilisé pour stocker les informations requises pour authentifier le compte de stockage Windows Azure. L'objet contenant les informations d'identification SQL stocke le nom du compte et les informations de la clé d'accès. Pour plus d’informations, consultez le [Introduction aux Concepts et composants de la clé](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) section dans le **SQL Server Backup to URL** rubrique. Pour une procédure pas à pas sur la création des informations d’identification SQL pour stocker les informations d’authentification Windows Azure Storage, consultez [leçon 2 : créer des informations d’identification SQL Server](../../tutorials/lesson-2-create-a-sql-server-credential.md).  
  
###  <a name="Concepts_Components"></a> Concepts et composants clés  
 La [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] est une fonctionnalité qui gère les opérations de sauvegarde. Il stocke les métadonnées dans le **msdb** sauvegardes du journal des travaux de système de base de données et utilise pour écrire des transactions et la base de données complète.  
  
#### <a name="components"></a>Components  
 Transact-SQL est l'interface principale utilisée pour interagir avec la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Les procédures stockées système sont utilisées pour activer, configurer et surveiller la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Les fonctions système sont utilisées pour récupérer des paramètres de configuration existants, des valeurs de paramètre et des informations sur le fichier de configuration. Les événements étendus sont utilisés pour exposer des erreurs et des avertissements. Les mécanismes d'alerte sont activés via les travaux SQL Agent et la gestion basées sur des stratégies SQL Server. Voici la liste des objets et la description de leurs fonctionnalités en relation à la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 Des applets de commande PowerShell sont également disponibles pour configurer la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. SQL Server Management Studio prend en charge la restauration de sauvegardes créées par la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] à l'aide de la tâche **Restaurer la base de données** .  
  
|||  
|-|-|  
|Objet système|Description|  
|**MSDB**|Stocke les métadonnées et l'historique de toutes les sauvegardes créées par la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|  
|[smart_admin.set_db_backup &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)|Procédures stockées système pour activer et configurer la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour une base de données.|  
|[smart_admin.set_instance_backup &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/dn451009(v=sql.120).aspx)|Procédures stockées système pour activer et configurer les paramètres par défaut [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour l’instance de SQL Server.|  
|[smart_admin.sp_ backup_master_switch &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql)|Procédures stockées système pour interrompre et reprendre la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|  
|[smart_admin.sp_set_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql)|Procédures stockées système pour activer et configurer la surveillance pour la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Exemples : activer les événements étendus, les paramètres de courrier électronique pour les notifications.|  
|[smart_admin.sp_backup_on_demand &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql)|Système de procédure stockée qui est utilisé pour effectuer une sauvegarde ad hoc pour une base de données est activé pour utiliser [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] sans rompre la séquence de journaux.|  
|[smart_admin.fn_backup_db_config &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-backup-db-config-transact-sql)|Fonction système qui retourne actuel [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] état et la configuration des valeurs d’une base de données, ou pour toutes les bases de données sur l’instance.|  
|[smart_admin.fn_is_master_switch_on &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-is-master-switch-on-transact-sql)|Fonction système qui retourne l'état du commutateur principal.|  
|[smart_admin.sp_get_backup_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-get-backup-diagnostics-transact-sql)|Procédure stockée système utilisée pour retourner les événements enregistrés par les événements étendus.|  
|[smart_admin.fn_get_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)|Fonction système qui retourne les valeurs actuelles des paramètres système de la sauvegarde comme les paramètres de surveillance et de courrier électronique pour les alertes.|  
|[smart_admin.fn_available_backups &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql)|Procédure stockée utilisée pour récupérer les sauvegardes disponibles pour une base de données spécifiée ou pour toutes les bases de données dans une instance.|  
|[smart_admin.fn_get_current_xevent_settings &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql)|Fonction système qui retourne les paramètres actuels des événements étendus.|  
|[smart_admin.fn_get_health_status &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-health-status-transact-sql)|Fonction système qui retourne le décompte agrégé des erreurs enregistrées par les événements étendus pour une période spécifiée.|  
|[Surveiller la sauvegarde managée SQL Server sur Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)|Événements étendus pour la surveillance, notifications par message électronique des erreurs et avertissements, gestion basée sur une stratégie SQL Server pour la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|  
  
#### <a name="backup-strategy"></a>Stratégie de sauvegarde  
 **Stratégie de sauvegarde utilisée par [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]:**  
  
 Le type des sauvegardes planifiées et leur fréquence sont déterminés en fonction de la charge de travail de la base de données. Les paramètres de période de rétention sont utilisés pour déterminer la période pendant laquelle un fichier de sauvegarde doit être retenu dans le stockage et la capacité à restaurer une base de données à un point précis dans le temps au cours de la période de rétention.  
  
 **Conteneur de sauvegarde et les Conventions d’affectation de noms de fichiers :**  
  
 La [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] nomme le conteneur de stockage Windows Azure en utilisant le nom de l'instance SQL Server pour les bases de données, excepté les bases de données de disponibilité.  Pour les bases de données de disponibilité, le GUID du groupe de disponibilité est utilisé pour nommer le conteneur de stockage Windows Azure.  
  
 Le fichier de sauvegarde des bases de données autres que des bases de données de disponibilité est nommé en utilisant les 40 premiers caractères du nom de la base de données, le GUID de la base de données ‘-‘ et l'horodateur. Le caractère de soulignement est inséré entre les segments comme délimiteurs. L'extension **.bak** est utilisée pour le fichier en cas de sauvegarde complète et l'extension **.log** est utilisée pour les sauvegardes de journal. Pour les bases de données d'un groupe de disponibilité, en plus de la convention d'attribution de noms décrite ci-dessus, le GUID de la base de données du groupe de disponibilité est ajouté après les 40 caractères du nom de la base de données. La valeur du GUID de la base de données du groupe de disponibilité est la valeur de group_database_id dans sys.databases.  
  
 **Sauvegarde de base de données complète :** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] agent planifie une sauvegarde de base de données complète si une des opérations suivantes est vraie.  
  
-   La [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] est activée sur une base de données pour la première fois, ou la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] est activée avec les paramètres par défaut au niveau de l'instance.  
  
-   La taille du journal depuis la dernière sauvegarde de base de données complète est égale ou supérieure à 1 Go.  
  
-   L'intervalle maximum d'une semaine est dépassé depuis la dernière sauvegarde de base de données complète.  
  
-   La séquence de journaux de transactions consécutifs est rompue. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] vérifie périodiquement si la séquence de journaux de transactions consécutifs est intacte en comparant le premier et le dernier LSN des fichiers de sauvegarde. Si la séquence de journaux de transactions consécutifs est rompue pour un motif quelconque, la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] planifie une sauvegarde de base de données complète. Le motif le plus fréquent d'une rupture de la séquence de journaux de transactions consécutifs est le plus souvent une commande de sauvegarde émise à l'aide de Transact-SQL ou via la tâche de sauvegarde dans SQL Server Management Studio.  D'autres scénarios communs sont la suppression accidentelle des fichiers journaux de sauvegarde ou le remplacement accidentel des sauvegardes.  
  
 **Sauvegarde de fichier journal :** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] planifie une sauvegarde du journal si une des opérations suivantes est vraie :  
  
-   L'historique des sauvegardes de journaux est introuvable. Cela se produit habituellement lorsque la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] est activée la première fois.  
  
-   L'espace du journal des transactions utilisé dépasse 5 Mo.  
  
-   L'intervalle maximum de 2 heures est dépassé depuis la dernière sauvegarde de journal.  
  
-   Lorsque la sauvegarde du journal des transactions traîne derrière une sauvegarde complète de la base de données. Le but est de conserver la séquence de journaux de transactions consécutifs avant la sauvegarde complète.  
  
#### <a name="retention-period-settings"></a>Paramètres de période de rétention  
 Lorsque vous configurez la sauvegarde, vous devez définir la période de rétention en jours : 1 jour au minimum et 30 jours au maximum.  
  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] , en fonction des paramètres de la période de rétention, évalue la capacité à restaurer une base de données à un point précis dans le temps au cours de la période de rétention pour déterminer quels sont les fichiers de sauvegarde à conserver et quels sont ceux à supprimer. Le paramètre backup_finish_date de la sauvegarde est utilisé pour déterminer et vérifier la durée spécifiée dans les paramètres de la période de rétention.  
  
#### <a name="important-considerations"></a>Éléments importants à prendre en considération  
 Certains éléments doivent être pris en considération, car ils ont un impact important sur les opérations de [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Ils sont répertoriés ci-dessous :  
  
-   Pour une base de données, si un travail de sauvegarde complète de base de données est en cours, la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] attend la fin du travail avant d'effectuer une autre sauvegarde complète de la même base de données. De même, une seule sauvegarde de journal de transactions peut être exécutée à la fois. Toutefois, une sauvegarde de base de données complète et une sauvegarde de journal peuvent s'exécuter simultanément. Les échecs sont enregistrés en tant qu'événements étendus.  
  
-   Si plus de 10 sauvegardes de base de données complètes sont planifiées simultanément, un avertissement est généré au moyen du canal de débogage des événements étendus. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] met alors en file d'attente les bases de données qui restent à sauvegarder, jusqu'à ce que toutes les sauvegardes soient planifiées et terminées.  
  
###  <a name="support_limits"></a> Limitations de prise en charge  
 Voici quelques limitations spécifiques à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] :  
  
-   L'agent de [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] prend en charge les sauvegardes complètes de base de données et les sauvegardes de fichier journal uniquement.  La sauvegarde automatique de fichier n'est pas prise en charge.  
  
-   Les opérations de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] sont actuellement prises en charge à l'aide de Transact-SQL. La surveillance et le dépannage peuvent être effectués à l'aide d'événements étendus. La prise en charge de PowerShell et SMO est limitée à la configuration des paramètres par défaut du stockage et de la période de rétention pour une instance de SQL Server, et à la surveillance de l'état de la sauvegarde et de l'état d'intégrité général en fonction des stratégies de gestion basée sur des stratégies SQL Server.  
  
-   Les bases de données système ne sont pas prises en charge.  
  
-   Le service de stockage Blob Windows Azure est la seule option de stockage de sauvegarde prise en charge. Les sauvegardes sur disque ou sur bande ne sont pas prises en charge.  
  
-   Actuellement, la taille maximale de fichier autorisée pour un objet blob de page dans le Stockage Microsoft Azure est 1 To. Les fichiers de sauvegarde d'une taille supérieure à 1 To échouent. Afin d'éviter cette situation, nous vous recommandons, pour les bases de données de grande taille, d'utiliser la compression et de tester la taille du fichier de sauvegarde avant de configurer la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Pour le test, effectuez une sauvegarde sur un disque local ou une sauvegarde manuelle dans le stockage Windows Azure à l'aide de l'instruction Transact-SQL `BACKUP TO URL`. Pour plus d’informations, consultez [SQL Server Backup to URL](sql-server-backup-to-url.md).  
  
-   Modèles de récupération : seules les bases de données en mode de récupération complète ou en mode de récupération utilisant les journaux de transactions sont prises en charge.  Les bases de données utilisant le mode de récupération simple ne sont pas prises en charge.  
  
-   [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] peut avoir d'autres limitations lorsqu'elle est configurée avec d'autres technologies prenant en charge la sauvegarde, la haute disponibilité ou la récupération d'urgence. Pour plus d’informations, consultez [SQL Server Managed Backup pour Windows Azure : interopérabilité et Coexistence](../../database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md).  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
|||  
|-|-|  
|**Les descriptions des tâches**|**Rubrique**|  
|Tâches de base telles que la configuration de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour une base de données, ou la configuration des paramètres par défaut au niveau de l'instance, la désactivation de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] au niveau de l'instance ou de la base de données, l'interruption et la reprise de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|[Sauvegarde managée SQL Server sur Microsoft Azure : Paramètres de conservation et de stockage](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)|  
|**Didacticiel :** instructions étape par étape pour la configuration et la surveillance [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|[Configuration de la sauvegarde managée SQL Server sur Microsoft Azure](enable-sql-server-managed-backup-to-microsoft-azure.md)|  
|**Didacticiel :** instructions étape par étape pour la configuration et de surveillance [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour les bases de données dans le groupe de disponibilité.|[Configuration de la sauvegarde managée de SQL Server sur Microsoft Azure pour les groupes de disponibilité](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)|  
|Outils, concepts et tâches relatifs à la surveillance de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|[Surveiller la sauvegarde managée SQL Server sur Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)|  
|Outils et étapes pour dépanner la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|[Dépannage de la sauvegarde managée de SQL Server sur Microsoft Azure](../../database-engine/troubleshooting-sql-server-managed-backup-to-windows-azure.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Backup and Restore with Windows Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)   
 [SQL Server Backup to URL](sql-server-backup-to-url.md)   
 [SQL Server sauvegarde managée sur Windows Azure : interopérabilité et Coexistence](../../database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)   
 [Dépannage de la sauvegarde managée de SQL Server sur Microsoft Azure](../../database-engine/troubleshooting-sql-server-managed-backup-to-windows-azure.md)  
  
  
