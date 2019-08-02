---
title: Problèmes courants liés au service Launchpad et à l’exécution de scripts externes
ms.prod: sql
ms.technology: ''
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c90c59f3b59850bb0e2d1cf4cf40eb569e965eba
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715285"
---
# <a name="common-issues-with-launchpad-service-and-external-script-execution-in-sql-server"></a>Problèmes courants liés au service Launchpad et à l’exécution de scripts externes dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server Service Launchpad approuvé prend en charge l’exécution de scripts externes pour R et Python. 

Plusieurs problèmes peuvent empêcher le démarrage de Launchpad, y compris les problèmes de configuration ou les modifications, ou les protocoles réseau manquants. Cet article fournit des conseils de dépannage pour de nombreux problèmes. Pour les problèmes que nous avons manqués, vous pouvez poser des questions sur le [Forum de machine learning Server](https://social.msdn.microsoft.com/Forums/en-US/home?category=MicrosoftR).

## <a name="determine-whether-launchpad-is-running"></a>Déterminer si Launchpad est en cours d’exécution

1. Ouvrez le panneau **services** (services. msc). Ou, à partir de la ligne de commande, tapez **SQLServerManager13. msc** ou **SQLServerManager14. msc** pour ouvrir [Gestionnaire de configuration SQL Server](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Notez le compte de service sous lequel Launchpad s’exécute. Chaque instance où R ou python est activé doit avoir sa propre instance du service launchpad. Par exemple, le service pour une instance nommée peut être semblable à _MSSQLLaunchpad $ nom_instance_.

3. Si le service est arrêté, redémarrez-le. Lors du redémarrage, en cas de problème de configuration, un message est publié dans le journal des événements système et le service est de nouveau arrêté. Consultez le journal des événements système pour plus d’informations sur la raison pour laquelle le service s’est arrêté.

4. Examinez le contenu de RSetup. log et assurez-vous qu’il n’y a pas d’erreurs dans le programme d’installation. Par exemple, le message qui s' *arrête avec le code 0* indique l’échec du démarrage du service.

5. Pour rechercher d’autres erreurs, examinez le contenu de rlauncher. log.

## <a name="check-the-launchpad-service-account"></a>Vérifier le compte de service Launchpad

Le compte de service par défaut peut être «\$NT Service SQL2016» ou «\$NT Service SQL2017». La dernière partie peut varier en fonction du nom de votre instance SQL.

Le service Launchpad (launchpad. exe) s’exécute à l’aide d’un compte de service à faibles privilèges. Toutefois, pour démarrer R et Python et communiquer avec l’instance de base de données, le compte de service Launchpad requiert les droits d’utilisateur suivants:

- Ouvrir une session en tant que service (SeServiceLogonRight)
- Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)
- Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)
- Ajuster les quotas de mémoire pour un processus (SeIncreaseQuotaSizePrivilege)

