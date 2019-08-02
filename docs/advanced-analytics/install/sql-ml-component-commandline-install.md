---
title: Installation de l’invite de commandes des composants R et Python
description: Exécutez SQL Server installation en ligne de commande pour ajouter le langage R et l’intégration Python à une instance du moteur de base de données SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3e1e74c9d14c93cf44a7da5db4795a1524d238be
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715270"
---
# <a name="install-sql-server-machine-learning-r-and-python-components-from-the-command-line"></a>Installer des composants SQL Server Machine Learning R et Python à partir de la ligne de commande
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fournit des instructions pour l’installation de SQL Server composants Machine Learning à partir d’une ligne de commande:

+ [Nouvelle instance de base de données](#indb)
+ [Ajouter à une instance de moteur de base de données existante](#add-existing)
+ [Installation sans assistance](#silent)
+ [Nouveau serveur autonome](#shared-feature)

Vous pouvez spécifier une interaction en mode silencieux, de base ou complète avec l’interface utilisateur du programme d’installation. Cet article complète l' [installation SQL Server à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md), en couvrant les paramètres propres aux composants R et Python machine learning.

## <a name="pre-install-checklist"></a>Liste de vérification préalable à l’installation

+ Exécutez les commandes à partir d’une invite de commandes avec élévation de privilèges. 

+ Une instance du moteur de base de données est requise pour les installations dans la base de données. Vous ne pouvez pas installer uniquement les fonctionnalités R ou python, même si vous pouvez [les ajouter de façon incrémentielle à une instance existante](#add-existing). Si vous souhaitez uniquement R et Python sans le moteur de base de données, installez le [serveur autonome](#shared-feature).

+ Ne pas installer sur un cluster de basculement. Le mécanisme de sécurité utilisé pour isoler les processus R et Python n’est pas compatible avec un environnement de cluster de basculement Windows Server.

+ N’installez pas sur un contrôleur de domaine. La partie Machine Learning Services du programme d’installation échoue.

+ Évitez d’installer des instances autonomes et dans la base de données sur le même ordinateur. Un serveur autonome est en concurrence pour les mêmes ressources, ce qui permet de sous-utiliser les performances des deux installations.


## <a name="command-line-arguments"></a>Arguments de ligne de commande

L’argument FEATURes est obligatoire, comme les contrats de contrat de licence. 

En cas d’installation à partir de l’invite de commandes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge le mode silencieux complet à l’aide du paramètre /Q ou le mode silencieux simple à l’aide du paramètre /QS. Le commutateur /QS affiche seulement la progression ; il n'accepte pas d'entrée et n'affiche aucun message d'erreur. Le paramètre /QS est pris en charge uniquement lorsque /Action=install est spécifié.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
| Arguments | Description |
|-----------|-------------|
| /FEATURES = AdvancedAnalytics | Installe la version dans la base de données: SQL Server R Services (dans la base de données).  |
| /FEATURES = SQL_SHARED_MR | Installe la fonctionnalité R pour la version autonome: SQL Server R Server (autonome). Un serveur autonome est une «fonctionnalité partagée» non liée à une instance du moteur de base de données.|
| /IACCEPTROPENLICENSETERMS  | Indique que vous avez accepté les termes du contrat de licence pour l’utilisation des composants R Open source. |
| /IACCEPTPYTHONLICENSETERMS | Indique que vous avez accepté les termes du contrat de licence pour l’utilisation des composants Python. |
| /IACCEPTSQLSERVERLICENSETERMS | Indique que vous avez accepté les termes du contrat de licence pour l’utilisation de SQL Server.|
| /MRCACHEDIRECTORY | Pour l’installation hors connexion, définit le dossier contenant les fichiers CAB du composant R. |
::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
| Arguments | Description |
|-----------|-------------|
| /FEATURES = AdvancedAnalytics | Installe la version dans la base de données: SQL Server Machine Learning Services (dans la base de données).  |
| /FEATURES = SQL_INST_MR | Couplez-le avec AdvancedAnalytics. Installe la fonctionnalité R (en base de données), y compris Microsoft R Open et les packages R propriétaires. |
| /FEATURES = SQL_INST_MPY | Couplez-le avec AdvancedAnalytics. Installe la fonctionnalité Python (en base de données), y compris Anaconda et les packages python propriétaires. |
| /FEATURES = SQL_SHARED_MR | Installe la fonctionnalité R pour la version autonome: SQL Server Machine Learning Server (autonome). Un serveur autonome est une «fonctionnalité partagée» non liée à une instance du moteur de base de données.|
| /FEATURES = SQL_SHARED_MPY | Installe la fonctionnalité Python pour la version autonome: SQL Server Machine Learning Server (autonome). Un serveur autonome est une «fonctionnalité partagée» non liée à une instance du moteur de base de données.|
| /IACCEPTROPENLICENSETERMS  | Indique que vous avez accepté les termes du contrat de licence pour l’utilisation des composants R Open source. |
| /IACCEPTPYTHONLICENSETERMS | Indique que vous avez accepté les termes du contrat de licence pour l’utilisation des composants Python. |
| /IACCEPTSQLSERVERLICENSETERMS | Indique que vous avez accepté les termes du contrat de licence pour l’utilisation de SQL Server.|
| /MRCACHEDIRECTORY | Pour l’installation hors connexion, définit le dossier contenant les fichiers CAB du composant R. |
| /MPYCACHEDIRECTORY | Réservé pour un usage ultérieur. Utilisez% TEMP% pour stocker les fichiers CAB du composant Python pour l’installation sur les ordinateurs qui n’ont pas de connexion Internet. |
::: moniker-end

## <a name="indb"></a>Installations de l’instance dans la base de données

Les analyses dans la base de données sont disponibles pour les instances du moteur de base de données, nécessaires à l’ajout de la fonctionnalité **AdvancedAnalytics** à votre installation. Vous pouvez installer une instance du moteur de base de données avec Advanced Analytics ou [l’ajouter à une instance existante](#add-existing). 

Pour afficher les informations de progression sans les invites d’écran interactives, utilisez l’argument/QS.

> [!IMPORTANT]
> Après l’installation, deux étapes de configuration supplémentaires sont conservées. L’intégration n’est pas terminée tant que ces tâches ne sont pas effectuées. Pour obtenir des instructions, consultez [tâches de après l’installation](#post-install) .

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
### <a name="sql-server-machine-learning-services-database-engine-advanced-analytics-with-python-and-r"></a>SQL Server Machine Learning Services: moteur de base de données, analytique avancée avec Python et R

Pour une installation simultanée de l’instance du moteur de base de données, indiquez le nom de l’instance et une connexion d’administrateur (Windows). Inclut des fonctionnalités pour l’installation des composants de base et de langage, ainsi que l’acceptation de tous les termes du contrat de licence.

```cmd
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

Il s’agit de la même commande, mais avec une connexion SQL Server sur un moteur de base de données utilisant l’authentification mixte.

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<sql-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

Cet exemple est python uniquement, indiquant que vous pouvez ajouter une langue en omettant une fonctionnalité.

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTPYTHONLICENSETERMS
```
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
### <a name="sql-server-r-services-database-engine-and-advanced-analytics-with-r"></a>SQL Server R Services: moteur de base de données et analytique avancée avec R

Pour une installation simultanée de l’instance du moteur de base de données, indiquez le nom de l’instance et une connexion d’administrateur (Windows). Inclut des fonctionnalités pour l’installation des composants de base et de langage, ainsi que l’acceptation de tous les termes du contrat de licence.

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS 
```
::: moniker-end

## <a name="post-install"></a>Configuration après l’installation (obligatoire)

S’applique uniquement aux installations dans la base de données.

Une fois l’installation terminée, vous disposez d’une instance de moteur de base de données avec R et Python, les packages Microsoft R et Python, Microsoft R Open, Anaconda, les outils, les exemples et les scripts qui font partie de la distribution. 

Deux tâches supplémentaires sont nécessaires pour terminer l’installation:


::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
1. Redémarrez le service moteur de base de données.

1. Machine Learning Services SQL Server: Activez les scripts externes avant de pouvoir utiliser la fonctionnalité. Suivez les instructions de la procédure d' [installation de SQL Server machine learning services (dans la base de données)](sql-machine-learning-services-windows-install.md) à l’étape suivante. 
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
1. Redémarrez le service moteur de base de données.

1. SQL Server R Services: Activez les scripts externes avant de pouvoir utiliser la fonctionnalité. Suivez les instructions de la [SQL Server R services d’installation (dans la base de données)](sql-r-services-windows-install.md) à l’étape suivante. 
::: moniker-end

## <a name="add-existing"></a>Ajouter des analytiques avancées à une instance de moteur de base de données existante

Lorsque vous ajoutez des analytiques avancées dans la base de données à une instance de moteur de base de données existante, indiquez le nom de l’instance. Par exemple, si vous avez déjà installé un moteur de base de données SQL Server 2017 et Python, vous pouvez utiliser cette commande pour ajouter R.

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQL_INST_MR /INSTANCENAME=MSSQLSERVER 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTROPENLICENSETERMS
```

## <a name="silent"></a>Installation sans assistance

Une installation sans assistance supprime la vérification des emplacements de fichiers. cab. Pour cette raison, vous devez spécifier l’emplacement où les fichiers. cab doivent être décompressés. Pour Python, les fichiers CAB doivent se trouver dans% TEMP *. Pour R, vous pouvez définir le chemin d’accès au dossier à l’aide du répertoire Temp pour ce.
 
```cmd  
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS 
/MRCACHEDIRECTORY=%temp% 
```

## <a name="shared-feature"></a>Installations de serveurs autonomes

Un serveur autonome est une «fonctionnalité partagée» non liée à une instance du moteur de base de données. Les exemples suivants montrent une syntaxe valide pour l’installation du serveur autonome.

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
SQL Server Machine Learning Server prend en charge Python et R sur un serveur autonome:

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR,SQL_SHARED_MPY  
/IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
SQL Server R Server est R uniquement:

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR 
/IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```
::: moniker-end

Une fois l’installation terminée, vous disposez d’un serveur, de packages Microsoft, de distributions Open source de R et Python, d’outils, d’exemples et de scripts qui font partie de la distribution. 

Pour ouvrir une fenêtre de console R, accédez `\Program files\Microsoft SQL Server\150 (or 140/130)\R_SERVER\bin\x64` à et double-cliquez sur **RGui. exe**. Vous débutez avec R ? Essayez ce didacticiel: [Commandes R de base et fonctions RevoScaleR: 25 exemples](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler)courants.

Pour ouvrir une commande Python, accédez à `\Program files\Microsoft SQL Server\150 (or 140)\PYTHON_SERVER\bin\x64` et double-cliquez sur **Python. exe**.

## <a name="get-help"></a>Obtenir de l’aide

Vous avez besoin d’aide pour l’installation ou la mise à niveau? Pour obtenir des réponses aux questions les plus fréquentes et les problèmes connus, consultez l’article suivant:

* [FAQ sur la mise à niveau et l’installation-Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Pour vérifier l’état d’installation de l’instance et résoudre les problèmes courants, essayez ces rapports personnalisés.

* [Rapports personnalisés pour SQL Server](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Étapes suivantes

Les développeurs r peuvent commencer par des exemples simples et découvrir les principes de base du fonctionnement de R avec SQL Server. Pour l’étape suivante, consultez les liens suivants:

+ [Tutoriel : Exécuter R dans T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Tutoriel : Analyse en base de données pour les développeurs R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Les développeurs python peuvent apprendre à utiliser Python avec SQL Server en suivant les didacticiels suivants:

+ [Tutoriel : Exécuter python dans T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Tutoriel : Analytique en base de données pour les développeurs python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Pour consulter des exemples de Machine Learning basés sur des scénarios réels, consultez didacticiels [machine learning](../tutorials/machine-learning-services-tutorials.md).