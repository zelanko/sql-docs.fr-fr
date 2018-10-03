---
title: Dépannage de SQL Server Managed Backup to Windows Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: a34d35b0-48eb-4ed1-9f19-ea14754650da
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 00d66f99c09292046f2372621faf65e01757b80c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48121748"
---
# <a name="troubleshooting-sql-server-managed--backup-to-windows-azure"></a>Dépannage de la sauvegarde managée de SQL Server sur Microsoft Azure
  Cette rubrique décrit les tâches et les outils que vous pouvez utiliser pour résoudre les erreurs qui peuvent se produire lors des opérations de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
## <a name="overview"></a>Vue d'ensemble  
 La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] comprend des contrôles intégrés et des étapes de dépannage, par conséquent, la plupart des défaillances internes sont prises en charge par le processus de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] lui-même.  
  
 C'est par exemple le cas lorsqu'un fichier de sauvegarde est supprimé et entraîne la rupture de la séquence de journaux de transactions consécutifs en affectant la récupérabilité. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] identifie la rupture de la séquence de journaux de transactions et planifie une sauvegarde à effectuer immédiatement. Toutefois, nous vous recommandons de surveiller l'état et de résoudre les erreurs qui nécessitent une intervention manuelle.  
  
 La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] enregistre les événements et les erreurs à l'aide de procédures stockées système, de vues système et d'événements étendus. Les vues et les procédures stockées système fournissent les informations de configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], l'état des sauvegardes planifiées, ainsi que les erreurs capturées par les événements étendus. La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] utilise les événements étendus pour capturer les erreurs qui doivent être résolues. En plus d'enregistrer les événements, les stratégies SQL Server Smart Admin fournissent l'état d'intégrité utilisé par le travail de notification par courrier électronique pour notifier les erreurs et les problèmes. Pour plus d’informations, consultez [moniteur sauvegarde managée SQL Server sur Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] utilise également la même journalisation que celle utilisée lors de la sauvegarde manuelle dans le stockage Windows Azure (Sauvegarde SQL Server vers une URL). Pour plus d’informations sur la sauvegarde vers une URL relative des problèmes, consultez la section Dépannage de [SQL Server Backup to URL meilleures pratiques et dépannage](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
### <a name="general-troubleshooting-steps"></a>Étapes de dépannage générales  
  
1.  Activez la notification par courrier électronique pour recevoir des courriers électroniques en cas d'erreurs ou d'avertissements.  
  
     Exécutez aussi régulièrement `smart_admin.fn_get_health_status` pour vérifier le nombre agrégé des erreurs. Par exemple, `number_of_invalid_credential_errors` est le nombre de fois où la sauvegarde intelligente a tenté une sauvegarde, mais a rencontré une erreur d'informations d'identification non valides. `Number_of_backup_loops` et `number_of_retention_loops` ne sont pas des erreurs ; mais indiquent le nombre de fois où le thread de sauvegarde et le thread de rétention ont analysé la liste de bases de données. En règle générale, lorsque @begin_time et @end_time ne sont pas fournies, la fonction affiche les informations des 30 dernières minutes, puis nous devrions voir normalement des valeurs zéro pour ces deux colonnes. Si des valeurs égales à zéro s'affichent, cela indique que le système est surchargé ou qu'il ne répond pas. Pour plus d’informations, consultez **résolution des problèmes de système** section plus loin dans cette rubrique.  
  
2.  Passez en revue les journaux des événements étendus pour obtenir plus de détails sur les erreurs et les autres événements associés.  
  
3.  Utilisez les informations des journaux pour résoudre le problème.  En cas de problème ou d'erreur système, vous devrez peut-être redémarrer le service ou SQL Server Agent.  
  
### <a name="common-causes-of-errors"></a>Causes courantes d'erreur  
 Voici une liste des causes courantes aboutissant à un échec :  
  
1.  **Modifications apportées aux informations d’identification SQL :** si le nom de l’information d’identification utilisé par [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est modifié ou si elle est supprimée, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ne sera pas en mesure d’effectuer des sauvegardes. La modification doit être appliquées aux paramètres de configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
2.  **Modifications apportées aux valeurs de clé de l’accès de stockage :** si les valeurs de clé de stockage sont modifiées pour le compte Windows Azure, mais les informations d’identification SQL n’est pas mis à jour avec les nouvelles valeurs, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] échoue lors de l’authentification pour le stockage et ne parvient pas à la sauvegarde bases de données configurées pour utiliser ce compte.  
  
3.  **Modifications apportées à un compte de stockage Windows Azure :** suppression ou modification du nom de compte de stockage sans provoquent modifications correspondantes apportées à l’information d’identification SQL [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] échoue et aucune sauvegarde ne va être retirée. Si vous supprimez un compte de stockage, assurez-vous que les bases de données sont reconfigurées avec des informations de compte de stockage valides. Si un compte de stockage est renommé ou les valeurs de clé sont modifiées, vérifiez que ces changements sont répercutés dans les informations d'identification SQL utilisées par la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
4.  **Changements apportés aux propriétés de la base de données :** changements apportés aux modèles de récupération ou modification du nom peut provoquer des sauvegardes échouent.  
  
5.  **Modifications apportées au mode de récupération :** si le mode de récupération de la base de données est modifié de simple de complet ou journalisé en bloc, sauvegardes s’arrêtent, et les bases de données va être ignorées par [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Pour plus d’informations, consultez [SQL Server Managed Backup pour Windows Azure : interopérabilité et Coexistence](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
### <a name="most-common-error-messages-and-solutions"></a>Messages d'erreur courants et solutions  
  
1.  **Erreurs lors de l’activation ou la configuration [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]:**  
  
     Erreur : « Impossible d'accéder à l'URL de stockage… Fournissez une SQL informations d’identification valides... » : Vous pouvez voir cela et autres erreurs similaires qui fait référence aux informations d’identification SQL.  Dans ces cas de figure, vérifiez le nom indiqué dans les informations d'identification SQL fournies et les autres informations stockées, notamment, le nom du compte de stockage et la clé d'accès au stockage, puis assurez-vous que les informations sont actuelles et valides.  
  
     Erreur : »... Impossible de configurer la base de données … car il s’agit d’une base de données système » : vous verrez cette erreur si vous essayez d’activer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données système.  La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ne prend pas en charge les bases de données système.  Pour configurer la sauvegarde d'une base de données système, utilisez d'autres technologies de sauvegarde SQL Server, comme les plans de maintenance.  
  
     Erreur : «... Fournissez une période de rétention... » : Vous pouvez voir des erreurs concernant la période de rétention si vous le n'avez pas spécifié une période de rétention pour l’instance ou la base de données lorsque vous configurez ces valeurs pour la première fois. Vous verrez également cette erreur si vous avez utilisé une valeur non comprise dans la plage 1 à 30. Les valeurs autorisées pour la période de rétention sont un nombre compris entre 1 et 30.  
  
2.  **Erreurs de Notification de courrier électronique :**  
  
     Erreur : « la messagerie de base de données n'est pas activée... » – Vous verrez cette erreur si vous activez les notifications par courrier électronique, mais la messagerie de base de données n’est pas configurée sur l’instance. Vous devez configurer la messagerie de base de données sur l'instance pour recevoir une notification de l'état d'intégrité de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Pour plus d’informations sur la façon d’activer la messagerie de base de données, consultez [configurer la messagerie de base de données](../relational-databases/database-mail/configure-database-mail.md). Vous devez également permettre à SQL Server Agent d'utiliser la messagerie de base de données pour les notifications. Pour plus d’informations, consultez [avant de commencer](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md#BeforeYouBegin).  
  
     Voici une liste de numéros d'erreur que vous pouvez voir, qui sont associés aux notifications par message électronique :  
  
    -   Numéro d’erreur : 45209  
  
    -   Numéro d’erreur : 45210  
  
    -   ErrorNumber : 45211  
  
3.  **Erreurs de connectivité :**  
  
    -   **Erreurs liées à la connectivité SQL :** ces erreurs se produisent lorsqu’il existe des problèmes de connexion à une instance de SQL Server. Les événements étendus exposent ces types d'erreurs via le canal d'administration. Voici deux événements étendus que vous pouvez voir pour les erreurs relatives à ce type de problème de connectivité :  
  
         FileRetentionAdminXEvent avec l'event_type = SqlError. Pour les détails de cette erreur, observez l'error_code, l'error_message et le stack_trace de cet événement. L'error_code est le numéro d'erreur de SqlException.  
  
         SmartBackupAdminXevent avec les messages/préfixes de message suivants :  
  
         *« Une erreur interne s’est produite lors de la configuration de sauvegarde managée SQL Server pour les paramètres par défaut de Windows Azure par exemple. Erreur peut être temporaire. »*  
  
         *« Probablement rencontre des problèmes de connectivité avec SQL Server. Elle est ignorée dans l’itération actuelle. »*  
  
         *« Interrogation des informations sur l’utilisation du journal a échoué. L'échec peut être temporaire. Elle est ignorée dans l’itération actuelle. »*  
  
         *« Exception SQL rencontrée lors du chargement des métadonnées de l’agent SSMBackup2WA. L'échec peut être temporaire. Opération sera retentée. »*  
  
         *« SSMBackup2WA a rencontré une exception SQL lors de … "*  
  
    -   **Erreurs de connexion au compte de stockage :**  
  
         Les exceptions de stockage sont répertoriées dans FileRetentionAdminXEvent avec l'event_type = XstoreError. Pour les détails de l'erreur, observez l'error_message et le stack_trace de cet événement.  
  
         Étant donné que la sauvegarde managée de SQL Server utilise la technologie de sauvegarde vers l'URL sous-jacente, les erreurs liées à la connectivité du stockage s'appliquent aux deux fonctionnalités. Pour plus d’informations sur les étapes de dépannage, consultez **section Dépannage** de la [SQL Server Backup to URL meilleures pratiques et dépannage](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md) article.  
  
### <a name="troubleshooting-system-issues"></a>Dépannage des problèmes du système  
 Voici des scénarios d'un problème avec le système (SQL Server, SQL Server Agent) et ses effets sur [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] :  
  
-   **Sqlservr.exe ne répond plus ou s’arrête lorsque [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est en cours d’exécution :** si SQL Server cesse de fonctionner, s’arrête l’Agent SQL, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] également s’arrête et les événements sont consignés dans le fichier SQL Agent.out.  
  
     Si SQL Server ne répond plus, des événements sont consignés dans le canal d'administration.  Exemple du journal des événements :  
  
     *Erreur SQL (moteur ne répond ne pas ou obtient sqlException : SqlException :*   
     *trace de la pile, le message et code d’erreur seront affichera dans un événement étendu du canal admin, avec des informations supplémentaires, telles que :*   
    *« Probablement rencontre des problèmes de connectivité avec SQL Server. Base de données est ignorée dans l’itération actuelle »*  
  
-   **L’Agent SQL ne répond plus ou cesse de fonctionner lorsque [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est en cours d’exécution :**  
  
     Si l'Agent SQL s'arrête, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] s'arrête également et des événements sont consignés dans le canal d'administration. Ce comportement est similaire à celui des scénarios dans lesquels SQL Server ne répond plus.  
  
     Si l'Agent SQL ne répond plus, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ne pourra pas continuer les opérations de sauvegarde, et des événements sont consignés dans le canal d'administration. Exemple du journal des événements :  
  
     *Travail se bloque : voir les événements étendus de canal admin*   
    *« Une mise à jour de progression n’a pas été reçu à partir de SQL Server dans plus de "+ Constants.DBBackupInfoMsgMaxWaitTime + « heures pour la sauvegarde de base de données.   Sauvegarde sur le Cloud SSM doit continuer à attendre. »*  
  
 Si vous avez activé la notification par courrier électronique, vous recevrez une notification qui comprend **nombre de boucles de sauvegarde** et **nombre de boucles de rétention**. Si la valeur retournée dans la notification pour une de ces deux colonnes ou les deux est zéro, cela peut indiquer que le système ne répond pas.  
  
> [!WARNING]  
>  Les processus internes qui génèrent les résultats du rapport supposent que les journaux de diagnostic du moteur sont dans le même emplacement que le journal d'erreurs SQL Agent, qui est par défaut dans le même dossier que les journaux d'erreurs de l'instance de SQL Server. Si les journaux de diagnostic du moteur sont déplacés dans un autre emplacement que l'emplacement du journal d'erreurs de SQL Agent, le système ne trouve pas les journaux de diagnostic de la sauvegarde intelligente et, par conséquent, le rapport dans la notification par messagerie peut-être incorrect. Par exemple, vous pouvez voir une valeur de **0** dans tous les champs, y compris le nombre de boucles de sauvegarde et le nombre de boucles de rétention. Dans ce cas, lorsque les journaux de diagnostic sont déplacés dans un autre emplacement, cela ne signifie pas que le système ne répond pas, mais qu'il ne trouve pas les journaux. Vérifiez d'abord que l'emplacement des journaux de diagnostic et des journaux d'erreurs de SQL Agent est le même. Pour vérifier l’emplacement actuel des journaux de diagnostics, vous pouvez utiliser [sys.dm_os_server_diagnostics_log_configurations](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-server-diagnostics-log-configurations). Le `path` colonne retourne l’emplacement actuel du moteur de journaux de diagnostic.  Il doit être dans le même dossier que les journaux des erreurs SQL Agent. Pour obtenir le chemin d'accès du journal d'erreurs de SQL Agent, utilisez la procédure stockée `dbo.sp_get_sqlagent_properties`.  
  
 Consultez les journaux des événements étendus pour afficher les détails des erreurs. Résolvez les erreurs, ou redémarrez SQL Server Agent pour résoudre le problème.  
  
  
