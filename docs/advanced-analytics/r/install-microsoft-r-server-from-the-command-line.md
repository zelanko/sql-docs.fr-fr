---
title: "Installer Microsoft R Server à partir de la ligne de commande | Microsoft Docs"
ms.custom: 
ms.date: 04/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb4446ba-e9ce-4b93-9854-5e8a58507da0
caps.latest.revision: 4
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 811709fae77dee6daa46a97a51c44c02e372d9a8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="install-microsoft-r-server-from-the-command-line"></a>Installer Microsoft R Server à partir de la ligne de commande
    
Cette rubrique décrit comment utiliser des arguments de ligne de commande de SQL Server d’installer Microsoft R Server dans SQL Server 2016, ou Machine Learning Server (autonome) dans SQL Server 2017. 

> [!NOTE]
Vous pouvez également installer Microsoft R Server à l’aide d’un programme d’installation Windows distinct. Pour plus d’informations, consultez [installer R Server 9.0.1 pour Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows). 

## <a name="prerequisites"></a>Conditions préalables

Cette méthode d’installation nécessite que vous savez comment effectuer une installation de ligne de commande de SQL Server et savez familiarisés avec ses arguments de scripts.

- Pour une installation**sans assistance** , vous devez spécifier l’emplacement de l’utilitaire d’installation et utiliser des arguments pour indiquer les fonctionnalités à installer. 
- Pour une installation **silencieuse** , fournissez les mêmes arguments et ajoutez le commutateur **/q** . Aucune invite n’est affichée et aucune interaction n’est nécessaire. Toutefois, le programme d’installation échoue si des arguments obligatoires sont omis.

Pour plus d’informations, consultez [Installer SQL Server 2016 à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).

## <a name="sql-server-2017-microsoft-machine-learning-server-standalone"></a>SQL Server 2017 : L’ordinateur Microsoft apprentissage Server (autonome)

Exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges pour installer uniquement Microsoft Learning serveur (autonome) et ses composants requis.  L’exemple montre les arguments utilisés pour installer R.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR, SQL_INST_MR  /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS 
```

Pour afficher la progression et les invites, supprimez l’argument _/q_.

- **FONCTIONNALITÉS = SQL_SHARED_MR** obtient uniquement les composants serveur de Machine Learning. Cela inclut les composants requis, qui sont installés en mode silencieux par défaut.
- **SQL_INST_MR** est requis pour prendre en charge de l’installer pour le langage R.
- **SQL_INST_MPY** est requis pour installer la prise en charge de Python.
- **IACCEPTROPENLICENSETERMS** indique vous avez accepté les termes du contrat de licence pour l’utilisation des composants open source de R.
- **IACCEPTPYTHONLICENSETERMS** indique vous avez accepté les termes du contrat de licence pour utiliser les composants de Python.
- **IACCEPTSQLSERVERLICENSETERMS** est obligatoire pour exécuter l’Assistant Installation.

**Remarques**

1. L’argument de fonctionnalités est requis, tout comme le contrat de licence de SQL Server.
2. Spécifiez au moins une langue, ainsi que l’indicateur de contrat de licence.
3. Vous pouvez installer une langue, ou R et Python, mais une licence distincte est nécessaire pour chacun.

## <a name="sql-server-2016-microsoft-r-server-standalone"></a>SQL Server 2016 : Microsoft R Server (autonome)

Exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges pour installer uniquement Microsoft R Server (autonome) et ses composants prérequis.  L’exemple montre les arguments utilisés avec le programme d’installation de SQL Server 2016.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

## <a name="offline-installation"></a>Installation hors connexion

Si vous installez le serveur de Machine Learning ou Microsoft R Server (autonome) sur un ordinateur qui n’a pas accès à Internet, vous devez télécharger les composants R requis à l’avance et les copier dans un dossier local. Pour connaître les emplacements de téléchargement, consultez [Installation des composants R sans accès à Internet](../r/installing-ml-components-without-internet-access.md).

## <a name="what-is-installed"></a>Ce qui est installé

Une fois l’installation terminée, vous pouvez consulter le fichier de configuration créé par le programme d’installation de SQL Server, ainsi qu’un résumé des actions d’installation.

Par défaut, tous le programme d’installation des journaux et des résumés pour SQL Server et les fonctionnalités associées sont créées dans les dossiers suivants :

- SQL Server 2016 :`C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log`
- SQL Server 2017 :`C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\Log`

Un sous-dossier distinct est créé pour chaque fonctionnalité installée.

Pour configurer une autre instance de Microsoft R Server avec les mêmes paramètres, vous pouvez réutiliser le fichier de configuration qui est créé lors de l’installation. Pour plus d’informations, consultez [Installation de SQL Server à l’aide d’un fichier de configuration](https://msdn.microsoft.com/library/dd239405.aspx)


## <a name="customize-your-r-environment"></a>Personnaliser votre environnement R

Après l’installation, vous pouvez installer des packages R supplémentaires. Pour plus d’informations, consultez [Installation et gestion des packages R](../r/install-additional-r-packages-on-sql-server.md).

> [!IMPORTANT]
> Si vous envisagez d’exécuter votre code R sur SQL Server, assurez-vous que vous installez les packages sur l’ordinateur que vous utiliserez pour le développement de la solution et l’instance de SQL Server sur lequel vous allez exécuter ou déployer la solution.

Une fois que vous avez installé l’ordinateur des Services de formation pour R (de-de base de données), vous pouvez utiliser le programme d’installation Windows distinct pour mettre à niveau la version de R est associé à une instance de SQL Server spécifiée. Pour plus d’informations, consultez [SqlBindR utilisé pour mettre à niveau la R](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).



