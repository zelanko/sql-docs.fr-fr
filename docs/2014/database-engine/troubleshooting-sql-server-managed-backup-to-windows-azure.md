---
title: Résolution des problèmes de gestion de SQL Server de sauvegarde sur Azure | Microsoft Docs
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
ms.openlocfilehash: cbdf7f9b9e8a428ed3d3bf6bfcfe14dbd7da68fc
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153932"
---
# <a name="troubleshooting-sql-server-managed--backup-to-azure"></a>Dépannage de la sauvegarde managée de SQL Server sur Azure
  Cette rubrique décrit les tâches et les outils que vous pouvez utiliser pour résoudre les erreurs qui peuvent se produire lors des opérations de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
## <a name="overview"></a>Présentation  
 La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] comprend des contrôles intégrés et des étapes de dépannage, par conséquent, la plupart des défaillances internes sont prises en charge par le processus de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] lui-même.  
  
 Un exemple de ce cas de figure est la suppression d’un fichier de sauvegarde, ce qui se traduit par une rupture de la séquence de journaux qui affecte la récupérabilité. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] identifie l’interruption dans la chaîne de journalisation et planifie une sauvegarde qui doit être effectuée immédiatement. Toutefois, nous vous recommandons de surveiller l'état et de résoudre les erreurs qui nécessitent une intervention manuelle.  
  
 La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] enregistre les événements et les erreurs à l'aide de procédures stockées système, de vues système et d'événements étendus. Les vues et les procédures stockées système fournissent les informations de configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], l'état des sauvegardes planifiées, ainsi que les erreurs capturées par les événements étendus. La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] utilise les événements étendus pour capturer les erreurs qui doivent être résolues. En plus d'enregistrer les événements, les stratégies SQL Server Smart Admin fournissent l'état d'intégrité utilisé par le travail de notification par courrier électronique pour notifier les erreurs et les problèmes. Pour plus d’informations, consultez [Monitor SQL Server Managed Backup to Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] utilise également la même journalisation que celle utilisée lors de la sauvegarde manuelle dans le stockage Azure (SQL Server sauvegarde vers une URL). Pour plus d’informations sur les problèmes liés à la sauvegarde vers une URL, consultez la section résolution des problèmes dans [SQL Server meilleures pratiques et résolution des problèmes de sauvegarde vers une URL](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
### <a name="general-troubleshooting-steps"></a>Étapes de dépannage générales  
  
1.  Activez la notification par courrier électronique pour recevoir des courriers électroniques en cas d'erreurs ou d'avertissements.  
  
     Exécutez aussi régulièrement `smart_admin.fn_get_health_status` pour vérifier le nombre agrégé des erreurs. Par exemple, `number_of_invalid_credential_errors` est le nombre de fois où la sauvegarde intelligente a tenté une sauvegarde, mais a rencontré une erreur d'informations d'identification non valides. `Number_of_backup_loops` et `number_of_retention_loops` ne sont pas des erreurs ; mais indiquent le nombre de fois où le thread de sauvegarde et le thread de rétention ont analysé la liste de bases de données. En règle générale, lorsque @begin_time et @end_time ne sont pas fournis, la fonction affiche les informations des 30 dernières minutes, puis les valeurs non nulles sont normalement affichées pour ces deux colonnes. Si des valeurs égales à zéro s'affichent, cela indique que le système est surchargé ou qu'il ne répond pas. Pour plus d’informations, consultez la section **résolution des problèmes système** plus loin dans cette rubrique.  
  
2.  Passez en revue les journaux des événements étendus pour obtenir plus de détails sur les erreurs et les autres événements associés.  
  
3.  Utilisez les informations des journaux pour résoudre le problème.  En cas de problème ou d'erreur système, vous devrez peut-être redémarrer le service ou SQL Server Agent.  
  
### <a name="common-causes-of-errors"></a>Causes courantes d'erreur  
 Voici une liste des causes courantes aboutissant à un échec :  
  
1.  **Modifications apportées aux informations d’identification SQL :** Si le nom des informations d’identification utilisées par [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est modifié ou supprimé, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ne sera pas en mesure d’effectuer des sauvegardes. La modification doit être appliquées aux paramètres de configuration de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
2.  **Modifications apportées aux valeurs des clés d’accès de stockage :** Si les valeurs de clé de stockage sont modifiées pour le compte Azure, mais que les informations d’identification SQL ne sont pas mises à jour avec les nouvelles valeurs, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] échoue lors de l’authentification auprès du stockage et ne parvient pas à sauvegarder les bases de données configurées pour utiliser ce compte.  
  
3.  **Modifications apportées au compte de stockage Azure :** La suppression ou le changement de nom du compte de stockage sans modification correspondante des informations d’identification SQL entraîne l’échec de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] et aucune sauvegarde n’est effectuée. Si vous supprimez un compte de stockage, assurez-vous que les bases de données sont reconfigurées avec des informations de compte de stockage valides. Si un compte de stockage est renommé ou les valeurs de clé sont modifiées, vérifiez que ces changements sont répercutés dans les informations d'identification SQL utilisées par la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
4.  **Modifications apportées aux propriétés de la base de données :** Les modifications apportées aux modèles de récupération ou à la modification du nom peuvent entraîner l’échec des sauvegardes.  
  
