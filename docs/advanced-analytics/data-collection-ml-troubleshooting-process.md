---
title: "Résoudre les problèmes de collecte de données pour l’apprentissage - SQL Server"
ms.custom: 
ms.date: 06/16/2017
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4225b87b8aab3bac5e023ef194cf7a2bc35c8dc2
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="troubleshoot-data-collection-for-machine-learning"></a>Résoudre les problèmes de collecte de données pour l’apprentissage

Cet article décrit le type de données que vous devez rassembler lorsque vous tentez de résoudre des problèmes avec le programme d’installation, de configuration ou de performances de l’apprentissage automatique dans SQL Server. Ces données incluent les journaux, les messages d’erreur et les informations système.

L’article décrit les sources d’informations qui sont particulièrement utiles lorsque vous effectuez des diagnostics sur une base d’auto-assistance. Collecte de ces informations est également utile lorsque vous demandez un support technique pour les problèmes liés aux fonctionnalités de SQL Server machine learning.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 d’apprentissage Services (R et Python)

## <a name="sql-server-and-r-versions"></a>Versions de SQL Server et R

Notez que si la version est une nouvelle installation ou une mise à niveau. S’il s’agit d’une mise à niveau, déterminez comment elle a été effectuée :

- La version mise à jour à partir de ? 
- Avez-vous supprimé des anciens composants, ou la mise en place ?
- N’a changé le toutes les sélections de fonctionnalités pendant la mise à niveau ? 

### <a name="which-edition-of-sql-server-is-installed-and-which-version"></a>Quelle édition de SQL Server est installée et la version ? 

SQL Server R Services a été introduite dans SQL Server 2016. Les versions précédentes ne prennent pas en charge apprentissage. En outre, les service packs suivants pour la version 2016 incluaient plusieurs correctifs de bogues et améliorations. Dans un premier temps, vous devez envisager d’installer le Service Pack 1 ou version ultérieure.

Dans SQL Server 2017, prise en charge est étendue pour le langage Python. Prise en charge de Python n’a pas été fourni dans les versions antérieures.

