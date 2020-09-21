---
title: Résolution des problèmes courants liés au service Launchpad
description: Cet article fournit des conseils pour résoudre de nombreux problèmes empêchant le démarrage du service SQL Server Trusted Launchpad, notamment des problèmes ou des changements de configuration et des protocoles réseau manquants.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 07/30/2019
ms.topic: troubleshooting
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e814e135c7e7054231aea3988a30afe755e1fc9d
ms.sourcegitcommit: 04fb4c2d7ccddd30745b334b319d9d2dd34325d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89570286"
---
# <a name="troubleshoot-issues-with-launchpad-service-and-external-script-execution-in-sql-server"></a>Résolution des problèmes courants liés au service Launchpad et à l’exécution de scripts externes dans SQL Server
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Cet article fournit des conseils de résolution des problèmes impliquant le service SQL Server Launchpad approuvé. Le service Launchpad prend en charge l’exécution de scripts externes pour R et Python. Plusieurs problèmes peuvent empêcher Launchpad de démarrer, notamment des problèmes ou des changements de configuration et des protocoles réseau manquants.  

## <a name="determine-whether-launchpad-is-running"></a>Déterminer si Launchpad est en cours d’exécution

1. Ouvrez le panneau **Services** (Services.msc). Ou, à partir de la ligne de commande, tapez **SQLServerManager13.msc** ou **SQLServerManager14.msc** pour ouvrir le [Gestionnaire de configuration SQL Server](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Notez le compte de service sous lequel Launchpad s’exécute. Chaque instance où R ou Python est activé doit avoir sa propre instance du service Launchpad. Par exemple, le service pour une instance nommée peut se présenter comme suit : _MSSQLLaunchpad$InstanceName_.

3. Si le service est arrêté, redémarrez-le. En cas de problème de configuration au redémarrage, un message est publié dans le journal des événements système et le service est de nouveau arrêté. Consultez le journal des événements système pour savoir pourquoi le service s’est arrêté.

4. Examinez le contenu de RSetup.log et vérifiez que l’installation ne comporte aucune erreur. Par exemple, le message *Sortie avec le code 0* indique l’échec du démarrage du service.

5. Pour rechercher d’autres erreurs, passez en revue le contenu de rlauncher.log.

## <a name="check-the-launchpad-service-account"></a>Vérifier le compte de service Launchpad

Le compte de service par défaut peut être « NT Service\$SQL2016 » ou « NT Service\$SQL2017 ». La dernière partie peut varier en fonction du nom de votre instance SQL.

Le service Launchpad (Launchpad.exe) s’exécute à l’aide d’un compte de service à faibles privilèges. Toutefois, pour démarrer R et Python et communiquer avec l’instance de base de données, le compte de service Launchpad nécessite les droits d’utilisateur suivants :

- Ouvrir une session en tant que service (SeServiceLogonRight)
- Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)
- Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)
- Ajuster les quotas de mémoire pour un processus (SeIncreaseQuotaSizePrivilege)

