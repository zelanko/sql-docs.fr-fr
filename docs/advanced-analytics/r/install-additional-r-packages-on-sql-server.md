---
title: "Installer des packages R supplémentaires sur SQL Server | Documents Microsoft"
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: "16"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 2821983b39dcd4c301ea4b49713de0cdd3550a65
ms.sourcegitcommit: 60d0c9415630094a49d4ca9e4e18c3faa694f034
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="install-additional-r-packages-on-sql-server"></a>Installer des packages R supplémentaires sur SQL Server

Cet article décrit comment installer de nouveaux packages R à une instance de SQL Server où l’apprentissage automatique est activé.

**S’applique à :** 
+ [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)]  [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]
+ [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

## <a name="prerequisites"></a>Prerequisites

+ Déterminer s’il existe une version de Windows du package : [mise en route de la version de package approprié et le format](#packageVersion)

+ Si le serveur n’a pas accès à internet, vous devez télécharger les fichiers binaires Windows à l’avance : [fichiers zip de téléchargement](#bkmk_zipPreparation)

+ Identifier les dépendances du package. 

    - Si le serveur a accès à internet, vous n’avez pas besoin à vous soucier des dépendances ; tous les packages requis peuvent être installés automatiquement.

    - Si le serveur ne **pas** ont accès à internet, vous devez identifier toutes les dépendances et télécharger les packages requis à l’avance, dans un format compressé. Un moyen simple pour ce faire consiste à utiliser [miniCRAN](create-a-local-package-repository-using-minicran.md) pour préparer une collection de packages avec toutes les dépendances. Ce référentiel peut ensuite être copié sur l’ordinateur serveur.

+ Vérifier la compatibilité du package. Le package doit être compatible avec la version de R est en cours d’exécution dans SQL Server.

    Vérifiez également si le package (ou tous les packages dont il a besoin) contient des fonctionnalités qui seraient bloquées par SQL Server ou par la stratégie. Par exemple, certains packages ne sont pas envisageables pour un environnement SQL Server renforcé. De tels packages peuvent inclure des packages qui accèdent au réseau, qui utilisent Java ou autres infrastructures généralement pas utilisés dans un environnement SQL Server ou des packages qui requièrent l’accès de système de fichier avec élévation de privilèges.

+ Autorisations

    Un accès administratif à l’ordinateur exécutant SQL Server est requis.

    En outre, pour s’exécuter dans SQL Server, les packages doivent être installés dans la bibliothèque par défaut qui est associée à l’instance actuelle. Pour obtenir des instructions sur la localisation de la bibliothèque par défaut, consultez [packages R sont installés avec SQL Server](installing-and-managing-r-packages.md).
    
    Si vous êtes un utilisateur expérimenté de R, vous pouvez être habitué à l’installation des packages à partir de la ligne de commande sans autorisations spéciales ou sans les télécharger à l’avance. Toutefois, cette méthode ne fonctionne pas dans SQL Server. Dans de nombreux cas SQL Server ordinateurs n’ont pas d’une connexion internet. En outre, l’accès aux fichiers de serveur ou un stockage externe peut-être être limité. Packages installés dans une bibliothèque de l’utilisateur ne sont pas accessibles par runnign de travaux R dans SQL Server. 

    Si vous n’avez pas un accès administratif à l’ordinateur SQL Server, recherchez un administrateur de base de données à l’aide sur l’installation du package.

+ Pour chaque instance où vous devez utiliser le package, exécutez installation séparément.

     Les packages ne peuvent pas être partagés entre les instances. Vous pouvez utiliser la même source de fichier compressé pour installer le package à des instances distinctes, mais une copie distincte du package est ajoutée à la bibliothèque de chaque instance.

## <a name="install-packages"></a>Installer des packages

Cette section fournit les étapes d’installation de package pour les scénarios suivants :

+ [Installation de nouveaux packages sur un serveur avec accès à Internet](#bkmk_rInstall)
+ [Effectuer une installation hors connexion de packages sur un serveur avec **aucune** accès à internet](#bkmk_offlineInstall)
+ [Installer des packages dans un contexte de calcul de SQL Server à l’aide de RevoScaleR](#bkmk_rAddPackage)
+ [Installer des packages à l’aide de l’instruction de créer une bibliothèque externe](#bkmk_createlibrary) (SQL Server 2017 uniquement ; autres restrictions s’appliquent)

### <a name="bkmk_rInstall"></a>Installation en ligne à l’aide des outils R

Vous pouvez utiliser les outils R standard pour installer de nouveaux packages sur une instance de SQL Server 2016 ou SQL Server 2017. Toutefois, vous devez être un administrateur pour ce faire.

1.  Accédez au dossier sur le serveur où sont installées les bibliothèques R pour l’instance.

    > [!IMPORTANT] 
    > Veillez à installer des packages à la bibliothèque par défaut qui est associée à l’instance actuelle. Ne jamais installer de packages vers un répertoire de l’utilisateur.

    Si vous n’avez pas les autorisations requises, contactez l’administrateur de base de données et fournir une liste des packages que vous avez besoin.

2.  Ouvrez une invite de commandes R en tant qu’administrateur.

    Par exemple, si vous utilisez l’invite de commandes Windows, accédez au répertoire où se trouvent les RTerm.Exe ou RGui.exe. 

    **Instance par défaut**

    SQL Server 2017 :`C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`
    
    SQL Server 2016 :`C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`

    **Instance nommée**

    SQL Server 2017 :`C:\Program files\MSSQL14.<instanceName>\R_SERVICES\bin\x64`
    
    SQL Server 2016 :`C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`

    Si vous avez utilisé la liaison pour mettre à niveau les composants d’apprentissage automatique, le chemin d’accès peut ont changé. Vérifiez toujours le chemin d’accès de l’instance avant d’installer de nouveaux packages. 

3.  Exécutez la commande R `install.packages` pour installer le package. Par exemple, l’instruction suivante installe le package d’e1071 populaires. 

    ```R
    install.packages("e1071", lib = lib.SQL)
    ```

    Des guillemets doubles sont requis pour le nom du package.

4. Lorsque vous êtes invité pour un site miroir, sélectionnez n’importe quel site qui est adapté à votre emplacement.

5. Si le package cible dépend de packages supplémentaires, le programme d’installation de R télécharge les dépendances et les installe pour vous automatiquement.

> [!IMPORTANT]
> Pour chaque instance où vous devez utiliser le package, exécutez installation séparément. Les packages ne peuvent pas être partagés entre les instances.

### <a name = "bkmk_offlineInstall"></a>Installation hors connexion à l’aide des outils R 

Si vous envisagez d’installer le package possède des dépendances, préparer **tous les** requis des packages à l’avance.  Consultez le [conseils d’installation](#bkmk_tips) section de l’aide sur la préparation des packages.

> [!IMPORTANT]
>  Chaque fois que vous installez des packages sur un serveur qui n’a pas accès à internet, il est essentiel que vous analysez les dépendances complètes à l’avance et vous assurer que vous avez téléchargé tous les packages requis **avant** début de l’installation. Nous vous recommandons de [miniCRAN](https://mran.microsoft.com/package/miniCRAN) pour ce processus. Ce package de R utilise une liste des packages que vous souhaitez installer, analyse des dépendances et obtient tous les fichiers pour vous. miniCRAN crée ensuite un référentiel unique que vous pouvez copier sur l’ordinateur serveur.
> 
> Pour plus d’informations, consultez [créer un référentiel de package local à l’aide de miniCRAN](create-a-local-package-repository-using-minicran.md)

1. Copiez le package ou le référentiel dans un format compressé à un partage local, ou un autre emplacement accessible au serveur.

2.  Recherchez le dossier sur le serveur où sont installées les bibliothèques R pour l’instance.

    Par exemple, si vous utilisez l’invite de commandes Windows, accédez au répertoire où se trouvent les RTerm.Exe ou RGui.exe.

    **Instance par défaut**

    SQL Server 2017 :`C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`
    
    SQL Server 2016 :`C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`

    **Instance nommée**

    SQL Server 2017 :`C:\Program files\MSSQL14.<instanceName>\R_SERVICES\bin\x64`
    
    SQL Server 2016 :`C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`

3. Ouvrez une invite de commandes R en tant qu’administrateur.

4.  Exécutez la commande R `install.packages` et spécifiez le package ou le nom du référentiel et l’emplacement des fichiers compressés.

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    Cette commande extrait le package R `mynewpackage` à partir de son fichier zip local, si vous avez enregistré la copie dans le répertoire `C:\Temp\Downloaded packages`, puis installe le package sur l’ordinateur local. Si le package possède des dépendances, le programme d’installation vérifie pour les packages existants dans la bibliothèque. Si vous avez créé un référentiel qui inclut les dépendances, le programme d’installation installe les packages requireed également.

    Si tous les packages requis ne sont pas présents dans la bibliothèque de l’instance et ne peut pas être trouvés dans les fichiers, l’installation du package cible échoue.

### <a name="bkmk_rAddPackage"></a>Installer des packages R sur un serveur à partir d’un client distant de R

Dans les versions récentes de [R Server ou serveur de Machine Learning](https://docs.microsoft.com/machine-learning-server/rebranding-microsoft-r-server), RevoScaleR inclut des fonctions qui prennent en charge l’installation de nouveaux packages R dans un contexte de calcul de SQL Server. 

1. Avant de commencer, assurez-vous que ces conditions sont remplies :

    + Votre client a RevoScale 9.0.1 ou version ultérieure.
    + Une version équivalente de RevoScaleR a été installée sur l’instance de SQL Server.
    + Le [fonctionnalité de gestion de package](..\r\r-package-how-to-enable-or-disable.md) a été activée sur l’instance.
    + Vous êtes un membre d’un rôle de base de données qui vous permet d’installer des packages dans un partagé ou prvate contexte, sur l’instance spécifiée et ddatabase.

2. À partir d’une ligne de commande R, définir une chaîne de connexion à l’instance et de la base de données et utiliser la chaîne de connexion avec le [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) constructeur pour créer un contexte de calcul de SQL Server.

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```
3. Créer une liste des packages que vous souhaitez installer et enregistrer la liste dans une variable de chaîne.

    ```R
    packageList <- c("e1071", "mice")
    ```

4. Appelez [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) et de transmettre le contexte de calcul et la variable de chaîne qui contient les noms de package.

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    Si des packages dépendants sont nécessaires, elles sont également installées, en supposant qu'une connexion internet est disponible.
    
    Dans cet exemple, étant donné que le propriétaire et l’étendue n’a pas été spécifié, packages sont installés à l’aide des informations d’identification de l’utilisateur qui effectue la connexion, dans l’étendue par défaut pour cet utilisateur.

### <a name="bkmk_createlibrary"></a>Permet d’installer les packages d’un référentiel de miniCRAN et de créer une bibliothèque externe 

SQL Server 2017 fournit de nouvelles fonctionnalités pour l’installation et la gestion des packages R à l’aide de T-SQL. Toutefois, ce processus requiert qu’un package soit disponible comme local compressé fichier, plutôt que de le télécharger à partir d’internet. L’instruction échoue si tous les packages ne sont pas préparés à l’avance.

CRÉER une bibliothèque externe est pris en charge dans les conditions suivantes :

+ Vous installez un package sans dépendances
+ Vous installez plusieurs packages, ou avec des dépendances et que vous avez préparé tous les packages à l’avance. 

**Étapes**

1.  Préparer le package au format compressé, ou créer un référentiel miniCRAN contenant le package et ses dépendances.  

2. Copiez le fichier compressé ou référentiel vers un dossier local sur le serveur.

     > [!IMPORTANT]
     > Le fichier que vous spécifiez comme source doit contenir le package cible, ainsi que tous les packages requis associés.

3. En tant qu’administrateur, exécutez l’instruction T-SQL `CREATE EXTERNAL LIBRARY` pour télécharger de la collection de package compressé pour la base de données.

    Par exemple, l’instruction suivante fait référence à un référentiel miniCRAN contenant le package randomForest et ses dépendances. 

    ```R
    CREATE EXTERNAL LIBRARY randomForest
    FROM (CONTENT = 'C:\Downloads\Rpackages\randomForest_4.6-12.zip')
    WITH (LANGUAGE = 'R');
    ```

    Vous ne pouvez pas utiliser un nom quelconque dans l’instruction CREATE ; le nom de bibliothèque externe doit avoir le même nom que vous utiliserez lors du chargement ou de l’appel.

4. Installez l’ou les packages pour une utilisation avec SQL Server, en exécutant du code à l’intérieur d’une procédure stockée.
    
    ```SQL
    EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    # install randomForest and its dependencies
    library(randomForest)'
    ```

    En cas de réussite, le **Messages** fenêtre doit signaler un message telles que « package 'randomForest' a été décompressé et les sommes de MD5 vérifié » et « Terminé chaînés d’exécution ».

    Si l’installation échoue, tous les packages d’installation échouent, et les tentatives suivantes pour installer le package peuvent également échouer, avec le message : 

    « Erreur dans rxSqlPkgInstallPackages... Impossible d’installer des packages - Veuillez consulter le journal pour plus d’informations »

## <a name="package-installation-tips-and-frequently-asked-questions-faq"></a>Conseils d’installation de package et les questions fréquemment posées (FAQ)

Cette section fournit des conseils assorties et questions courantes liées à l’installation du package R dans SQL Server.

###  <a name="packageVersion"></a>Obtenir la version de package approprié et le format

Il existe plusieurs sources de packages R, les plus connues étant CRAN et Bioconductor. Le site officiel pour le langage R (<https://www.r-project.org/>) répertorie la plupart de ces ressources. De nombreux packages sont publiés sur GitHub, où vous pouvez obtenir le code source. Toutefois, vous pouvez ont reçu des packages R développés par une personne dans votre entreprise.

Quelle que soit la source, vous devez vous assurer que le package que vous souhaitez installer a un format binaire pour la plateforme Windows. Dans le cas contraire, le package téléchargé ne peut pas exécuter dans l’environnement SQL Server.

### <a name="bkmk_zipPreparation"></a>Télécharger le package comme un fichier compressé

Pour l’installation sur un serveur sans accès à internet, vous devez télécharger une copie du package dans le format d’un fichier compressé pour l’installation en mode hors connexion. Ne pas décompressez le package.

Par exemple, la procédure suivante décrit pour obtenir la version correcte de la [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) package à partir de Bioconductor, en supposant que de l’ordinateur a accès à internet.

1.  Dans la liste d’ **archives de package** , recherchez la version **binaire Windows** .

2.  Cliquez sur le lien vers le. Fichier ZIP, puis sélectionnez **enregistrer la cible sous**.

3.  Accédez au dossier local dans lequel les packages compressés sont stockés, puis cliquez sur **enregistrer**.

    Ce processus crée une copie locale du package. Si vous obtenez une erreur de téléchargement, essayez un site miroir différent.

4. Une fois que l’archive de package a été téléchargé, vous pouvez installer le package, ou copier le package compressé vers un serveur qui n’a pas accès à internet.

> [!TIP]
> Si par inadvertance, vous installez le package au lieu de télécharger les fichiers binaires, une copie du fichier ZIP téléchargé est également enregistrée sur votre ordinateur. Surveiller les messages d’état que le package est installé pour déterminer l’emplacement du fichier. Vous pouvez copier ce fichier sur le serveur qui n’a pas accès à internet.
> Si vous téléchargez le package à l’aide de cette méthode, les dépendances du package ne sont pas inclus. 

Pour plus d’informations sur le contenu du fichier de format zip et comment créer un package R, nous vous recommandons de ce didacticiel, vous pouvez télécharger au format PDF à partir du site du projet R : [création de Packages R](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf).

### <a name="bkmk_packageDependencies"></a>Obtenir les dépendances de package

Packages R dépendent souvent plusieurs packages, certains d'entre eux peuvent être disponibles dans la bibliothèque de R par défaut utilisée par l’instance. Parfois, un package requiert une version différente d’un package dépendant qui est déjà installé.

Si vous avez besoin d’installer plusieurs packages ou souhaitez vous assurer que tous les membres de votre organisation Obtient le type de package approprié et la version, nous vous recommandons d’utiliser le [miniCRAN](https://mran.microsoft.com/package/miniCRAN) package pour créer un référentiel local qui peut être partagé entre plusieurs d’utilisateurs ou d’ordinateur. Pour plus d’informations, consultez [créer un référentiel de package local à l’aide de miniCRAN](create-a-local-package-repository-using-minicran.md).

### <a name="permissions"></a>Autorisations

Cette section décrit le différents niveaux d’autorisations requises pour l’installation des packages dans SQL Server 2016 et SQL Server 2017. L’installation peut être réalisée à l’aide des outils R ou SQL Server, mais les processus et les autorisations diffèrent légèrement.

-   SQL Server 2016

    Dans cette version, seul un administrateur sur l’ordinateur peut installer des packages à l’emplacement requis. Les outils R standard vous permet d’installer des packages, mais vous devez exécuter en tant qu’administrateur et utiliser les outils R associés à l’instance.

-   SQL Server 2017

    Si vous disposez d’un accès administratif, vous pouvez installer des packages sur une instance à l’échelle à l’aide des outils R.

    Si vous êtes propriétaire d’une base de données, vous pouvez installer des packages R à partir d’un client distant, si vous définissez une connexion et se connectez à l’instance à l’aide de RxInSqlServer.
    
    Cette version inclut de nouvelles fonctionnalités pour prendre en charge la gestion des packages R ou Python par les administrateurs de base de données dans les prochaines versions. Pour utiliser cette fonctionnalité, un administrateur doit d’abord activer les fonctions de gestion de packages sur chaque instance. Une fois que cette fonctionnalité est activée, chaque utilisateur peut installer des packages à une base de données spécifique, en fonction de leur rôle de base de données. Pour plus d’informations, consultez [activer ou désactiver la gestion des packages R pour SQL Server](../r/r-package-how-to-enable-or-disable.md).

> [!IMPORTANT]
> 
> Les utilisateurs expérimentés de R sont habitués à l’installation des packages dans une bibliothèque de l’utilisateur, puis de référencer le package dans le dossier dans le cadre de la solution R, en spécifiant un chemin d’accès de fichier. Toutefois, cette pratique n’est pas pris en charge dans SQL Server. Pour plus d’informations et des solutions de contournement, consultez [comment utiliser des packages dans les bibliothèques utilisateur](packages-installed-in-user-libraries.md).

### <a name="establish-a-single-mirror-site-as-standard"></a>Établir un site miroir unique comme norme

Pour éviter d’avoir à sélectionner un site miroir chaque fois que vous ajoutez un package, vous pouvez configurer votre environnement de développement R afin de toujours utiliser le même référentiel. Pour ce faire, modifiez le fichier de paramètres globaux R, **. Rprofile**et ajoutez la ligne suivante :

`options(repos=structure(c(CRAN="<mirror site URL>")))`

Miroirs CRAN sont répertoriés sur [ce site](https://cran.r-project.org/mirrors.html).

Pour plus d’informations sur les préférences et d’autres fichiers chargés au démarrage du runtime R, exécutez cette commande à partir d’une console R :`?Startup`

### <a name="know-which-library-you-are-using-for-installation"></a>Connaître la bibliothèque dans laquelle vous utilisez pour l’installation

Si vous avez modifié précédemment l’environnement R sur l’ordinateur, avant d’installer quoi que ce soit, prenez un moment, puis vérifiez que la variable d’environnement R `.libPath` utilise simplement un chemin d’accès.

Ce chemin d’accès doit pointer vers le dossier R_SERVICES pour l’instance. Pour plus d’informations, consultez [packages R sont installés avec SQL Server](installing-and-managing-r-packages.md).

### <a name="side-by-side-installation-with-r-server"></a>Installation côte à côte avec R Server

Si vous avez installé Microsoft Machine Learning Server (autonome) en plus des Services de SQL Server Machine Learning, votre ordinateur doit disposer des installations séparées de R pour chacune, avec des doublons de tous les outils R et les bibliothèques.

> [!IMPORTANT]
> 
> Les packages qui sont installés à la bibliothèque R_SERVER sont utilisés uniquement par Microsoft R Server et ne sont pas accessibles par SQL Server.
> 
> Veillez à utiliser le `R_SERVICES` bibliothèque lors de l’installation des packages que vous souhaitez utiliser dans SQL Server.

### <a name="how-to-determine-which-packages-are-already-installed"></a>Comment déterminer les packages qui sont déjà installés ?

 Consultez [packages R sont installés avec SQL Server](installing-and-managing-r-packages.md)