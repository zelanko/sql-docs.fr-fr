---
title: "Cr&#233;er un r&#233;f&#233;rentiel de la Package Local &#224; l’aide de miniCRAN | Microsoft Docs"
ms.custom: ""
ms.date: "05/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27f2a1ce-316f-4347-b206-8a1b9eebe90b
caps.latest.revision: 4
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 4
---
# Cr&#233;er un r&#233;f&#233;rentiel de la Package Local &#224; l’aide de miniCRAN
Cette rubrique décrit comment vous pouvez créer un référentiel de package R en utilisant le package R **miniCRAN**. 

Étant donné que [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] instances sont généralement situés sur un serveur qui ne dispose pas de connectivité Internet, la méthode standard d’installation des packages R (la commande R `install.packages()`) peuvent ne pas fonctionner, car le programme d’installation de package ne peut pas accéder au CRAN ou autres sites de mise en miroir.

Il existe deux options pour l’installation des packages à partir d’un partage local ou le référentiel :

+ Le package miniCRAN permet de créer un référentiel de packages que vous avez besoin, puis installez à partir de ce référentiel. Cette rubrique décrit la méthode miniCRAN.

+ Téléchargez les packages que vous avez besoin et leurs dépendances, comme les fichiers zip et les enregistrer dans un dossier local puis copier ce dossier à le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ordinateur. Pour plus d’informations sur la méthode de copie manuelle, consultez [installer des Packages supplémentaires sur SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md).


## Étape 1. Installer miniCRAN et télécharger des packages 


1. Installez le package miniCRAN sur un ordinateur qui a accès à Internet.

   ~~~~
   # Install miniCRAN ---------------------------------------------------

   if(!require("miniCRAN")) install.packages("miniCRAN")
   if(!require("igraph")) install.packages("igraph")
   library(miniCRAN)

   # Define the package source: a CRAN mirror, or an MRAN snapshot
   CRAN_mirror <- c(CRAN = "https://mran.microsoft.com/snapshot/2016-04-01")

   # Define the local download location
   local_repo <- "~/miniCRAN"
   ~~~~

2. Télécharger ou installer les packages que vous avez besoin sur cet ordinateur. Cela créera la structure de dossiers que vous devez copier les packages à le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] plus tard.

   ~~~~
   # List the packages you need 
   # Do not specify dependencies
   pkgs_needed <- c("ggplot2", "ggdendro")
   ~~~~

3. Copier le référentiel miniCRAN dans la bibliothèque R_SERVICES sur la [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] instance.

## Étape 2. Installer les packages sur l’ordinateur SQL Server 

4. Sur le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] l’ordinateur, exécutez la commande R  `install.packages()`. Vous pouvez utiliser un des outils qui sont installées avec R [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], tel que Rgui.exe, ou vous pouvez exécuter la commande dans le cadre d’un [!INCLUDE[tsql_md](../../includes/tsql-md.md)] procédure stockée.
5. À l’invite pour spécifier un référentiel, sélectionnez le dossier contenant les fichiers que vous venez de copier ; Autrement dit, le référentiel local miniCRAN.

   ~~~~
   pkgs_needed <- c("ggplot2", "ggdendro")
   local_repo  <- "~/miniCRAN"
   
   .libPaths()[1]
   "C:/Program Files/Microsoft SQL Server/130/R_SERVER/library"

   lib <- .libPaths()[1]

   install.packages(pkgs_needed, 
                 repos = file.path("file://", normalizePath(local_repo, winslash = "/")),
                 lib = lib,
                 type = "win.binary",
                 dependencies = TRUE
                 )
   ~~~~

6. Vérifiez que les packages ont été installés en exécutant ce code R.
   ~~~~
   installed.packages()
   ~~~~



## Accusés de réception

La source de ces informations est cet article par Andre de Vries, qui a également développé le package miniCRAN. Pour plus d’informations et connaître la procédure détaillée, consultez  [des packages d’installation de R sur une instance de SQL Server 2016 hors ligne](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html)