Pour plus d’informations sur ces droits d’utilisateur, consultez la section « Privilèges et droits Windows » dans [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

> [!TIP]
> Si vous connaissez bien l’outil Support Diagnostics Platform (SDP) pour les diagnostics SQL Server, vous pouvez utiliser SDP pour passer en revue le fichier de sortie nommé MachineName_UserRights.txt.

## <a name="user-group-for-launchpad-cannot-log-on-locally"></a>Le groupe d’utilisateurs pour Launchpad ne peut pas se connecter localement

Pendant l’installation de Machine Learning Services, SQL Server crée le groupe d’utilisateurs Windows, **SQLRUserGroup**, puis le provisionne avec tous les droits permettant à Launchpad de se connecter à SQL Server et d’exécuter les travaux de scripts externes. Si ce groupe d’utilisateurs est activé, il est également utilisé pour exécuter des scripts Python.

Toutefois, dans les organisations où des stratégies de sécurité plus restrictives sont appliquées, les droits requis par ce groupe ont peut-être été supprimés manuellement ou ils peuvent être automatiquement révoqués par la stratégie. Si les droits ont été supprimés, Launchpad ne peut plus se connecter à SQL Server et SQL Server ne peut pas appeler le runtime externe.

Pour corriger ce problème, vérifiez que le groupe **SQLRUserGroup** dispose du droit système **Permettre l’ouverture d’une session locale**.

Pour plus d’informations, consultez [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

## <a name="permissions-to-run-external-scripts"></a>Autorisations d’exécution de scripts externes

Même si Launchpad est configuré correctement, il retourne une erreur si l’utilisateur n’est pas autorisé à exécuter des scripts R ou Python.

Si vous avez installé SQL Server en tant qu’administrateur de base de données ou que vous êtes propriétaire de base de données, vous bénéficiez automatiquement de cette autorisation. Toutefois, les autres utilisateurs disposent généralement d’autorisations plus limitées. S’ils essaient d’exécuter un script R, Launchpad génère une erreur.

Pour corriger le problème, dans SQL Server Management Studio, un administrateur de la sécurité peut modifier la connexion SQL ou le compte d’utilisateur Windows en exécutant le script suivant :

```sql
GRANT EXECUTE ANY EXTERNAL SCRIPT TO <username>
```

Pour plus d’informations, consultez [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md).

## <a name="common-launchpad-errors"></a>Erreurs courantes avec Launchpad

Cette section liste les messages d’erreur les plus courants retournés par Launchpad.

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"
## <a name="unable-to-launch-runtime-for-r-script"></a>« Impossible de lancer le runtime pour le script R »

Si le groupe Windows pour les utilisateurs R (également utilisé pour Python) ne peut pas se connecter à l’instance exécutant R services, vous pouvez voir les erreurs suivantes :

- Erreurs générées quand vous essayez d’exécuter des scripts R :

    * *Impossible de lancer le runtime pour le script « R ». Vérifiez la configuration du runtime « R ».*

    * *Une erreur de script externe s’est produite. Impossible de lancer le runtime.*

- Erreurs générées par le service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] :

    * *Failed to initialize the launcher RLauncher.dll (Impossible d’initialiser le lanceur RLauncher.dll)*

    * *No launcher dlls were registered! (Aucune DLL de lanceur n’a été enregistrée.)*

    * *Les journaux de sécurité indiquent que le compte NT SERVICE n’a pas pu se connecter*

Pour plus d’informations sur l’octroi des autorisations nécessaires à ce groupe d’utilisateurs, consultez [Installer SQL Server R Services](../install/sql-r-services-windows-install.md).

> [!NOTE]
> Cette limitation ne s’applique pas si vous utilisez des connexions SQL pour exécuter des scripts R à partir d’une station de travail distante.
::: moniker-end

## <a name="logon-failure-the-user-has-not-been-granted-the-requested-logon-type"></a>« Échec d’ouverture de session : l’utilisateur ne bénéficie pas du type d’ouverture de session demandé »

Par défaut, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] utilise le compte suivant au démarrage : `NT Service\MSSQLLaunchpad`. Le compte est configuré par le programme d’installation de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] avec toutes les autorisations nécessaires.

Si vous affectez un autre compte à Launchpad ou que le droit est supprimé par une stratégie sur l’ordinateur SQL Server, le compte risque de ne pas disposer des autorisations nécessaires et vous pouvez obtenir cette erreur :

>*Échec d’ouverture de session ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) : l’utilisateur ne bénéficie pas du type d’ouverture de session demandé sur cet ordinateur.*

Pour accorder les autorisations nécessaires au nouveau compte de service, utilisez l’application Stratégie de sécurité locale et mettez à jour les autorisations sur le compte pour inclure les autorisations suivantes :

+ Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)
+ Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)
+ Ouvrir une session en tant que service (SeServiceLogonRight)
+ Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)

## <a name="unable-to-communicate-with-the-launchpad-service"></a>« Impossible de communiquer avec le service Launchpad »

Si vous avez installé et activé Machine Learning, mais que vous recevez cette erreur quand vous tentez d’exécuter un script R ou Python, il est possible que le service Launchpad de l’instance ait cessé de fonctionner.

1. À partir d’une invite de commandes Windows, ouvrez le Gestionnaire de configuration SQL Server. Pour plus d'informations, consultez [SQL Server Configuration Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Cliquez avec le bouton droit sur SQL Server Launchpad pour l’instance, puis sélectionnez **Propriétés**.

3. Sélectionnez l’onglet **Service**, puis vérifiez que le service est en cours d’exécution. Si ce n’est pas le cas, optez pour le **Mode de démarrage****Automatique**, puis sélectionnez **Appliquer**.

4. Le redémarrage du service corrige généralement le problème, ce qui permet aux scripts de machine learning de s’exécuter. Si le redémarrage ne résout pas le problème, notez le chemin et les arguments de la propriété **Chemin binaire**, puis effectuez les étapes suivantes :

    a. Examinez le fichier .config du lanceur et vérifiez que le répertoire de travail est valide.

    b. Vérifiez que le groupe Windows utilisé par Launchpad peut se connecter à l’instance SQL Server.

    c. Si vous modifiez les propriétés du service, redémarrez le service Launchpad.

