---
title: Créer un référentiel de packages R local à l’aide de miniCRAN
description: Découvrez comment installer des packages R hors connexion à l’aide du package miniCRAN pour créer un référentiel local de packages et de dépendances.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 68f86d673b944a029c7bd0f74c9594692bd579f4
ms.sourcegitcommit: 00350f6ffb73c2c0d99beeded61c5b9baa63d171
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70196332"
---
# <a name="create-a-local-r-package-repository-using-minicran"></a>Créer un référentiel de packages R local à l’aide de miniCRAN
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article explique comment installer des packages R hors connexion à l’aide de [miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) pour créer un référentiel local de packages et de dépendances. **miniCRAN** identifie et télécharge les packages et les dépendances dans un dossier unique que vous copiez sur d’autres ordinateurs pour l’installation du package R hors connexion.

Vous pouvez spécifier un ou plusieurs packages, et **miniCRAN** lit de manière récursive l’arborescence des dépendances pour ces packages. Il télécharge ensuite uniquement les packages listés et leurs dépendances à partir de CRAN ou de référentiels similaires.

Une fois l’opération terminée, **miniCRAN** crée un référentiel cohérent en interne comprenant les packages sélectionnés et toutes les dépendances requises. Vous pouvez déplacer ce référentiel local vers le serveur, puis procéder à l’installation des packages sans connexion Internet.

Les utilisateurs expérimentés de R recherchent souvent la liste des packages dépendants dans le fichier de DESCRIPTION d’un package téléchargé. Toutefois, les packages listés dans Imports peuvent avoir des dépendances de second niveau. Pour cette raison, nous vous recommandons d’utiliser **miniCRAN** pour assembler la collection complète des packages requis.

## <a name="why-create-a-local-repository"></a>Pourquoi créer un référentiel local

L’objectif de la création d’un référentiel de packages local est de fournir un emplacement unique qu’un administrateur de serveur ou d’autres utilisateurs de l’organisation peuvent utiliser pour installer de nouveaux packages R sur un serveur, en particulier ceux qui n’ont pas accès à Internet. Après avoir créé le référentiel, vous pouvez le modifier en ajoutant de nouveaux packages ou en mettant à niveau la version des packages existants.

Les référentiels de packages sont utiles dans les scénarios suivants:

- **Sécurité** : De nombreux utilisateurs R sont habitués à télécharger et à installer de nouveaux packages R à partir de CRAN ou de l’un de ses sites miroir. Toutefois, pour des raisons de sécurité, les [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] serveurs de production qui exécutent généralement n’ont pas de connectivité Internet.

- **Installation plus facile en mode hors connexion**: Pour installer un package sur un serveur hors connexion, vous devez également télécharger toutes les dépendances de package. L’utilisation de miniCRAN facilite l’extraction de toutes les dépendances dans le format correct. À l’aide de miniCRAN, vous pouvez éviter les erreurs de dépendance de package lors de la préparation des packages à installer avec l’instruction [Create external library](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) .

- **Amélioration**de la gestion des versions: Dans un environnement multi-utilisateur, il existe de bonnes raisons d’éviter une installation non restreinte de plusieurs versions de package sur le serveur. Utilisez un référentiel local pour fournir un ensemble cohérent de packages pour vos utilisateurs.

## <a name="install-minicran"></a>Installer miniCRAN

Le package **miniCRAN** dépend de 18 autres packages cran, parmi lesquels est le package **RCurl** , qui a une dépendance système sur le package **devel** . De même, le **code XML** du package a une dépendance vis-à-vis de **libxml2-devel**. Pour résoudre les dépendances, nous vous recommandons de créer le référentiel local à l’origine sur un ordinateur avec un accès Internet complet.

Exécutez les commandes suivantes sur un ordinateur avec un R, des outils R et une connexion Internet de base. Il est supposé qu’il ne s’agit pas de votre SQL Server ordinateur. Les commandes suivantes installent le package **miniCRAN** et le package **igraph** . Cet exemple vérifie si le package est déjà installé, mais vous pouvez ignorer les `if` instructions et installer les packages directement.

```R
if(!require("miniCRAN")) install.packages("miniCRAN") 
if(!require("igraph")) install.packages("igraph") 
library("miniCRAN")
```

## <a name="set-the-cran-mirror-and-mran-snapshot"></a>Définir le miroir CRAN et l’instantané MRAN

Spécifiez un site miroir à utiliser pour l’obtention des packages. Par exemple, vous pouvez utiliser le site MRAN ou tout autre site de votre région qui contient les packages dont vous avez besoin. Si un téléchargement échoue, essayez un autre site miroir.

```R
CRAN_mirror <- c(CRAN = "https://cran.cnr.berkeley.edu")
```

## <a name="create-a-local-folder"></a>Créer un dossier local

