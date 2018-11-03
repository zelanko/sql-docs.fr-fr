---
title: Problèmes courants avec le service Launchpad et l’exécution du script externe dans SQL Server | Microsoft Docs
ms.prod: sql
ms.technology: mlserver
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b480c400ae2068bb6701192e77d97672ddeb024e
ms.sourcegitcommit: b29745051be2326268f165cf72f5eb95dc893564
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50254445"
---
# <a name="common-issues-with-launchpad-service-and-external-script-execution-in-sql-server"></a>Problèmes courants avec le service Launchpad et l’exécution du script externe dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

 Service Launchpad approuvé de SQL Server prend en charge l’exécution du script externe pour R et Python. Sur SQL Server 2016 R Services SP1 fournit le service. SQL Server 2017 inclut l’ervice de Launchpad dans le cadre de l’installation d’intitial.

Plusieurs problèmes peuvent empêcher Launchpad à partir de démarrage, y compris les problèmes de configuration ou de modifications ou manquantes des protocoles réseau. Cet article fournit des conseils de dépannage pour de nombreux problèmes. Pour un nous avez manqués, vous pouvez publier des questions à la [forum Machine Learning Server](https://social.msdn.microsoft.com/Forums/home?category=MicrosoftR).

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 Machine Learning Services

## <a name="determine-whether-launchpad-is-running"></a>Déterminer si Launchpad est en cours d’exécution.

1. Ouvrez le **Services** panneau (Services.msc). Ou, à partir de la ligne de commande, tapez **SQLServerManager13.msc** ou **SQLServerManager14.msc** pour ouvrir [Gestionnaire de Configuration SQL Server](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Prenez note du compte de service Launchpad sous lequel s’exécute. Chaque instance où R ou Python est activé doit avoir sa propre instance du service Launchpad. Par exemple, le service pour une instance nommée peut être quelque chose comme _MSSQLLaunchpad$ InstanceName_.

3. Si le service est arrêté, redémarrez-le. Sur le redémarrage, s’il existe des problèmes avec la configuration, un message est publié dans le journal des événements système, et le service est arrêté à nouveau. Vérifiez le journal des événements système pour plus d’informations sur l’arrêt du service.

4. Passez en revue le contenu de RSetup.log et assurez-vous qu’il n’y a aucune erreur dans le programme d’installation. Par exemple, le message *sortie avec le code 0* indique l’échec du service de démarrage.

5. Pour rechercher les autres erreurs, passez en revue le contenu de rlauncher.log.

## <a name="check-the-launchpad-service-account"></a>Vérifiez le compte de service Launchpad

Le compte de service par défaut peut être « NT Service\$SQL2016 » ou « NT Service\$SQL2017 ». La dernière partie peut varier, selon le nom de votre instance SQL.

Le service Launchpad (Launchpad.exe) s’exécute à l’aide d’un compte de service de faibles privilèges. Toutefois, pour démarrer R et Python et communiquer avec l’instance de base de données, le compte de service Launchpad nécessite les droits d’utilisateur suivants :

- Ouvrir une session en tant que service (SeServiceLogonRight)
- Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)
- Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)
- Ajuster les quotas de mémoire pour un processus (SeIncreaseQuotaSizePrivilege)