## <a name="fatal-error-creation-of-tmpfile-failed"></a>« Erreur irrécupérable : la création de tmpFile a échoué »

Dans ce scénario, vous avez correctement installé les fonctionnalités de machine learning et Launchpad est en cours d’exécution. Vous essayez d’exécuter un code R ou Python simple, mais Launchpad échoue avec une erreur semblable à la suivante : 

>*Impossible de communiquer avec le runtime pour le script R. Vérifiez les conditions requises du runtime R.*

En même temps, le runtime du script externe écrit le message suivant dans le message STDERR : 

>*Erreur irrécupérable : la création de tmpfile a échoué.*

Cette erreur indique que le compte que Launchpad tente d’utiliser n’a pas l’autorisation de se connecter à la base de données. Cette situation peut se produire quand des stratégies de sécurité strictes sont implémentées. Pour déterminer si c’est le cas, passez en revue les journaux de SQL Server et vérifiez si le compte MSSQLSERVER01 a été refusé au moment de la connexion. Les mêmes informations sont fournies dans les journaux spécifiques à R\_SERVICES ou PYTHON\_SERVICES. Recherchez ExtLaunchError.log.

Par défaut, 20 comptes sont configurés et associés au processus Launchpad.exe, avec les noms MSSQLSERVER01 à MSSQLSERVER20. Si vous utilisez beaucoup R ou Python, vous pouvez augmenter le nombre de comptes.

Pour résoudre le problème, vérifiez que le groupe dispose de l’autorisation *Permettre l’ouverture d’une session locale* sur l’instance locale où les fonctionnalités de machine learning ont été installées et activées. Dans certains environnements, ce niveau d’autorisation peut nécessiter une exception de l’objet de stratégie de groupe de la part de l’administrateur réseau.

## <a name="not-enough-quota-to-process-this-command"></a>« Quota insuffisant pour traiter cette commande »

Cette erreur peut signifier plusieurs choses :

- Launchpad peut ne pas avoir suffisamment d’utilisateurs externes pour exécuter la requête externe. Par exemple, si vous exécutez plus de 20 requêtes externes simultanément et qu’il n’y a que 20 utilisateurs par défaut, une ou plusieurs requêtes peuvent échouer.

- La mémoire disponible est insuffisante pour traiter la tâche R. Cette erreur se produit le plus souvent dans un environnement par défaut où SQL Server peut utiliser jusqu’à 70 % des ressources de l’ordinateur. Pour plus d’informations sur la façon de modifier la configuration du serveur afin d’autoriser R à utiliser plus de ressources, consultez [Opérationnalisation de votre code R](../r/operationalizing-your-r-code.md).

## <a name="cant-find-package"></a>« Package introuvable »

Si vous exécutez du code R dans SQL Server et que vous recevez ce message, alors que vous n’obteniez pas ce message quand vous exécutiez le même code en dehors de SQL Server, cela signifie que le package n’a pas été installé à l’emplacement de la bibliothèque par défaut utilisé par SQL Server.

Cette erreur peut se produire dans plusieurs situations :

- Vous avez installé un nouveau package sur le serveur, mais l’accès a été refusé. R a donc installé le package dans une bibliothèque utilisateur.

- Vous avez installé R Services, puis un autre outil R ou un ensemble de bibliothèques, notamment Microsoft R Server (autonome), Microsoft R Client, RStudio, etc.

Pour déterminer l’emplacement de la bibliothèque de packages R utilisée par l’instance, ouvrez SQL Server Management Studio (ou tout autre outil permettant d’effectuer des requêtes sur des bases de données), connectez-vous à l’instance, puis exécutez la procédure stockée suivante :

```sql
EXEC sp_execute_external_script @language = N'R',  
@script = N' print(normalizePath(R.home())); print(.libPaths());'; 
```

#### <a name="sample-results"></a>Exemples de résultats

*Message(s) STDOUT provenant du script externe :*

*[1] "C:\\Program Files\\Microsoft SQL Server\\MSSQL13.SQL2016\\R_SERVICES"*

*[1] "C:/Program Files/Microsoft SQL Server/MSSQL13.SQL2016/R_SERVICES/library"*

