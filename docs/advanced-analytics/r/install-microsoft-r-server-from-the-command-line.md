---
title: "Installer Machine Learning Server (autonome) ou Microsoft R Server (autonome) à partir de la ligne de commande | Documents Microsoft"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb4446ba-e9ce-4b93-9854-5e8a58507da0
caps.latest.revision: "4"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 19ecd44707cd6a94b9a521184b0c588806a63869
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="install-machine-learning-server-standalone-or-microsoft-r-server-standalone-from-the-command-line"></a>Installer Machine Learning Server (autonome) ou Microsoft R Server (autonome) à partir de la ligne de commande

Cet article décrit comment utiliser des arguments de ligne de commande de SQL Server pour installer les fonctionnalités suivantes de SQL Server à l’aide de la ligne de commande :

+ [Apprentissage automatique Server (autonome) dans SQL Server 2017](#bkmk_mls2017) 
+ [Microsoft R Server (autonome), dans SQL Server 2016](#bkmk_mrs2016)

Un **sans assistance** installation nécessite que vous spécifiez l’emplacement de l’utilitaire de configuration et utilisez des arguments pour indiquer les fonctionnalités à installer.

Pour une installation **silencieuse** , fournissez les mêmes arguments et ajoutez le commutateur **/q** . Aucune invite n’est fournis et aucune intervention est nécessaire. Toutefois, le programme d’installation échoue si tous les arguments requis sont omis.

## <a name="prerequisites"></a>Prerequisites

Vous devez savoir comment effectuer une installation de ligne de commande de SQL Server et de vous familiariser avec ses arguments de scripts.

Pour plus d’informations, consultez [installer SQL Server à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).

Si vous installez le serveur de Machine Learning ou Microsoft R Server (autonome) sur un ordinateur qui n’a pas accès à Internet, vous devez télécharger les composants requis de R (ou Python) à l’avance et les copier dans un dossier local. Pour les emplacements de téléchargement, consultez [l’installation des composants d’apprentissage machine sans accès à internet](installing-ml-components-without-internet-access.md).


## <a name="bkmk_mls2017"></a>Installer Microsoft d’apprentissage automatique Server (autonome)

**S’applique à : SQL Server 2017**

Exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges pour installer uniquement Machine Learning Server (autonome) et ses composants requis.

+ L’argument de fonctionnalités est requis, tout comme le contrat de licence de SQL Server.
+ Vous pouvez installer une langue, ou R et Python, mais une licence distincte est nécessaire pour chacun.

Cet exemple montre les arguments utilisés pour installer R.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR, SQL_INST_MR  /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

Cet exemple montre les arguments utilisés pour installer Python.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR, SQL_INST_MPY  /IACCEPTPYTHONOPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

+ Pour afficher la progression et les invites, supprimez l’argument _/q_.
+ Si vous utilisez l’argument **fonctionnalités = SQL_SHARED_MR**, seuls les composants de Machine Learning Server sont installés, et Python ni de R. Cette installation comprend toutes les conditions préalables qui sont installés en mode silencieux par défaut. Toutefois, nous vous recommandons de vous ajoutez au moins une langue lors de l’installation pour la première fois.
+ Ajouter **SQL_INST_MR** pour installer la prise en charge de R.
+ Ajouter **SQL_INST_MPY** pour installer la prise en charge de Python.
+ **IACCEPTROPENLICENSETERMS** indique vous avez accepté les termes du contrat de licence pour l’utilisation des composants open source de R.
+ **IACCEPTPYTHONLICENSETERMS** indique vous avez accepté les termes du contrat de licence pour utiliser les composants de Python.
+ **IACCEPTSQLSERVERLICENSETERMS** est obligatoire pour exécuter l’Assistant Installation.


## <a name="bkmk_mrs2016"></a> Installer Microsoft R Server (autonome)

**S’applique à : SQL Server 2016**

Exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges pour installer **uniquement** Microsoft R Server (autonome) et ses composants requis. 

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

> [!TIP]
> Nous vous recommandons de ne pas installer ce sur le même ordinateur qui héberge une instance de SQL Server R Services.

## <a name="post-installation-tasks"></a>Tâches de post-installation

Pour configurer une autre instance de Microsoft R Server avec les mêmes paramètres, vous pouvez réutiliser le fichier de configuration qui est créé lors de l’installation. Pour plus d’informations, consultez [installer SQL Server à l’aide d’un fichier de configuration](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md).

### <a name="review-installed-components"></a>Composants installée de révision

Une fois l’installation terminée, vous pouvez consulter le fichier de configuration créé par le programme d’installation de SQL Server, ainsi qu’un résumé des actions d’installation.

Par défaut, tous le programme d’installation des journaux et des résumés pour SQL Server et les fonctionnalités associées sont créées dans les dossiers suivants :

+ SQL Server 2017 :`C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\Log`
+ SQL Server 2016 :`C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log`

Un sous-dossier distinct est créé pour chaque fonctionnalité que vous avez installé.

### <a name="customize-the-r-or-python-environment"></a>Personnaliser l’environnement R ou Python

Après l’installation, vous pouvez installer des packages R ou Python supplémentaires. Le processus diffère légèrement selon que vous utilisez SQL Server 2016 ou SQL Server 2017.

Dans SQl Server 2017, vous pouvez installer et gérer des packages R à l’aide de T-SQL. Pour plus d’informations, consultez [installation et gestion des packages R](../r/install-additional-r-packages-on-sql-server.md).

Pour Python et dans SQL Server 2016, un administrateur doit installer toutes les bibliothèques supplémentaires qui peuvent être requises.

> [!IMPORTANT]
> Si vous envisagez d’exécuter votre code R sur SQL Server, assurez-vous que vous installez les packages sur l’ordinateur que vous utiliserez pour le développement de la solution et l’instance de SQL Server sur lequel vous allez exécuter ou déployer la solution.

### <a name="upgrading-r-server-or-sql-server-machine-learning"></a>La mise à niveau d’apprentissage automatique R Server ou SQL Server

Si vous n’avez pas l’intention d’utiliser SQL Server, vous pouvez installer Microsoft R Server ou serveur d’apprentissage Machine à l’aide d’un programme d’installation Windows distinct. Pour les emplacements de téléchargement et des instructions, consultez ces liens :

+ [Installer le serveur d’apprentissage pour Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Installer R Server 9.0.1 pour Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) 

Le programme d’installation de windows distinctes pour le serveur d’apprentissage Machine peut également servir à mettre à niveau les composants associés à l’instance d’apprentissage automatique.  Pour plus d'informations, consultez ces liens :

+ [Permet de mettre à niveau R SqlBindR](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)
