---
title: Créer un référentiel de packages R local à l’aide de miniCRAN (SQL Server Machine Learning) | Documents Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4ce6479c0e7087e63271811abb47a2174747638e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-local-r-package-repository-using-minicran"></a>Créer un référentiel de packages R local à l’aide de miniCRAN
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Le [miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) package a été créé par Andre de Vries pour prendre en charge ces scénarios courants : 

+ Analyse des dépendances de package pour un package unique ou un ensemble de packages
+ Préparation d’un ensemble de packages R pour l’installation sur un serveur sans accès à internet.

L’utilisateur spécifie un ensemble de packages souhaitées et miniCRAN récursive lit l’arborescence des dépendances pour ces packages et télécharge uniquement les packages répertoriés et leurs dépendances CRAN des référentiels similaire.

Comme sortie, miniCRAN crée un référentiel de cohérent interne comprenant les packages sélectionnés et toutes les dépendances requises. Vous pouvez ensuite déplacer ce référentiel local vers le serveur et continuer à installer les packages sans l’aide d’internet.

Les utilisateurs expérimentés de R ressemblent souvent pour obtenir la liste des packages dépendants dans le fichier DESCRIPTION pour le package téléchargé. Toutefois, les packages répertoriés dans **importations** peut avoir des dépendances de deuxième niveau. Pour cette raison, nous recommandons l’utilisation de la **miniCRAN** (méthode).

## <a name="what-is-a-package-repository"></a>Qu’est un référentiel de packages

La création d’un référentiel de package local vise à fournir un emplacement unique par un administrateur de serveur ou d’autres utilisateurs de l’organisation peuvent utiliser pour installer de nouveaux packages R sur un serveur qui n’a pas accès à internet. Après avoir créé le référentiel, vous pouvez le modifier en ajoutant de nouveaux packages ou de la mise à niveau la version des packages existants.

Le [miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) le package pour R a été écrit par [Andre de Vries](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html) pour le rendre plus facile de créer une cohérence gérés ensemble de packages R pour une organisation. 

Référentiels de package sont utiles dans ces scénarios :

- **Sécurité**: les utilisateurs de R sont habitués à télécharger et installer de nouveaux packages R à volonté, de CRAN ou l’un de ses sites de mise en miroir. Toutefois, pour des raisons de sécurité, les serveurs de production en cours d’exécution [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] n’ont généralement pas de connectivité internet.

- **Simplifie l’installation hors connexion**: pour installer le package à un serveur en mode hors connexion nécessite que vous téléchargez également toutes les dépendances du package, à l’aide miniCRAN plus facilement obtenir toutes les dépendances dans le format correct.

    À l’aide de miniCRAN, vous pouvez éviter les erreurs de dépendance de package lors de la préparation des packages à installer avec le [créer une bibliothèque externe](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) instruction.

- **Amélioration de la gestion de version**: dans un environnement multi-utilisateur, il existe de bonnes raisons d’éviter sans restriction de l’installation de plusieurs versions de package sur le serveur. Utiliser un référentiel local pour fournir un ensemble cohérent de packages pour une utilisation par vos analystes. 

