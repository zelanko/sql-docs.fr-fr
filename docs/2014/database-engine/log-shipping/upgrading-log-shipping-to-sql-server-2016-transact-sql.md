---
title: Mise à niveau de la copie des journaux de transaction vers SQL Server 2014 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], upgrading
ms.assetid: b1289cc3-f5be-40bb-8801-0e3eed40336e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 80330d03853c984cfd26100b02918eb218705085
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84931140"
---
# <a name="upgrade-log-shipping-to-sql-server-2014-transact-sql"></a>Mettre à niveau la copie des journaux de transaction vers SQL Server 2014 (Transact-SQL)
  Il est possible de conserver les configurations de copie des journaux de transaction lors d'une mise à niveau de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Cette rubrique décrit les scénarios et les méthodes conseillées pour la mise à niveau d'une configuration de la copie des journaux de transaction.

> [!NOTE]
>  [La compression de la sauvegarde](../../relational-databases/backup-restore/backup-compression-sql-server.md) a été introduite dans [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)]. Une configuration mise à niveau de copie des journaux de transaction utilise l’option de configuration du niveau serveur par défaut pour la **compression de sauvegarde** pour contrôler si la compression de la sauvegarde est utilisée pour les fichiers de sauvegarde du journal des transactions. Le comportement de la compression de la sauvegarde des sauvegardes de fichiers journaux peut être spécifié pour chaque configuration de la copie des journaux de transaction. Pour plus d’informations, consultez [Configurer la copie des journaux de transaction &#40;Transact-SQL&#41;](configure-log-shipping-sql-server.md).


##  <a name="protect-your-data-before-the-upgrade"></a><a name="ProtectData"></a> Protéger vos données avant la mise à niveau
 Comme méthode conseillée, nous vous recommandons de protéger vos données avant une mise à niveau de la copie des journaux de transaction.

 **Pour protéger vos données**

1.  Effectuez une sauvegarde complète de chaque base de données primaire.

     Pour plus d’informations, consultez [Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).

2.  Exécutez la commande [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) sur chaque base de données primaire.

##  <a name="upgrading-the-monitor-server-instance"></a><a name="UpgradeMonitor"></a>Mise à niveau de l’instance du serveur moniteur
 L'instance du serveur moniteur, si elle existe, peut être mise à niveau à tout moment.

 Pendant que le serveur moniteur est mis à niveau, la configuration de la copie des journaux de transaction continue à fonctionner, mais son état n'est pas enregistré dans les tables sur le moniteur. Les alertes qui ont été configurées ne sont pas déclenchées tant que le serveur moniteur est en cours de mise à niveau. Après la mise à niveau, vous pouvez mettre à jour les informations dans les tables du moniteur en exécutant la procédure stockée système [sp_refresh_log_shipping_monitor](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql).

##  <a name="upgrading-log-shipping-configurations-with-a-single-secondary-server"></a><a name="UpgradeSingleSecondary"></a>Mise à niveau des configurations de copie des journaux de route avec un seul serveur secondaire
 Le processus de mise à niveau décrit dans cette section présume une configuration composée du serveur principal et d'un seul serveur secondaire. La figure ci-après illustre cette configuration, avec une instance du serveur principal, A, et une seule instance du serveur secondaire, B.

 ![Un serveur secondaire et aucun serveur moniteur](../media/ls-2-wayconfig-nomonitor.gif "Un serveur secondaire et aucun serveur moniteur")

 Pour plus d'informations sur la mise à niveau de plusieurs serveurs secondaires, consultez [Mise à niveau de plusieurs instances du serveur secondaire](#MultipleSecondaries), plus loin dans cette rubrique.
 

###  <a name="upgrading-the-secondary-server-instance"></a><a name="UpgradeSecondary"></a>Mise à niveau de l’instance de serveur secondaire
 Le processus de mise à niveau implique la mise à niveau des instances de serveur secondaire d'une configuration [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (ou une version supérieure) de copie des journaux de transaction vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] avant la mise à niveau de l'instance du serveur principal. Mettez toujours à niveau l'instance du serveur secondaire en premier. Si le serveur principal a été mis à niveau avant un serveur secondaire, la copie des journaux de transaction échoue parce qu'une sauvegarde créée sur une version plus récente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas être restaurée sur une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

 La copie des journaux de transaction se poursuit durant le processus de mise à niveau parce que les serveurs secondaires mis à niveau continuent à restaurer les sauvegardes des journaux à partir du serveur principal [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (ou une version supérieure). Le processus de mise à niveau des instances de serveur secondaire dépend en partie du fait que la configuration de la copie des journaux de transaction possède ou non plusieurs serveurs secondaires. Pour plus d'informations, consultez [Mise à niveau de plusieurs instances du serveur secondaire](#MultipleSecondaries), plus loin dans cette rubrique.

 Pendant que l'instance de serveur secondaire est mise à niveau, les travaux de copie et de restauration de la copie des journaux de transaction ne s'exécutent pas, de telle sorte que les sauvegardes des journaux des transactions non restaurées s'accumulent. La quantité accumulée dépend de la fréquence de la sauvegarde planifiée sur le serveur principal. De même, si un serveur moniteur séparé a été configuré, il se peut que des alertes soient déclenchées et indiquent que les restaurations n'ont pas été effectuées sur une durée supérieure à l'intervalle configuré.

 Une fois que le serveur secondaire a été mis à niveau, les travaux des agents de la copie des journaux de transaction reprennent et poursuivent la copie et la restauration des sauvegardes de journaux à partir de l'instance du serveur principal, le serveur A. La durée requise pour que le serveur secondaire mette la base de données secondaire à jour varie, selon le temps nécessaire pour mettre à niveau le serveur secondaire et la fréquence des sauvegardes sur le serveur principal.

> [!NOTE]
>  Pendant la mise à niveau du serveur, la base de données secondaire n'est pas mise à niveau vers une base de données [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Elle ne sera mise à niveau que si elle est placée en ligne.

> [!IMPORTANT]
>  L'option RESTORE WITH STANDBY n'est pas prise en charge pour une base de données qui requiert une mise à niveau. Si une base de données secondaire mise à niveau a été configurée à l'aide de RESTORE WITH STANDBY, les journaux des transactions ne peuvent plus être restaurés après la mise à niveau. Pour reprendre la copie des journaux de transaction sur cette base de données secondaire, vous devrez reconfigurer la copie des journaux de transaction sur ce serveur de secours. Pour plus d’informations sur l’option STANDBY, consultez [Restore Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).

###  <a name="upgrading-the-primary-server-instance"></a><a name="UpgradePrimary"></a> Mise à niveau de l'instance du serveur principal
 Lors de la planification d'une mise à niveau, un élément important à prendre en compte est la durée pendant laquelle votre base de données ne sera pas disponible. Le scénario de mise à niveau le plus simple est que la base de données ne soit pas disponible pendant que vous mettez à niveau le serveur principal (scénario 1, ci-après).

 Au prix d'un processus de mise à niveau plus compliqué, vous pouvez augmenter la disponibilité de votre base de données en basculant le serveur principal [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (ou une version supérieure) vers un serveur secondaire [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] avant de mettre à niveau le serveur principal d'origine (scénario 2, ci-après). Il existe deux variantes du scénario de basculement : vous pouvez revenir au serveur principal d'origine et sauvegarder la configuration de la copie des journaux de transaction originale. Autre solution, vous pouvez supprimer la configuration de la copie des journaux de transaction originale avant de mettre à niveau le serveur principal d'origine, puis, ultérieurement, créer une configuration à l'aide du nouveau serveur principal. Cette section décrit ces deux scénarios.

> [!IMPORTANT]
>  Veillez à mettre à niveau l'instance du serveur secondaire avant l'instance du serveur principal. Pour plus d'informations, consultez [Mise à niveau de l'instance du serveur secondaire](#UpgradeSecondary), plus haut dans cette rubrique.


####  <a name="scenario-1-upgrade-primary-server-instance-without-failover"></a><a name="Scenario1"></a>Scénario 1 : mettre à niveau l’instance de serveur principal sans basculement
 C'est le scénario plus simple, mais il se traduit par un temps mort plus important que le basculement. L'instance de serveur principal est simplement mise à niveau et la base de données n'est pas disponible pendant cette mise à niveau.

 Une fois que le serveur est mis à niveau, la base de données est automatiquement remise en ligne, ce qui entraîne sa mise à niveau. Après que la base de données a été mise à niveau, les travaux de la copie des journaux de transaction reprennent.

#### <a name="scenario-2-upgrade-primary-server-instance-with-failover"></a>Scénario 2 : mettre à niveau l'instance de serveur principal avec basculement
 Ce scénario optimise la disponibilité et réduit le temps mort. Il utilise un basculement contrôlé vers l'instance de serveur secondaire, ce qui maintient la base de données disponible pendant que vous mettez à niveau l'instance de serveur principal d'origine. Le temps mort est limité à la période de temps relativement courte nécessaire au basculement, et non à la durée requise pour mettre à niveau l'instance de serveur principal.

 La mise à niveau de l'instance de serveur principal avec le basculement implique trois procédures générales : exécuter un basculement contrôlé sur le serveur secondaire, mettre à niveau l'instance de serveur principal d'origine vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]et installer la copie des journaux de transaction sur une instance de serveur principal [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Ces procédures sont décrites dans la présente section.

> [!IMPORTANT]
>  Si vous prévoyez d'avoir l'instance de serveur secondaire comme nouvelle instance de serveur principal, vous devez supprimer la configuration de la copie des journaux de transaction. La copie des journaux de transaction doit être reconfigurée à partir du nouveau serveur principal vers le nouveau serveur secondaire, une fois que l'instance de serveur principal d'origine a été mise à niveau. Pour plus d’informations, consultez [Supprimer l’envoi de journaux &#40;SQL Server&#41;](remove-log-shipping-sql-server.md).


#####  <a name="procedure-1-perform-a-controlled-failover-to-the-secondary-server"></a><a name="Procedure1"></a>Procédure 1 : effectuer un basculement contrôlé sur le serveur secondaire
 Basculement contrôlé vers le serveur secondaire :

1.  Exécutez manuellement une [sauvegarde de la fin du journal](../../relational-databases/backup-restore/tail-log-backups-sql-server.md) du journal des transactions sur la base de données primaire en spécifiant WITH NORECOVERY. Cette sauvegarde capture les enregistrements de journal qui n'ont pas encore été sauvegardés et place la base de données hors connexion. Notez que pendant que la base de données est hors connexion, le travail de sauvegarde de la copie des journaux de transaction échoue.

     L'exemple suivant crée une sauvegarde de la fin du journal de la base de données `AdventureWorks` du serveur principal. Le fichier de sauvegarde est intitulé `Failover_AW_20080315.trn`:

    ```
    BACKUP LOG AdventureWorks 
      TO DISK = N'\\FileServer\LogShipping\AdventureWorks\Failover_AW_20080315.trn' 
       WITH NORECOVERY;
    GO
    ```

     Nous vous recommandons d'utiliser une convention d'affectation des noms de fichier distincte afin de différencier le fichier de sauvegarde créé manuellement des fichiers de sauvegarde créés par le travail de sauvegarde de la copie des journaux de transaction.

2.  Sur le serveur secondaire :

    1.  Assurez-vous que toutes les sauvegardes effectuées automatiquement par les travaux de sauvegarde de la copie des journaux de transaction ont été appliquées. Pour vérifier quels travaux de sauvegarde ont été appliqués, utilisez la procédure stockée système [sp_help_log_shipping_monitor](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-transact-sql) sur le serveur moniteur ou sur les serveurs principal et secondaires. Le même fichier doit apparaître dans les colonnes **last_backup_file**, **last_copied_file**et **last_restored_file** . Si l'un des fichiers de sauvegarde n'a pas été copié et restauré, appelez manuellement les travaux de copie et de restauration de l'agent pour la configuration de la copie des journaux de transaction.

         Pour plus d'informations sur le démarrage d'un travail, consultez [Start a Job](../../ssms/agent/start-a-job.md).

    2.  Copiez le dernier fichier de sauvegarde de journal créé dans l'étape 1 à partir du partage de fichiers vers l'emplacement local utilisé par la copie des journaux de transaction sur le serveur secondaire.

    3.  Restaurez la dernière sauvegarde de fichier journal en spécifiant WITH RECOVERY pour mettre la base de données en ligne. Dans le cadre de sa mise en ligne, la base de données est mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].

         L'exemple suivant restaure sauvegarde de la fin du journal de la base de données `AdventureWorks` sur la base de données secondaire. L'exemple utilise l'option WITH RECOVERY, qui place la base de données en ligne :

        ```
        RESTORE LOG AdventureWorks 
          FROM DISK = N'c:\logshipping\Failover_AW_20080315.trn' 
           WITH RECOVERY;
        GO
        ```

        > [!NOTE]
        >  Pour une configuration qui contient plusieurs serveurs secondaires, certains éléments supplémentaires sont à prendre en compte. Pour plus d'informations, consultez [Mise à niveau de plusieurs instances du serveur secondaire](#MultipleSecondaries), plus loin dans cette rubrique.

    4.  Basculez la base de données en redirigeant les clients depuis le serveur principal original (serveur A) vers le serveur secondaire en ligne (serveur B).

    5.  Veillez à ce que le journal des transactions de la base de données secondaire ne se remplisse pas pendant que la base de données est en ligne. Pour empêcher le journal des transactions de se remplir, vous pouvez avoir besoin de le sauvegarder. Si tel est le cas, nous vous recommandons de le sauvegarder dans un emplacement partagé, un *partage de sauvegarde*, pour que les sauvegardes soient disponibles pour être restaurées sur l'autre instance de serveur.

#####  <a name="procedure-2-upgrade-the-original-primary-server-instance-to-sscurrent"></a><a name="Procedure2"></a>Procédure 2 : mettre à niveau l’instance du serveur principal d’origine vers[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
 Après avoir mis à niveau l'instance du serveur principal d'origine vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], la base de données demeure hors connexion et dans le format.

#####  <a name="procedure-3-set-up-log-shipping-on-sscurrent"></a><a name="Procedure3"></a>Procédure 3 : configurer la copie des journaux de connexion sur[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
 Le reste du processus de mise à niveau dépend du fait que la copie des journaux de transaction est toujours configurée ou pas, comme suit :

-   Si vous avez conservé la configuration de copie des journaux de transaction [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)](ou version supérieure), revenez à l'instance du serveur principal d'origine. Pour plus d'informations, consultez [Pour revenir à l'instance du serveur principal d'origine](#SwitchToOrigPrimary), plus loin dans cette section.

