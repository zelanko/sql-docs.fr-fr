---
title: "Créer un référentiel de package local à l’aide de miniCRAN | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f2a1ce-316f-4347-b206-8a1b9eebe90b
caps.latest.revision: 4
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e8af93b3e132290eef4b43da568b9381ff8e5a04
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-a-local-package-repository-using-minicran"></a>Créer un référentiel de package local à l’aide de miniCRAN
Cette rubrique explique comment créer un référentiel de package R local en utilisant le package R **miniCRAN**. 

Étant donné que les instances [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] se trouvent généralement sur un serveur sans connectivité Internet, la méthode standard d’installation des packages R (la commande R `install.packages()`) peut ne pas fonctionner, car le programme d’installation de package ne peut alors pas accéder au CRAN ou à un autre site miroir.

Il existe deux façons d’installer des packages à partir d’un partage ou référentiel local :

+ Utilisez le package miniCRAN pour créer un référentiel local des packages dont vous avez besoin, puis installez les packages à partir de ce référentiel. Cette rubrique décrit la méthode miniCRAN.

+ Téléchargez les packages, et leurs dépendances, dont vous avez besoin sous forme de fichiers zip, enregistrez-les dans un dossier local, puis copiez ce dossier sur l’ordinateur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur la méthode de copie manuelle, consultez [Installer des packages supplémentaires sur SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md).


## <a name="step-1-install-minicran-and-download-packages"></a>Étape 1. Installer miniCRAN et télécharger les packages 


1. Installez le package miniCRAN sur un ordinateur ayant accès à Internet.

   ~~~~
   # Install miniCRAN and igraph

   if(!require("miniCRAN")) install.packages("miniCRAN")
   if(!require("igraph")) install.packages("igraph")
   library(miniCRAN)

   # Define the package source: a CRAN mirror, or an MRAN snapshot
   CRAN_mirror <- c(CRAN = "https://mran.microsoft.com/snapshot/2016-04-01")

   # Define the local download location
   local_repo <- "~/miniCRAN"
   ~~~~

2. Téléchargez ou installez les packages souhaités sur cet ordinateur à l’aide du script R suivant. Ce script crée la structure de dossier nécessaire pour pouvoir ensuite copier les packages sur l’ordinateur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

   ~~~~
   # List the packages to get. Do not specify dependencies.
   pkgs_needed <- c("ggplot2", "ggdendro")
   # Plot the dependency graph 
   plot(makeDepGraph(pkgs_needed)) 
   
   # Create the local repo 
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror) 
   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.2") 

   # List local packages 
   pdb <- as.data.frame( 
     pkgAvail(local_repo, type = "win.binary", Rversion = "3.2"),  
     stringsAsFactors = FALSE) 
   head(pdb) 
   pdb$Package 
   pdb[, c("Package", "Version", "License")] 
   ~~~~


## <a name="step-2-copy-the-minicran-repository-to-the-sql-server-computer"></a>Étape 2. Copier le référentiel miniCRAN sur l’ordinateur SQL Server 

Copiez le référentiel miniCRAN dans la bibliothèque R_SERVICES sur l’instance [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

+ Pour SQL Server 2016, le dossier par défaut est `C:/Program Files/Microsoft SQL Server/MSSQL13.MSSQLSERVER/R_SERVICES/library1`.
+ Pour SQL Server 2017, le dossier par défaut est `C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library1`.

Si vous avez installé R Services à l’aide d’une instance nommée, n’oubliez pas d’inclure le nom de l’instance dans le chemin pour vous assurer que les bibliothèques seront installées sur l’instance correcte. Par exemple, le chemin par défaut d’une instance nommée RTEST02 est `C:\Program Files\Microsoft SQL Server\MSSQL13.RTEST02\R_SERVICES\library`.

Si vous avez installé SQL Server sur un lecteur différent, ou modifié d’autres éléments du chemin d’installation, veillez également à répercuter ces modifications.

## <a name="step-3-install-the-packages-on-sql-server-using-the-minicran-repository"></a>Étape 3. Installer les packages sur SQL Server en utilisant le référentiel miniCRAN

Sur l’ordinateur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], ouvrez une ligne de commande R ou une interface RGUI en tant qu’administrateur. 
  
> [!TIP]
> Vous pouvez avoir plusieurs bibliothèques R sur l’ordinateur. Par conséquent, pour vous assurer que les packages seront installés sur l’instance correcte, utilisez la copie de RGUI ou de RTerm qui est installée avec l’instance spécifique sur laquelle vous souhaitez installer les packages.
  
Quand vous êtes invité à spécifier un référentiel, sélectionnez le dossier contenant les fichiers que vous venez de copier, c’est-à-dire le référentiel miniCRAN local.

   ~~~~
   # Run this R code as administrator on the SQL Server computer 
   pkgs_needed <- c("ggplot2", "ggdendro") 
   local_repo  <- "~/miniCRAN" 

   # OPTIONAL: If you are not running R from the instance library as recommended, you must specify the path
   #   .libPaths()[1] 
   # "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library " 
   # lib <- .libPaths()[1]
   
   install.packages(pkgs_needed,  
                    repos = file.path("file://", normalizePath(local_repo, winslash = "/")), 
                    lib = lib, 
                    type = "win.binary", 
                    dependencies = TRUE 
                    ) 
   installed.packages() 
   ~~~~

Vérifiez que les packages ont bien été installés.
   ~~~~
   installed.packages()
   ~~~~



## <a name="acknowledgements"></a>Remerciements

Ces informations sont tirées de l’article écrit par Andre de Vries, le développeur du package miniCRAN. Pour obtenir plus d’informations et la procédure pas à pas complète, consultez l’article [How to install R packages on an off-line SQL Server 2016 instance](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html)