5.  **Modifications du mode de récupération :** Si le mode de récupération de la base de données est modifié en mode simple ou journalisé en bloc, les sauvegardes s’arrêtent et les bases de données sont ignorées par [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Pour plus d’informations, consultez [SQL Server gestion de la sauvegarde sur Azure : interopérabilité et coexistence](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
### <a name="most-common-error-messages-and-solutions"></a>Messages d'erreur courants et solutions  
  
1.  **Erreurs lors de l’activation ou de la configuration de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]:**  
  
     Erreur : «échec de l’accès à l’URL de stockage... Fournissez des informations d’identification SQL valides...» : vous pouvez voir cela et d’autres erreurs similaires se rapportant aux informations d’identification SQL.  Dans ce cas, examinez le nom des informations d’identification SQL que vous avez fournies, ainsi que les informations stockées dans les informations d’identification SQL, le nom du compte de stockage et la clé d’accès de stockage, et assurez-vous qu’elles sont à jour et valides.  
  
     Erreur : «... Impossible de configurer la base de données... comme il s’agit d’une base de données système», cette erreur s’affiche si vous tentez d’activer [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour une base de données système.  La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ne prend pas en charge les bases de données système.  Pour configurer la sauvegarde d'une base de données système, utilisez d'autres technologies de sauvegarde SQL Server, comme les plans de maintenance.  
  
     Erreur : «... Fournir une période de rétention....» : vous pouvez voir des erreurs concernant la période de rétention si vous n’avez pas spécifié de période de rétention pour la base de données ou l’instance lorsque vous configurez ces valeurs pour la première fois. Vous verrez également cette erreur si vous avez utilisé une valeur non comprise dans la plage 1 à 30. Les valeurs autorisées pour la période de rétention sont un nombre compris entre 1 et 30.  
  
2.  **Erreurs de notification par courrier électronique :**  
  
     Erreur : « Database Mail n’est pas activé... ». cette erreur s’affiche si vous activez les notifications par courrier électronique, mais que Database Mail n’est pas configurée sur l’instance. Vous devez configurer la messagerie de base de données sur l'instance pour recevoir une notification de l'état d'intégrité de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Pour plus d’informations sur l’activation de la messagerie de base de données, consultez [configurer des Database mail](../relational-databases/database-mail/configure-database-mail.md). Vous devez également permettre à SQL Server Agent d'utiliser la messagerie de base de données pour les notifications. Pour plus d’informations, consultez [avant de commencer](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md#BeforeYouBegin).  
  
     Voici une liste de numéros d'erreur que vous pouvez voir, qui sont associés aux notifications par message électronique :  
  
    -   ErrorNumber : 45209  
  
    -   ErrorNumber : 45210  
  
    -   ErrorNumber : 45211  
  
3.  **Erreurs de connectivité :**  
  
    -   **Erreurs liées à la connectivité SQL :** Ces erreurs se produisent en cas de problème de connexion à SQL Server instance. Les événements étendus exposent ces types d'erreurs via le canal d'administration. Voici deux événements étendus que vous pouvez voir pour les erreurs relatives à ce type de problème de connectivité :  
  
         FileRetentionAdminXEvent avec l'event_type = SqlError. Pour les détails de cette erreur, observez l'error_code, l'error_message et le stack_trace de cet événement. Le error_code est le numéro d’erreur de SqlException.  
  
         SmartBackupAdminXevent avec les messages/préfixes de message suivants :  
  
         *«Une erreur interne s’est produite lors de la configuration de SQL Server sauvegarde managée dans les paramètres Azure par défaut pour l’instance. L’erreur peut être temporaire.»*  
  
         *«Il est probable que des problèmes de connectivité avec SQL Server. La base de données est ignorée dans l’itération actuelle.»*  
  
         *«Échec de l’interrogation des informations sur l’utilisation du journal. L’échec peut être temporaire. La base de données est ignorée dans l’itération actuelle.»*  
  
         *«Exception SQL rencontrée lors du chargement des métadonnées de l’agent SSMBackup2WA. L’échec peut être temporaire. L’opération va être retentée.»*  
  
         *«SSMBackup2WA a rencontré une exception SQL lors de... "*  
  
    -   **Erreurs lors de la connexion au compte de stockage :**  
  
         Les exceptions de stockage sont répertoriées dans FileRetentionAdminXEvent avec l'event_type = XstoreError. Pour les détails de l'erreur, observez l'error_message et le stack_trace de cet événement.  
  
         Étant donné que la sauvegarde managée de SQL Server utilise la technologie de sauvegarde vers l'URL sous-jacente, les erreurs liées à la connectivité du stockage s'appliquent aux deux fonctionnalités. Pour plus d’informations sur les étapes de dépannage, consultez la **section Troubleshooting** de l’article [meilleures pratiques et dépannage de la SQL Server sauvegarde vers une URL](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md) .  
  
### <a name="troubleshooting-system-issues"></a>Dépannage des problèmes du système  
 Voici des scénarios d'un problème avec le système (SQL Server, SQL Server Agent) et ses effets sur [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] :  
  
-   **Sqlservr. exe cesse de répondre ou cesse de fonctionner lorsque [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est en cours d’exécution :** Si SQL Server cesse de fonctionner, l’agent SQL s’arrête normalement, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] s’arrête également et les événements sont consignés dans le fichier SQL Agent. out.  
  
     Si SQL Server ne répond plus, des événements sont consignés dans le canal d'administration.  Exemple du journal des événements :  
  
     *Erreur SQL (le moteur ne répond pas ou récupérez SqlException : SqlException :*    
     *code d’erreur, message et StackTrace s’affichent dans un canal d’administration XEvent, ainsi que des informations supplémentaires, telles que :*    
    *«Il est probable que des problèmes de connectivité avec SQL Server. La base de données est ignorée dans l’itération actuelle.»*  
  
-   **L’agent SQL ne répond plus ou cesse de fonctionner lorsque [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est en cours d’exécution :**  
  
     Si l'Agent SQL s'arrête, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] s'arrête également et des événements sont consignés dans le canal d'administration. Ce comportement est similaire à celui des scénarios dans lesquels SQL Server ne répond plus.  
  
     Si l'Agent SQL ne répond plus, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ne pourra pas continuer les opérations de sauvegarde, et des événements sont consignés dans le canal d'administration. Exemple du journal des événements :  
  
     *Blocage du travail : Voir le canal d’administration xevents*   
    *« Une mise à jour de progression n’a pas été reçue de SQL Server dans plus de «constantes. DBBackupInfoMsgMaxWaitTime + » heures pour la sauvegarde de base de données.   La sauvegarde du Cloud SSM va continuer à attendre.»*  
  
 Si vous avez activé la notification par message électronique, vous recevrez une notification qui comprend le **Nombre de boucles de sauvegarde** et le **Nombre de boucles de rétention**. Si la valeur retournée dans la notification pour une de ces deux colonnes ou les deux est zéro, cela peut indiquer que le système ne répond pas.  
  
> [!WARNING]  
>  Les processus internes qui génèrent les résultats du rapport supposent que les journaux de diagnostic du moteur sont dans le même emplacement que le journal d'erreurs SQL Agent, qui est par défaut dans le même dossier que les journaux d'erreurs de l'instance de SQL Server. Si les journaux de diagnostic du moteur sont déplacés dans un autre emplacement que l'emplacement du journal d'erreurs de SQL Agent, le système ne trouve pas les journaux de diagnostic de la sauvegarde intelligente et, par conséquent, le rapport dans la notification par messagerie peut-être incorrect. Par exemple, vous pouvez voir la valeur **0** dans tous les champs, y compris pour le nombre de boucles de sauvegarde et pour le nombre de boucles de rétention. Dans ce cas, lorsque les journaux de diagnostic sont déplacés dans un autre emplacement, cela ne signifie pas que le système ne répond pas, mais qu'il ne trouve pas les journaux. Vérifiez d'abord que l'emplacement des journaux de diagnostic et des journaux d'erreurs de SQL Agent est le même. Pour vérifier l’emplacement actuel des journaux de diagnostic, vous pouvez utiliser [sys. dm_os_server_diagnostics_log_configurations](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-server-diagnostics-log-configurations). La colonne `path` retourne l’emplacement actuel des journaux de diagnostic du moteur.  Il doit se trouver dans le même dossier que les journaux d’erreurs de l’agent SQL. Pour obtenir le chemin d'accès du journal d'erreurs de SQL Agent, utilisez la procédure stockée `dbo.sp_get_sqlagent_properties`.  
  
 Consultez les journaux des événements étendus pour afficher les détails des erreurs. Résolvez les erreurs, ou redémarrez SQL Server Agent pour résoudre le problème.  
  
  