Créez un dossier local dans lequel stocker les packages collectés. Si vous répétez cette procédure souvent, vous souhaiterez peut-être utiliser un nom descriptif, tel que «miniCRANZooPackages» ou «miniCRANMyRPackageV2».

Spécifiez le dossier en tant que référentiel local. La syntaxe R utilise une barre oblique pour les noms de chemin d’accès, qui est opposée aux conventions Windows.

```R
local_repo <- "C:/miniCRANZooPackages"
```

## <a name="add-packages-to-the-local-repo"></a>Ajouter des packages au référentiel local

Une fois **miniCRAN** installé et chargé, créez une liste qui spécifie les packages supplémentaires que vous souhaitez télécharger.

N’ajoutez **pas** de dépendances à cette liste initiale. Le package **igraph** utilisé par **miniCRAN** génère automatiquement la liste des dépendances. Pour plus d’informations sur l’utilisation du graphique de dépendance généré, consultez [utilisation de miniCRAN pour identifier les dépendances de package](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html).

1. Ajoutez des packages cibles «Zoo» et «Forecast» à une variable.

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```

2. Le cas échéant, tracer le graphique de dépendance. Cela n’est pas nécessaire, mais il peut être informatif.

    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. Créez le référentiel local. Veillez à modifier la version R, si nécessaire, en fonction de la version installée sur votre instance SQL Server. Si vous avez effectué une mise à niveau de composant, votre version peut être plus récente que la version d’origine. Pour plus d’informations, consultez [obtenir des informations sur les packages R](../package-management/r-package-information.md).

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3");
    ```

   À partir de ces informations, le package miniCRAN crée la structure de dossiers dont vous avez besoin pour copier [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] les packages vers le plus tard.

À ce stade, vous devez disposer d’un dossier contenant les packages dont vous avez besoin, ainsi que tous les packages supplémentaires requis. Le dossier doit contenir une collection de packages Zippés. Ne Décompressez pas les packages et ne renommez pas les fichiers.

Si vous le souhaitez, exécutez le code suivant pour répertorier les packages contenus dans le référentiel miniCRAN local.

```R
pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE);
head(pdb);
pdb$Package;
pdb[, c("Package", "Version", "License")]
```

## <a name="add-packages-to-the-instance-library"></a>Ajouter des packages à la bibliothèque d’instances

Une fois que vous disposez d’un référentiel local avec les packages dont vous avez besoin, déplacez le référentiel du package vers l’ordinateur SQL Server. La procédure suivante décrit comment installer les packages à l’aide des outils R.

1. Copiez le dossier contenant le référentiel miniCRAN, dans son intégralité, sur le serveur sur lequel vous prévoyez d’installer les packages. Le dossier a généralement cette structure: 

   `<miniCRAN root>/bin/windows/contrib/version/<all packages>`

   Dans cette procédure, nous partons du principe qu’il s’agit d’un dossier du lecteur racine.

2. Ouvrez un outil R associé à l’instance (par exemple, vous pouvez utiliser RGUI. exe). Cliquez avec le bouton droit et sélectionnez **exécuter en tant qu’administrateur** pour permettre à l’outil d’effectuer des mises à jour de votre système.

   ::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
   - Par exemple, l’emplacement de fichier par défaut pour `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`RGUI est.
   ::: moniker-end

   ::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
   - Par exemple, l’emplacement du fichier pour RGUI `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`est.
   ::: moniker-end

   ::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
   - Par exemple, l’emplacement du fichier pour RGUI `C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\R_SERVICES\bin\x64`est.
   ::: moniker-end

3. Obtient le chemin d’accès de la bibliothèque d’instances et l’ajoute à la liste des chemins d’accès de bibliothèque.

   ::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
   Par exemple,

   ```R
   outputlib <- "C:/Program Files/Microsoft SQL Server/MSSQL13.MSSQLSERVER/R_SERVICES/library"
   ```

   ::: moniker-end

   ::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
   Par exemple,

   ```R
   outputlib <- "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library"
   ```

   ::: moniker-end

   ::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
   Par exemple,

   ```R
   outputlib <- "C:/Program Files/Microsoft SQL Server/MSSQL15.MSSQLSERVER/R_SERVICES/library"
   ```

   ::: moniker-end

4. Spécifiez le nouvel emplacement sur le serveur sur lequel vous avez copié le dépôt miniCRAN `server_repo`sous la forme.

    Dans cet exemple, nous partons du principe que vous avez copié le référentiel dans un dossier temporaire sur le serveur.

    ```R
    inputlib <- "C:/miniCRANZooPackages"
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

+ [Récupérer les informations du package R](../package-management/r-package-information.md)
+ [Didacticiels R](../tutorials/sql-server-r-tutorials.md)
