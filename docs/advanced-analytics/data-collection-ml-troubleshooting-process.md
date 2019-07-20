---
title: Résoudre les problèmes de collecte de données pour Machine Learning
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/28/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: f7d5e39d0ca0a89312a6fefd261eff950859d0a2
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68343385"
---
# <a name="troubleshoot-data-collection-for-machine-learning"></a>Résoudre les problèmes de collecte de données pour Machine Learning

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit les méthodes de collecte des données que vous devez utiliser lorsque vous tentez de résoudre des problèmes par vous-même ou avec l’aide du support technique Microsoft.

**S’applique à :** SQL Server 2016 R services, SQL Server 2017 Machine Learning Services (R et Python)

## <a name="sql-server-version-and-edition"></a>Version et édition de SQL Server

SQL Server 2016 R services est la première version de SQL Server pour inclure la prise en charge de R intégrée. SQL Server 2016 Service Pack 1 (SP1) inclut plusieurs améliorations majeures, notamment la possibilité d’exécuter des scripts externes. Si vous êtes un client SQL Server 2016, vous devez envisager d’installer SP1 ou une version ultérieure.

SQL Server 2017 a ajouté l’intégration du langage Python. Vous ne pouvez pas accéder à la fonctionnalité d’intégration de Python dans les versions antérieures.