Pour résoudre le problème, vous devez réinstaller le package dans la bibliothèque d’instances SQL Server.

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"
>[!NOTE]
>Si vous avez mis à niveau une instance de SQL Server 2016 pour utiliser la dernière version de Microsoft R, l’emplacement de la bibliothèque par défaut est différent. Pour plus d’informations, consultez [Utiliser SqlBindR pour mettre à niveau une instance de R Services](../install/upgrade-r-and-python.md).
::: moniker-end

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"
## <a name="launchpad-shuts-down-due-to-mismatched-dlls"></a>Launchpad s’arrête en raison de DLL incompatibles

Si vous installez le moteur de base de données avec d’autres fonctionnalités, appliquez un correctif au serveur, puis ajoutez la fonctionnalité Machine Learning à l’aide du média d’origine, il est possible que la mauvaise version des composants Machine Learning soit installée. Quand Launchpad détecte une incompatibilité de version, il s’arrête et crée un fichier de vidage sur incident.

Pour éviter ce problème, veillez à installer les nouvelles fonctionnalités au même niveau de correctif que l’instance de serveur.

**Procédure de mise à niveau incorrecte :**

1. Installez SQL Server 2016 sans R Services.
2. Effectuez la mise à niveau vers SQL Server 2016 mise à jour cumulative 2 (CU2).
3. Installez R Services (en base de données) à l’aide du média RTM.

**Procédure de mise à niveau correcte :**

1. Installez SQL Server 2016 sans R Services.
2. Effectuez la mise à niveau de SQL Server 2016 vers le niveau de correctif souhaité. Par exemple, installez le Service Pack 1 (SP1), puis la mise à jour cumulative 2.
3. Pour ajouter la fonctionnalité au niveau de correctif approprié, réexécutez le programme d’installation de SP1 et de CU2, puis choisissez R Services (en base de données). 

## <a name="launchpad-fails-to-start-if-8dot3-notation-is-required"></a>Launchpad ne parvient pas à démarrer si la notation 8dot3 est requise

> [!NOTE] 
> Sur les anciens systèmes, Launchpad peut ne pas démarrer si la notation 8dot3 est requise. Cette exigence a été supprimée dans les versions ultérieures. Les clients SQL Server 2016 R Services doivent installer, au choix :
> * SQL Server 2016 SP1 et CU1 : [Mise à jour cumulative 1 pour SQL Server](https://support.microsoft.com/help/3208177/cumulative-update-1-for-sql-server-2016-sp1)
> * SQL Server 2016 RTM mise à jour cumulative 3 et ce [correctif logiciel](https://support.microsoft.com/help/3210110/on-demand-hotfix-update-package-for-sql-server-2016-cu3), disponible à la demande.

Pour assurer la compatibilité avec R, SQL Server 2016 R Services (en base de données) exige que le lecteur sur lequel la fonctionnalité est installée prenne en charge la création de noms de fichiers courts à l’aide de la *notation 8dot3*. Un nom de fichier 8.3 est également appelé *nom de fichier court*. Il est utilisé pour assurer la compatibilité avec les versions antérieures de Microsoft Windows ou pour remplacer les noms de fichiers longs.

Si le volume sur lequel vous installez R ne prend pas en charge les noms de fichiers courts, les processus qui lancent R à partir de SQL Server peuvent ne pas être en mesure de localiser le bon fichier exécutable. Dans ce cas, Launchpad ne démarre pas.

Pour éviter cela, vous pouvez activer la notation 8dot3 sur le volume où SQL Server et R Services sont installés. Vous devez ensuite fournir le nom court pour le répertoire de travail dans le fichier de configuration de R Services.

1. Pour activer la notation 8dot3, exécutez l’utilitaire fsutil avec l’argument *8dot3name* comme indiqué ici : [fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

2. Une fois la notation 8dot3 activée, ouvrez le fichier RLauncher.config et notez la propriété de `WORKING_DIRECTORY`. Pour plus d’informations sur la localisation de ce fichier, consultez [Collecte de données pour la résolution des problèmes de machine learning](data-collection-ml-troubleshooting-process.md).

3. Utilisez l’utilitaire fsutil avec l’argument *file* pour spécifier un chemin de fichier court vers le dossier spécifié dans WORKING_DIRECTORY.

4. Modifiez le fichier config pour spécifier le même répertoire de travail que celui que vous avez entré dans la propriété WORKING_DIRECTORY. Vous pouvez également spécifier un autre répertoire de travail et choisir un chemin existant qui est déjà compatible avec la notation 8dot3.
::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

[Résolution des problèmes connus dans Machine Learning Services](machine-learning-troubleshooting-overview.md)

[Collecte de données pour la résolution des problèmes de machine learning](data-collection-ml-troubleshooting-process.md)

[Installer SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)

[Résoudre les problèmes de connexion au moteur de base de données](../../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