Pour plus d’informations sur ces droits d’utilisateur, consultez la section « des privilèges Windows et droits » dans [Windows de configurer les comptes de service et autorisations](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

> [!TIP]
> Si vous êtes familiarisé avec l’utilisation de l’outil de plate-forme SDP (Support Diagnostics) pour les diagnostics de SQL Server, vous pouvez utiliser SDP pour passer en revue le fichier de sortie portant le nom MachineName_UserRights.txt.

## <a name="user-group-for-launchpad-cannot-log-on-locally"></a>Groupe d’utilisateurs pour Launchpad ne peut pas ouvrir une session localement

Pendant l’installation des Services Machine Learning, SQL Server crée le groupe d’utilisateurs Windows **SQLRUserGroup** et il configure ensuite avec tous les droits nécessaires pour Launchpad pour vous connecter à SQL Server et exécuter des tâches de script externe. Si ce groupe d’utilisateurs est activé, il est également utilisé pour exécuter des scripts Python.

Toutefois, dans les organisations où sont appliquées des stratégies de sécurité plus restrictives, les droits qui sont requis par ce groupe a peut-être été manuellement supprimés ou ils peuvent être automatiquement révoqués par la stratégie. Si les droits ont été supprimées, Launchpad peut ne plus se connecter à SQL Server et SQL Server ne peut pas appeler le runtime externe.

Pour corriger ce problème, vérifiez que le groupe **SQLRUserGroup** dispose du droit système **Permettre l’ouverture d’une session locale**.

Pour plus d’informations, consultez [Windows de configurer les comptes de service et autorisations](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

## <a name="permissions-to-run-external-scripts"></a>Autorisations pour exécuter des scripts externes

Même si Launchpad est configuré correctement, elle retourne une erreur si l’utilisateur n’est pas autorisé à exécuter des scripts R ou Python.

Si vous avez installé SQL Server en tant qu’un administrateur de base de données ou si vous êtes un propriétaire de base de données, vous sont accordées automatiquement cette autorisation. Toutefois, les autres utilisateurs généralement avaient plus d’autorisations limitées. S’ils essaient d’exécuter un script R, ils obtiennent une erreur de Launchpad.

Pour corriger ce problème, dans SQL Server Management Studio, un administrateur de sécurité permettre modifier la connexion SQL ou un compte d’utilisateur Windows en exécutant le script suivant :

```SQL
GRANT EXECUTE ANY EXTERNAL SCRIPT TO <username>
```

Pour plus d’informations, consultez [GRANT (Transact-SQL](../t-sql/statements/grant-transact-sql.md).

## <a name="common-launchpad-errors"></a>Erreurs courantes de Launchpad

Cette section répertorie les messages d’erreur courants qui renvoie du Launchpad.

## <a name="unable-to-launch-runtime-for-r-script"></a>« Impossible de lancer le runtime pour le script R »

Si le groupe Windows pour les utilisateurs R (également utilisé pour Python) ne peut pas ouvrir une session sur l’instance qui exécute R Services, vous pouvez voir les erreurs suivantes :

- Erreurs générées lorsque vous essayez d’exécuter des scripts R :

    * *Impossible de lancer le runtime pour le script « R ». Vérifiez la configuration du runtime « R ».*

    * *Une erreur de script externe s’est produite. Impossible de lancer le runtime.*

- Erreurs générées par le [!INCLUDE[rsql_launchpad](../includes/rsql-launchpad-md.md)] service :

    * *Impossible d’initialiser le lanceur RLauncher.dll*

    * *Aucune DLL de lanceur n’a été enregistrée.*

    * *Journaux de sécurité indiquent que le compte NT SERVICE n’a pas pu se connecter*

Pour plus d’informations sur la façon d’accorder à ce groupe d’utilisateurs les autorisations nécessaires, consultez [installer SQL Server 2016 R Services](install/sql-r-services-windows-install.md).

> [!NOTE]
> Cette limitation ne s’applique pas si vous utilisez des connexions SQL pour exécuter des scripts R à partir d’une station de travail distante.

## <a name="logon-failure-the-user-has-not-been-granted-the-requested-logon-type"></a>« Échec de la connexion : l’utilisateur ne bénéficie pas du type d’accès demandé »

Par défaut, [!INCLUDE[rsql_launchpad_md](../includes/rsql-launchpad-md.md)] utilise le compte suivant au démarrage : `NT Service\MSSQLLaunchpad`. Le compte est configuré par [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] le programme d’installation pour que toutes les autorisations nécessaires.

Si vous assignez un autre compte à Launchpad, ou le droit est supprimé par une stratégie sur l’ordinateur SQL Server, le compte n’est peut-être pas les autorisations nécessaires, et vous pouvez voir cette erreur :

>*Échec d’ouverture de session ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) : l’utilisateur ne bénéficie pas du type d’ouverture de session demandé sur cet ordinateur.*

Pour accorder des autorisations nécessaires pour le nouveau compte de service, utilisez l’application de la stratégie de sécurité locale et mettre à jour les autorisations sur le compte à inclure les autorisations suivantes :

+ Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)
+ Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)
+ Ouvrir une session en tant que service (SeServiceLogonRight)
+ Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)

## <a name="unable-to-communicate-with-the-launchpad-service"></a>« Impossible de communiquer avec le service Launchpad »

Si vous avez installé et activé apprentissage, mais vous obtenez cette erreur lorsque vous essayez d’exécuter un script R ou Python, le service Launchpad de l’instance peut avoir cessé de fonctionner.

1. À partir d’une invite de commandes Windows, ouvrez le Gestionnaire de configuration SQL Server. Pour plus d'informations, consultez [SQL Server Configuration Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Avec le bouton droit de Launchpad de SQL Server pour l’instance, puis sélectionnez **propriétés**.

3. Sélectionnez le **Service** onglet et vérifiez que le service est en cours d’exécution. Si elle n’est pas en cours d’exécution, modifiez le **StartMode** à **automatique**, puis sélectionnez **appliquer**.

