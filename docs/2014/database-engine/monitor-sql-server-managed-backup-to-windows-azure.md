---
title: Surveiller SQL Server Managed Backup to Windows Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: cfb9e431-7d4c-457c-b090-6f2528b2f315
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b7b7b6cc8127b339a45a5f651af6db4d0b595b80
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62844557"
---
# <a name="monitor-sql-server-managed-backup-to-windows-azure"></a>Surveiller la sauvegarde managée SQL Server sur Windows Azure
  La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] possède des mesures intégrées permettant d'identifier les problèmes et les erreurs pendant les processus de sauvegarde et les corrige lorsque cela est possible.  Toutefois, dans certaines situations, l'intervention de l'utilisateur est requise. Cette rubrique décrit les outils que vous pouvez utiliser pour déterminer l'état d'intégrité général des sauvegardes, et identifier les erreurs qui doivent être corrigées.  
  
## <a name="overview-of-includesssmartbackupincludesss-smartbackup-mdmd-built-in-debugging"></a>Présentation du débogage intégré de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]  
 La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] vérifie périodiquement les sauvegardes planifiées et tente de replanifier toute sauvegarde ayant échoué. Elle interroge régulièrement le compte de stockage pour identifier une rupture des séquences de journaux de transactions affectant la récupérabilité de la base de données et planifie de nouvelles sauvegardes en conséquence. Il prend également en compte les stratégies d'accélération de Windows Azure et possède des mécanismes pour gérer plusieurs sauvegardes de base de données. La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] enregistre et utilise des événements étendus pour suivre toutes les activités. Les canaux d'événements étendus utilisés par l'agent de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] comprennent les canaux d'administration, opérationnel, analytique et de débogage. Les événements tombant sous la catégorie d'administration sont généralement liés aux erreurs, nécessitent l'intervention de l'utilisateur et sont activés par défaut. Les événements analytiques sont également activés par défaut, mais ne sont généralement pas liés à des erreurs nécessitant l'intervention de l'utilisateur. Les événements opérationnels sont généralement informatifs. Par exemple, les événements opérationnels incluent la planification d’une sauvegarde, la réussite de la sauvegarde. Le débogage est le plus détaillé et est utilisé en interne par [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour déterminer les problèmes et corrigez-les si nécessaire.  
  
### <a name="configure-monitoring-parameters-for-includesssmartbackupincludesss-smartbackup-mdmd"></a>Configurer les paramètres de surveillance de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]  
 Le **smart_admin.sp_set_parameter** procédure stockée système vous permet de spécifier les paramètres de surveillance. Les sections suivantes expliquent pas à pas la procédure d'activation des événements étendus et l'activation de la notification par courrier électronique des erreurs et des avertissements.  
  
 Le **smart_admin.fn_get_parameter** fonction peut être utilisée pour obtenir la valeur actuelle d’un paramètre spécifique ou tous les paramètres configurés. Si les paramètres n'ont jamais été configurés, la fonction ne retourne aucune valeur.  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. La configuration actuelle des événements étendus et des notifications par courrier électronique est retournée.  
  
```  
Use msdb  
Go  
SELECT * FROM smart_admin.fn_get_parameter (NULL)  
GO  
```  
  
 Pour plus d’informations, consultez [smart_admin.fn_get_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)  
  
### <a name="extended-events-for-monitoring"></a>Événements étendus pour la surveillance  
 Les événements d'administration, opérationnels et analytiques sont activés par défaut. Les événements d'administration sont les plus importants et utiles pour détecter les erreurs qui nécessitent une intervention manuelle. Vous pouvez activer les événements opérationnels et de débogage, mais tenez compte du fait qu'ils sont commentés, et demandent à être filtrés. Les procédures ci-dessous montrent comment surveiller les événements enregistrés via les événements étendus.  
  
> [!IMPORTANT]  
>  Contrairement aux événements étendus du moteur SQL, la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ne prend pas en charge les principes de session d'événements étendus. Procédures stockées système et fonctions sont les outils utilisés pour interagir avec des événements étendus. Vous pouvez également consulter le journal des événements étendus dans le répertoire des journaux.  
  
