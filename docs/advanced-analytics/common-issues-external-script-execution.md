---
title: Problèmes courants liés à l’exécution du script externe dans SQL Server | Documents Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b1994227284d395e4a8043c6e272bead5cd6c372
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="common-issues-with-external-script-execution-in-sql-server"></a>Problèmes courants liés à l’exécution du script externe dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article contient une liste des problèmes connus et les problèmes courants liés à l’exécution du code R ou Python dans SQL Server.

Avant de commencer, nous vous recommandons de collecter certaines informations relatives à votre système. Pour savoir comment procéder, consultez [collecte des données pour la résolution des problèmes](data-collection-ml-troubleshooting-process.md).

En outre, consultez la liste des problèmes courants qui sont spécifiques à la configuration initiale ou la configuration : [le programme d’installation et de mise à niveau FAQ](r/upgrade-and-installation-faq-sql-server-r-services.md).

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 d’apprentissage automatique Services

## <a name="launchpad-issues"></a>Problèmes de LaunchPad

Le service SQL Server approuvée Launchpad gère l’exécution de scripts externes et la communication avec R, Python ou autres runtimes externe. Plusieurs problèmes peuvent empêcher le Launchpad à partir de démarrage, y compris les problèmes de configuration ou de modifications ou manquant des protocoles réseau.

Dans le cadre du processus de dépannage, commencez par répondre aux questions suivantes :

- Launchpad toujours que l’exécution échoue ou qu’il ne s’est arrêté fonctionne ?
- Quel compte de service Launchpad s’exécute sous ?
- Les droits d’utilisateur du compte de service Launchpad a-t-il ?

### <a name="determine-whether-launchpad-is-running"></a>Déterminer si le Launchpad est en cours d’exécution

1. Ouvrez le **Services** Panneau de configuration (Services.msc). Ou, à partir de la ligne de commande, tapez **SQLServerManager13.msc** ou **SQLServerManager14.msc** pour ouvrir [Gestionnaire de Configuration SQL Server](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Prenez note de Launchpad s’exécute sous le compte de service. Chaque instance d’où R ou Python est activée doit avoir sa propre instance du service Launchpad. Par exemple, le service pour une instance nommée peut être un nom tel que _MSSQLLaunchpad$ InstanceName_.

3. Si le service est arrêté, redémarrez-le. Sur le redémarrage, s’il existe des problèmes avec la configuration, un message est publié dans le journal des événements système et le service est arrêté à nouveau. Vérifiez le journal des événements système pour plus d’informations sur l’arrêt du service.

4. Passez en revue le contenu de RSetup.log et assurez-vous qu’il n’y a pas d’erreurs dans le programme d’installation. Par exemple, le message *sortie avec le code 0* indique l’échec de démarrage du service.

5. Pour rechercher les autres erreurs, examinez le contenu de rlauncher.log.

### <a name="check-the-launchpad-service-account"></a>Vérifier le compte de service Launchpad

Le compte de service par défaut peut être « Service NT\$SQL2016 » ou « Service NT\$SQL2017 ». La dernière partie peut varier selon le nom de votre instance SQL.

Le service Launchpad (Launchpad.exe) s’exécute à l’aide d’un compte de service de faibles. Toutefois, pour démarrer R et Python et communiquer avec l’instance de base de données, le compte de service Launchpad nécessite des droits d’utilisateur suivants :

- Ouvrir une session en tant que service (SeServiceLogonRight)
- Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)
- Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)
- Ajuster les quotas de mémoire pour un processus (SeIncreaseQuotaSizePrivilege)

