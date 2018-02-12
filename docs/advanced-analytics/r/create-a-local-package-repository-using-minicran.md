---
title: "Créer un référentiel de package local à l’aide de miniCRAN | Documents Microsoft"
ms.custom: 
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f2a1ce-316f-4347-b206-8a1b9eebe90b
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 61446dbf91fc16d0fa46eb2ae524806f1ca56f83
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2018
---
# <a name="create-a-local-package-repository-using-minicran"></a>Créer un référentiel de package local à l’aide de miniCRAN
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Il existe deux façons dont vous pouvez préparer les packages R pour une installation sur un serveur sans accès à internet.

-   [Le package miniCRAN permet de créer un référentiel local unique](#bkmk_miniCRAN)

    Le [miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) crée un référentiel cohérent en interne, composé de packages sélectionnés à partir de dépôts de CRAN de type. L’utilisateur spécifie un ensemble de packages souhaitées, et de façon récursive miniCRAN lit l’arborescence des dépendances pour ces packages et qu’il télécharge uniquement les packages répertoriés et leurs dépendances.

    Vous pouvez ensuite déplacer ce référentiel local vers le serveur et continuer à installer les packages sans l’aide d’internet.

-   [Télécharger et copier les packages un par un manuellement](#bkmk_manual)

    Vous trouverez la liste des packages dépendants dans le fichier DESCRIPTION pour le package téléchargé. 
    
    Toutefois, les packages répertoriés dans **importations** peut avoir des dépendances de deuxième niveau. Pour cette raison, nous recommandons l’utilisation de la **miniCRAN** (méthode).

> [!TIP]
> Saviez-vous que vous pouvez utiliser miniCRAN pour préparer les packages à utiliser dans Azure Machine Learning ? Pour plus d’informations, consultez ce billet de blog : [à l’aide de miniCRAN dans Azure ML, par Michele Usuelli](https://www.r-bloggers.com/using-minicran-in-azure-ml/) 

## <a name="prepare-packages-using-minicran"></a>Préparer les packages à l’aide de miniCRAN

La création d’un référentiel de package local vise à fournir un emplacement unique par un administrateur de serveur ou d’autres utilisateurs de l’organisation peuvent utiliser pour installer de nouveaux packages R sur un serveur qui n’a pas accès à internet.

Le [miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) le package pour R a été écrit par [Andre de Vries](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html) pour le rendre plus facile de créer une cohérence gérés ensemble de packages R pour une organisation. 

Il existe de nombreux avantages à l’utilisation de miniCRAN pour créer le référentiel :

-   **Sécurité**: les utilisateurs de R sont habitués à télécharger et installer de nouveaux packages R à volonté, de CRAN ou l’un de ses sites de mise en miroir. Toutefois, pour des raisons de sécurité, les serveurs de production en cours d’exécution [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] n’ont généralement pas de connectivité internet.

-   **Simplifie l’installation hors connexion**: pour installer le package à un serveur en mode hors connexion nécessite que vous téléchargez également toutes les dépendances du package, à l’aide miniCRAN plus facilement obtenir toutes les dépendances dans le format correct.

-   **Amélioration de la gestion de version**: dans un environnement multi-utilisateur, il existe de bonnes raisons d’éviter sans restriction de l’installation de plusieurs versions de package sur le serveur.

Après avoir créé le référentiel, vous pouvez le modifier en ajoutant de nouveaux packages ou de la mise à niveau la version des packages existants.

> [!NOTE]
> Le package miniCRAN lui-même est dépendant de 18 autres packages CRAN, parmi lesquelles est le package de RCurl, qui a une dépendance de système sur le package de développement de curl. De même, le XML du package a une dépendance sur le développement de libxml2. Par conséquent, nous recommandons que vous générez votre référentiel local initialement sur un ordinateur avec accès total à Internet, afin que vous pouvez satisfaire facilement toutes ces dépendances. Une fois créé, vous pouvez déplacer le référentiel vers un autre emplacement.

### <a name="step-1-install-the-minicran-package"></a>Étape 1. Installez le package miniCRAN

Vous commencez par créer un référentiel miniCRAN à utiliser en tant que source. Vous devez créer ce référentiel sur un ordinateur qui a accès à internet.

1.  Installer le package miniCRAN et requis **igraph** package.

    ```R
    if(!require("miniCRAN")) install.packages("miniCRAN") if(!require("igraph"))
    install.packages("igraph") library(miniCRAN)
    ```

### <a name="step-2-define-a-package-source-a-cran-mirror-or-an-mran-snapshot"></a>Étape 2. Définir une source de package : un miroir CRAN, ou un instantané MRAN

1. Spécifiez un site miroir à utiliser lors de l’obtention de packages.

    ```R
    CRAN_mirror \<- c(CRAN = "https://mran.microsoft.com/snapshot/2017-08-01")
    ```

2.  Tapez le nom d’un dossier local dans lequel stocker les packages collectées. 

    Veillez à créer le dossier à l’avance. Une erreur est générée si le `local_repo` dossier n’existe pas lorsque vous exécutez le code R ultérieurement.

    Le dossier doit avoir un nom descriptif. Par exemple, évitez d’utiliser « miniCRAN » et à la place le type quelque chose comme « GeneticsPackages » ou « TeamRPackages1.0.2 ».

    ```R
    local_repo <- "~/miniCRAN"
    ```

    L’opérateur d’expansion tilde retourne une variable d’environnement, avec des résultats équivalents à `Sys.getenv("R_USER")`.

### <a name="step-3-add-packages-to-the-repository"></a>Étape 3. Ajouter des packages dans le référentiel

1.  Une fois miniCRAN est installé, créez une liste qui spécifie les packages supplémentaires que vous souhaitez télécharger.

    N’ajoutez pas de dépendances à cette liste initiale ; le **igraph** package utilisé par miniCRAN génère la liste des dépendances pour vous. Pour plus d’informations sur l’utilisation du graphique de dépendance généré, consultez [pour identifier les dépendances du package à l’aide de miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html).

    Le script R suivant montre comment obtenir les packages de la cible, « zoo » et « prévision ».

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```
2. Il n’est pas nécessaire que vous tracez le graphique de dépendance, mais il peut être informatif.
    
    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. Créer le référentiel local. Veillez à modifier la version de R si nécessaire

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror)
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3")
    ```

    À partir de ces informations, le package miniCRAN crée la structure de dossiers, vous devez copier les packages à la [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] plus tard.

4. À ce stade, vous devez avoir un dossier contenant les packages que vous avez besoin, et tous les packages supplémentaires qui étaient requis.

    Vous pouvez exécuter le code suivant pour répertorier les packages contenus dans le référentiel miniCRAN.

    ```R
    pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE)
    head(pdb)
    pdb$Package
    pdb[, c("Package", "Version", "License")]
    ```

### <a name="step-4-use-the-repository-to-add-r-packages-to-the-instance-library"></a>Étape 4. L’espace de stockage permet d’ajouter des packages R à la bibliothèque de l’instance

Après avoir créé le référentiel et ajouté les packages que vous avez besoin, vous devez déplacer le référentiel de packages à l’ordinateur du serveur et assurez-vous que les packages R sont installés dans la bibliothèque appropriée à utiliser à partir de SQL Server.

Selon la version de SQL Server, il existe deux options pour l’ajout de nouveaux packages dans la bibliothèque R associée à l’instance de SQL Server :

- Installer à la bibliothèque de l’instance à l’aide de la miniCRAN référentiel et outils R.

- Télécharger des packages à une base de données SQL Server et l’installer à l’aide de l’instruction de créer une bibliothèque externe. Cette option nécessite SQL Server 2017. Consultez [installer des packages R supplémentaires sur SQL Server](install-additional-r-packages-on-sql-server.md).

La procédure suivante décrit comment installer les packages à l’aide des outils R.

1. Copiez le dossier contenant le référentiel miniCRAN, dans son intégralité, sur le serveur où vous prévoyez d’installer les packages.

2. Ouvrez une invite de commandes R à l’aide de l’outil de R associé à l’instance.

    - Pour SQL Server 2017, le dossier par défaut est `C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library`.

    - Pour SQL Server 2016, le dossier par défaut est `C:/Program Files/Microsoft SQL Server/MSSQL13.MSSQLSERVER/R_SERVICES/library`.

    - Pour une instance nommée, le chemin d’accès par défaut serait quelque chose comme : `<instance_path>.RTEST/R_SERVICES/library`.

    -  Si vous avez installé SQL Server sur un lecteur différent, ou modifié d’autres éléments du chemin d’installation, veillez également à répercuter ces modifications.

3.  Obtenir le chemin d’accès de la bibliothèque de l’instance et l’ajouter à la liste des chemins d’accès de la bibliothèque.

    ```R
    .libPaths()[1]  
    lib \<- .libPaths()[1]
    ```

    Sur le serveur SQL Server, cette commande doit retourner le chemin d’accès de la bibliothèque associée à l’instance, tels que : « C:/Program Files/Microsoft SQL Server/MSSQL14. MSSQLSERVER/R_SERVICES/bibliothèque »

4.  Spécifiez l’emplacement sur le serveur où vous avez copié le référentiel mininCRAN dans `server_repo`.

    Dans cet exemple, nous supposons que vous avez copié le référentiel dans votre dossier utilisateur sur le serveur.

    ```R
    R server_repo <- "C:\\Users\\MyUserName\\miniCRAN"
    ```

5.  Étant donné que vous travaillez dans un nouvel espace de travail R sur le serveur, vous devez également entrer la liste des packages à installer.

    ```R
    tspackages <- c("zoo", "forecast")
    ```

6.  Installer les packages, en fournissant le chemin d’accès à la copie locale du référentiel miniCRAN.

    ```R
    install.packages(tspackages, repos = file.path("file://", normalizePath(server_repo, winslash = "/")), lib = lib, type = "win.binary", dependencies = TRUE)
    ```

7.  À partir de la bibliothèque de l’instance, vous pouvez afficher les packages installés à l’aide d’une commande comme suit :

    ```R
    installed.packages()
    ```

> [!NOTE] 
> Dans SQL Server, un administrateur de serveur doit installer des packages à partir du référentiel miniCRAN dans la bibliothèque par défaut utilisée par l’instance. 

## <a name="manually-download-single-packages"></a>Télécharger manuellement les packages uniques

Si vous ne souhaitez pas utiliser miniCRAN, vous pouvez télécharger également manuellement les packages que vous avez besoin et leurs dépendances. Cela nécessite que vous êtes un administrateur ou un seul propriétaire d’un serveur.

Après avoir téléchargé les packages, vous installez les packages R à partir de l’emplacement du fichier compressé.

1. Télécharger les fichiers zip de packages et les enregistrer dans un dossier local

2. Copiez ce dossier à la [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] ordinateur.

3. Installez les packages dans la bibliothèque d’instance de SQL Server.

> [!NOTE]
> Lorsque vous utilisez des outils R pour installer des packages, ils sont installés pour l’instance dans sa globalité. 
> 
> Si vous souhaitez installer le package dans une base de données et de partager le package avec les utilisateurs à l’aide de rôles de base de données, vous devez télécharger la bibliothèque à l’aide de l’instruction de créer une bibliothèque externe. Consultez [installer des packages R supplémentaires dans SQL Server](install-additional-r-packages-on-sql-server.md)