Pour plus d’informations sur ces droits d’utilisateur, consultez la section «privilèges et droits Windows» dans [configurer les comptes de service Windows et les autorisations](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

> [!TIP]
> Si vous êtes familiarisé avec l’utilisation de l’outil SDP (support Diagnostics Platform) pour SQL Server Diagnostics, vous pouvez utiliser SDP pour examiner le fichier de sortie portant le nom MachineName_UserRights. txt.

## <a name="user-group-for-launchpad-cannot-log-on-locally"></a>Le groupe d’utilisateurs pour Launchpad ne peut pas se connecter localement

Pendant l’installation de Machine Learning Services, SQL Server crée le groupe d’utilisateurs Windows **SQLRUserGroup** , puis le configure avec tous les droits nécessaires à la connexion de Launchpad à SQL Server et à l’exécution de tâches de script externes. Si ce groupe d’utilisateurs est activé, il est également utilisé pour exécuter des scripts Python.

Toutefois, dans les organisations où des stratégies de sécurité plus restrictives sont appliquées, les droits requis par ce groupe ont peut-être été supprimés manuellement, ou ils peuvent être automatiquement révoqués par la stratégie. Si les droits ont été supprimés, Launchpad ne peut plus se connecter à SQL Server et SQL Server ne peut pas appeler le runtime externe.

Pour corriger ce problème, vérifiez que le groupe **SQLRUserGroup** dispose du droit système **Permettre l’ouverture d’une session locale**.

Pour plus d’informations, consultez [Configurer les comptes de service Windows et les autorisations](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

## <a name="permissions-to-run-external-scripts"></a>Autorisations d’exécution de scripts externes

Même si Launchpad est configuré correctement, il renvoie une erreur si l’utilisateur n’est pas autorisé à exécuter des scripts R ou python.

Si vous avez installé SQL Server en tant qu’administrateur de base de données ou que vous êtes propriétaire de la base de données, vous bénéficiez automatiquement de cette autorisation. Toutefois, les autres utilisateurs disposent généralement d’autorisations plus limitées. S’ils essaient d’exécuter un script R, ils reçoivent une erreur launchpad.

Pour corriger le problème, dans SQL Server Management Studio, un administrateur de la sécurité peut modifier la connexion SQL ou le compte d’utilisateur Windows en exécutant le script suivant:

```sql
GRANT EXECUTE ANY EXTERNAL SCRIPT TO <username>
```

Pour plus d’informations, consultez [Grant (Transact-SQL](../t-sql/statements/grant-transact-sql.md)).

## <a name="common-launchpad-errors"></a>Erreurs courantes de Launchpad

Cette section répertorie les messages d’erreur les plus courants que Launchpad retourne.

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"
## <a name="unable-to-launch-runtime-for-r-script"></a>«Impossible de lancer le runtime pour le script R»

Si le groupe Windows pour les utilisateurs R (également utilisé pour Python) ne peut pas se connecter à l’instance qui exécute R services, vous pouvez voir les erreurs suivantes:

- Erreurs générées lorsque vous essayez d’exécuter des scripts R:

    * *Impossible de lancer le runtime pour le script « R ». Vérifiez la configuration du runtime « R ».*

    * *Une erreur de script externe s’est produite. Impossible de lancer le runtime.*

- Erreurs générées par [!INCLUDE[rsql_launchpad](../includes/rsql-launchpad-md.md)] le service:

    * *Impossible d’initialiser le lanceur RLauncher.dll*

    * *Aucune DLL de lanceur n’a été enregistrée.*

    * *Les journaux de sécurité indiquent que le SERVICE NT de compte n’a pas pu se connecter*

Pour plus d’informations sur la façon d’accorder à ce groupe d’utilisateurs les autorisations nécessaires, consultez [installer SQL Server R services](install/sql-r-services-windows-install.md).

> [!NOTE]
> Cette limitation ne s’applique pas si vous utilisez des connexions SQL pour exécuter des scripts R à partir d’une station de travail distante.
::: moniker-end

## <a name="logon-failure-the-user-has-not-been-granted-the-requested-logon-type"></a>«Échec de l’ouverture de session: l’utilisateur n’a pas reçu le type de connexion demandé»

Par défaut, [!INCLUDE[rsql_launchpad_md](../includes/rsql-launchpad-md.md)] utilise le compte suivant au démarrage: `NT Service\MSSQLLaunchpad`. Le compte est configuré par [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] le programme d’installation pour disposer de toutes les autorisations nécessaires.

Si vous affectez un autre compte à Launchpad ou si le droit est supprimé par une stratégie sur l’ordinateur SQL Server, il se peut que le compte ne dispose pas des autorisations nécessaires et que l’erreur suivante s’affiche:

>*Échec d’ouverture de session ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) : l’utilisateur ne bénéficie pas du type d’ouverture de session demandé sur cet ordinateur.*

Pour accorder les autorisations nécessaires au nouveau compte de service, utilisez l’application stratégie de sécurité locale et mettez à jour les autorisations sur le compte pour inclure les autorisations suivantes:

+ Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)
+ Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)
+ Ouvrir une session en tant que service (SeServiceLogonRight)
+ Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)

## <a name="unable-to-communicate-with-the-launchpad-service"></a>«Impossible de communiquer avec le service Launchpad»

Si vous avez installé puis activé Machine Learning, mais que vous recevez cette erreur lorsque vous tentez d’exécuter un script R ou python, le service Launchpad de l’instance a peut-être cessé de fonctionner.

1. À partir d’une invite de commandes Windows, ouvrez le Gestionnaire de configuration SQL Server. Pour plus d'informations, consultez [SQL Server Configuration Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Cliquez avec le bouton droit sur SQL Server Launchpad pour l’instance, puis sélectionnez **Propriétés**.

3. Sélectionnez l’onglet **service** , puis vérifiez que le service est en cours d’exécution. S’il n’est pas en cours d’exécution, définissez le **mode de démarrage** sur **automatique**, puis sélectionnez **appliquer**.

4. Le redémarrage du service résout généralement le problème de manière à ce qu’Machine Learning scripts puissent s’exécuter. Si le redémarrage ne résout pas le problème, notez le chemin d’accès et les arguments dans la propriété **chemin d’accès binaire** , puis procédez comme suit:

    a. Examinez le fichier. config du lanceur et assurez-vous que le répertoire de travail est valide.

    b. Assurez-vous que le groupe Windows utilisé par Launchpad peut se connecter à l’instance SQL Server.

    c. Si vous modifiez l’une des propriétés du service, redémarrez le service launchpad.