Pour obtenir de l’aide sur l’édition et les versions de, consultez cet article, qui répertorie les numéros de build de chacune des [versions de SQL Server](https://social.technet.microsoft.com/wiki/contents/articles/783.sql-server-versions.aspx#Service_Pack_editions).

Selon l’édition de SQL Server que vous utilisez, certaines fonctionnalités Machine Learning peuvent être indisponibles ou limitées. Les articles suivants répertorient les fonctionnalités de Machine Learning dans les éditions Enterprise, Developer, standard et Express.

* [Éditions et fonctionnalités prises en charge de SQL Server](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)
* [Fonctionnalités R et Python par éditions de SQL Server](r/differences-in-r-features-between-editions-of-sql-server.md)

## <a name="r-language-and-tool-versions"></a>Langage R et versions d’outils

En général, la version de Microsoft R qui est installée lorsque vous sélectionnez la fonctionnalité R services ou la fonctionnalité Machine Learning Services est déterminée par le numéro de build SQL Server. Si vous effectuez une mise à niveau ou un correctif SQL Server, vous devez également mettre à niveau ou corriger ses composants R.

Pour obtenir la liste des mises en production et des liens vers les téléchargements de composants R, consultez [installer des composants machine learning sans accès à Internet](https://docs.microsoft.com/sql/advanced-analytics/r/installing-ml-components-without-internet-access). Sur les ordinateurs disposant d’un accès à Internet, la version requise de R est identifiée et installée automatiquement.

Il est possible de mettre à niveau les composants R Server séparément du moteur de base de données SQL Server, dans un processus connu sous le nom de liaison. Par conséquent, la version de R que vous utilisez lorsque vous exécutez du code R dans SQL Server peut différer selon la version installée de SQL Server et si vous avez migré le serveur vers la dernière version de R.

### <a name="determine-the-r-version"></a>Déterminer la version de R

Le moyen le plus simple de déterminer la version R consiste à obtenir les propriétés d’exécution en exécutant une instruction telle que la suivante:

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
> Si R services ne fonctionne pas, essayez d’exécuter uniquement la partie script R à partir de l’RGui.

En dernier recours, vous pouvez ouvrir des fichiers sur le serveur pour déterminer la version installée. Pour ce faire, localisez le fichier rlauncher. config pour obtenir l’emplacement du runtime R et le répertoire de travail actuel. Nous vous recommandons de créer et d’ouvrir une copie du fichier afin de ne pas modifier accidentellement des propriétés.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name\MSSQL\Binn\rlauncher.config`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Binn\rlauncher.config`

Pour accéder aux versions R et RevoScaleR, ouvrez une invite de commandes R ou ouvrez l’RGui associée à l’instance.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64\RGui.exe`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES\bin\x64\RGui.exe`

La console R affiche les informations de version au démarrage. Par exemple, la version suivante représente la configuration par défaut pour SQL Server 2017:

    *Microsoft R Open 3.3.3*

    *The enhanced R distribution from Microsoft*

    *Microsoft packages Copyright (C) 2017 Microsoft*

    *Loading Microsoft R Server packages, version 9.1.0.*

## <a name="python-versions"></a>Versions de Python

Il existe plusieurs façons d’utiliser la version de Python. La méthode la plus simple consiste à exécuter cette instruction à partir de Management Studio ou d’un autre outil de requête SQL:

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

Si Machine Learning Services n’est pas en cours d’exécution, vous pouvez déterminer la version de Python installée en examinant le fichier pythonlauncher. config. Nous vous recommandons de créer et d’ouvrir une copie du fichier afin de ne pas modifier accidentellement des propriétés.

1. Pour SQL Server 2017 uniquement:`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog\pythonlauncher.config`
2. Obtient la valeur de **PYTHONHOME**.
3. Obtient la valeur du répertoire de travail actuel.

> [!NOTE]
> Si vous avez installé python et R dans SQL Server 2017, le répertoire de travail et le pool de comptes de travail sont partagés pour les langages R et Python.

## <a name="are-multiple-instances-of-r-or-python-installed"></a>Plusieurs instances de R ou python sont-elles installées?

Vérifiez si plusieurs copies des bibliothèques R sont installées sur l’ordinateur. Cette duplication peut se produire dans les cas suivants:

* Pendant l’installation, vous devez sélectionner R services (en base de données) et R Server (autonome).
* Vous installez Microsoft R Client en plus de SQL Server.
* Un autre ensemble de bibliothèques R a été installé à l’aide de Outils R pour Visual Studio, R Studio, Microsoft R Client ou un autre IDE R.
* L’ordinateur héberge plusieurs instances de SQL Server, et plus d’une instance utilise Machine Learning.

Les mêmes conditions s’appliquent à python.

Si vous constatez que plusieurs bibliothèques ou runtimes sont installés, assurez-vous que vous obtenez uniquement les erreurs associées aux runtimes python ou R qui sont utilisées par l’instance SQL Server.

## <a name="origin-of-errors"></a>Origine des erreurs

Les erreurs que vous voyez lorsque vous tentez d’exécuter du code R peuvent provenir de l’une des sources suivantes:

* SQL Server moteur de base de données, y compris la procédure stockée sp_execute_external_script
* Le SQL Server Launchpad approuvé
* Autres composants de l’infrastructure d’extensibilité, y compris les lanceurs et les processus satellites R et Python
* Fournisseurs, tels que Microsoft Open Database Connectivity (ODBC)
* Langage R

Lorsque vous utilisez le service pour la première fois, il peut être difficile de savoir quels sont les messages provenant de quels services. Nous vous recommandons de capturer non seulement le texte exact du message, mais le contexte dans lequel vous avez vu le message. Notez le logiciel client que vous utilisez pour exécuter Machine Learning Code:

* Utilisez-vous Management Studio? Une application externe?
* Exécutez-vous du code R dans un client distant ou directement dans une procédure stockée?

## <a name="sql-server-log-files"></a>SQL Server les fichiers journaux

Obtient le journal des erreurs de SQL Server le plus récent. L’ensemble complet des journaux d’erreurs se compose des fichiers du répertoire de journaux par défaut suivant:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.SQL2016\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> Le nom exact du dossier diffère selon le nom de l’instance.

## <a name="errors-returned-by-spexecuteexternalscript"></a>Erreurs retournées par sp_execute_external_script

Obtenir le texte complet des erreurs retournées, le cas échéant, lorsque vous exécutez la commande sp_execute_external_script.

Pour supprimer les problèmes R ou python, vous pouvez exécuter ce script, qui démarre le runtime R ou python et transmet les données.

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

## <a name="errors-generated-by-the-extensibility-framework"></a>Erreurs générées par l’infrastructure d’extensibilité

SQL Server génère des journaux distincts pour les runtimes de langage de script externes. Ces erreurs ne sont pas générées par le langage Python ou R. Ils sont générés à partir des composants d’extensibilité dans SQL Server, y compris les lanceurs spécifiques à la langue et leurs processus satellites.

Vous pouvez récupérer ces journaux à partir des emplacements par défaut suivants:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> Le nom exact du dossier diffère en fonction du nom de l’instance. Selon votre configuration, le dossier peut se trouver sur un autre lecteur.

Par exemple, les messages de journal suivants sont liés à l’infrastructure d’extensibilité:

* *Échec de LogonUser pour l’utilisateur MSSQLSERVER01*
  
  Cela peut indiquer que les comptes de travail qui exécutent des scripts externes ne peuvent pas accéder à l’instance.

* *Échec de InitializePhysicalUsersPool*
  
  Ce message peut signifier que vos paramètres de sécurité empêchent le programme d’installation de créer le pool de comptes de travail requis pour exécuter des scripts externes.

* *Échec de l’initialisation du gestionnaire de contexte de sécurité*

* *Échec de l’initialisation du gestionnaire de session satellite*

## <a name="system-events"></a>Événements système

1. Ouvrez Windows observateur d’événements et recherchez dans le journal des **événements système** des messages qui incluent la chaîne *Launchpad*.
2. Ouvrez le fichier ExtLaunchErrorlog et recherchez la chaîne *ErrorCode*. Examinez le message associé à ErrorCode.

Par exemple, les messages suivants sont des erreurs système courantes liées au SQL Server infrastructure d’extensibilité:

* *Le service SQL Server Launchpad (MSSQLSERVER) n’a pas pu démarrer en raison de l’erreur suivante:<text>*

* *Le service n’a pas répondu à temps à la demande de démarrage ou de contrôle.*

* *Un délai d’attente a été atteint (120000 millisecondes) lors de l’attente de la connexion du service SQL Server Launchpad (MSSQLSERVER).*

## <a name="dump-files"></a>Fichiers dump

Si vous connaissez le débogage, vous pouvez utiliser les fichiers de vidage pour analyser un échec dans launchpad.

1. Localisez le dossier qui contient les journaux d’amorçage du programme d’installation pour SQL Server. Par exemple, dans SQL Server 2016, le chemin d’accès par défaut est C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log.
2. Ouvrez le sous-dossier du journal de démarrage qui est spécifique à l’extensibilité.
3. Si vous devez envoyer une demande de support, ajoutez tout le contenu de ce dossier dans un fichier compressé. Par exemple, C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log\LOG\ExtensibilityLog.
  
L’emplacement exact peut être différent sur votre système, et il peut se trouver sur un lecteur autre que votre lecteur C. Veillez à obtenir les journaux de l’instance sur laquelle Machine Learning est installé.

## <a name="configuration-settings"></a>Paramètres de configuration

Cette section répertorie les composants ou fournisseurs supplémentaires qui peuvent être une source d’Erreurs lorsque vous exécutez des scripts R ou python.

### <a name="what-network-protocols-are-available"></a>Quels protocoles réseau sont disponibles?

Machine Learning Services requiert les protocoles réseau suivants pour la communication interne entre les composants d’extensibilité et pour la communication avec les clients R ou python externes.

* Canaux nommés
* TCP/IP

Ouvrez Gestionnaire de configuration SQL Server pour déterminer si un protocole est installé et, s’il est installé, pour déterminer s’il est activé.

### <a name="security-configuration-and-permissions"></a>Configuration et autorisations de sécurité

Pour les comptes de travail:

1. Dans le panneau de configuration, ouvrez **utilisateurs et groupes**, puis recherchez le groupe utilisé pour exécuter des tâches de script externe. Par défaut, le groupe est **SQLRUserGroup**.
2. Vérifiez que le groupe existe et qu’il contient au moins un compte de travail.
3. Dans SQL Server Management Studio, sélectionnez l’instance où les travaux R ou python seront exécutés, sélectionnez **sécurité**, puis déterminez s’il existe une ouverture de session pour SQLRUserGroup.
4. Passez en revue les autorisations pour le groupe d’utilisateurs.

Pour les comptes d’utilisateur individuels:

1. Déterminez si l’instance prend en charge l’authentification en mode mixte, les connexions SQL uniquement ou l’authentification Windows uniquement. Ce paramètre affecte vos exigences en matière de code R ou python.
2. Pour chaque utilisateur qui doit exécuter du code R, déterminez le niveau d’autorisations requis sur chaque base de données où les objets seront écrits à partir de R, les données seront consultées ou les objets seront créés.
3. Pour activer l’exécution des scripts, créez des rôles ou ajoutez des utilisateurs aux rôles suivants, si nécessaire:

   - Tout sauf *db_owner*: Exiger l’exécution d’un SCRIPT externe.
   - *db_datawriter* : Pour écrire des résultats à partir de R ou python.
   - *db_ddladmin*: Pour créer des objets.
   - *db_datareader* : Pour lire les données utilisées par le code R ou python.
4. Notez si vous avez modifié des comptes de démarrage par défaut lorsque vous avez installé SQL Server 2016.
5. Si un utilisateur a besoin d’installer de nouveaux packages R ou d’utiliser des packages R qui ont été installés par d’autres utilisateurs, vous devrez peut-être activer la gestion des packages sur l’instance, puis attribuer des autorisations supplémentaires. Pour plus d’informations, consultez [activer ou désactiver la gestion des packages R](r/r-package-how-to-enable-or-disable.md).

### <a name="what-folders-are-subject-to-locking-by-antivirus-software"></a>Quels dossiers sont soumis au verrouillage par un logiciel antivirus?

Un logiciel antivirus peut verrouiller des dossiers, ce qui empêche la configuration des fonctionnalités de Machine Learning et l’exécution de scripts réussie. Déterminez si les dossiers de l’arborescence SQL Server sont soumis à une analyse antivirus.

Toutefois, lorsque plusieurs services ou fonctionnalités sont installés sur une instance, il peut être difficile d’énumérer tous les dossiers possibles utilisés par l’instance. Par exemple, lorsque de nouvelles fonctionnalités sont ajoutées, les nouveaux dossiers doivent être identifiés et exclus.

En outre, certaines fonctionnalités créent des dossiers de manière dynamique au moment de l’exécution. Par exemple, les tables OLTP en mémoire, les procédures stockées et les fonctions créent toutes des répertoires au moment de l’exécution. Ces noms de dossiers contiennent souvent des GUID et ne peuvent pas être prédits. La SQL Server Launchpad approuvée crée de nouveaux répertoires de travail pour les travaux de script R et Python.

Étant donné qu’il n’est pas possible d’exclure tous les dossiers requis par le processus de SQL Server et ses fonctionnalités, nous vous recommandons d’exclure l’intégralité de l’arborescence de répertoires de l’instance SQL Server.

### <a name="is-the-firewall-open-for-sql-server-does-the-instance-support-remote-connections"></a>Le pare-feu est-il ouvert pour SQL Server? L’instance prend-elle en charge les connexions à distance?

1. Pour déterminer si SQL Server prend en charge les connexions à distance, consultez [configurer des connexions au serveur distant](../database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md).

2. Déterminez si une règle de pare-feu a été créée pour SQL Server. Pour des raisons de sécurité, dans une installation par défaut, il est possible que le client R ou python distant ne puisse pas se connecter à l’instance. Pour plus d’informations, consultez [résolution des problèmes de connexion à SQL Server](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md).

## <a name="see-also"></a>Voir aussi

[Résoudre les problèmes de Machine Learning dans SQL Server](machine-learning-troubleshooting-faq.md)
