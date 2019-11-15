---
title: Collecte de données pour la résolution de problèmes
description: Découvrez les méthodes de collecte de données à utiliser quand vous tentez de résoudre des problèmes par vous-même ou avec l’aide du support technique de Microsoft.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 15c570594f84bf8d1d61abac4bc4e4c372f18784
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727609"
---
# <a name="troubleshoot-data-collection-for-machine-learning"></a>Collecte de données pour la résolution de problèmes de machine learning

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article décrit les méthodes de collecte de données à utiliser quand vous tentez de résoudre des problèmes par vous-même ou avec l’aide du support technique de Microsoft.

## <a name="sql-server-version-and-edition"></a>Version et édition de SQL Server

SQL Server 2016 R Services est la première version de SQL Server à intégrer la prise en charge de R. SQL Server 2016 Service Pack 1 (SP1) inclut plusieurs améliorations majeures, notamment la possibilité d’exécuter des scripts externes. Si vous utilisez SQL Server 2016, songez à installer SP1 ou ultérieur.

SQL Server 2017 et ultérieur intègrent le langage Python. L’intégration des fonctionnalités Python n’est pas proposée dans les versions antérieures.

Si vous avez besoin d’aide pour trouver l’édition et les versions, consultez cet article qui liste les numéros de build des différentes [versions de SQL Server](https://social.technet.microsoft.com/wiki/contents/articles/783.sql-server-versions.aspx#Service_Pack_editions).

Selon l’édition de SQL Server que vous utilisez, certaines fonctionnalités de machine learning peuvent être indisponibles ou limitées. Les articles suivants listent les fonctionnalités de machine learning dans les éditions Entreprise, Développeur, Standard et Express.

* [Éditions et fonctionnalités prises en charge de SQL Server](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)
* [Fonctionnalités R et Python par éditions de SQL Server](r/differences-in-r-features-between-editions-of-sql-server.md)

## <a name="r-language-and-tool-versions"></a>Versions des outils et du langage R

En général, la version de Microsoft R qui est installée quand vous sélectionnez la fonctionnalité R Services ou Machine Learning Services est déterminée par le numéro de build de SQL Server. Si vous mettez à niveau SQL Server ou appliquer un correctif, vous devez effectuer la même opération sur ses composants R.

Pour obtenir la liste des versions et des liens vers les téléchargements des composants R, consultez [Installer des composants de machine learning sans accès à Internet](https://docs.microsoft.com/sql/advanced-analytics/r/installing-ml-components-without-internet-access). Sur les ordinateurs disposant d’un accès à Internet, la version requise de R est identifiée et installée automatiquement.

Il est possible de mettre à niveau les composants R Server séparément du moteur de base de données SQL Server, dans un processus appelé « liaison ». La version de R que vous utilisez quand vous exécutez du code R dans SQL Server peut donc varier en fonction de la version de SQL Server installée et selon que vous ayez ou non migré le serveur vers la dernière version de R.

### <a name="determine-the-r-version"></a>Déterminer la version de R

Le moyen le plus simple de déterminer la version de R consiste à obtenir les propriétés de runtime en exécutant une instruction telle que la suivante :

```sql
exec sp_execute_external_script
       @language = N'R'
       , @script = N'
# Transform R version properties to data.frame
OutputDataSet <- data.frame(
  property_name = c("R.version", "Revo.version"),
  property_value = c(R.Version()$version.string, Revo.version$version.string),
  stringsAsFactors = FALSE)
# Retrieve properties like R.home, libPath & default packages
OutputDataSet <- rbind(OutputDataSet, data.frame(
  property_name = c("R.home", "libPaths", "defaultPackages"),
  property_value = c(R.home(), .libPaths(), paste(getOption("defaultPackages"), collapse=", ")),
  stringsAsFactors = FALSE)
)
'
WITH RESULT SETS ((PropertyName nvarchar(100), PropertyValue nvarchar(4000)));

```

> [!TIP]
> Si R Services ne fonctionne pas, essayez d’exécuter uniquement la partie du script R à partir de RGui.

En dernier recours, vous pouvez ouvrir des fichiers sur le serveur pour déterminer la version installée. Pour ce faire, localisez le fichier rlauncher.config pour obtenir l’emplacement du runtime R et le répertoire de travail actuel. Nous vous recommandons de créer et d’ouvrir une copie du fichier pour ne pas modifier accidentellement des propriétés.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name\MSSQL\Binn\rlauncher.config`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Binn\rlauncher.config`

Pour obtenir la version de R et les versions de RevoScaleR, ouvrez une invite de commande R ou le RGui associé à l’instance.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64\RGui.exe`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES\bin\x64\RGui.exe`

La console R affiche les informations de version au démarrage. Par exemple, la version suivante représente la configuration par défaut pour SQL Server 2017 :

    *Microsoft R Open 3.3.3*

    *The enhanced R distribution from Microsoft*

    *Microsoft packages Copyright (C) 2017 Microsoft*

    *Loading Microsoft R Server packages, version 9.1.0.*

## <a name="python-versions"></a>Versions de Python

Vous pouvez obtenir la version de Python de plusieurs façons. Le moyen le plus simple consiste à exécuter l’instruction suivante à partir de Management Studio ou d’un autre outil de requête SQL :

```sql
-- Get Python runtime properties:
exec sp_execute_external_script
       @language = N'Python'
       , @script = N'
import sys
import pkg_resources
OutputDataSet = pandas.DataFrame(
                    {"property_name": ["Python.home", "Python.version", "Revo.version", "libpaths"],
                    "property_value": [sys.executable[:-10], sys.version, pkg_resources.get_distribution("revoscalepy").version, str(sys.path)]}
)
'
with WITH RESULT SETS (SQL keywords) ((PropertyName nvarchar(100), PropertyValue nvarchar(4000)));
```

Si Machine Learning Services n’est pas en cours d’exécution, vous pouvez déterminer la version de Python installée en examinant le fichier pythonlauncher.config. Nous vous recommandons de créer et d’ouvrir une copie du fichier pour ne pas modifier accidentellement des propriétés.

1. Pour SQL Server 2017 uniquement : `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog\pythonlauncher.config`
2. Obtenez la valeur de **PYTHONHOME**.
3. Obtenez la valeur du répertoire de travail actuel.

> [!NOTE]
> Si vous avez installé Python et R dans SQL Server 2017, le répertoire de travail et le pool de comptes de travail sont partagés pour les langages R et Python.

## <a name="are-multiple-instances-of-r-or-python-installed"></a>Plusieurs instances de R ou de Python sont-elles installées ?

Vérifiez si plusieurs copies des bibliothèques R sont installées sur l’ordinateur. Cette duplication peut se produire dans les cas suivants :

* Pendant l’installation, vous sélectionnez R Services (en base de données) et R Server (autonome).
* Vous installez Microsoft R Client en plus de SQL Server.
* Un autre ensemble de bibliothèques R a été installé à l’aide d’Outils R pour Visual Studio, R Studio, Microsoft R Client ou un autre IDE R.
* L’ordinateur héberge plusieurs instances de SQL Server, et plusieurs utilisent le machine learning.

Les mêmes conditions s’appliquent à Python.

Si vous constatez que plusieurs bibliothèques ou runtimes sont installés, vérifiez que vous obtenez uniquement les erreurs associées aux runtimes Python ou R qui sont utilisés par l’instance SQL Server.

## <a name="origin-of-errors"></a>Origine des erreurs

Les erreurs que vous voyez quand vous tentez d’exécuter du code R peuvent provenir des sources suivantes :

* Moteur de base de données SQL Server, notamment la procédure stockée sp_execute_external_script
* SQL Server Trusted Launchpad
* Autres composants du framework d’extensibilité, notamment les lanceurs R et Python et les processus satellites
* Fournisseurs, tels que Microsoft Open Database Connectivity (ODBC)
* Langage R

Quand vous utilisez le service pour la première fois, il peut être difficile de savoir de quels services proviennent les messages. Nous vous recommandons de capturer non seulement le texte exact du message, mais également son contexte. Notez le logiciel client que vous utilisez pour exécuter le code machine learning :

* Utilisez-vous Management Studio ? Une application externe ?
* Exécutez-vous du code R dans un client distant ou directement dans une procédure stockée ?

## <a name="sql-server-log-files"></a>Fichiers journaux SQL Server

Obtenez le journal des erreurs de SQL Server le plus récent. L’ensemble complet des journaux des erreurs se compose des fichiers du répertoire de journaux par défaut suivant :

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.SQL2016\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> Le nom exact du dossier varie en fonction du nom de l’instance.

## <a name="errors-returned-by-sp_execute_external_script"></a>Erreurs retournées par sp_execute_external_script

Obtenez le texte complet des erreurs retournées, le cas échéant, quand vous exécutez la commande sp_execute_external_script.

Pour ne pas tenir compte des problèmes liés à R ou Python, vous pouvez exécuter ce script qui démarre le runtime R ou Python et passe les données dans les deux sens.

**Pour R**

```sql
exec sp_execute_external_script @language =N'R',  
@script=N'OutputDataSet<-InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

**Pour Python**

```sql
exec sp_execute_external_script @language =N'Python',  
@script=N'OutputDataSet= InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

## <a name="errors-generated-by-the-extensibility-framework"></a>Erreurs générées par le framework d’extensibilité

SQL Server génère des journaux distincts pour les runtimes de langage de script externes. Ces erreurs ne sont pas générées par le langage Python ou R. Elles proviennent des composants d’extensibilité dans SQL Server, notamment des lanceurs spécifiques au langage et de leurs processus satellites.

Vous pouvez obtenir ces journaux à partir des emplacements par défaut suivants :

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> Le nom exact du dossier varie en fonction du nom de l’instance. Selon votre configuration, le dossier peut se trouver sur un autre lecteur.

Par exemple, les messages de journal suivants sont liés au framework d’extensibilité :

* *Échec de LogonUser pour l’utilisateur MSSQLSERVER01*
  
  Ce message peut indiquer que les comptes de travail qui exécutent des scripts externes ne peuvent pas accéder à l’instance.

* *Échec de InitializePhysicalUsersPool*
  
  Ce message peut signifier que vos paramètres de sécurité empêchent le programme d’installation de créer le pool de comptes de travail requis pour exécuter des scripts externes.

* *Échec d’initialisation du gestionnaire de contexte de sécurité*

* *Échec d’initialisation du gestionnaire de session satellite*

## <a name="system-events"></a>Événements système

1. Ouvrez l’observateur d’événements Windows et recherchez dans le journal des **événements système** des messages contenant la chaîne *Launchpad*.
2. Ouvrez le fichier ExtLaunchErrorlog et recherchez la chaîne *ErrorCode*. Examinez le message associé au code d’erreur.

Par exemple, les messages suivants sont des erreurs système courantes liées au framework d’extensibilité SQL Server :

* *Le service SQL Server Launchpad (MSSQLSERVER) n’a pas pu démarrer en raison de l’erreur :<text>*

* *Le service n’a pas répondu assez vite à la demande de lancement ou de contrôle.*

* *Le dépassement de délai (120 000 millisecondes) a été atteint lors de l’attente de la connexion du service SQL Server Launchpad (MSSQLSERVER).*

## <a name="dump-files"></a>Fichiers de vidage sur incident

Si vous avez des connaissances en matière de débogage, vous pouvez utiliser les fichiers de vidage sur incident pour analyser une défaillance dans Launchpad.

1. Localisez le dossier qui contient les journaux de démarrage du programme d’installation pour SQL Server. Par exemple, dans SQL Server 2016, le chemin par défaut est C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log.
2. Ouvrez le sous-dossier du journal de démarrage spécifique à l’extensibilité.
3. Si vous devez envoyer une demande de support, ajoutez tout le contenu de ce dossier dans un fichier zip. Par exemple, C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log\LOG\ExtensibilityLog.
  
L’emplacement exact peut être différent sur votre système et peut se trouver sur un lecteur autre que votre lecteur C. Veillez à obtenir les journaux de l’instance où le machine learning est installé.

## <a name="configuration-settings"></a>Paramètres de configuration

Cette section liste les composants ou fournisseurs supplémentaires qui peuvent être une source d’erreurs quand vous exécutez des scripts R ou Python.

### <a name="what-network-protocols-are-available"></a>Quels sont les protocoles réseau disponibles ?

Machine Learning Services nécessite les protocoles réseau suivants pour la communication interne entre les composants d’extensibilité et pour la communication avec les clients R ou Python externes.

* Canaux nommés
* TCP/IP

Ouvrez le Gestionnaire de configuration SQL Server pour déterminer si un protocole est installé et, le cas échéant, pour savoir s’il est activé.

### <a name="security-configuration-and-permissions"></a>Configuration de la sécurité et autorisations

Pour les comptes de travail :

1. Dans le Panneau de configuration, ouvrez **Utilisateurs et groupes** et recherchez le groupe utilisé pour exécuter des travaux de script externes. Par défaut, le groupe est **SQLRUserGroup**.
2. Vérifiez que le groupe existe et qu’il contient au moins un compte de travail.
3. Dans SQL Server Management Studio, sélectionnez l’instance où les travaux R ou Python seront exécutés, sélectionnez **Sécurité**, puis déterminez s’il existe une ouverture de session pour SQLRUserGroup.
4. Passez en revue les autorisations du groupe d’utilisateurs.

Pour les comptes d’utilisateur individuels :

1. Déterminez si l’instance prend en charge l’authentification en mode mixte, les connexions SQL uniquement ou l’authentification Windows uniquement. Ce paramètre affecte les exigences relatives au code R ou Python.
2. Pour chaque utilisateur ayant besoin d’exécuter du code R, déterminez le niveau d’autorisation requis sur chaque base de données où des objets seront écrits à partir de R, des données seront consultées ou des objets seront créés.
3. Pour activer l’exécution de scripts, créez des rôles ou ajoutez des utilisateurs aux rôles suivants si nécessaire :

   - Tout sauf *db_owner* : exiger EXECUTE ANY EXTERNAL SCRIPT.
   - *db_datawriter* : pour écrire des résultats à partir de R ou Python.
   - *db_ddladmin* : pour créer des objets.
   - *db_datareader* : pour lire les données utilisées par le code R ou Python.
4. Notez si vous avez modifié des comptes de démarrage par défaut quand vous avez installé SQL Server 2016.
5. Si un utilisateur a besoin d’installer de nouveaux packages R ou d’utiliser des packages R qui ont été installés par d’autres utilisateurs, vous devrez peut-être activer la gestion des packages sur l’instance, puis affecter des autorisations supplémentaires. Pour plus d’informations, consultez [Activer ou désactiver la gestion des packages R](r/r-package-how-to-enable-or-disable.md).

### <a name="what-folders-are-subject-to-locking-by-antivirus-software"></a>Quels sont les dossiers verrouillés par un antivirus ?

Un antivirus peut verrouiller des dossiers, ce qui empêche à la fois la configuration des fonctionnalités de machine learning et l’exécution de scripts. Déterminez si des dossiers de l’arborescence SQL Server font l’objet d’une analyse antivirus.

Toutefois, quand plusieurs services ou fonctionnalités sont installés sur une instance, il peut être difficile d’énumérer tous les dossiers possibles utilisés par l’instance. Par exemple, quand de nouvelles fonctionnalités sont ajoutées, les nouveaux dossiers doivent être identifiés et exclus.

En outre, certaines fonctionnalités créent des dossiers de manière dynamique au moment de l’exécution. Par exemple, les tables OLTP en mémoire, les procédures stockées et les fonctions créent toutes des répertoires au moment de l’exécution. Ces noms de dossiers contiennent souvent des GUID et ne peuvent pas être prédits. SQL Server Trusted Launchpad crée des répertoires de travail pour les travaux de script R et Python.

Étant donné qu’il n’est pas possible d’exclure tous les dossiers requis par le processus SQL Server et ses fonctionnalités, nous vous recommandons d’exclure l’intégralité de l’arborescence de répertoires de l’instance SQL Server.

### <a name="is-the-firewall-open-for-sql-server-does-the-instance-support-remote-connections"></a>Le pare-feu est-il ouvert pour SQL Server ? L’instance prend-elle en charge les connexions à distance ?

1. Pour déterminer si SQL Server prend en charge les connexions à distance, consultez [Configurer les connexions au serveur distant](../database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md).

2. Déterminez si une règle de pare-feu a été créée pour SQL Server. Pour des raisons de sécurité, dans une installation par défaut, il est possible que le client R ou Python distant ne puisse pas se connecter à l’instance. Pour plus d’informations, consultez [Résolution des problèmes de connexion à SQL Server](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md).

## <a name="see-also"></a>Voir aussi

[Résoudre les problèmes de machine learning dans SQL Server](machine-learning-troubleshooting-faq.md)
