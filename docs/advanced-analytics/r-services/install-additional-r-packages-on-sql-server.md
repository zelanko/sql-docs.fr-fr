---
title: "Installer des Packages R suppl&#233;mentaires sur SQL Server | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 16
---
# Installer des Packages R suppl&#233;mentaires sur SQL Server
Cette rubrique décrit comment installer de nouveaux packages R à une instance de [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] sur un ordinateur qui a accès à Internet.

## <a name="1-locate-the-windows-binaries-in-zip-file-format"></a>1. Recherchez les fichiers binaires Windows au format de fichier ZIP

Packages R sont pris en charge sur de nombreuses plateformes. Vous devez vous assurer que le package que vous souhaitez installer un format binaire pour la plate-forme Windows. Sinon, le package téléchargé ne fonctionnera pas.

Par exemple, pour obtenir le package [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) à partir de Bioconductor :  
  
1.  Dans la liste d’ **archives de package** , recherchez la version **binaire Windows** .  
  
2.  Cliquez sur le lien du fichier .ZIP, puis sélectionnez  **Enregistrer la cible sous**.  
  
3.  Accédez au dossier local dans lequel les packages compressés sont stockés, puis cliquez sur **Enregistrer**.  
  
 Ce processus crée une copie locale du package. Vous pouvez ensuite installer le package, ou copier le package compressé vers un serveur qui n’a pas accès à Internet.  
  
  
## <a name="2-open-the-default-r-package-library-for-sql-server-r-services"></a>2. Ouvrez la bibliothèque de package par défaut R pour les Services de SQL Server R 

Accédez au dossier sur le serveur où les packages R associés [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] ont été installés. Il est important d’installer les packages de la bibliothèque par défaut qui est associé à l’instance actuelle. 

Pour obtenir des instructions sur la localisation de cette bibliothèque, consultez la page [installation et la gestion des Packages R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md).

   Pour chaque instance où vous allez exécuter un package, vous devez installer une copie distincte des packages. Packages ne peut pas être partagés entre les instances.
     
  
## <a name="3-open-an-administrative-command-prompt"></a>3. Ouvrez une invite de commandes d’administration 

Ouvrez R en tant qu’administrateur.  Vous pouvez pour cela à l’aide de la commande Windows p, ropt, ou en utilisant un des utilitaires R.
  
### <a name="using-the-windows-command-prompt"></a>Utiliser l’invite de commandes Windows 

1. Ouvrez une invite de commandes Windows en tant qu’administrateur et accédez au répertoire où se trouvent les fichiers RTerm.Exe ou RGui.exe.  
  
    Dans une installation par défaut, il s’agit du répertoire **\bin** de R. Par exemple, dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], les outils R sont trouvent ici : 

    **Instance par défaut**

     `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin` 
 
     **Instance nommée**
   
     `C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`  
  
2. Exécutez **R.Exe**.  
  
### <a name="using-the-r-commandline-utilities"></a>Utiliser les utilitaires de ligne de commande R 
  
1. Utilisez l’Explorateur Windows pour accéder au répertoire contenant les outils R.  
  
2. Avec le bouton droit **RGui.exe** ou **RTerm.exe**, puis sélectionnez **Exécuter en tant qu’administrateur**.  
## <a name="4-install-the-package"></a>4. Installez le package

La commande R pour installer le package dépend de si vous obtenez le package à partir d’Internet ou d’un fichier zip local.  
  
### <a name="install-package-from-internet"></a>Installez le package à partir d’Internet  
  
1.  En général, vous utilisez la commande suivante pour installer un nouveau package de CRAN ou un des sites de mise en miroir.  
  
    ```  
    install.packages("target_package_name")  
    ```
    
    Notez que des guillemets doubles entourant le nom du package sont toujours requis.

2.  Pour spécifier la bibliothèque dans lequel le package doit être installé, utilisez une commande similaire à celle-ci pour définir l’emplacement de la bibliothèque :
    
    ```  
    lib.SQL <- "C:\\Program Files\\Microsoft SQL Server\\MSSQL13.MSSQLSERVER\\R_SERVICES\\library"    
    ```

    Notez que pour [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], actuellement bibliothèque d’un seul package est autorisée. N’installez pas de packages à une bibliothèque de l’utilisateur, ou vous ne serez pas en mesure d’exécuter le package à partir de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].   
     
3.  Définir l’emplacement de la bibliothèque, l’instruction suivante installe le package d’e1070 populaires dans la bibliothèque de package utilisée par les Services de R.  
  
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
  
### <a name="manual-package-installation-or-installing-on-computer-with-no-internet-access"></a>Installation manuelle de package, ou l’installer sur un ordinateur sans accès Internet 

1. Si vous envisagez d’installer le package possède des dépendances, obtenir les packages requis à l’avance et les ajouter au dossier avec un autre package zippé.

    > [!TIP]
    > 
    > Nous vous recommandons de définir un référentiel local à l’aide de [miniCRAN](https://mran.revolutionanalytics.com/package/miniCRAN/) Si vous avez besoin prendre en charge une installation hors connexion fréquente des packages R.  
  
2.  À l’invite de commandes R, tapez la commande suivante pour spécifier le chemin d’accès et le nom du package à installer :  
   
    ```  
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)  
    ``` 
     
    Cette commande extrait le package R à partir de son fichier zip local, en supposant que vous avez enregistré la copie dans le répertoire `C:\Temp\Downloaded packages`, et installe le package (avec ses dépendances) dans la bibliothèque R sur l’ordinateur local.  
  
3.  Si vous avez déjà modifié l’environnement R sur l’ordinateur, vous devez vous assurer que la variable d’environnement R `.libPath` utilise qu’un seul chemin d’accès, qui pointe vers le dossier R_SERVICES pour l’instance.  
  
> [!NOTE]
> Si vous avez installé le serveur Microsoft R (autonome) en plus des Services de R SQL Server, votre ordinateur a une installation distincte de R avec les outils R et les bibliothèques. Les packages sont installés à la bibliothèque R_SERVER sont utilisés uniquement par Microsoft R Server et ne sont pas accessibles par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
> 
>  Veillez à utiliser la bibliothèque R_SERVICES lors de l’installation des packages que vous souhaitez utiliser dans SQL Server.

  
## <a name="see-also"></a>Voir aussi  
 [Configurer les Services SQL Server R &#40 ; -base de données &#41 ;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  