##### <a name="to-configure-and-view-extended-events"></a>Pour configurer et afficher les événements étendus  
  
1.  Consultez les canaux d'événements étendus disponibles et leur état en exécutant la requête suivante :  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     La sortie de cette requête affiche l'event_name, qu'il soit configurable ou non, et l'état activé ou désactivé actuel.  Pour plus d’informations, consultez [smart_admin.fn_get_current_xevent_settings &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql).  
  
2.  Pour activer les événements de débogage, exécutez la requête suivante :  
  
    ```  
    --  to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
     Pour plus d’informations sur la procédure stockée, consultez [smart_admin.sp_set_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql).  
  
3.  Pour consulter les événements enregistrés, exécutez la requête suivante :  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
### <a name="aggregated-error-countshealth-status"></a>Nombre agrégé d'erreurs/état d'intégrité  
 Le **smart_admin.fn_get_health_status** fonction retourne une table de nombre agrégé d’erreurs pour chaque catégorie peut être utilisé pour surveiller l’état d’intégrité [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Cette même fonction est également utilisée par le mécanisme de notification par courrier électronique configuré au niveau du système, décrit plus loin dans cette rubrique.   
Ces nombres agrégés peuvent servir à surveiller l'intégrité du système. Par exemple, si la colonne number_ of_retention_loops indique 0 pour 30 minutes, il est possible que la gestion de la rétention soit trop longue, ou que l'événement ne fonctionne pas correctement. Les colonnes contenant des erreurs peuvent indiquer des problèmes et les journaux des événements étendus doivent être consultés pour en découvrir la cause. Vous pouvez également appeler **smart_admin.sp_get_backup_diagnostics** procédure stockée pour rechercher les détails de l’erreur.  
  
### <a name="using-agent-notification-for-assessing-backup-status-and-health"></a>Utiliser la notification de l'agent pour déterminer l'état de sauvegarde et d'intégrité  
 La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] comprend un mécanisme de notification utilisant les stratégies de gestion basées sur la stratégie SQL Server.  
  
 **Configuration requise :**  
  
-   Une messagerie de base de données est requise pour utiliser cette fonctionnalité. Pour plus d’informations sur comment activer la messagerie de base de données pour l’instance de SQL Server, consultez [configurer la messagerie de base de données](../relational-databases/database-mail/configure-database-mail.md).  
  
-   Les propriétés du système d'alerte de SQL Server Agent doivent être configurées pour utiliser la messagerie de base de données.  
  
 **Architecture de notification :**  
  
-   **Gestion basée sur la stratégie :** Deux stratégies sont utilisées pour surveiller l’intégrité de sauvegarde : **Intelligente de stratégie de contrôle d’intégrité système Admin**et le **intelligente de stratégie de contrôle d’intégrité d’Action utilisateur administrateur**. La stratégie d'intégrité du système Smart Admin évalue les erreurs critiques, comme des informations d'identification SQL manquantes ou non valides, les erreurs de connectivité, et signale l'intégrité du système. Elle nécessite généralement une action manuelle pour corriger le problème sous-jacent. La stratégie d'intégrité des actions de l'utilisateur Smart Admin évalue les avertissements concernant, par exemple, les sauvegardes corrompues, ou d'autres événements similaires.  Elle ne nécessite généralement aucune action, et signale simplement un événement. Ces problèmes sont automatiquement résolus par l'agent de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
-   **L’Agent SQL Server** travail : La notification est effectuée à l’aide d’un travail de SQL Server Agent comportant trois étapes de travail. Dans la première étape, l'agent détecte si la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est configurée pour une base de données ou pour l'instance. S'il trouve la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] activée et configurée, il exécute la seconde étape à l'aide d'une applet de commande PowerShell qui évalue l'état d'intégrité selon les stratégies de gestion basée sur les stratégies SQL Server. S’il trouve une erreur ou un avertissement, il échoue qui ensuite déclenche la troisième étape : La troisième étape envoie une notification par courrier électronique avec le rapport d’erreur / d’avertissement.  Notez toutefois que ce travail SQL Server Agent n'est pas activé par défaut. Pour activer la tâche de notification de courrier électronique, utilisez le **smart_admin.sp_set_backup_parameter** procédure stockée système.  La procédure suivante décrit ces étapes de façon détaillée :  
  
##### <a name="enabling-email-notification"></a>Activation de la notification par courrier électronique  
  
1.  Si la messagerie de base de données n’est pas déjà configurée, utilisez les étapes décrites dans [configurer la messagerie de base de données](../relational-databases/database-mail/configure-database-mail.md).  
  
2.  Définir la base de données comme système de messagerie pour le système d’alerte SQL Server : Cliquez avec le bouton droit sur **Agent SQL Server**, sélectionnez **système d’alerte**, vérifiez le **activer le profil de messagerie** zone, sélectionnez **messagerie de base de données** comme le  **Système de messagerie**, puis sélectionnez un profil de messagerie créé précédemment.  
  
3.  Exécutez la requête suivante dans une fenêtre de requête et indiquez l'adresse de messagerie qui recevra les notifications :  
  
    ```  
    Use msdb  
    Go  
    EXEC smart_admin.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'  
  
    ```  
  
     Un travail SQL Server Agent est créé pour collecter l'état d'intégrité et envoyer des notifications en cas d'erreur ou de problème au niveau des sauvegardes.  
  
 Voici un exemple de script pour activer la messagerie de base de données et configurer la notification par courrier électronique au moyen d'un travail SQL Server Agent :  
  
```  
-- Prereq: Make sure that SQL Server service runs in a service account that has  
--  access to SMTP Server   
-- set SQL Server service account as domain account   
  