## <a name="fatal-error-creation-of-tmpfile-failed"></a>«Erreur irrécupérable lors de la création de tmpFile»

Dans ce scénario, vous avez correctement installé les fonctionnalités de Machine Learning et Launchpad est en cours d’exécution. Vous essayez d’exécuter un code R ou python simple, mais Launchpad échoue avec une erreur semblable à la suivante: 

>*Impossible de communiquer avec le runtime pour le script R. Vérifiez la configuration requise du runtime R.*

En même temps, l’exécution du script externe écrit le message suivant dans le message STDERR: 

>*Erreur irrécupérable: échec de la création de tmpfile.*

Cette erreur indique que le compte que Launchpad tente d’utiliser n’a pas l’autorisation de se connecter à la base de données. Cette situation peut se produire lorsque des stratégies de sécurité strictes sont implémentées. Pour déterminer si c’est le cas, passez en revue les journaux de SQL Server et vérifiez si le compte MSSQLSERVER01 a été refusé au niveau de la connexion. Les mêmes informations sont fournies dans les journaux qui sont spécifiques à R\_services ou aux\_services Python. Recherchez ExtLaunchError. log.

Par défaut, 20 comptes sont configurés et associés au processus launchpad. exe, avec les noms MSSQLSERVER01 à MSSQLSERVER20. Si vous utilisez beaucoup R ou python, vous pouvez augmenter le nombre de comptes.

Pour résoudre le problème, assurez-vous que le groupe dispose des autorisations *autoriser l’ouverture d’une session locale* sur l’instance locale où les fonctionnalités de machine learning ont été installées et activées. Dans certains environnements, ce niveau d’autorisation peut nécessiter une exception de l’objet de stratégie de groupe de l’administrateur réseau.

## <a name="not-enough-quota-to-process-this-command"></a>«Quota insuffisant pour traiter cette commande»

Cette erreur peut se traduire par l’une des raisons suivantes:

- Launchpad peut ne pas avoir d’utilisateurs externes suffisants pour exécuter la requête externe. Par exemple, si vous exécutez plus de 20 requêtes externes simultanément et qu’il n’y a que 20 utilisateurs par défaut, une ou plusieurs requêtes peuvent échouer.

- La mémoire disponible est insuffisante pour traiter la tâche R. Cette erreur se produit le plus souvent dans un environnement par défaut, où SQL Server peut utiliser jusqu’à 70% des ressources de l’ordinateur. Pour plus d’informations sur la façon de modifier la configuration du serveur pour qu’il prenne en charge une utilisation plus importante des ressources par R, consultez [fonctionnement de votre code r](r/operationalizing-your-r-code.md).

## <a name="cant-find-package"></a>«Impossible de trouver le package»

Si vous exécutez du code R dans SQL Server et que vous recevez ce message, mais que vous n’avez pas obtenu le message lorsque vous avez exécuté le même code en dehors de SQL Server, cela signifie que le package n’a pas été installé à l’emplacement de la bibliothèque par défaut utilisé par SQL Server.

Cette erreur peut se produire de plusieurs façons:

- Vous avez installé un nouveau package sur le serveur, mais l’accès a été refusé, donc R a installé le package dans une bibliothèque utilisateur.

- Vous avez installé R services, puis vous avez installé un autre outil R ou un ensemble de bibliothèques, y compris Microsoft R Server (autonome), Microsoft R Client, RStudio, et ainsi de suite.

Pour déterminer l’emplacement de la bibliothèque de packages R utilisée par l’instance, ouvrez SQL Server Management Studio (ou tout autre outil de requête de base de données), connectez-vous à l’instance, puis exécutez la procédure stockée suivante:

```sql
EXEC sp_execute_external_script @language = N'R',  
@script = N' print(normalizePath(R.home())); print(.libPaths());'; 
```

#### <a name="sample-results"></a>Exemples de résultats

*Message(s) STDOUT provenant du script externe :*

*[1] "C:\\Program Files\\Microsoft SQL Server\\MSSQL13. SQL2016\\R_SERVICES»*

*[1] «C:/Program Files/Microsoft SQL Server/MSSQL13. SQL2016/R_SERVICES/bibliothèque "*

