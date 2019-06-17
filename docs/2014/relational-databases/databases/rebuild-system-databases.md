---
title: Reconstruire des bases de données système | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], rebuilding
- REBUILDDATABASE parameter
- rebuilding databases, master
- system databases [SQL Server], rebuilding
ms.assetid: af457ecd-523e-4809-9652-bdf2e81bd876
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b58378e8ba2193a186fb58e3e784bf9bc3cb4d4c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62871276"
---
# <a name="rebuild-system-databases"></a>Reconstruire des bases de données système
  Les bases de données système doivent être reconstruites pour résoudre des problèmes d’altération dans les bases de données système [master](master-database.md), [model](model-database.md), [msdb](msdb-database.md)ou [resource](resource-database.md) ou pour modifier le classement au niveau du serveur par défaut. Cette rubrique fournit des instructions détaillées sur la reconstruction des bases de données système dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Conditions préalables](#Prerequisites)  
  
-   **Procédures :**  
  
     [Reconstruire des bases de données système](#RebuildProcedure)  
  
     [Reconstruire la base de données resource](#Resource)  
  
     [Créer une nouvelle base de données msdb](#CreateMSDB)  
  
-   **Suivi :**  
  
     [Corriger les erreurs liées à la reconstruction](#Troubleshoot)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Lorsque les bases de données système master, model, msdb et tempdb sont reconstruites, les bases de données sont supprimées et recréées à leur emplacement d'origine. Si un nouveau classement est spécifié dans l'instruction de reconstruction, les bases de données système sont créées à l'aide de ce paramètre de classement. Les modifications apportées par les utilisateurs à ces bases de données sont perdues. Par exemple, les utilisateurs peuvent avoir défini des objets dans la base de données master et planifié des travaux dans msdb ou avoir modifié le paramétrage par défaut dans la base de données model.  
  
###  <a name="Prerequisites"></a> Conditions préalables  
 Avant de reconstruire les bases de données système, effectuez les tâches suivantes pour être certain de pouvoir restaurer les bases de données système avec leurs paramètres actuels.  
  
1.  Enregistrez toutes les valeurs de configuration à l'échelle du serveur.  
  
    ```  
    SELECT * FROM sys.configurations;  
    ```  
  
2.  Enregistrez tous les Service Packs et correctifs logiciels appliqués à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le classement actuel. Vous devrez réappliquer ces mises à jour après avoir reconstruit les bases de données système.  
  
    ```  
    SELECT  
    SERVERPROPERTY('ProductVersion ') AS ProductVersion,  
    SERVERPROPERTY('ProductLevel') AS ProductLevel,  
    SERVERPROPERTY('ResourceVersion') AS ResourceVersion,  
    SERVERPROPERTY('ResourceLastUpdateDateTime') AS ResourceLastUpdateDateTime,  
    SERVERPROPERTY('Collation') AS Collation;  
    ```  
  
3.  Enregistrez l'emplacement actuel de tous les fichiers de données et fichiers journaux des bases de données système. La reconstruction des bases de données système installe toutes les bases de données système à leur emplacement d'origine. Si vous avez déplacé des fichiers de données ou des fichiers journaux de bases de données système, vous devrez à nouveau les déplacer.  
  
    ```  
    SELECT name, physical_name AS current_file_location  
    FROM sys.master_files  
    WHERE database_id IN (DB_ID('master'), DB_ID('model'), DB_ID('msdb'), DB_ID('tempdb'));  
    ```  
  
4.  Localisez la sauvegarde actuelle des bases de données master, model et msdb.  
  
5.  Si l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configurée en tant que serveur de distribution de réplication, localisez la sauvegarde actuelle de la base de données de distribution.  
  
6.  Vérifiez que vous disposez des autorisations appropriées pour reconstruire les bases de données système. Pour effectuer cette opération, vous devez être membre du rôle serveur fixe `sysadmin`. Pour plus d’informations, consultez [Rôles de niveau serveur](../security/authentication-access/server-level-roles.md).  
  
7.  Vérifiez que des copies des fichiers modèles de données et de journaux de master, model et msdb existent sur le serveur local. L'emplacement par défaut des fichiers modèles est C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Templates. Ces fichiers sont utilisés pendant le processus de reconstruction et doivent être présents pour que l'installation réussisse. S'il en manque, exécutez la fonctionnalité Réparer du programme d'installation ou copiez manuellement les fichiers à partir du média d'installation. Pour trouver les fichiers sur le média d'installation, accédez au répertoire correspondant à la plateforme appropriée (x86 ou x64), puis accédez à setup\sql_engine_core_inst_msi\Pfiles\SqlServr\MSSQL.X\MSSQL\Binn\Templates.  
  
##  <a name="RebuildProcedure"></a> Reconstruire des bases de données système  
 La procédure suivante reconstruit les bases de données système master, model, msdb et tempdb. Vous ne pouvez pas spécifier les bases de données système à reconstruire. Pour les instances cluster, cette procédure doit être effectuée sur le nœud actif et la ressource [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le groupe d'applications cluster correspondant doit être en mode hors connexion avant d'effectuer la procédure.  
  
 Cette procédure ne reconstruit pas la base de données resource. Consultez la section « Procédure de reconstruction de la base de données resource », plus loin dans cette rubrique.  
  
#### <a name="to-rebuild-system-databases-for-an-instance-of-sql-server"></a>Pour reconstruire les bases de données système pour une instance de SQL Server :  
  
1.  Insérez le média d'installation [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dans le lecteur de disque ou, à partir d'une invite de commandes, changez de répertoire pour accéder à l'emplacement du fichier setup.exe situé sur le serveur local. L'emplacement par défaut sur le serveur est C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Release.  
  
2.  À partir d'une fenêtre d'invite de commandes, tapez la commande ci-dessous. Les crochets indiquent des paramètres facultatifs. N'entrez pas les crochets. Si vous utilisez un système d'exploitation Windows avec le Contrôle de compte d'utilisateur activé, l'exécution du programme d'installation requiert des privilèges élevés. Pour utiliser l'invite de commandes, vous devez être administrateur.  
  
     `Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName /SQLSYSADMINACCOUNTS=accounts [ /SAPWD= StrongPassword ] [ /SQLCOLLATION=CollationName]`  
  
    |Nom du paramètre|Description|  
    |--------------------|-----------------|  
    |/QUIET ou /Q|Spécifie que le programme d'installation doit s'exécuter sans interface utilisateur.|  
    |/ACTION=REBUILDDATABASE|Spécifie que le programme d'installation doit recréer les bases de données système.|  
    |/INSTANCENAME=*Nom_Instance*|Représente le nom de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour l'instance par défaut, entrez MSSQLSERVER.|  
    |/SQLSYSADMINACCOUNTS=*comptes*|Spécifie les comptes de groupes Windows ou les comptes individuels à ajouter au rôle serveur fixe `sysadmin`. Lorsque vous spécifiez plusieurs comptes, utilisez l'espace comme séparateur. Par exemple, entrez **BUILTIN\Administrateurs MonDomaine\MonUtilisateur**. Lorsque vous spécifiez un compte qui contient un espace vide dans son nom, placez le compte entre guillemets doubles. Par exemple, entrez `NT AUTHORITY\SYSTEM`.|  
    |[ /SAPWD=*MotDePasseFort* ]|Spécifie le mot de passe pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sa` compte. Ce paramètre est requis si l’instance utilise le mode Authentification mixte (authentification[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows).<br /><br /> **\*\* Note de sécurité \* \***  le `sa` compte est bien connu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte et il est souvent la cible par des utilisateurs malveillants. Il est par conséquent essentiel d'utiliser un mot de passe fort pour la connexion `sa`.<br /><br /> Ne spécifiez pas ce paramètre pour le mode Authentification Windows.|  
    |[ /SQLCOLLATION=*NomClassement* ]|Spécifie un nouveau classement au niveau du serveur. Ce paramètre est facultatif. S'il n'est pas spécifié, c'est le classement actuel du serveur qui est utilisé.<br /><br /> **\*\* Important \*\*** La modification du classement de niveau serveur ne modifie pas le classement des bases de données utilisateur existantes. En revanche, les bases de données utilisateur qui seront créées utiliseront le nouveau classement par défaut.<br /><br /> Pour plus d’informations, consultez [Définir ou modifier le classement du serveur](../collations/set-or-change-the-server-collation.md).|  
  
3.  Lorsque le programme d'installation a terminé la reconstruction des bases de données système, il revient à l'invite de commandes sans afficher de message. Examinez le fichier journal Summary.txt pour vérifier que le processus s'est correctement déroulé. Ce fichier se trouve à l'emplacement C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs.  
  
## <a name="post-rebuild-tasks"></a>Tâches à effectuer après la reconstruction  
 Après avoir reconstruit la base de données, vous devrez peut-être effectuer les tâches supplémentaires suivantes :  
  
-   Restaurer vos sauvegardes complètes les plus récentes des bases de données master, model et msdb. Pour plus d’informations, consultez [Sauvegarder et restaurer des bases de données système &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
    > [!IMPORTANT]  
    >  Si vous avez modifié le classement du serveur, ne restaurez pas les bases de données système. Cette opération remplacerait le nouveau classement par le paramétrage de classement précédent.  
  
     Si une sauvegarde n'est pas disponible ou si la sauvegarde restaurée n'est pas actuelle, recréez toutes les entrées manquantes. Par exemple, recréez toutes les entrées manquantes pour vos bases de données utilisateur, unités de sauvegarde, connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , points de terminaison, et ainsi de suite. Le meilleur moyen de recréer des entrées est d'exécuter les scripts d'origine qui les ont créées.  
  
> [!IMPORTANT]  
>  Nous vous conseillons de protéger vos scripts et de les conserver en lieu sûr pour éviter que des personnes non autorisées ne les modifient.  
  
-   Si l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configurée comme serveur de distribution de réplication, vous devez restaurer la base de données de distribution. Pour plus d’informations, consultez [Sauvegarder et restaurer des bases de données répliquées](../replication/administration/back-up-and-restore-replicated-databases.md).  
  
-   Déplacer les bases de données système vers les emplacements que vous avez enregistrés précédemment. Pour plus d’informations, consultez [Déplacer des bases de données système](system-databases.md).  
  
-   Vérifier que les valeurs de configuration à l'échelle du serveur correspondent à celles que vous avez enregistrées précédemment.  
  
##  <a name="Resource"></a> Reconstruire la base de données resource  
 La procédure suivante reconstruit la base de données système resource. La reconstruction de la base de données resource entraîne la perte de tous les Service Packs et correctifs logiciels, qui devront par conséquent être réappliqués.  
  
#### <a name="to-rebuild-the-resource-system-database"></a>Pour reconstruire la base de données système resource :  
  
1.  Lancez le programme d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (setup.exe) à partir du média de distribution.  
  
2.  Dans la zone de navigation gauche, cliquez sur **Maintenance**, puis sur **Réparer**.  
  
3.  La règle de support du programme d'installation et les routines de fichiers sont exécutées pour garantir que les composants requis sont installés sur votre système et que les règles de validation du programme d'installation ont été correctement exécutées sur l'ordinateur. Cliquez sur **OK** ou sur **Installer** pour continuer.  
  
4.  Dans la page Sélectionner une instance, sélectionnez l'instance à réparer, puis cliquez sur **Suivant**.  
  
5.  Les règles de réparation sont exécutées pour valider l'opération. Pour continuer, cliquez sur **Suivant**.  
  
6.  Dans la page **Prêt à réparer** , cliquez sur **Réparer**. La page Terminé indique que l'opération est terminée.  
  
##  <a name="CreateMSDB"></a> Créer une nouvelle base de données msdb  
 Si le `msdb` base de données est endommagée et que vous n’avez pas d’une sauvegarde de la `msdb` base de données, vous pouvez créer un nouveau `msdb` à l’aide de la **instmsdb** script.  
  
> [!WARNING]  
>  Reconstruction le `msdb` de base de données à l’aide de la **instmsdb** script éliminera toutes les informations stockées dans `msdb` telles que les travaux, alerte, opérateurs, des plans de maintenance, l’historique de sauvegarde, les paramètres de gestion basée sur des stratégies , Mail, entrepôt de données de performances, etc. de base de données.  
  
1.  Arrêtez tous les services qui établissent des connexions au [!INCLUDE[ssDE](../../includes/ssde-md.md)], dont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, [!INCLUDE[ssRS](../../includes/ssrs.md)], [!INCLUDE[ssIS](../../includes/ssis-md.md)]et toutes les applications qui utilisent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en tant que banque de données.  
  
2.  Démarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir de la ligne de commande à l'aide de la commande : `NET START MSSQLSERVER /T3608`  
  
     Pour plus d'informations, consultez [Démarrer, arrêter, suspendre, reprendre, redémarrer les services SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).  
  
3.  Dans une autre fenêtre de ligne de commande, détachez le `msdb` base de données en exécutant la commande suivante, en remplaçant  *\<nom_serveur >* avec l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: `SQLCMD -E -S<servername> -dmaster -Q"EXEC sp_detach_db msdb"`  
  
4.  À l’aide de l’Explorateur Windows, renommez le `msdb` fichiers de base de données. Par défaut, ils se trouvent dans le sous-dossier DATA de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
5.  À l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , arrêtez et redémarrez le service [!INCLUDE[ssDE](../../includes/ssde-md.md)] normalement.  
  
6.  Dans une fenêtre de ligne de commande, connectez-vous à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et exécutez la commande : `SQLCMD -E -S<servername> -i"C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.sql" -o" C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.out"`  
  
     Remplacez *\<nom_serveur>* par l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Utilisez le chemin d'accès au système de fichiers de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
7.  À l'aide du Bloc-notes Windows, ouvrez le fichier **instmsdb.out** et vérifiez qu'il ne présente aucune erreur.  
  
8.  Réappliquez tous les Service Packs ou les correctifs logiciels installés sur l'instance.  
  
9. Recréez le contenu de l’utilisateur stocké dans le `msdb` base de données, tel que les travaux, alertes, etc.  
  
10. Sauvegarde le `msdb` base de données.  
  
##  <a name="Troubleshoot"></a> Corriger les erreurs liées à la reconstruction  
 Les erreurs de syntaxe et autres erreurs d'exécution sont affichées dans la fenêtre d'invite de commandes. Vérifiez que l'instruction Setup ne comporte pas les erreurs de syntaxe suivantes :  
  
-   Barre oblique (/) manquante devant chaque nom de paramètre.  
  
-   Signe égal (=) manquant entre le nom du paramètre et sa valeur.  
  
-   Présence d'espaces entre le nom du paramètre et le signe égal.  
  
-   Présence de virgules (,) ou d'autres caractères qui ne sont pas spécifiés dans la syntaxe.  
  
 Une fois l'opération de reconstruction terminée, examinez les journaux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour vérifier s'ils contiennent des erreurs. L'emplacement par défaut des journaux est C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs. Pour localiser le fichier journal qui contient les résultats du processus de reconstruction, accédez au dossier Logs à partir d'une invite de commandes, puis exécutez `findstr /s RebuildDatabase summary*.*`. Cette recherche vous dirige vers les fichiers journaux qui contiennent les résultats de la reconstruction des bases de données système. Ouvrez les fichiers journaux et recherchez les messages d'erreur pertinents.  
  
## <a name="see-also"></a>Voir aussi  
 [Bases de données système](system-databases.md)  
  
  