Si vous avez besoin d’aide pour déterminer quelle version et Édition, consultez cet article, qui répertorie les numéros de build pour chacun de la [versions de SQL Server](https://social.technet.microsoft.com/wiki/contents/articles/783.sql-server-versions.aspx#Service_Pack_editions).

Selon l’édition de SQL Server, vous utilisez, certaines fonctionnalités d’apprentissage peut être indisponible ou limité.

Consultez les rubriques suivantes pour obtenir la liste des fonctionnalités d’apprentissage machine dans les éditions Enterprise, Developer, Standard et Express.

* [Éditions et des fonctionnalités prises en charge de SQL Server](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)
* [Différences de fonctionnalités de R entre les éditions de SQL Server](https://docs.microsoft.com/sql/advanced-analytics/r/differences-in-r-features-between-editions-of-sql-server)

### <a name="which-version-of-microsoft-r-is-installed"></a>La version de Microsoft R est installée ?

En général, la version de Microsoft R qui est installé lorsque vous sélectionnez la fonctionnalité Services de R ou la fonction Machine Learning Services est déterminée par le numéro de version de SQL Server. Si vous mettez à niveau ou de correctif logiciel SQL Server, vous devez également mettre à niveau ou ses composants R de correctif logiciel.

Pour obtenir la liste des versions et des liens vers des téléchargements de composants R, consultez [installer les composants d’apprentissage ordinateur sans accès à internet](https://docs.microsoft.com/sql/advanced-analytics/r/installing-ml-components-without-internet-access). Sur les ordinateurs ayant accès à internet, la version requise de R est identifiée et installée automatiquement.

Il est possible de mettre à niveau les composants R Server séparément à partir du moteur de base de données SQL Server, dans un processus appelé liaison. Par conséquent, la version de R que vous utilisez lorsque vous exécutez le code R dans SQL Server peut-être différer selon la version installée de SQL Server et que si vous avez migré le serveur vers la dernière version de R.

#### <a name="determine-the-r-version"></a>Déterminer la version de R

Pour déterminer la version de R, le plus simple consiste à obtenir les propriétés d’exécution en exécutant une instruction telle que les éléments suivants :

```SQL
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
> Si R Services ne fonctionne pas, essayez d’exécuter uniquement la partie du script R à partir de l’interface RGui.

En dernier recours, vous pouvez ouvrir des fichiers sur le serveur pour déterminer la version installée. Pour ce faire, recherchez le fichier de rlauncher.config pour obtenir l’emplacement du runtime R et le répertoire de travail actuel. Nous vous recommandons de faire et ouvrir une copie du fichier afin que vous ne modifiez pas accidentellement des propriétés.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name\MSSQL\Binn\rlauncher.config`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Binn\rlauncher.config`

Pour obtenir la version de R et les versions de RevoScaleR, ouvrez une invite de commandes R, ou ouvrez l’interface RGui qui est associé à l’instance.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64\RGui.exe`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES\bin\x64\RGui.exe`


La console R affiche les informations de version au démarrage. Par exemple, la version suivante représente la configuration par défaut pour SQL Server 2017 CTP 2.0 :

    *Microsoft R Open 3.3.3*
    
    *The enhanced R distribution from Microsoft*
    
    *Microsoft packages Copyright (C) 2017 Microsoft*
    
    *Loading Microsoft R Server packages, version 9.1.0.*


### <a name="what-version-of-python-is-installed"></a>Quelle version de Python est installée ?

Prise en charge pour Python est disponible uniquement dans SQL Server 2017 Community Technology Preview (CTP) 2.0 et versions ultérieures.

Il existe plusieurs façons d’obtenir la version de Python. La plus simple consiste à exécuter cette instruction à partir de Management Studio ou tout autre outil de requête SQL :

```SQL
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

Si la Machine Learning Services n’est pas en cours d’exécution, vous pouvez déterminer la version installée de Python en examinant le fichier pythonlauncher.config. Nous vous recommandons de faire et ouvrir une copie du fichier afin que vous ne modifiez pas accidentellement des propriétés.

1. Pour SQL Server 2017 uniquement :`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog\pythonlauncher.config `
2. Obtenir la valeur de **PYTHONHOME**.
3. Obtenir la valeur du répertoire de travail actuel.


> [!NOTE]
> Si vous avez installé les Python et R dans SQL Server 2017, le répertoire de travail et le pool de comptes de travail sont partagés pour les langues R et Python.

### <a name="are-multiple-instances-of-r-or-python-installed"></a>Plusieurs instances de R ou Python installé ?

Vérifiez si plusieurs copies des bibliothèques R est installé sur l’ordinateur. Cette duplication peut se produire si :

* Lors de l’installation, vous sélectionnez R Services (de-de base de données) et R Server (autonome). 
* Vous installez le Client Microsoft R en plus de SQL Server.
* Un autre ensemble de bibliothèques R a été installé à l’aide des outils R pour Visual Studio, R Studio, le Client Microsoft R ou un autre IDE R.
* L’ordinateur héberge plusieurs instances de SQL Server, et une seule instance utilise l’apprentissage.

Les mêmes conditions s’appliquent à Python.

Si vous trouvez que plusieurs bibliothèques, ou runtimes sont installés, assurez-vous que vous obtenez uniquement les erreurs associées aux runtimes Python ou R qui sont utilisées par l’instance de SQL Server.

## <a name="errors-and-messages"></a>Erreurs et des messages

Les erreurs que vous voyez lorsque vous tentez d’exécuter le code R peuvent provenir d’une des sources suivantes :

- Moteur de base de données SQL Server, y compris la procédure stockée sp_execute_external_script
- Le serveur SQL Server approuvée Launchpad 
- Autres composants de l’infrastructure d’extensibilité, y compris les lanceurs R et Python et des processus satellites
- Base de données de fournisseurs, tels que Microsoft Open Connectivity (ODBC)
- Langage R

Lorsque vous travaillez avec le service pour la première fois, il peut être difficile de déterminer quels messages sont issus les services. Il est recommandé que vous capturez non seulement le texte du message exacte, mais le contexte dans lequel vous avez vu le message. Notez le logiciel client que vous utilisez pour exécuter le code machine learning :

- Vous utilisez Management Studio ? Une application externe ?
- Vous exécutez du code R dans un client distant, ou directement dans une procédure stockée ?

### <a name="what-errors-has-sql-server-logged"></a>Les erreurs SQL Server a ouvert une session ?

Obtenir le plus récent journal des erreurs de SQL Server. L’ensemble complet de journaux d’erreurs se compose des fichiers à partir du répertoire de journal par défaut suivant :

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.SQL2016\MSSQL\Log\ExtensibilityLog`

> [!NOTE] 
> Le nom exact des dossiers diffère selon le nom d’instance.


### <a name="what-errors-were-returned-by-the-spexecuteexternalscript-command"></a>Les erreurs ont été retournées par la commande sp_execute_external_script ?

Obtenir le texte complet des erreurs sont retournées, si elle existe, lorsque vous exécutez la commande sp_execute_external_script. 

Pour supprimer les problèmes de R ou Python pas prises en compte, vous pouvez exécuter ce script, ce qui démarre le runtime R ou Python et transmet des données dans les deux sens.

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

### <a name="what-errors-are-generated-by-the-extensibility-framework"></a>Les erreurs sont générées par l’infrastructure d’extensibilité ?

SQL Server génère des journaux distincts pour les exécutions de langage de script externe. Ces erreurs ne sont pas générés par le langage Python ou R. Elles sont générées à partir des composants d’extensibilité dans SQL Server, y compris linguistiques lanceurs et leurs processus satellite.

Vous pouvez obtenir ces journaux à partir d’emplacements par défaut suivants :

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog `

> [!NOTE] 
> Le nom de dossier exact diffère selon le nom d’instance. Selon votre configuration, le dossier peut être sur un autre lecteur.

Par exemple, les messages de journal suivantes sont liées à l’infrastructure d’extensibilité :

* *Échec de LogonUser pour l’utilisateur MSSQLSERVER01*
  
  Cela peut indiquer que les comptes de travail qui exécutent des scripts externes ne peuvent pas accéder à l’instance.

* *InitializePhysicalUsersPool a échoué* 
  
  Ce message peut signifier que vos paramètres de sécurité empêchent le programme d’installation à partir de la création du pool de comptes de travail qui sont nécessaires pour exécuter des scripts externes.

* *Échoué de l’initialisation du Gestionnaire de contexte de sécurité* 

* *Échoué de l’initialisation du Gestionnaire de sessions satellites*

### <a name="are-there-any-related-system-events"></a>Y a-t-il des événements système associés ?

1. Ouvrez l’Observateur d’événements Windows et recherchez le **événement système** journal pour les messages qui contiennent la chaîne *Launchpad*. 
2. Ouvrez le fichier ExtLaunchErrorlog et recherchez la chaîne *ErrorCode*. Examinez le message associé avec le code d’erreur.

Par exemple, les messages suivants sont des erreurs système courantes liées à l’infrastructure d’extensibilité SQL Server : 

* *Le service Launchpad de SQL Server (MSSQLSERVER) a échoué car l’erreur suivante :<text>*

* *Le service n’a pas répondu à la demande de démarrage ou de contrôle en temps voulu.* 

* *Un délai d’attente a été atteint (120000 en millisecondes) pendant l’attente pour le service Launchpad de SQL Server (MSSQLSERVER) pour se connecter.* 

### <a name="did-any-components-start-and-then-crash"></a>Des composants démarrer et puis incident ?

Si vous savez sur le débogage, vous pouvez utiliser les fichiers de vidage pour analyser une défaillance dans le Launchpad.

1. Recherchez le dossier qui contient les journaux d’amorçage d’installation de SQL Server. Par exemple, dans SQL Server 2016, le chemin d’accès par défaut est C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log.
2. Ouvrez le sous-dossier de journal d’amorçage est spécifique à l’extensibilité.
3. Si vous devez envoyer une demande de prise en charge, ajoutez tout le contenu de ce dossier dans un fichier compressé. Par exemple, C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log\LOG\ExtensibilityLog.
  
L’emplacement exact peut être différent sur votre système, et il peut être sur un lecteur autre que votre lecteur C. Veillez à obtenir les journaux pour l’instance où l’apprentissage est installé. 


## <a name="related-tools-and-configuration"></a>Configuration et les outils connexes

Cette section répertorie les composants supplémentaires ou des fournisseurs qui peuvent être une source d’erreurs lorsque vous exécutez des scripts R ou Python.

### <a name="what-network-protocols-are-available"></a>Les protocoles réseau sont disponibles ?

Machine Learning Services nécessite les protocoles réseau suivants pour la communication interne entre les composants d’extensibilité et pour la communication avec les clients externes de R ou Python.

* Canaux nommés
* TCP/IP

Ouvrez le Gestionnaire de Configuration SQL Server pour déterminer si un protocole est installé et, s’il est installé, afin de déterminer si elle est activée.

### <a name="security-configuration-and-permissions"></a>Autorisations et la configuration de sécurité

Pour les comptes de travail :

1. Dans le panneau de configuration, ouvrez **utilisateurs et groupes**, recherchez le groupe utilisé pour exécuter des tâches de script externe. Par défaut, le groupe est **SQLRUserGroup**.
2. Vérifiez que le groupe existe et qu’il contient le compte d’au moins un travail.
3. Dans SQL Server Management Studio, sélectionnez l’instance où sont exécutés les travaux R ou Python, sélectionnez **sécurité**, puis déterminez s’il existe une ouverture de session pour SQLRUserGroup.
4. Examinez les autorisations pour le groupe d’utilisateurs.

Pour les comptes d’utilisateur individuels :

1. Déterminer si l’instance prend en charge l’authentification en Mode mixte, uniquement les connexions SQL ou l’authentification Windows uniquement. Ce paramètre affecte votre R ou exigences de code Python.
2. Pour chaque utilisateur ayant besoin d’exécuter le code R, déterminez le niveau requis d’autorisations sur chaque base de données où les objets seront écrites à partir de R, les données seront accessibles ou objets seront créés.
3. Pour activer l’exécution du script, créer des rôles ou ajouter des utilisateurs aux rôles suivants, selon les besoins :

   - Tout sauf *db_owner*: nécessitent EXECUTE ANY EXTERNAL SCRIPT.
   - *db_datawriter*: pour écrire les résultats à partir de R ou Python. 
   - *db_ddladmin*: pour créer des objets. 
   - *db_datareader*: lire les données qui sont utilisées par le code R ou Python. 
4. Notez que si vous avez modifié les comptes de démarrage par défaut lors de l’installation de SQL Server 2016.
5. Si un utilisateur a besoin installer de nouveaux packages R ou utiliser des packages R qui ont été installées par d’autres utilisateurs, vous devrez peut-être activer la gestion des packages sur l’instance et lui attribuer des autorisations supplémentaires. Pour plus d’informations, consultez [activer ou désactiver la gestion des packages R](r\r-package-how-to-enable-or-disable.md).

### <a name="what-folders-are-subject-to-locking-by-antivirus-software"></a>Les dossiers qui sont soumises à verrouillage par un logiciel antivirus ?

Le logiciel antivirus peut verrouiller des dossiers, ce qui empêche le programme d’installation de l’apprentissage de fonctionnalités et l’exécution du script réussie. Déterminer si tous les dossiers dans l’arborescence de SQL Server sont soumis à une analyse antivirus.

Toutefois, lorsque plusieurs fonctions ou services sont installées sur une instance, il peut être difficile à énumérer tous les dossiers possibles qui sont utilisées par l’instance. Par exemple, lorsque de nouvelles fonctionnalités sont ajoutées, les nouveaux dossiers doivent être identifiés et exclus.

En outre, certaines fonctionnalités de créer des dossiers dynamiquement lors de l’exécution. Par exemple, les tables OLTP en mémoire, les procédures stockées et fonctions créent nouveaux répertoires lors de l’exécution. Souvent, ces noms de dossiers contiennent des GUID et ne peut pas être prédite. Le Launchpad approuvé de SQL Server crée des répertoires de travail pour R et Python script de travaux.

Car il ne seront peut-être pas possible d’exclure tous les dossiers qui sont requises par le processus SQL Server et de ses fonctionnalités, nous vous recommandons d’exclure l’arborescence entière du répertoire de l’instance de SQL Server.

### <a name="is-the-firewall-open-for-sql-server-does-the-instance-support-remote-connections"></a>Est le pare-feu ouvert pour SQL Server ? L’instance prend en charge les connexions à distance ?

1. Pour déterminer si SQL Server prend en charge les connexions à distance, consultez [configurer des connexions au serveur distant](../database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md).

2. Déterminer si une règle de pare-feu a été créée pour SQL Server. Pour des raisons de sécurité, dans une installation par défaut, il ne peut pas possible pour un client R ou Python à distance pour se connecter à l’instance. Pour plus d’informations, consultez [résolution des problèmes de connexion à SQL Server](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md).

### <a name="can-you-run-r-script-outside-t-sql"></a>Peut exécuter un script R à l’extérieur de T-SQL ?

Vous pouvez essayer du runtime R qui est associé à l’instance SQL Server à l’aide d’autres outils R en cours d’exécution. De cette façon, vous pouvez déterminer si les bibliothèques requises sont installées.

Une installation de base de R inclut plusieurs outils que vous pouvez utiliser pour exécuter un script R à partir de la ligne de commande, ainsi que RGui d’exécution interactive des scripts.

Si le runtime R fonctionne, mais votre script retourne des erreurs, nous vous recommandons d’essayer de déboguer le script dans un environnement de développement R dédié, telles que les outils R pour Visual Studio.

Nous vous recommandons également que vous passez en revue et légèrement Réécrivez le script pour corriger les problèmes liés aux types de données qui peuvent se produire lorsque vous déplacez des données entre R et le moteur de base de données. Pour plus d’informations, consultez [R bibliothèques et types de données](r/r-libraries-and-data-types.md).

En outre, vous pouvez utiliser le package sqlrutils pour regrouper votre script R dans un format qui est plus simple qu’une procédure stockée. Pour plus d'informations, consultez :
* [Générer une procédure stockée pour le code R à l’aide du package sqlrutils](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
* [Créer une procédure stockée à l’aide de sqlrutils](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## <a name="see-also"></a>Voir aussi

[Résoudre les problèmes d’apprentissage dans SQL Server](machine-learning-troubleshooting-faq.md)
