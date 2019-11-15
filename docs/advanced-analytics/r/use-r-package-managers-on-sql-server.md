---
title: Utiliser des gestionnaires de package R
description: Utilisez les commandes R standard, telles que install.packages, pour ajouter de nouveaux packages R à SQL Server 2016 R Services ou à SQL Server Machine Learning Services (dans la base de données).
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1f6d828a7267ab2b4b1def17f9d1c6bf4a6018dc
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69633619"
---
# <a name="use-r-package-managers-to-install-r-packages-on-sql-server"></a>Utiliser les gestionnaires de packages R pour installer des packages R sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Vous pouvez utiliser les outils R standard pour installer de nouveaux packages sur une instance SQL Server 2016 ou SQL Server 2017, à condition que l’ordinateur dispose d’un port 80 ouvert et que vous ayez les droits d’administrateur.

> [!IMPORTANT] 
> Assurez-vous d’installer les packages dans la bibliothèque par défaut qui est associée à l’instance actuelle. N’installez jamais de packages dans un répertoire utilisateur.

Cette procédure utilise RGui, mais vous pouvez utiliser RTerm ou tout autre outil de ligne de commande R qui prend en charge l’accès de niveau élevé.

## <a name="install-a-package-using-rgui"></a>Installer un package à l’aide de RGui

1. [Déterminez l’emplacement de la bibliothèque d’instances](../package-management/r-package-information.md). Recherchez le dossier dans lequel les outils R sont installés. Par exemple, le chemin d’accès par défaut d’une instance par défaut SQL Server 2017 est le suivant : `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`

1. Cliquez avec le bouton droit sur RGui.exe, puis sélectionnez **Exécuter en tant qu’administrateur**. Si vous ne disposez pas des autorisations requises, contactez l’administrateur de la base de données et indiquez la liste des packages dont vous avez besoin.

1. À partir de la ligne de commande, si vous connaissez le nom du package, vous pouvez taper : `install.packages("the_package-name")` Des guillemets doubles entourant le nom du package sont requis.

1. Lorsque vous êtes invité à fournir un site miroir, sélectionnez n’importe quel site approprié pour l’emplacement où vous êtes.

Si le package cible dépend de packages supplémentaires, le programme d’installation de R télécharge automatiquement les dépendances et les installe pour vous.

Si vous avez plusieurs instances SQL Server, telles que des instances côte à côte de SQL Server 2016 R Services et SQL Server Machine Learning Services, exécutez l’installation séparément pour chaque instance si vous souhaitez utiliser le package dans les deux contextes. Il n’est pas possible de partager des packages entre les instances.

## <a name = "bkmk_offlineInstall"></a> Installation hors connexion à l’aide des outils R

Si le serveur n’a pas accès à Internet, des étapes supplémentaires sont nécessaires pour préparer les packages. Pour installer des packages R sur un serveur qui n’a pas accès à Internet, vous devez effectuer les opérations suivantes :

+ Analysez les dépendances à l’avance.
+ Téléchargez le package cible sur un ordinateur disposant d’un accès à Internet.
+ Téléchargez tous les packages requis sur le même ordinateur et placez tous les packages dans une archive de package unique.
+ Compressez l’archive si elle n’est pas déjà au format zip.
+ Copiez l’archive de package vers un emplacement sur le serveur.
+ Installez le package cible en spécifiant le fichier d’archive comme source.

> [!IMPORTANT] 
>  Veillez à analyser toutes les dépendances et à télécharger **tous** les packages requis **avant** de commencer l’installation. Nous vous recommandons [miniCRAN](https://mran.microsoft.com/package/miniCRAN) pour ce processus. Ce package R s’appuie sur une liste des packages que vous souhaitez installer, analyse les dépendances et récupère tous les fichiers zip pour vous. miniCRAN crée ensuite un référentiel unique que vous pouvez copier sur l’ordinateur serveur. Pour plus d’informations, consultez [Créer un référentiel de packages local à l’aide de miniCRAN](create-a-local-package-repository-using-minicran.md)

Cette procédure suppose que vous avez préparé tous les packages dont vous avez besoin, au format zip, et que vous êtes prêt à les copier sur le serveur.

1. Copiez le fichier zip du package, ou, pour plusieurs packages, le référentiel complet contenant tous les packages au format zip, à un emplacement accessible par le serveur.

2. Ouvrez le dossier sur le serveur où sont installés les outils R pour l’instance. Par exemple, si vous utilisez l’invite de commandes Windows sur un système avec SQL Server R 2016 R Services, utilisez `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`.

3. Cliquez avec le bouton droit sur RGui ou RTerm, puis sélectionnez **Exécuter en tant qu’administrateur**.

4. Exécutez la commande R `install.packages` et spécifiez le nom du package ou du référentiel, ainsi que l’emplacement des fichiers zip.

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    Cette commande extrait le package R `mynewpackage` à partir de son fichier zip local, en supposant que vous ayez enregistré la copie dans le répertoire `C:\Temp\Downloaded packages`, puis installe le package sur l’ordinateur local. Si le package a des dépendances, le programme d’installation recherche les packages existants dans la bibliothèque. Si vous avez créé un référentiel qui inclut les dépendances, le programme d’installation installe également les packages requis.

    Si certains packages requis ne sont pas présents dans la bibliothèque d’instances et sont introuvables dans les fichiers zip, l’installation du package cible échoue.

## <a name="see-also"></a>Voir aussi

+ [Installer de nouveaux packages R](install-additional-r-packages-on-sql-server.md)
+ [Installer de nouveaux packages Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Didacticiels, exemples, solutions](../tutorials/machine-learning-services-tutorials.md)
