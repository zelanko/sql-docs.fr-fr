---
title: Créer un référentiel de packages R local à l’aide de miniCRAN
description: Utilisez miniCran pour détecter, assembler et installer les dépendances du package R dans un package consolidé unique.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 34b7fee6b5eef1503f56dd72c6d8ff10911bbdc1
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470214"
---
# <a name="create-a-local-r-package-repository-using-minicran"></a>Créer un référentiel de packages R local à l’aide de miniCRAN
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

le package [miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) , créé par [andre de Vries](https://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html), identifie et télécharge les packages et les dépendances dans un dossier unique, que vous pouvez copier sur d’autres ordinateurs pour une installation de package R hors connexion.

En guise d’entrée, spécifiez un ou plusieurs packages. **miniCRAN** lit de manière récursive l’arborescence des dépendances pour ces packages et télécharge uniquement les packages listés et leurs dépendances à partir de cran ou de référentiels similaires.

En sortie, **miniCRAN** crée un référentiel cohérent en interne qui se compose des packages sélectionnés et de toutes les dépendances requises. Vous pouvez ensuite déplacer ce référentiel local vers le serveur, puis procéder à l’installation des packages sans connexion Internet.

> [!NOTE]
> Les utilisateurs expérimentés de R recherchent souvent la liste des packages dépendants dans le fichier de DESCRIPTION du package téléchargé. Toutefois, les packages listés dans Imports peuvent avoir des dépendances de second niveau. Pour cette raison, nous vous recommandons d’utiliser **miniCRAN** pour assembler la collection complète des packages requis.

## <a name="why-create-a-local-repository"></a>Pourquoi créer un référentiel local

L’objectif de la création d’un référentiel de packages local est de fournir un emplacement unique qu’un administrateur de serveur ou d’autres utilisateurs de l’organisation peuvent utiliser pour installer de nouveaux packages R sur un serveur, en particulier ceux qui n’ont pas accès à Internet. Après avoir créé le référentiel, vous pouvez le modifier en ajoutant de nouveaux packages ou en mettant à niveau la version des packages existants.

Les référentiels de packages sont utiles dans les scénarios suivants:

- **Sécurité** : De nombreux utilisateurs R sont habitués à télécharger et à installer de nouveaux packages R à partir de CRAN ou de l’un de ses sites miroir. Toutefois, pour des raisons de sécurité, les [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] serveurs de production qui exécutent généralement n’ont pas de connectivité Internet.

- **Installation plus facile en mode hors connexion**: Pour installer le package sur un serveur hors connexion, vous devez également télécharger toutes les dépendances de package. l’utilisation de miniCRAN facilite l’extraction de toutes les dépendances dans le format approprié.

    À l’aide de miniCRAN, vous pouvez éviter les erreurs de dépendance de package lors de la préparation des packages à installer avec l’instruction [Create external library](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) .

- **Amélioration**de la gestion des versions: Dans un environnement multi-utilisateur, il existe de bonnes raisons d’éviter une installation non restreinte de plusieurs versions de package sur le serveur. Utilisez un référentiel local pour fournir un ensemble cohérent de packages à utiliser par vos analystes. 

> [!TIP]
> Vous pouvez également utiliser miniCRAN pour préparer les packages à utiliser dans Azure Machine Learning. Pour plus d’informations, consultez ce blog: [Utilisation de miniCRAN dans Azure ML, par Michele Usuelli](https://www.r-bloggers.com/using-minicran-in-azure-ml/) 

## <a name="install-minicran"></a>Installer miniCRAN

Le package **miniCRAN** dépend de 18 autres packages cran, parmi lesquels est le package **RCurl** , qui a une dépendance système sur le package **devel** . De même, le **code XML** du package a une dépendance vis-à-vis de **libxml2-devel**. Pour résoudre les dépendances, nous vous recommandons de créer le référentiel local à l’origine sur un ordinateur avec un accès Internet complet. 

Exécutez les commandes suivantes sur un ordinateur avec un R, des outils R et une connexion Internet de base. Il est supposé qu’il ne s’agit *pas* de votre SQL Server ordinateur. Les commandes suivantes installent le package **miniCRAN** et le package **igraph** requis. Cet exemple vérifie si le package est déjà installé, mais vous pouvez ignorer les instructions If et installer les packages directement.

```R
if(!require("miniCRAN")) install.packages("miniCRAN") 
if(!require("igraph")) install.packages("igraph") 
library("miniCRAN")
```

## <a name="set-the-cran-mirror-and-mran-snapshot"></a>Définir le miroir CRAN et l’instantané MRAN

Spécifiez un site miroir à utiliser pour l’obtention des packages. Par exemple, vous pouvez utiliser le site MRAN ou tout autre site de votre région qui contient les packages dont vous avez besoin. Si le téléchargement échoue, essayez un autre site miroir.

```R
CRAN_mirror <- c(CRAN = "https://mran.microsoft.com")
CRAN_mirror <- c(CRAN = "https://cran.cnr.berkeley.edu")
```

## <a name="create-a-local-folder"></a>Créer un dossier local

Créez un dossier local, par exemple `C:\mylocalrepo` dans lequel stocker les packages collectés. Si vous répétez cette procédure souvent, vous devez probablement utiliser un nom plus descriptif, tel que «miniCRANZooPackages» ou «miniCRANMyRPackagev2».

Spécifiez le dossier en tant que référentiel local. La syntaxe R utilise une barre oblique pour les noms de chemin d’accès, qui est opposée aux conventions Windows.

```R
local_repo <- "C:/mylocalrepo"
```

## <a name="add-packages-to-the-local-repo"></a>Ajouter des packages au référentiel local

Une fois **miniCRAN** installé et chargé, créez une liste qui spécifie les packages supplémentaires que vous souhaitez télécharger.

N’ajoutez **pas** de dépendances à cette liste initiale. Le package **igraph** utilisé par **miniCRAN** génère la liste des dépendances pour vous. Pour plus d’informations sur l’utilisation du graphique de dépendance généré, consultez [utilisation de miniCRAN pour identifier les dépendances de package](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html).

1. Ajoutez des packages cibles, «zoo» et «Forecast» à une variable.

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```

2. Le cas échéant, tracer le graphique de dépendance, mais il peut être informatif.
    
    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. Créez le référentiel local. Veillez à modifier la version R si nécessaire pour la version installée sur votre instance SQL Server. La version 3.2.2 se trouve sur SQL Server 2016, la version 3,3 est sur SQL Server 2017. Si vous avez effectué une mise à niveau de composant, votre version peut être plus récente. Pour plus d’informations, consultez [obtenir des informations sur les packages R et Python](../package-management/installed-package-information.md).

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3");
    ```

   À partir de ces informations, le package miniCRAN crée la structure de dossiers dont vous avez besoin pour copier [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] les packages vers le plus tard.

À ce stade, vous devez disposer d’un dossier contenant les packages dont vous avez besoin et des packages supplémentaires qui étaient nécessaires. Le chemin d’accès doit ressembler à l’exemple suivant: C:\mylocalrepo\bin\windows\contrib\3.3 et doit contenir une collection de packages Zippés. Ne Décompressez pas les packages et ne renommez pas les fichiers.

Si vous le souhaitez, exécutez le code suivant pour répertorier les packages contenus dans le référentiel miniCRAN local.

```R
pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE);
head(pdb);
pdb$Package;
pdb[, c("Package", "Version", "License")]
```

## <a name="add-packages-to-the-instance-library"></a>Ajouter des packages à la bibliothèque d’instances

Une fois que vous disposez d’un référentiel local avec les packages dont vous avez besoin, déplacez le référentiel du package vers l’ordinateur SQL Server. La procédure suivante décrit comment installer les packages à l’aide des outils R.

1. Copiez le dossier contenant le référentiel miniCRAN, dans son intégralité, sur le serveur sur lequel vous prévoyez d’installer les packages. Le dossier présente généralement la structure suivante: miniCRAN racine > bin > Windows > contrib > version > tous les packages. Dans les exemples suivants, nous supposons un dossier du lecteur racine: 

2. Ouvrez un outil R associé à l’instance (par exemple, vous pouvez utiliser RGUI. exe). Cliquez avec le bouton droit sur **exécuter en tant qu’administrateur** pour permettre à l’outil d’effectuer des mises à jour de votre système.

    - Pour SQL Server 2017, l’emplacement du fichier pour RGUI `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`est.

    - Pour SQL Server 2016, l’emplacement du fichier pour RGUI `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`est.

3. Obtient le chemin d’accès de la bibliothèque d’instances et l’ajoute à la liste des chemins d’accès de bibliothèque. Sur SQL Server 2017, le chemin d’accès est similaire à l’exemple suivant.

    ```R
    outputlib <- "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library"
    ```

4. Spécifiez le nouvel emplacement sur le serveur où vous avez copié le dépôt **miniCRAN** , sous `server_repo`la forme.

    Dans cet exemple, nous partons du principe que vous avez copié le référentiel dans un dossier temporaire sur le serveur.

    ```R
    inputlib <- "C:/temp/mylocalrepo"
    ```

5. Dans la mesure où vous travaillez dans un nouvel espace de travail R sur le serveur, vous devez également fournir la liste des packages à installer.

    ```R
    mypackages <- c("zoo", "forecast")
    ```

6. Installez les packages, en fournissant le chemin d’accès à la copie locale du référentiel miniCRAN.

    ```R
    install.packages(mypackages, repos = file.path("file://", normalizePath(inputlib, winslash = "/")), lib = outputlib, type = "win.binary", dependencies = TRUE);
    ```

7. À partir de la bibliothèque d’instances, vous pouvez afficher les packages installés à l’aide d’une commande telle que la suivante:

    ```R
    installed.packages()
    ```

## <a name="see-also"></a>Voir aussi

+ [Obtenir les informations sur le package](../package-management/installed-package-information.md)
+ [Didacticiels R](../tutorials/sql-server-r-tutorials.md)