Pour résoudre le problème, vous devez réinstaller le package dans la bibliothèque d’instances SQL Server.

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"
>[!NOTE]
>Si vous avez mis à niveau une instance de SQL Server 2016 pour utiliser la dernière version de Microsoft R, l’emplacement par défaut de la bibliothèque est différent. Pour plus d’informations, consultez [utiliser SqlBindR pour mettre à niveau une instance de R services](install/upgrade-r-and-python.md).
::: moniker-end

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"
## <a name="launchpad-shuts-down-due-to-mismatched-dlls"></a>Launchpad s’arrête en raison de dll incompatibles

Si vous installez le moteur de base de données avec d’autres fonctionnalités, corrigez le problème du serveur, puis ajoutez ultérieurement la fonctionnalité Machine Learning à l’aide du support d’origine, la version incorrecte des composants Machine Learning peut être installée. Lorsque Launchpad détecte une incompatibilité de version, il s’arrête et crée un fichier de vidage.

Pour éviter ce problème, veillez à installer les nouvelles fonctionnalités au même niveau de correctif que l’instance de serveur.

**La mauvaise façon de mettre à niveau:**

1. Installez SQL Server 2016 sans R services.
2. Mettez à niveau SQL Server 2016 mise à jour cumulative 2.
3. Installez R services (en base de données) à l’aide du média RTM.

**La méthode correcte pour mettre à niveau:**

1. Installez SQL Server 2016 sans R services.
2. Effectuez une mise à niveau de SQL Server 2016 vers le niveau de correctif souhaité. Par exemple, installez le Service Pack 1, puis la mise à jour cumulative 2.
3. Pour ajouter la fonctionnalité au niveau de correctif approprié, exécutez à nouveau SP1 et le programme d’installation de CU2, puis choisissez R services (dans la base de données). 

## <a name="launchpad-fails-to-start-if-8dot3-notation-is-required"></a>Launchpad ne parvient pas à démarrer si la notation 8dot3 est requise

> [!NOTE] 
> Sur les systèmes plus anciens, Launchpad ne peut pas démarrer si une spécification de notation 8dot3 est requise. Cette exigence a été supprimée dans les versions ultérieures. SQL Server 2016 R services les clients doivent installer l’un des éléments suivants:
> * SQL Server 2016 SP1 et CU1: [Mise à jour cumulative 1 pour SQL Server](https://support.microsoft.com/help/3208177/cumulative-update-1-for-sql-server-2016-sp1).
> * SQL Server 2016 RTM, mise à jour cumulative 3 et ce [correctif](https://support.microsoft.com/help/3210110/on-demand-hotfix-update-package-for-sql-server-2016-cu3), disponible à la demande.

Pour la compatibilité avec R, SQL Server 2016 R services (dans la base de données) nécessitait le lecteur sur lequel la fonctionnalité est installée pour prendre en charge la création de noms de fichiers courts à l’aide de la *notation 8dot3*. Un nom de fichier 8,3 est également appelé *nom de fichier abrégé*et il est utilisé pour la compatibilité avec les versions antérieures de Microsoft Windows ou à la place des noms de fichiers longs.

Si le volume sur lequel vous installez R ne prend pas en charge les noms de fichiers courts, les processus qui lancent R à partir de SQL Server peuvent ne pas être en mesure de localiser le fichier exécutable approprié et Launchpad ne démarre pas.

Pour résoudre ce problème, vous pouvez activer la notation 8dot3 sur le volume où SQL Server est installé et où R services est installé. Vous devez ensuite fournir le nom court pour le répertoire de travail dans le fichier de configuration de R Services.

1. Pour activer la notation 8dot3, exécutez l’utilitaire fsutil avec l’argument *8dot3name* comme décrit ici: [fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

2. Une fois la notation 8dot3 activée, ouvrez le fichier RLauncher. config et notez la propriété de `WORKING_DIRECTORY`. Pour plus d’informations sur la recherche de ce fichier, consultez [collecte de données pour machine learning résolution des problèmes](data-collection-ml-troubleshooting-process.md).

3. Utilisez l’utilitaire fsutil avec l’argument *file* pour spécifier un chemin d’accès de fichier bref pour le dossier spécifié dans WORKING_DIRECTORY.

4. Modifiez le fichier de configuration pour spécifier le même répertoire de travail que celui que vous avez entré dans la propriété WORKING_DIRECTORY. Vous pouvez également spécifier un autre répertoire de travail et choisir un chemin d’accès existant qui est déjà compatible avec la notation 8dot3.
::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

[Dépannage Machine Learning Services et problèmes connus](machine-learning-troubleshooting-faq.md)

[Collecte de données pour la résolution des problèmes Machine Learning](data-collection-ml-troubleshooting-process.md)

[FAQ sur la mise à niveau et l’installation](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Résoudre les problèmes de connexion du moteur de base de données](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