EXEC sp_configure 'show advanced', 1  
RECONFIGURE  
GO  
  
-- Enable DBMail  
EXEC sp_configure 'Database Mail XPs',1  
GO  
RECONFIGURE  
GO  
  
-- Configure DBMail  
DECLARE @emailid NVARCHAR(255)  
-- Note: change this email to your own email id  
SET @emailid = N'emailalias@mycompany.com'  
  
DECLARE @smtpserver NVARCHAR(255)  
SET @smtpserver = N'smtphost.domainname.com'  
  
DECLARE @mailprofile NVARCHAR(255)  
SET @mailprofile = N'my_profile'  
  
EXEC msdb.dbo.sysmail_add_account_sp @account_name=N'myaccount',  
                @email_address = @emailid,  
                @replyto_address = @emailid,  
                @mailserver_name = @smtpserver,  
                @use_default_credentials = 1  
  
EXEC msdb.dbo.sysmail_add_profile_sp @profile_name=@mailprofile  
EXEC msdb.dbo.sysmail_add_profileaccount_sp @profile_name=@mailprofile, @account_name=N'myaccount', @sequence_number=1  
  
-- Set SQL Agent to use DBMail profile  
EXEC msdb.dbo.sp_set_sqlagent_properties @databasemail_profile = @mailprofile  
  
-- Configure Notifications   
EXEC msdb.smart_admin.sp_set_parameter  
@parameter_name = 'SSMBackup2WANotificationEmailIds',  
@parameter_value = @emailid  
  
-- To test is you are receiving notifications  
-- delete few backup files from your storage container, Wait for 15 minutes & see if you get any email notification  
  
```  
  
### <a name="using-powershell-to-setup-custom-health-monitoring"></a>Utiliser PowerShell pour configurer une surveillance de l'intégrité personnalisée  
 Le **Test-SqlSmartAdmin** cmdlet peut être utilisée pour créer une analyse d’intégrité personnalisées. Par exemple, l'option de notification décrite dans la section précédente peut être configurée au niveau de l'instance.  Si plusieurs instances de SQL Server utilisent la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], l'applet de commande PowerShell peut être utilisée pour créer des scripts qui collectent l'état et l'intégrité des sauvegardes de toutes les instances.  
  
 Le **Test-SqlSmartAdmin** applet de commande évalue les erreurs et les avertissements retournés par les stratégies de gestion en fonction des stratégies SQL Server et des rapports avec un état.  Par défaut, cette applet de commande utilise les stratégies système. Pour inclure une stratégie personnalisée, utilisez le paramètre `-AllowUserPolicies`.  
  
 Voici un exemple de script PowerShell qui retourne un rapport d'erreurs et avertissements en fonction des stratégies système et des stratégies utilisateur créées :  
  
```  
$policyResults = get-sqlsmartadmin | test-sqlsmartadmin -AllowUserPolicies  
$policyResults.PolicyEvaluationDetails | select Name, Category, Expression, Result, Exception | fl  
  