Pour plus d’informations sur ces droits d’utilisateur, consultez la section « privilèges et droits Windows » dans [Windows de configurer les comptes de service et autorisations](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

> [!TIP]
> Si vous êtes familiarisé avec l’utilisation de l’outil de prise en charge des Diagnostics plate-forme (SDP) pour les diagnostics de SQL Server, vous pouvez utiliser SDP pour passer en revue le fichier de sortie portant le nom MachineName_UserRights.txt.

### <a name="review-launchpad-requirements"></a>Passez en revue les exigences de Launchpad

Une de plusieurs problèmes peuvent empêcher Launchpad de démarrer. Le service Launchpad peut démarrer, puis arrêter ou de panne ou le service se bloque avec un délai de connexion. Dans ces cas, le système a généralement été modifié ou configuré de sorte que le Launchpad ne peut pas s’exécuter.

#### <a name="determine-whether-8dot3-notation-is-enabled"></a>Déterminer si la notation de modèle 8.3 est activée

Pour la compatibilité avec R, SQL Server 2016 R Services (de-de base de données) requis le lecteur où la fonctionnalité est installée pour prendre en charge la création de noms de fichiers courts à l’aide de *modèle 8.3 notation*. Un nom de fichier au format 8.3 est également appelé un *nom de fichier court*, et il est utilisé pour la compatibilité avec les versions antérieures de Microsoft Windows ou en guise d’alternative à des noms de fichier longs.

Si le volume sur lequel vous installez R ne prend pas en charge les noms de fichiers courts, les processus qui lancent R à partir de SQL Server ne peuvent pas être en mesure de localiser le fichier exécutable correct et Launchpad ne démarrera pas.

Pour résoudre ce problème, vous pouvez activer la notation de modèle 8.3 sur le volume où SQL Server est installé et sur lequel les Services de R est installé. Vous devez ensuite fournir le nom court pour le répertoire de travail dans le fichier de configuration de R Services.

1. Pour activer la notation de modèle 8.3, exécutez l’utilitaire fsutil avec le *8dot3name* argument comme décrit ici : [fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

2. Après l’activation de la notation de modèle 8.3, ouvrez le fichier RLauncher.config et notez la propriété de `WORKING_DIRECTORY`. Pour plus d’informations sur la façon de trouver ce fichier, consultez [collecte des données pour la résolution des problèmes de Machine Learning](data-collection-ml-troubleshooting-process.md).

3. Utiliser l’utilitaire fsutil avec le *fichier* argument pour spécifier un chemin d’accès de fichier court pour le dossier qui est spécifié dans WORKING_DIRECTORY.

4. Modifiez le fichier de configuration pour spécifier le même répertoire de travail que vous avez entré dans la propriété WORKING_DIRECTORY. Vous pouvez également spécifier un autre répertoire de travail et choisissez un chemin d’accès existant qui est déjà compatible avec la notation de modèle 8.3.

> [!NOTE] 
> Cette restriction a été supprimée dans les versions suivantes. Si vous rencontrez ce problème, installez un des éléments suivants :
> * SQL Server 2016 SP1 et CU1 : [mise à jour Cumulative 1 pour SQL Server](https://support.microsoft.com/help/3208177/cumulative-update-1-for-sql-server-2016-sp1).
> * SQL Server 2016 RTM, Cumulative Update 3 et cela [correctif](https://support.microsoft.com/help/3210110/on-demand-hotfix-update-package-for-sql-server-2016-cu3), qui est disponible à la demande.

#### <a name="the-user-group-for-launchpad-cannot-log-on-locally"></a>Le groupe d’utilisateurs pour Launchpad ne peut pas ouvrir une session localement

Pendant l’installation des services d’apprentissage automatique, SQL Server crée le groupe d’utilisateurs Windows **SQLRUserGroup** et il configure ensuite avec tous les droits nécessaires pour Launchpad pour vous connecter à SQL Server et exécuter des tâches de script externe. Si ce groupe d’utilisateurs est activé, il est également utilisé pour exécuter des scripts Python.

Toutefois, dans les organisations où les stratégies de sécurité restrictives sont appliquées, les droits requis par ce groupe peuvent avoir été supprimés manuellement ou ils peuvent être automatiquement révoqués par la stratégie. Si les droits ont été supprimées, Launchpad peut ne plus se connecter à SQL Server et SQL Server ne peut pas appeler le runtime externe.

Pour corriger ce problème, vérifiez que le groupe **SQLRUserGroup** dispose du droit système **Permettre l’ouverture d’une session locale**.

Pour plus d’informations, consultez [Windows de configurer les comptes de service et autorisations](https://msdn.microsoft.com/library/ms143504.aspx#Windows).

#### <a name="improper-setup-leading-to-mismatched-dlls"></a>Programme d’installation incorrecte à l’origine d’une DLL ne correspondent pas

Si vous installez le moteur de base de données avec d’autres fonctionnalités, le correctif logiciel du serveur et puis ajoutez ultérieurement la fonctionnalité d’apprentissage à l’aide du support d’origine, une version incorrecte des composants d’apprentissage peut être installée. Lorsque Launchpad détecte une incompatibilité de version, il s’arrête et crée un fichier dump.

Pour éviter ce problème, veillez à installer les nouvelles fonctionnalités au même niveau de correctif logiciel en tant que l’instance de serveur.

**Mauvaise méthode pour mettre à niveau :**

1. Installer SQL Server 2016 sans R Services.
2. Mise à niveau de la mise à jour Cumulative de SQL Server 2016 2.
3. Installer R Services (de-de base de données) à l’aide du support RTM.

**La méthode correcte pour mettre à niveau :**

1. Installer SQL Server 2016 sans R Services.
2. Mise à niveau de SQL Server 2016 vers le niveau de correctif souhaité. Par exemple, installer le Service Pack 1, puis Cumulative Update 2.
3. Pour ajouter la fonctionnalité au niveau du correctif approprié, réexécutez le programme d’installation de SP1 et CU2 et appuyez sur R Services (de-de base de données). 

#### <a name="check-whether-a-user-has-rights-to-run-external-scripts"></a>Vérifiez si un utilisateur dispose des droits pour exécuter des scripts externes

Même si le Launchpad est correctement configuré, il retourne une erreur si l’utilisateur n’est pas autorisé à exécuter des scripts R ou Python.

Si vous avez installé SQL Server en tant qu’un administrateur de base de données ou que vous êtes propriétaire d’une base de données, vous sont accordées automatiquement cette autorisation. Toutefois, les autres utilisateurs généralement aient plus d’autorisations limitées. S’ils essaient d’exécuter un script R, ils obtiennent une erreur de Launchpad.

Pour corriger le problème, dans SQL Server Management Studio, un administrateur de sécurité peut modifier le compte de connexion SQL ou un compte d’utilisateur Windows en exécutant le script suivant :

```SQL
GRANT EXECUTE ANY EXTERNAL SCRIPT TO <username>
```

Pour plus d’informations, consultez [GRANT (Transact-SQL](../t-sql/statements/grant-transact-sql.md).

### <a name="common-launchpad-errors"></a>Erreurs courantes de Launchpad

Cette section répertorie les messages d’erreur courants qui renvoie du Launchpad.

#### <a name="error-unable-to-launch-runtime-for-r-script"></a>Erreur : *Impossible de lancer le runtime pour le script R*

Si le groupe Windows pour les utilisateurs de R (également utilisé pour Python) ne peut pas se connecter à l’instance qui est en cours d’exécution R Services, vous pouvez voir les erreurs suivantes :

- Erreurs sont générées lorsque vous essayez d’exécuter des scripts R :

    * *Impossible de lancer le runtime pour le script « R ». Vérifiez la configuration du runtime « R ».*

    * *Une erreur de script externe s’est produite. Impossible de lancer le runtime.*

- Les erreurs générées par le [!INCLUDE[rsql_launchpad](../includes/rsql-launchpad-md.md)] service :

    * *Impossible d’initialiser le lanceur RLauncher.dll*

    * *Aucune DLL de lanceur n’a été enregistrée.*

    * *Journaux de sécurité indiquent que le compte de SERVICE NT a été incapable de se connecter*

Pour plus d’informations sur la façon d’accorder à ce groupe d’utilisateurs les autorisations nécessaires, consultez [installer SQL Server 2016 R Services](install/sql-r-services-windows-install.md).

> [!NOTE]
> Cette limitation ne s’applique pas si vous utilisez des connexions SQL pour exécuter des scripts R à partir d’une station de travail distante.

#### <a name="error-logon-failure-the-user-has-not-been-granted-the-requested-logon-type"></a>Erreur : *Échec d’ouverture de session : l’utilisateur ne dispose pas du type d’accès demandé*

Par défaut, [!INCLUDE[rsql_launchpad_md](../includes/rsql-launchpad-md.md)] utilise le compte suivant lors du démarrage : `NT Service\MSSQLLaunchpad`. Le compte est configuré par [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] le programme d’installation pour que toutes les autorisations nécessaires.

Si vous affectez un compte différent à Launchpad, ou le droit est supprimé par une stratégie sur l’ordinateur SQL Server, le compte n’a ne peut-être pas les autorisations nécessaires, et vous pouvez voir cette erreur :

>*Échec d’ouverture de session ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) : l’utilisateur ne bénéficie pas du type d’ouverture de session demandé sur cet ordinateur.*

Pour accorder des autorisations nécessaires pour le nouveau compte de service, utilisez l’application de la stratégie de sécurité locale et mettre à jour les autorisations sur le compte à inclure les autorisations suivantes :

+ Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)
+ Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)
+ Ouvrir une session en tant que service (SeServiceLogonRight)
+ Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)

#### <a name="error-unable-to-communicate-with-the-launchpad-service"></a>Erreur : *Impossible de communiquer avec le service Launchpad*

Si vous avez installé, puis apprentissage, mais que vous obtenez cette erreur lorsque vous essayez d’exécuter un script R ou Python, le Launchpad service pour l’instance est peut-être arrêté en cours d’exécution.

1. À partir d’une invite de commandes Windows, ouvrez le Gestionnaire de configuration SQL Server. Pour plus d’informations, consultez [SQL Server Configuration Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Avec le bouton droit de Launchpad de SQL Server pour l’instance, puis sélectionnez **propriétés**.

3. Sélectionnez le **Service** onglet et vérifiez que le service est en cours d’exécution. Si elle n’est pas en cours d’exécution, modifiez le **le Mode de démarrage** à **automatique**, puis sélectionnez **appliquer**.

4. Le redémarrage du service généralement de résoudre le problème afin que d’exécuter des scripts d’apprentissage machine. Si le redémarrage ne résout pas le problème, notez le chemin d’accès et les arguments dans le **chemin d’accès binaire** propriété et procédez comme suit :

    A. Vérifier le fichier .config de l’utilitaire de chargement et assurez-vous que le répertoire de travail est valide.

    B. Vérifiez que le groupe Windows qui est utilisé par le Launchpad peut se connecter à l’instance de SQL Server, comme décrit dans la [section précédente](#bkmk_LaunchpadTS).

    c. Si vous modifiez les propriétés de service, redémarrez le service Launchpad.

#### <a name="error-fatal-error-creation-of-tmpfile-failed"></a>Erreur : *Échec de la création d’une erreur irrécupérable de tmpFile*

Dans ce scénario, vous avez correctement installé les fonctionnalités de machine learning et Launchpad est en cours d’exécution. Vous essayez d’exécuter du code R ou Python simple, mais Launchpad échoue avec une erreur semblable à celui-ci : 

>*Impossible de communiquer avec le runtime pour le script R. Vérifiez la configuration requise du runtime R.*

En même temps, l’exécution du script externe écrit le message suivant en tant que partie du message STDERR : 

>*Erreur irrécupérable : la création de tmpfile a échoué.*

Cette erreur indique que le compte qui tente d’utiliser Launchpad ne dispose pas d’autorisation de se connecter à la base de données. Cette situation peut se produire lors de l’implémentation des stratégies de sécurité stricte. Pour déterminer si c’est le cas, passez en revue les journaux SQL Server et vérifiez pour voir si le compte MSSQLSERVER01 a été refusé lors de la connexion. Les mêmes informations sont fournies dans les fichiers journaux qui sont spécifiques à R\_SERVICES ou PYTHON\_SERVICES. Recherchez ExtLaunchError.log.

Par défaut, 20 comptes sont définies et associés au processus Launchpad.exe, avec les noms MSSQLSERVER01 via MSSQLSERVER20. Si vous faites un usage intensif de R ou Python, vous pouvez augmenter le nombre de comptes.

Pour résoudre ce problème, assurez-vous que le groupe a *autoriser la connexion localement* autorisations à l’instance locale où les fonctionnalités de machine learning ont été installées et activées. Dans certains environnements, ce niveau d’autorisation peut nécessiter une exception de la stratégie de groupe à partir de l’administrateur réseau.

## <a name="r-script-issues"></a>Problèmes de script R

Cette section contient certains problèmes courants qui sont spécifiques à l’exécution du script R et les erreurs de script R. La liste n’est pas exhaustive, car il existe de nombreux packages R et erreurs peuvent différer entre les versions du même package R. Nous vous conseillons de valider les erreurs de script R sur le [forum Microsoft R Server](https://social.msdn.microsoft.com/Forums/home?category=MicrosoftR), qui prend en charge les composants utilisés dans R Services (de-de base de données), Machine Learning Services avec Microsoft R, Python et le Client Microsoft R d’apprentissage automatique Serveur.

### <a name="multiple-r-instances-on-the-same-computer"></a>Plusieurs instances de R sur le même ordinateur

Il est facile de vous retrouver avec plusieurs distributions de R sur le même ordinateur, ainsi que plusieurs copies du même package R dans des versions différentes. Par exemple, si vous installez Machine Learning Server (autonome) et Machine Learning Services (de-de base de données), les programmes d’installation de créer des versions distinctes des bibliothèques R. 

Cette duplication devient un problème lorsque vous essayez d’exécuter un script à partir d’une ligne de commande et que vous ne savez pas les bibliothèques que vous utilisez. Ou bien, vous pouvez installer un package à la bibliothèque incorrecte et demandez plus tard pourquoi vous ne trouvez pas le package à partir de SQL Server.

+ Éviter l’utilisation directe des bibliothèques R et des outils qui sont installés pour l’utilisation de l’instance de SQL Server, sauf dans certains cas limités telles que le dépannage ou l’installation de nouveaux packages. 
+ Si vous devez utiliser un outil de ligne de commande R, vous pouvez installer [Microsoft R Client](https://docs.microsoft.com/r-server/r-client/what-is-microsoft-r-client). 
+ SQL Server fournit une gestion de base de données de packages R. Il s’agit de la façon la plus simple pour créer des bibliothèques de package de R peuvent être partagés entre les utilisateurs. Pour plus d’informations, consultez [gestion des packages R pour SQL Server](r/r-package-management-for-sql-server-r-services.md).

### <a name="avoid-clearing-the-workspace-while-youre-running-r-in-a-sql-compute-context"></a>Évitez de désactiver l’espace de travail en cours d’exécution R dans un contexte de calcul SQL

Bien qu’il soit courant d’effacement de l’espace de travail lorsque vous travaillez dans la console R, il peut avoir des conséquences inattendues dans SQL contexte de calcul.

`revoScriptConnection` est un objet dans l’espace de travail R qui contient des informations sur une session R appelée à partir de SQL Server. Toutefois, si votre code R inclut une commande pour effacer l’espace de travail (tels que `rm(list=ls())`), toutes les informations sur la session et d’autres objets dans l’espace de travail R sont également désactivées.

Pour résoudre ce problème, évitez d’effacement manque de discernement dans des variables et autres objets en cours d’exécution R dans SQL Server. Vous pouvez supprimer des variables spécifiques à l’aide de la **supprimer** fonction :

```R
remove('name1', 'name2', ...)
```

S’il existe plusieurs variables à supprimer, nous vous suggérons d’enregistrer les noms des variables temporaires à une liste et ensuite effectuer périodiques garbage collection sur la liste.

### <a name="implied-authentication-for-remote-execution-via-odbc"></a>Authentification implicite pour l’exécution à distance via ODBC

Si vous vous connectez à la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] commandes de l’ordinateur pour exécuter R à l’aide de la **RevoScaleR** fonctions, vous pouvez obtenir une erreur lorsque vous utilisez des appels ODBC qui écrivent des données sur le serveur. Cette erreur se produit uniquement lorsque vous utilisez l’authentification Windows.

La raison est que les comptes de travail qui sont créés pour R Services n’ont pas d’autorisation de se connecter au serveur. Par conséquent, les appels ODBC ne peut pas être exécutées en votre nom. Le problème ne se produit pas avec les connexions SQL, car, avec les connexions SQL, les informations d’identification sont transmises explicitement à partir du client de R à l’instance de SQL Server, puis à ODBC. Toutefois, à l’aide de connexions SQL est également moins sécurisée que l’authentification Windows.

Pour activer vos informations d’identification Windows à passer en toute sécurité à partir d’un script qui a lancé à distance, SQL Server doit émuler vos informations d’identification. Ce processus est appelé _l’authentification implicite_. Pour ce faire, les comptes de travail qui exécutent des scripts R ou Python sur l’ordinateur SQL Server doivent avoir les autorisations appropriées.

1. Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] en tant qu’administrateur sur l’instance où vous souhaitez exécuter le code R.

2. Exécutez le script suivant. Veillez à modifier le nom du groupe d’utilisateurs, si vous avez modifié la valeur par défaut et les noms d’ordinateur et d’instance.

    ```SQL
    USE [master]
    GO
    
    CREATE LOGIN [computername\\SQLRUserGroup] FROM WINDOWS WITH
    DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO
    ```

### <a name="the-r-script-works-outside-of-t-sql-but-not-in-a-stored-procedure"></a>Le script R fonctionne en dehors de T-SQL, mais pas dans une procédure stockée

Avant d’encapsuler votre code R dans une procédure stockée, il est judicieux d’exécuter votre code R dans un IDE externe, ou dans un des outils tels que RTerm ou RGui R. À l’aide de ces méthodes, vous pouvez tester et déboguer le code en utilisant les messages d’erreur détaillés sont retournés par R.

Toutefois, parfois le code qui fonctionne parfaitement dans un IDE ou l’utilitaire externe peut échouer à s’exécuter dans une procédure stockée ou le contexte de calcul dans un serveur SQL Server. Dans ce cas, il existe de nombreux problèmes pour rechercher des avant que vous pouvez supposer que le package ne fonctionne pas dans SQL Server.

1. Vérifiez si le Launchpad est en cours d’exécution.

2. Passez en revue les messages pour voir si les données d’entrée ou les données de sortie contient des colonnes avec des types de données incompatibles ou non pris en charge. Par exemple, les requêtes sur une base de données SQL retournent souvent GUID ou ROWGUID, qui sont tous deux non pris en charge. Pour plus d’informations, consultez [R bibliothèques et types de données](r/r-libraries-and-data-types.md).

3. Passez en revue les pages d’aide pour les fonctions R individuelles déterminer si tous les paramètres sont pris en charge pour le contexte de calcul de SQL Server. Pour obtenir l’aide ScaleR, utilisez les commandes d’aide inline R, ou consultez [une référence au Package](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler).

### <a name="you-get-different-results-from-the-same-script-when-running-in-sql-compared-to-other-environments"></a>Vous obtenez des résultats différents dans le même script lors de l’exécution dans SQL par rapport à d’autres environnements

Des scripts R peuvent retourner des valeurs différentes dans un contexte de SQL Server, pour plusieurs raisons :

- Conversion de type implicite est automatiquement effectuée sur certains types de données lorsque les données sont transmises entre SQL Server et R. Pour plus d’informations, consultez [R bibliothèques et types de données](r/r-libraries-and-data-types.md).

- Déterminez si le nombre de bits est un facteur. Par exemple, il existe souvent des différences dans les résultats des opérations mathématiques pour les bibliothèques de point flottant 32 bits et 64 bits.

- Déterminer si les valeurs NaN ont été générés pour les opérations. Cela peut invalider les résultats.

- Petites différences peuvent être amplifiées lorsque vous effectuez un réciproque d’un nombre proche de zéro.

- Les erreurs d’arrondi cumulées peuvent entraîner des éléments tels que les valeurs qui sont inférieures à zéro au lieu de zéro.

### <a name="error-not-enough-quota-to-process-this-command"></a>Erreur : *pas suffisamment de quota pour traiter cette commande*

Cette erreur peut indiquer plusieurs possibilités :

- LaunchPad peut avoir des utilisateurs externes insuffisantes pour exécuter la requête externe. Par exemple, si vous exécutez simultanément plus de 20 requêtes externes, et il existe uniquement 20 utilisateurs par défaut, une ou plusieurs requêtes risque d’échouer.

- Mémoire disponible est insuffisante pour traiter la tâche de R. Cette erreur se produit le plus souvent dans un environnement par défaut, où SQL Server peut être à l’aide de 70 pour cent des ressources de l’ordinateur. Pour plus d’informations sur la façon de modifier la configuration du serveur pour prendre en charge une plus grande utilisation de ressources par R, consultez [Opérationnalisation de votre code R](r/operationalizing-your-r-code.md).

### <a name="error-cant-find-package"></a>Erreur : *Impossible de trouver le package*

Si vous exécutez le code R dans SQL Server et obtenez ce message, mais n’avez pas reçu le message lorsque vous avez exécuté le même code en dehors de SQL Server, cela signifie que le package n’est pas installé à l’emplacement de bibliothèque par défaut utilisé par SQL Server.

Cette erreur peut se produire de différentes façons :

- Vous avez installé un nouveau package sur le serveur, mais l’accès a été refusé, R installé le package dans une bibliothèque de l’utilisateur.

- Vous installé R Services installé un autre outil de R ou ensemble de bibliothèques, y compris Microsoft R Server (autonome), le Client Microsoft R, RStudio et ainsi de suite.

Pour déterminer l’emplacement de la bibliothèque de package de R qui est utilisée par l’instance, ouvrez SQL Server Management Studio (ou tout autre outil de requête de base de données), connectez-vous à l’instance, puis exécutez la procédure stockée suivante :

```SQL
EXEC sp_execute_external_script @language = N'R',  
@script = N' print(normalizePath(R.home())); print(.libPaths());'; 
```

#### <a name="sample-results"></a>Exemples de résultats

*Message(s) STDOUT provenant du script externe :*

*[1] » C:\\fichiers programme\\Microsoft SQL Server\\MSSQL13. SQL2016\\R_SERVICES »*

*[1] » C:/Program Files/Microsoft SQL Server/MSSQL13. R_SERVICES/SQL2016/bibliothèque »*

Pour résoudre ce problème, vous devez réinstaller le package à la bibliothèque d’instance de SQL Server.

>[!NOTE]
>Si vous avez mis à niveau une instance de SQL Server 2016 à utiliser la dernière version de Microsoft R, l’emplacement de la bibliothèque par défaut est différent. Pour plus d’informations, consultez [SqlBindR utilisé pour mettre à niveau une instance de R Services](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="next-steps"></a>Étapes suivantes

[Problèmes connus et dépannage de machine Learning Services](machine-learning-troubleshooting-faq.md)

[Collecte de données pour la résolution des problèmes d’apprentissage](data-collection-ml-troubleshooting-process.md)

[FAQ sur la mise à niveau et l’installation](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Résoudre les problèmes de connexions du moteur de base de données](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
