---
title: "Installer des packages R supplémentaires sur SQL Server | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 11/08/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 16
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: adc0e5fc229547632759c5702e98d87f4b71cbb3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="install-additional-r-packages-on-sql-server"></a>Installer des packages R supplémentaires sur SQL Server
Cette rubrique explique comment installer de nouveaux packages R sur une instance [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] exécutée sur un ordinateur ayant un accès à Internet.

## <a name="1-locate-the-windows-binaries-in-zip-file-format"></a>1. Rechercher les fichiers binaires Windows au format de fichier ZIP

Les packages R sont pris en charge sur de nombreuses plateformes. Assurez-vous que le package que vous souhaitez installer a un format binaire approprié pour la plateforme Windows. Sinon, le package téléchargé ne peut pas s’exécuter.

Par exemple, pour obtenir le package [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) à partir de Bioconductor :  
  
1.  Dans la liste d’ **archives de package** , recherchez la version **binaire Windows** .  
  
2.  Cliquez sur le lien du fichier .ZIP, puis sélectionnez  **Enregistrer la cible sous**.  
  
3.  Accédez au dossier local dans lequel les packages compressés sont stockés, puis cliquez sur **Enregistrer**.  
  
 Ce processus crée une copie locale du package. Vous pouvez ensuite installer le package ou copier le package compressé sur un serveur qui n’a pas accès à Internet.  
  
  
## <a name="2-open-the-default-r-package-library-for-sql-server-r-services"></a>2. Ouvrir la bibliothèque de packages R par défaut pour SQL Server R Services 

Accédez au dossier sur le serveur où les packages R associés à [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] ont été installés. Il est important d’installer les packages dans la bibliothèque par défaut qui est associée à l’instance actuelle. 

Pour obtenir des instructions sur la localisation de cette bibliothèque, consultez [Installation et gestion des packages R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md).

   Pour chaque instance sur laquelle vous prévoyez d’exécuter un package, vous devez installer une copie distincte des packages. Il n’est pas possible de partager des packages entre les instances.
     
  
## <a name="3-open-an-administrative-command-prompt"></a>3. Ouvrir une invite de commandes d’administration 

Ouvrez R en tant qu’administrateur.  Vous pouvez le faire à partir d’une invite de commandes Windows ou à l’aide d’un des utilitaires R.
  
### <a name="using-the-windows-command-prompt"></a>Utiliser l’invite de commandes Windows 

1. Ouvrez une invite de commandes Windows en tant qu’administrateur, puis accédez au répertoire où se trouvent les fichiers RTerm.Exe ou RGui.exe.  
  
    Dans une installation par défaut, il s’agit du répertoire **\bin** de R. Par exemple, dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], les outils R se trouvent ici : 

    **Instance par défaut**

     `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin` 
 
     **Instance nommée**
   
     `C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`  
  
2. Exécutez **R.Exe**.  
  
### <a name="using-the-r-command-line-utilities"></a>Utiliser les utilitaires de ligne de commande R 
  
1. Utilisez l’Explorateur Windows pour accéder au répertoire contenant les outils R.  
  
2. Cliquez avec le bouton droit sur **RGui.exe** ou **RTerm.exe**, puis sélectionnez **Exécuter en tant qu’administrateur**.  
## <a name="4-install-the-package"></a>4. Installer le package

La commande R à utiliser pour installer le package varie selon que le package provient d’Internet ou d’un fichier zip local.  
  
### <a name="install-package-from-internet"></a>Installer le package à partir d’Internet  
  
1.  En général, vous utilisez la commande suivante pour installer un nouveau package à partir de CRAN ou d’un site miroir.  
  
    ```  
    install.packages("target_package_name")  
    ```
    
    Notez que des guillemets doubles entourant le nom du package sont toujours requis.

2.  Pour spécifier l’emplacement de la bibliothèque dans laquelle le package doit être installé, utilisez une commande similaire à celle-ci :
    
    ```  
    lib.SQL <- "C:\\Program Files\\Microsoft SQL Server\\MSSQL13.MSSQLSERVER\\R_SERVICES\\library"    
    ```

    Notez que pour [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], une seule bibliothèque de packages est actuellement autorisée. N’installez pas de package dans une bibliothèque utilisateur, car vous ne pourrez pas exécuter le package à partir de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].   
     
3.  Une fois l’emplacement de la bibliothèque défini, l’instruction suivante installe le package e1070 dans la bibliothèque de packages utilisée par R Services.  
  
    ```  
    install.packages("e1071", lib = lib.SQL)  
    ```  
  
4.  Vous êtes invité à indiquer le site miroir à partir duquel vous voulez obtenir le package. Sélectionnez n’importe quel site miroir approprié pour l’emplacement où vous êtes.  
  
    Pour obtenir la liste des sites miroirs CRAN, voir [ce site](https://cran.r-project.org/mirrors.html).  
  
    > [!TIP]  
    >  Pour éviter d’avoir à sélectionner un site miroir chaque fois que vous ajoutez un package, vous pouvez configurer votre environnement de développement R afin de toujours utiliser le même référentiel.  
    >   
    >  À cette fin, modifiez le fichier de paramètres globaux R, .Rprofile, puis ajoutez la ligne suivante :  
    >   
    >  `options(repos=structure(c(CRAN="<mirror site URL>")))`  
    >   
    >  Pour plus d’informations sur les préférences et d’autres fichiers chargés au démarrage du runtime R, exécutez la commande suivante à partir d’une console R :  
    >   
    >  `?Startup`  
  
5.  Si le package cible dépend de packages supplémentaires, le programme d’installation de R télécharge automatiquement les dépendances et les installe pour vous.  
  
### <a name="manual-package-installation-or-installing-on-computer-with-no-internet-access"></a>Installation manuelle d’un package ou installation d’un package sur un ordinateur sans accès à Internet 

1. Si vous envisagez d’installer un package avec des dépendances, téléchargez au préalable les packages nécessaires, puis ajoutez-les au dossier avec les autres fichiers de package compressés.

    > [!TIP]
    > 
    > Nous vous recommandons de créer un référentiel local à l’aide de [miniCRAN](https://mran.revolutionanalytics.com/package/miniCRAN/) si vous prévoyez de nombreuses installations hors connexion de packages R.  
  
2.  À l’invite de commandes R, tapez la commande suivante pour spécifier le chemin d’accès et le nom du package à installer :  
   
    ```  
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)  
    ``` 
     
    Cette commande extrait le package R à partir de son fichier zip local, en supposant que vous ayez enregistré la copie dans le répertoire `C:\Temp\Downloaded packages`, puis installe le package (avec ses dépendances) dans la bibliothèque R sur l’ordinateur local.  
  
3.  Si vous avez déjà modifié l’environnement R sur l’ordinateur, vérifiez que la variable d’environnement R `.libPath` utilise un seul chemin qui pointe vers le dossier R_SERVICES de l’instance.  
  
> [!NOTE]
> Si vous avez installé Microsoft R Server (Standalone) en plus de SQL Server R Services, votre ordinateur a une installation distincte de R avec l’ensemble des outils et bibliothèques de R. Les packages installés dans la bibliothèque R_SERVER sont utilisés uniquement par Microsoft R Server et ne peuvent pas être utilisés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
> 
>  Assurez-vous d’utiliser la bibliothèque R_SERVICES quand vous installez des packages que vous souhaitez utiliser ensuite dans SQL Server.

  
## <a name="see-also"></a>Voir aussi  
 [Configurer SQL Server R Services &#40;dans la base de données&#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  

