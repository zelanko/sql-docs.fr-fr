---
title: Créer un référentiel de package R local à l’aide de miniCRAN - SQL Server Machine Learning Services
description: Utiliser miniCran pour détecter, assembler et installer les dépendances de package R dans un package unique consolidé.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7dc2e286e6eb80fe1eef3e8b86ed1002a6344cfb
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53431752"
---
# <a name="create-a-local-r-package-repository-using-minicran"></a>Créer un référentiel de package R local à l’aide de miniCRAN
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) package, créé par [Andre de Vries](https://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html), identifie et télécharge les packages et dépendances dans un seul dossier, vous pouvez copier à d’autres ordinateurs pour l’installation de package R hors connexion.

En tant qu’entrée, spécifiez un ou plusieurs packages. **miniCRAN** lit l’arborescence des dépendances pour ces packages de manière récursive et télécharge uniquement les packages répertoriés et leurs dépendances à partir de CRAN ou de référentiels similaire.

En tant que sortie, **miniCRAN** crée un référentiel cohérent en interne comprenant des packages sélectionnés et toutes les dépendances requises. Vous pouvez ensuite déplacer ce dépôt local vers le serveur et continuer pour installer les packages sans connexion internet.

> [!NOTE]
> Les utilisateurs expérimentés de R tournent souvent pour obtenir la liste des packages dépendants dans le fichier DESCRIPTION pour le package téléchargé. Toutefois, les packages répertoriés dans **importations** pourraient présenter des dépendances de deuxième niveau. Pour cette raison, nous vous recommandons de **miniCRAN** d’assemblage de la collection complète des packages requis.

## <a name="why-create-a-local-repository"></a>Pourquoi créer un référentiel local

L’objectif de la création d’un référentiel de packages local consiste à fournir un emplacement unique administrateur de serveur ou d’autres utilisateurs de l’organisation peuvent utiliser pour installer de nouveaux packages R sur un serveur, en particulier une qui n’a pas accès à internet. Après avoir créé le référentiel, vous pouvez le modifier en ajoutant de nouveaux packages ou de la mise à niveau la version des packages existants.

Référentiels de packages sont utiles dans ces scénarios :

- **Sécurité**: Nombre d’utilisateurs R est habitué à télécharger et installer de nouveaux packages R à volonté, à partir de CRAN ou d’un de ses sites de mise en miroir. Toutefois, pour des raisons de sécurité, les serveurs de production en cours d’exécution [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ne disposent généralement pas de connectivité internet.

- **Simplifier l’installation hors connexion**: Pour installer le package à un serveur en mode hors connexion nécessite que vous téléchargez également toutes les dépendances de package, Using miniCRAN rend plus facile d’obtenir toutes les dépendances dans le format correct.

    À l’aide de miniCRAN, vous pouvez éviter les erreurs de dépendance de package lors de la préparation des packages à installer avec le [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) instruction.

- **Amélioration de la gestion de version**: Dans un environnement multi-utilisateur, il existe de bonnes raisons d’éviter sans restriction de l’installation de plusieurs versions de package sur le serveur. Utiliser un référentiel local pour fournir un ensemble cohérent de packages pour une utilisation par vos analystes. 

> [!TIP]
> Vous pouvez également utiliser miniCRAN pour préparer les packages à utiliser dans Azure Machine Learning. Pour plus d’informations, consultez ce billet de blog : [À l’aide de miniCRAN dans Azure ML, par Michele Usuelli](https://www.r-bloggers.com/using-minicran-in-azure-ml/) 

## <a name="install-minicran"></a>Installer miniCRAN

Le **miniCRAN** package lui-même est dépendant de 18 autres packages CRAN, entre ce qui est le **RCurl** package, ce qui a une dépendance de système sur le **curl-devel** package. De même, le package **XML** a une dépendance sur **libxml2-devel**. Pour résoudre les dépendances, nous vous recommandons de générer votre référentiel local initialement sur un ordinateur avec accès total à internet. 

Exécutez les commandes suivantes sur un ordinateur avec un base R, outils R et la connexion internet. Il est supposé qu’il s’agit *pas* votre ordinateur SQL Server. Les commandes suivantes installent le **miniCRAN** requis et package **igraph** package. Cet exemple vérifie si le package est déjà installé, mais vous pouvez ignorer l’if instructions et installer les packages directement.

```R
if(!require("miniCRAN")) install.packages("miniCRAN") 
if(!require("igraph")) install.packages("igraph") 
library("miniCRAN")
```

## <a name="set-the-cran-mirror-and-mran-snapshot"></a>Définir la mise en miroir CRAN et la capture instantanée MRAN

Spécifiez un site miroir à utiliser lors de l’obtention de packages. Par exemple, vous pouvez utiliser le site MRAN ou un autre site dans votre région qui contient les packages que vous avez besoin. Si le téléchargement échoue, essayez un autre site miroir.

```R
CRAN_mirror <- c(CRAN = "https://mran.microsoft.com")
CRAN_mirror <- c(CRAN = "https://cran.cnr.berkeley.edu")
```

## <a name="create-a-local-folder"></a>Créez un dossier local

Créer un dossier local, tel que `C:\mylocalrepo` dans lequel stocker les packages collectées. Si vous répétez cette procédure souvent, vous devez probablement utiliser un nom plus descriptif, tel que « miniCRANZooPackages » ou « miniCRANMyRPackagev2 ».

Spécifiez le dossier que le dépôt local. Syntaxe de R utilise une barre oblique pour les noms de chemin d’accès, ce qui est l’opposé de conventions de Windows.

```R
local_repo <- "C:/mylocalrepo"
```

## <a name="add-packages-to-the-local-repo"></a>Ajouter des packages au référentiel local

Après avoir **miniCRAN** est installé et chargé, créez une liste qui spécifie les packages supplémentaires que vous souhaitez télécharger.

Faire **pas** ajouter des dépendances à cette liste initiale. Le **igraph** package utilisé par **miniCRAN** génère la liste des dépendances pour vous. Pour plus d’informations sur l’utilisation du graphique de dépendance généré, consultez [à l’aide de miniCRAN pour identifier les dépendances de package](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html).

1. Ajouter des packages de cible, « zoo » et « prévision » à une variable.

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```

2. Si vous le souhaitez, tracer le graphique de dépendance, mais il peut être informative.
    
    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. Créer le référentiel local. Veillez à modifier la version de R si nécessaire pour la version installée sur votre instance de SQL Server. Version 3.2.2 est sur SQL Server 2016, la version 3.3 est sur SQL Server 2017. Si vous avez effectué une mise à niveau du composant, votre version peut être la plus récente. Pour plus d’informations, consultez [obtenir de R et Python sur les packages](determine-which-packages-are-installed-on-sql-server.md).

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3");
    ```

   À partir de ces informations, le package miniCRAN crée la structure de dossiers, vous devez copier les packages à le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] plus tard.

À ce stade, vous devez avoir un dossier contenant les packages que vous avez besoin, et tous les packages supplémentaires qui ont été requis. Le chemin d’accès doit être similaire à cet exemple : C:\mylocalrepo\bin\windows\contrib\3.3 et il doivent contenir une collection de packages compressés. Ne pas décompresser les packages ou renommez tous les fichiers.

Si vous le souhaitez, exécutez le code suivant pour répertorier les packages contenus dans le référentiel miniCRAN local.

```R
pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE);
head(pdb);
pdb$Package;
pdb[, c("Package", "Version", "License")]
```

## <a name="add-packages-to-the-instance-library"></a>Ajouter des packages à la bibliothèque de l’instance

Après avoir configuré un référentiel local avec les packages que vous avez besoin, déplacez le référentiel de packages à l’ordinateur SQL Server. La procédure suivante décrit comment installer les packages à l’aide des outils R.

1. Copiez le dossier contenant le référentiel miniCRAN, dans son intégralité, sur le serveur où vous prévoyez d’installer les packages. Le dossier présente généralement la structure suivante : miniCRAN racine > bin > windows > contrib > version > tous les packages. Dans les exemples suivants, nous partons du principe un dossier sur le lecteur racine : 

2. Ouvrez un outil de R associé à l’instance (par exemple, vous pourriez utiliser Rgui.exe). Avec le bouton droit **exécuter en tant qu’administrateur** pour permettre à l’outil mettre à jour votre système.

    - Pour SQL Server 2017, est l’emplacement du fichier pour RGUI `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`.

    - Pour SQL Server 2016, emplacement du fichier he pour RGUI est `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`.

3. Obtenir le chemin d’accès pour la bibliothèque de l’instance, puis ajoutez-le à la liste des chemins d’accès de la bibliothèque. Sur SQL Server 2017, le chemin d’accès est similaire à l’exemple suivant.

    ```R
    outputlib <- "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library"
    ```

4. Spécifiez le nouvel emplacement sur le serveur où vous avez copié le **miniCRAN** référentiel, comme `server_repo`.

    Dans cet exemple, nous partons du principe que vous avez copié le référentiel dans un dossier temporaire sur le serveur.

    ```R
    inputlib <- "C:/temp/mylocalrepo"
    ```

5. Étant donné que vous travaillez dans un nouvel espace de travail R sur le serveur, vous devez également entrer la liste des packages à installer.

    ```R
    mypackages <- c("zoo", "forecast")
    ```

6. Installer les packages, en fournissant le chemin d’accès à la copie locale du référentiel miniCRAN.

    ```R
    install.packages(mypackages, repos = file.path("file://", normalizePath(inputlib, winslash = "/")), lib = outputlib, type = "win.binary", dependencies = TRUE);
    ```

7. À partir de la bibliothèque de l’instance, vous pouvez afficher les packages installés à l’aide d’une commande semblable à ce qui suit :

    ```R
    installed.packages()
    ```

## <a name="see-also"></a>Voir aussi

+ [Obtenir les informations sur le package](determine-which-packages-are-installed-on-sql-server.md)
+ [Didacticiels R](../tutorials/sql-server-r-tutorials.md)
+ [Guides de procédures](sql-server-machine-learning-tasks.md)