> [!TIP]
> Vous pouvez également utiliser miniCRAN pour préparer les packages à utiliser dans Azure Machine Learning. Pour plus d’informations, consultez ce billet de blog : [à l’aide de miniCRAN dans Azure ML, par Michele Usuelli](https://www.r-bloggers.com/using-minicran-in-azure-ml/) 

## <a name="prepare-packages-using-minicran"></a>Préparer les packages à l’aide de miniCRAN

Le **miniCRAN** package lui-même dépend des autres packages CRAN 18, entre ce qui est la **RCurl** package, ce qui a une dépendance de système sur le **curl-développement** package. De même, le package **XML** a une dépendance sur **libxml2-développement**. 

Pour ces raisons, nous vous recommandons de générer votre référentiel local initialement sur un ordinateur avec accès total à Internet, afin que vous pouvez satisfaire facilement toutes ces dépendances. 

Une fois le référentiel a été créé, vous pouvez déplacer le référentiel vers un autre emplacement.

### <a name="step-1-install-the-minicran-package"></a>Étape 1. Installez le package miniCRAN

Vous commencez par créer un **miniCRAN** référentiel à utiliser en tant que source. Vous devez créer ce référentiel sur un ordinateur qui a accès à internet.

1. Installer le **miniCRAN** requis et package **igraph** package. Cet exemple vérifie si le package est déjà installé, mais vous pouvez contourner l’if instructions et installer les packages directement.

    ```R
    if(!require("miniCRAN")) install.packages("miniCRAN") 
    if(!require("igraph")) install.packages("igraph") 
    library("miniCRAN")
    ```

### <a name="step-2-define-a-package-source-a-cran-mirror-or-an-mran-snapshot"></a>Étape 2. Définir une source de package : un miroir CRAN, ou un instantané MRAN

1. Spécifiez un site miroir à utiliser lors de l’obtention de packages. Par exemple, vous pouvez utiliser le site MRAN ou un autre site dans votre région qui contient les packages que vous avez besoin. Si le téléchargement échoue, essayez un autre site de mise en miroir.

    ```R
    CRAN_mirror <- c(CRAN = "https://mran.microsoft.com")
    CRAN_mirror <- c(CRAN = "https://cran.cnr.berkeley.edu")
    ```

2. Tapez le nom d’un dossier local dans lequel stocker les packages collectées. 

    Veillez à créer le dossier à l’avance. Une erreur est générée si le `local_repo` dossier n’existe pas lorsque vous exécutez le code R ultérieurement.

    Le dossier doit avoir un nom descriptif. Ici, nous avons utilisé « miniCRAN », mais si vous répétez cette opération souvent, vous devez probablement utiliser un nom plus descriptif, tel que « miniCRANZooPackages » ou « miniCRANMyRPackagev2 ».

    ```R
    local_repo <- "~/miniCRAN"
    ```

    L’opérateur d’expansion tilde retourne une variable d’environnement, avec des résultats équivalents à `Sys.getenv("R_USER")`.

### <a name="step-3-add-packages-to-the-repository"></a>Étape 3. Ajouter des packages dans le référentiel

1. Après avoir **miniCRAN** est installé, créer une liste qui spécifie les packages supplémentaires que vous souhaitez télécharger.

    Faire **pas** ajouter des dépendances à cette liste initiale. Le **igraph** package utilisé par **miniCRAN** génère la liste des dépendances pour vous. Pour plus d’informations sur l’utilisation du graphique de dépendance généré, consultez [pour identifier les dépendances du package à l’aide de miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html).

    Le script R suivant ajoute les packages de cible, « zoo » et « prévision » à une variable.

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```
2. Il n’est pas nécessaire que vous tracez le graphique de dépendance, mais il peut être informatif.
    
    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. Créer le référentiel local. Veillez à modifier la version de R si nécessaire

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3");
    ```

    À partir de ces informations, le package miniCRAN crée la structure de dossiers, vous devez copier les packages à la [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] plus tard.

4. À ce stade, vous devez avoir un dossier contenant les packages que vous avez besoin, et tous les packages supplémentaires qui étaient requis.

    Vous pouvez exécuter le code suivant pour répertorier les packages contenus dans le référentiel miniCRAN.

    ```R
    pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE);
    head(pdb);
    pdb$Package;
    pdb[, c("Package", "Version", "License")]
    ```

### <a name="step-4-use-the-repository-to-add-r-packages-to-the-instance-library"></a>Étape 4. L’espace de stockage permet d’ajouter des packages R à la bibliothèque de l’instance

Après avoir créé le référentiel et ajouté les packages que vous avez besoin, vous devez déplacer le référentiel de packages à l’ordinateur du serveur et assurez-vous que les packages R sont installés dans la bibliothèque appropriée à utiliser à partir de SQL Server.

La procédure suivante décrit comment installer les packages à l’aide des outils R.

1. Copiez le dossier contenant le référentiel miniCRAN, dans son intégralité, sur le serveur où vous prévoyez d’installer les packages. Le dossier a en général, cette structure : miniCRAN racine > -> emplacement -> windows -> cotisation -> version non -> tous les packages.

2. Ouvrez une invite de commandes R à l’aide de l’outil de R associé à l’instance.

    - Pour SQL Server 2017, le dossier par défaut est `C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library`.

    - Pour SQL Server 2016, le dossier par défaut est `C:/Program Files/Microsoft SQL Server/MSSQL13.MSSQLSERVER/R_SERVICES/library`.

    - Pour une instance nommée, le chemin d’accès par défaut serait quelque chose comme : `<instance_path>.RTEST/R_SERVICES/library`.

    -  Si vous avez installé SQL Server sur un lecteur différent, ou modifié d’autres éléments du chemin d’installation, veillez également à répercuter ces modifications.

3. Obtenir le chemin d’accès de la bibliothèque de l’instance et l’ajouter à la liste des chemins d’accès de la bibliothèque.

    ```R
    .libPaths()[1];
    lib <- .libPaths()[1]
    ```

    Sur le serveur SQL Server, cette commande doit retourner le chemin d’accès de la bibliothèque associée à l’instance, tels que : « C:/Program Files/Microsoft SQL Server/MSSQL14. MSSQLSERVER/R_SERVICES/bibliothèque »

4. Spécifiez le nouvel emplacement sur le serveur où vous avez copié le **miniCRAN** référentiel, comme `server_repo`.

    Dans cet exemple, nous supposons que vous avez copié le référentiel dans un dossier temporaire sur le serveur.

    ```R
    source_repo <- "C:\\temp\\miniCRAN"
    ```

5. Étant donné que vous travaillez dans un nouvel espace de travail R sur le serveur, vous devez également entrer la liste des packages à installer.

    ```R
    tspackages <- c("zoo", "forecast")
    ```

6. Installer les packages, en fournissant le chemin d’accès à la copie locale du référentiel miniCRAN.

    ```R
    install.packages(tspackages, repos = file.path("file://", normalizePath;(source_repo, winslash = "/")), lib = lib, type = "win.binary", dependencies = TRUE);
    ```

7. À partir de la bibliothèque de l’instance, vous pouvez afficher les packages installés à l’aide d’une commande comme suit :

    ```R
    installed.packages()
    ```

> [!NOTE] 
> Pour utiliser le package dans SQL Server, les packages doivent être installés dans la bibliothèque par défaut utilisée par l’instance. 

## <a name="manually-install-a-single-package-from-a-zipped-file"></a>Installer manuellement un package unique à partir d’un fichier compressé

Si vous installez un package unique qui n’a aucune dépendance, ou vous ne pouvez pas utiliser **miniCRAN**, vous pouvez également télécharger manuellement le package que vous avez besoin. Cela nécessite que vous êtes un administrateur ou un seul propriétaire d’un serveur.

Après avoir téléchargé les packages, vous installez les packages R à partir de l’emplacement du fichier compressé.

1. Télécharger le package comme un fichier compressé et l’enregistrer dans un dossier local

2. Copiez ce dossier à la [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] ordinateur.

3. Installez les packages dans la bibliothèque d’instance de SQL Server à l’aide des commandes R classiques. Si le package possède des dépendances qui ne sont pas déjà installés et que vous les n'avez pas incluses, l’installation peut échouer. 

Vous pouvez également télécharger des packages individuels dans une instance de SQL Server 2017, à l’aide de la [instruction de créer une bibliothèque externe](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql). Ce processus requérait également un accès administratif.