```  
  
 Le script suivant retourne un rapport détaillé des erreurs et avertissements pour l'instance par défaut :  
  
```  
PS C:\>PS SQLSERVER:\SQL\COMPUTER\DEFAULT> (get-sqlsmartadmin ).EnumHealthStatus()  
```  
  
### <a name="objects-in-msdb-database"></a>Objets dans une base de données MSDB  
 Des objets sont installés pour implémenter cette fonctionnalité. Ces objets sont réservés à une utilisation interne. Cependant, il existe une table système qui peut être utile pour surveiller l'état de sauvegarde : smart_backup_files. La plupart des informations stockées dans cette table afférentes à la surveillance, comme le type de base de données de sauvegarde, nommez tout d’abord et le dernier lsn, dates d’expiration de sauvegarde sont exposées via la fonction système [smart_admin.fn_available_backups &#40;Transact-SQL &#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql). Cependant, la colonne d'état dans la table smart_backup_files qui indique l'état du fichier de sauvegarde n'est pas disponible via la fonction. Voici un exemple de requête que vous pouvez utiliser pour récupérer certaines informations, dont l'état, à partir de la table système :  
  
```  
USE msdb  
GO  
SELECT  
 database_name AS [Database Name]  
,backup_path AS [Backup Destination and File]  
,[Backup Type] =  
CASE backup_type  
WHEN 1 THEN 'FULL'  
WHEN 2 THEN 'LOG'  
END  
,[Backup Status] =  
CASE [status]  
WHEN 'A' THEN 'Available'  
WHEN 'B' THEN 'Copy In Progress'  
WHEN 'C' THEN 'Corrupted'  
WHEN 'D' THEN 'Deleted'  
WHEN 'F' THEN 'Copy Failed'  
WHEN 'U' THEN 'Unknown'  
END  
,first_lsn AS [First LSN]  
,last_lsn AS [Last LSN]  
,backup_start_date AS [Backup Start Time]  
,backup_finish_date AS [Backup Completion Time]  
,expiration_date AS [Backup Expiry Date/Time]  
FROM  
smart_backup_files;  
  
```  
  
 Voici une explication détaillée des différents états retournés :  
  
-   **Disponible - a :** Il s’agit d’un fichier de sauvegarde normal. La sauvegarde est terminée et est disponible dans le stockage Windows Azure.  
  
-   **Copie en cours-b :** Cet état est spécifiquement pour les bases de données de groupe de disponibilité. Si la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] détecte une interruption de la séquence des journaux de sauvegarde, elle tentera d'abord identifient la sauvegarde qui a peut-être provoqué une interruption dans la séquence. Lorsqu'elle trouve le fichier de sauvegarde, elle tente de le copier dans le stockage Windows Azure. Lorsque le processus de copie est en cours, elle affiche l'état.  
  
-   **Échec de copie - F:** Comme pour la copie en cours, il s’agit de bases de données de groupe de disponibilité t spécifique. Si le processus de copie échoue, l'état est marqué comme F.  
  
-   **Endommagé - C:** Si [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est impossible de vérifier le fichier de sauvegarde dans le stockage en utilisant la commande RESTORE HEADER_ONLY même après plusieurs tentatives, il marque ce fichier comme endommagé. La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] planifiera une sauvegarde pour s'assurer que le fichier endommagé n'entraîne pas une interruption de la séquence de sauvegarde.  
  
-   **Supprimé - D:** Impossible de trouver le fichier correspondant dans le stockage Windows Azure. La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] planifiera une sauvegarde si le fichier supprimé entraîne une interruption dans la séquence de sauvegarde.  
  
-   **Inconnu - U:** Cet état indique que [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] n’a pas encore été en mesure de vérifier l’existence du fichier et ses propriétés dans le stockage Windows Azure. À la prochaine exécution du processus, soit approximativement toutes les 15 minutes, cet état sera mis à jour.  
  
  