4. Le redémarrage du service généralement de résoudre le problème afin que les scripts d’apprentissage automatique peuvent s’exécuter. Si le redémarrage ne résout pas le problème, notez le chemin d’accès et les arguments dans le **chemin d’accès binaire** propriété et procédez comme suit :

    A. Vérifier le fichier .config du Lanceur et assurez-vous que le répertoire de travail est valide.

    B. Vérifiez que le groupe Windows qui est utilisé par Launchpad peut se connecter à l’instance de SQL Server, comme décrit dans la [section précédente](#bkmk_LaunchpadTS).

    c. Si vous modifiez les propriétés de service, redémarrez le service Launchpad.

## <a name="fatal-error-creation-of-tmpfile-failed"></a>« Échec de la création d’une erreur irrécupérable de tmpFile »

Dans ce scénario, vous avez correctement installé les fonctionnalités d’apprentissage automatique et Launchpad est en cours d’exécution. Vous essayez d’exécuter du code R ou Python simple, mais Launchpad échoue avec une erreur semblable à celui-ci : 

>*Impossible de communiquer avec le runtime pour le script R. Vérifiez la configuration requise du runtime R.*

En même temps, le runtime de script externe écrit le message suivant en tant que partie du message STDERR : 

>*Erreur irrécupérable : la création de tmpfile a échoué.*

Cette erreur indique que le compte qui tente d’utiliser Launchpad ne dispose pas d’autorisation de se connecter à la base de données. Cette situation peut se produire en cas d’implémentation des stratégies de sécurité strictes. Pour déterminer si c’est le cas, passez en revue les journaux de SQL Server et vérifier pour voir si le compte MSSQLSERVER01 a été refusé lors de la connexion. Les mêmes informations sont fournies dans les journaux qui sont propres à R\_SERVICES ou PYTHON\_SERVICES. Recherchez ExtLaunchError.log.

Par défaut, 20 comptes sont définies et associés au processus de Launchpad.exe, avec les noms MSSQLSERVER01 via MSSQLSERVER20. Si vous utilisez beaucoup de R ou Python, vous pouvez augmenter le nombre de comptes.

Pour résoudre ce problème, assurez-vous que le groupe possède *autoriser la connexion localement* autorisations à l’instance locale où les fonctionnalités d’apprentissage automatique ont été installées et activées. Dans certains environnements, ce niveau d’autorisation peut nécessiter une exception de l’objet stratégie de groupe à partir de l’administrateur réseau.

## <a name="not-enough-quota-to-process-this-command"></a>« Pas un quota suffisant pour traiter cette commande »

Cette erreur peut signifier plusieurs choses :

- LaunchPad peut avoir des utilisateurs externes insuffisantes pour exécuter la requête externe. Par exemple, si vous exécutez simultanément plus de 20 requêtes externes, et il existe seulement 20 utilisateurs par défaut, une ou plusieurs requêtes peuvent échouer.

- Mémoire disponible est insuffisante pour traiter la tâche R. Cette erreur se produit le plus souvent dans un environnement par défaut, où SQL Server peut être à l’aide de jusqu'à 70 pour cent des ressources de l’ordinateur. Pour plus d’informations sur la modification de la configuration du serveur pour prendre en charge le meilleur parti de ressources par R, consultez [Opérationnalisation de votre code R](r/operationalizing-your-r-code.md).

## <a name="cant-find-package"></a>« Impossible de trouver le package »

Si vous exécutez le code R dans SQL Server et obtenez ce message, mais n’avez pas reçu le message lorsque vous avez exécuté le même code en dehors de SQL Server, cela signifie que le package n’a pas installé à l’emplacement de bibliothèque par défaut utilisé par SQL Server.

Cette erreur peut se produire de nombreuses façons :

- Vous avez installé un nouveau package sur le serveur, mais l’accès a été refusé, R installé le package dans une bibliothèque utilisateur.

- Vous installez R Services installé un autre outil R ou ensemble de bibliothèques, y compris Microsoft R Server (autonome), Microsoft R Client, RStudio et ainsi de suite.

Pour déterminer l’emplacement de la bibliothèque de packages R qui est utilisée par l’instance, ouvrez SQL Server Management Studio (ou tout autre outil de requête de base de données), connectez-vous à l’instance, puis exécutez la procédure stockée suivante :

```SQL
EXEC sp_execute_external_script @language = N'R',  
@script = N' print(normalizePath(R.home())); print(.libPaths());'; 
```

#### <a name="sample-results"></a>Exemples de résultats

*Message(s) STDOUT provenant du script externe :*

*[1] « C:\\Program Files\\Microsoft SQL Server\\MSSQL13. SQL2016\\R_SERVICES »*

*[1] « C:/Program Files/Microsoft SQL Server/MSSQL13. SQL2016 / / bibliothèque R_SERVICES »*

Pour résoudre ce problème, vous devez réinstaller le package à la bibliothèque d’instance de SQL Server.

>[!NOTE]
>Si vous avez mis à niveau une instance de SQL Server 2016 pour utiliser la dernière version de Microsoft R, l’emplacement de bibliothèque par défaut est différent. Pour plus d’informations, consultez [SqlBindR utiliser pour mettre à niveau une instance de R Services](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="launchpad-shuts-down-due-to-mismatched-dlls"></a>LaunchPad est arrêté en raison de la DLL qui ne correspondent pas

Si vous installez le moteur de base de données avec d’autres fonctionnalités, correctifs, le serveur et que vous ajoutez ultérieurement la fonctionnalité de Machine Learning en utilisant le média d’origine, une version incorrecte des composants de Machine Learning peut être installée. Lorsque Launchpad détecte une incompatibilité de version, il s’arrête et crée un fichier dump.

Pour éviter ce problème, veillez à installer les nouvelles fonctionnalités au même niveau de correctif logiciel en tant que l’instance de serveur.

**La mauvaise façon de mettre à niveau :**

1. Installer SQL Server 2016 sans R Services.
2. Mettre à niveau SQL Server 2016 à jour Cumulative 2.
3. Installer R Services (en base de données) à l’aide du support RTM.

**La méthode correcte pour mettre à niveau :**

1. Installer SQL Server 2016 sans R Services.
2. Mettre à niveau SQL Server 2016 vers le niveau de correctif souhaité. Par exemple, installez le Service Pack 1, puis à jour Cumulative 2.
3. Pour ajouter la fonctionnalité au niveau de correctif correcte, réexécutez le programme d’installation de SP1 et CU2, puis choisissez R Services (en base de données). 

## <a name="launchpad-fails-to-start-if-8dot3-notation-is-required"></a>LaunchPad ne parvient pas à démarrer si la notation 8dot3 est requise

> [!NOTE] 
> Sur les systèmes plus anciens, Launchpad peut échouer à démarrer s’il existe une exigence de la notation 8dot3. Cette exigence a été supprimée dans les versions ultérieures. Les clients SQL Server 2016 R Services doivent installer une des opérations suivantes :
> * SQL Server 2016 SP1 et CU1 : [mise à jour Cumulative 1 pour SQL Server](https://support.microsoft.com/help/3208177/cumulative-update-1-for-sql-server-2016-sp1).
> * SQL Server 2016 RTM, mise à jour Cumulative 3 et cela [correctif](https://support.microsoft.com/help/3210110/on-demand-hotfix-update-package-for-sql-server-2016-cu3), qui est disponible à la demande.

Pour la compatibilité avec R, SQL Server 2016 R Services (en base de données) requis le lecteur où la fonctionnalité est installée pour prendre en charge la création de noms de fichiers courts à l’aide de *la notation 8dot3*. Un nom de 8.3 fichier est également appelé un *nom de fichier court*, et il est utilisé pour la compatibilité avec les versions antérieures de Microsoft Windows ou comme alternative aux noms de fichier longs.

Si le volume sur lequel vous installez R ne prend pas en charge les noms de fichiers courts, les processus qui lancent R à partir de SQL Server ne peuvent pas être en mesure de localiser le fichier exécutable correct et Launchpad ne démarrera pas.

Pour résoudre ce problème, vous pouvez activer la notation 8dot3 sur le volume où SQL Server est installé et où R Services est installé. Vous devez ensuite fournir le nom court pour le répertoire de travail dans le fichier de configuration de R Services.

1. Pour activer la notation 8dot3, exécutez l’utilitaire fsutil avec le *8dot3name* argument comme indiqué ici : [fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

2. Après l’activation de la notation 8dot3, ouvrez le fichier RLauncher.config et notez la propriété de `WORKING_DIRECTORY`. Pour plus d’informations sur la façon de trouver ce fichier, consultez [collecte des données pour la résolution des problèmes de Machine Learning](data-collection-ml-troubleshooting-process.md).

3. Utilisez l’utilitaire fsutil avec le *fichier* argument pour spécifier un chemin d’accès de fichier court pour le dossier spécifié dans WORKING_DIRECTORY.

4. Modifiez le fichier de configuration pour spécifier le même répertoire de travail que vous avez entré dans la propriété WORKING_DIRECTORY. Vous pouvez également spécifier un autre répertoire de travail et choisissez un chemin d’accès existant qui est déjà compatible avec la notation 8dot3.


## <a name="next-steps"></a>Étapes suivantes

[Problèmes connus et dépannage de machine Learning Services](machine-learning-troubleshooting-faq.md)

[Collecte de données pour la résolution des problèmes d’apprentissage](data-collection-ml-troubleshooting-process.md)

[FAQ sur la mise à niveau et l’installation](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Résoudre les problèmes de connexions du moteur de base de données](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