-   Si vous avez supprimé la configuration de la copie des journaux de transaction avant le basculement, créez une nouvelle configuration de la copie des journaux de transaction dans laquelle l'instance de serveur secondaire d'origine est la nouvelle instance de serveur principal. Pour plus d'informations, consultez [Pour conserver l'ancienne instance du serveur secondaire comme nouvelle instance du serveur principal](#KeepOldSecondaryAsNewPrimary), plus loin dans cette section.

######  <a name="to-switch-back-to-the-original-primary-server-instance"></a><a name="SwitchToOrigPrimary"></a>Pour revenir à l’instance du serveur principal d’origine

1.  Sur le serveur principal temporaire (serveur B), sauvegardez la fin du journal avec l'option WITH NORECOVERY pour créer une sauvegarde de la fin du journal et placer la base de données hors connexion. La sauvegarde de la fin du journal s'intitule `Switchback_AW_20080315.trn`. Par exemple :

    ```
    BACKUP LOG AdventureWorks 
      TO DISK = N'\\FileServer\LogShipping\AdventureWorks\Switchback_AW_20080315.trn' 
       WITH NORECOVERY;
    GO
    ```

2.  Si les sauvegardes des journaux des transactions ont eu lieu sur la base de données primaire temporaire, autres que la sauvegarde de fin créée à l'étape 1, restaurez ces sauvegardes de journaux à l'aide de WITH NORECOVERY sur la base de données hors connexion du serveur principal d'origine (serveur A). La base de données est mise à niveau au format [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] lorsque la première sauvegarde de journal est restaurée.

3.  Restaurez la sauvegarde de la fin du journal, `Switchback_AW_20080315.trn`, sur la base de données primaire d'origine (sur le serveur A) à l'aide de l'option WITH RECOVERY pour mettre la base de données en ligne.

4.  Basculez à nouveau vers la base de données primaire d'origine (sur le serveur A) en redirigeant les clients vers le serveur secondaire en ligne à partir du serveur principal d'origine.

 Après que la base de données a été placée en ligne, la configuration de la copie des journaux de transaction d'origine se poursuit.

######  <a name="to-keep-the-old-secondary-server-instance-as-the-new-primary-server-instance"></a><a name="KeepOldSecondaryAsNewPrimary"></a>Pour conserver l’ancienne instance de serveur secondaire comme nouvelle instance de serveur principal
 Établissez une nouvelle configuration de la copie des journaux de transaction en utilisant l'ancienne instance de serveur secondaire, B, comme serveur principal et l'ancienne instance de serveur principal, A, comme nouveau serveur secondaire :

> [!IMPORTANT]
>  L'ancienne configuration de la copie des journaux de transaction doit avoir été supprimée du serveur principal d'origine au démarrage du processus avant d'effectuer la sauvegarde manuelle des journaux des transactions qui a placé la base de données hors connexion.

1.  Pour éviter d'effectuer une sauvegarde et une restauration complètes de la base de données sur le nouveau serveur secondaire (serveur A), appliquez les sauvegardes de journaux de la nouvelle base de données primaire vers la nouvelle base de données secondaire. Dans l'exemple de configuration, cela nécessite de restaurer les sauvegardes de journaux effectuées sur le serveur B vers la base de données du serveur A.

2.  Sauvegardez le journal à partir de la nouvelle base de données primaire (serveur B).

3.  Restaurez les sauvegardes des journaux vers la nouvelle instance de serveur secondaire (serveur A) à l'aide de WITH NORECOVERY. La première opération de restauration met à jour la base de données vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].

4.  Configurez la copie des journaux de transaction avec le précédent serveur secondaire (serveur B) comme instance de serveur principal.

    > [!IMPORTANT]
    >  Si vous utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], spécifiez que la base de données secondaire est déjà initialisée.

     Pour plus d’informations, consultez [Configurer la copie des journaux de transaction &#40;Transact-SQL&#41;](configure-log-shipping-sql-server.md).

5.  Basculez la base de données en redirigeant les clients depuis le serveur principal original (serveur A) vers le serveur secondaire en ligne (serveur B).

    > [!IMPORTANT]
    >  Lorsque vous basculez vers une nouvelle base de données primaire, vous devez vous assurer que ses métadonnées sont cohérentes avec celles de la base de données principale d'origine. Pour plus d’informations, consultez [Gérer les métadonnées durant la mise à disposition d’une base de données sur une autre instance de serveur &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).

##  <a name="upgrading-multiple-secondary-server-instances"></a><a name="MultipleSecondaries"></a>Mise à niveau de plusieurs instances de serveur secondaire
 La figure ci-après illustre cette configuration, avec une instance du serveur principal, A, et deux instances du serveur secondaire, B et C.

 ![Deux serveurs secondaires et aucun serveur moniteur](../media/ls-3-wayconfig-nomonitor.gif "Deux serveurs secondaires et aucun serveur moniteur")

 Cette section traite de la procédure de mise à niveau avec basculement et du retour au serveur principal d'origine Lors de la mise à niveau de l'instance principale avec le basculement, le processus est plus complexe quand il y a plusieurs instances de serveur secondaire. Dans la procédure suivante, après que tous les serveurs secondaires ont été mis à niveau, le serveur principal est basculé vers l'une des bases de données secondaires mises à niveau. Le serveur principal d'origine est mis à niveau et la copie des journaux de transaction est basculée vers ce serveur.

> [!IMPORTANT]
>  Mettez toujours à niveau toutes les instances de serveur secondaires avant de mettre à niveau le serveur principal.

 **Pour effectuer une mise à niveau avec basculement et retourner au serveur principal d'origine**

1.  Mettez à niveau toutes les instances de serveur secondaire (serveur B et serveur C).

2.  Récupérez la fin du journal des transactions de la base de données primaire (sur le serveur A) et placez la base de données hors connexion, en sauvegardant le journal des transactions avec l'option WITH NORECOVERY.

3.  Sur le serveur secondaire vers lequel vous prévoyez de basculer (serveur B), mettez la base de données secondaire en ligne, en restaurant la sauvegarde du journal à l'aide de WITH RECOVERY.

4.  Sur chaque autre serveur secondaire (serveur C), laissez la base de données secondaire hors ligne en restaurant la sauvegarde de journal à l'aide de WITH NORECOVERY.

    > [!NOTE]
    >  Les travaux de copie et de restauration de la copie des journaux de transaction s'exécutent sur les serveurs secondaires, mais les travaux demeurent inactifs parce que les nouveaux fichiers de sauvegarde des journaux ne sont pas placés sur le partage de sauvegarde.

5.  Basculez la base de données en redirigeant les clients depuis le serveur principal original (serveur A) vers le serveur secondaire en ligne (serveur B). La base de données en ligne devient un serveur principal temporaire, en conservant la base de données disponible pendant que le serveur principal d'origine est hors connexion (serveur A).

6.  Mettez à niveau le serveur principal d'origine (serveur A).

7.  Sur la base de données vers laquelle vous avez basculé-la base de données primaire temporaire (sur le serveur B), sauvegardez manuellement le journal des transactions à l’aide de WITH NORECOVERY. La base de données est alors placée hors connexion.

8.  Restaurez toutes les sauvegardes des journaux des transactions que vous avez créées sur la base de données primaire temporaire (sur le serveur B) sur chaque autre base de données secondaire (sur le serveur C) à l'aide de WITH NORECOVERY. Cela permet à la copie des journaux de transaction de se poursuivre depuis la base de données primaire d'origine après sa mise à niveau, sans nécessiter une restauration de base de données complète sur chaque base de données secondaire.

9. Restaurez le journal des transactions depuis le serveur principal temporaire (serveur B) vers la base de données primaire d'origine (sur le serveur A) à l'aide de l'option WITH RECOVERY.

##  <a name="redeploying-log-shipping"></a><a name="Redeploying"></a>Redéploiement de la copie des journaux de session
 Si vous ne souhaitez pas migrer la configuration de la copie des journaux de transaction à l'aide de l'une des procédures indiquées ci-dessus, vous pouvez redéployer entièrement la copie des journaux de transaction en réinitialisant la base de données secondaire avec une sauvegarde et une restauration complètes de la base de données primaire. Cette option peut être souhaitable si vous avez une base de données peu volumineuse ou si une haute disponibilité n'est pas primordiale pendant la mise à niveau.

 Pour plus d’informations sur l’activation de la copie des journaux de session, consultez [configurer la copie des journaux de &#40;SQL Server&#41;](configure-log-shipping-sql-server.md).

## <a name="see-also"></a>Voir aussi
 Les [sauvegardes du journal des transactions &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md) [appliquer les sauvegardes du journal des transactions &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md) [les tables et les procédures stockées de copie des journaux de](log-shipping-tables-and-stored-procedures.md) transaction.
