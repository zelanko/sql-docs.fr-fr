---
title: "Installer des packages R supplémentaires sur SQL Server | Documents Microsoft"
ms.date: 11/15/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: "16"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 8c8e95bf2f0715684bb656d2b2de4dd94aea14f8
ms.sourcegitcommit: 06bb91d138a4d6395c7603a2d8f99c69a20642d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2017
---
# <a name="install-additional-r-packages-on-sql-server"></a>Installer des packages R supplémentaires sur SQL Server

Cet article décrit comment installer de nouveaux packages R à une instance de SQL Server où l’apprentissage automatique est activé.

> [!IMPORTANT]
> Le processus d’ajout de nouveaux packages diffère selon la version de SQL Server que vous exécutez et les outils que vous utilisez. 

**S’applique à :** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] et  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)]
[!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

## <a name="overview-of-package-installation-process"></a>Vue d’ensemble du processus d’installation de package

1.  Déterminer s’il existe une version de Windows du package : [mise en route de la version de package approprié et le format](#packageVersion)

2.  Si le serveur n’a pas accès à internet, téléchargez les fichiers binaires à l’avance : [fichiers zip de téléchargement](#bkmk_zipPreparation)

    Veillez à vérifier les dépendances de package et obtenir les packages associés qui peuvent être nécessaires lors de l’installation. Pour préparer une collection de packages et leurs dépendances, nous vous recommandons du [miniCRAN package](#bkmk_packageDependencies).

    Si vous obtenez des erreurs de téléchargement ou l’installation, essayez d’un site miroir différent.

3.  Comment installer le package dépend de si le serveur a accès à internet et sur votre version de SQL Server. Les processus recommandés sont les suivantes :

    **Installation du package pour SQL Server 2016**
    
    1. Le chercheur de données fournit les packages requis pour un projet ou une équipe. Utilisez [miniCRAN](create-a-local-package-repository-using-minicran.md) pour préparer des collections de packages avec leurs dépendances.

    2. L’administrateur de base de données installe les packages à la bibliothèque de l’instance à l’aide des outils R.

    **Installation du package pour SQL Server 2017**

    1. L’administrateur de base de données permet la gestion des packages sur l’instance et ajoute les utilisateurs aux nouveaux rôles de gestion de package.

    2. Le chercheur de données fournit les packages requis pour un projet ou une équipe. Utilisez [miniCRAN](create-a-local-package-repository-using-minicran.md) pour préparer des collections de packages avec leurs dépendances.

    3. Le package est chargé à l’instance de SQL Server, à l’aide de l’instruction de créer une bibliothèque externe.
    
    4. Une fois que le package a été ajouté à l’instance, tout utilisateur disposant des autorisations appropriées permettre installer les packages à la base de données d’exécution des scripts de R, en appelant le code R à partir de `sp_execute_external_script`.
    
    5. Les utilisateurs disposant des autorisations appropriées peuvent également installer ou rechercher les packages à partir d’un client distant de R, à l’aide de la nouvelle fonction RevoScaleR pour la gestion des packages.

## <a name="install-new-packages"></a>Installation de nouveaux packages

Cette section fournissent des procédures détaillées pour les scénarios d’installation de package de clés. Choisir la meilleure méthode, en fonction de :

- La version de SQL Server que vous utilisez

- Si vous êtes l’unique propriétaire de l’instance ou tentez de gérer les packages de plusieurs personnes à l’aide de rôles de base de données.

- Si vous installez un package, ou plusieurs packages avec des dépendances

**Utilisez la gestion des packages SQL Server**

Si votre instance prend en charge les fonctionnalités de gestion de package, vous pouvez utiliser T-SQL ou des outils R classiques.

-  Package de téléchargement R à un serveur SQL Server où la gestion des packages et basée sur les rôles de package d’accès est activée. Un utilisateur installe le package à l’aide de T-SQL.

    [Installer des packages à l’aide de créer une bibliothèque externe](#bkmk_sqlInstall)

- Un client distant de R permet d’ajouter de nouveaux packages vers un serveur. Nécessite SQL Server 2017. Gestion des packages doit avoir été activée sur le serveur. 

    [Utiliser R pour installer des packages sur un serveur de gestion de packages est activée](#bkmk_rAddPackage)

- Préparer une bibliothèque de package pour une utilisation avec une bibliothèque externe créer qui contient plusieurs packages, ainsi que leurs dépendances.

    [Pour installer plusieurs packages à partir d’un référentiel miniCRAN](#bkmk_minicran)

**Utilisez les outils R classiques**

Si vous utilisez une version antérieure de SQL Server R services, suivez ces instructions pour installer les packages à l’aide des outils R classiques. Si vous le souhaitez, utilisez miniCRAN pour préparer une collection de packages pour l’installation.

-  Installer un package R dans la bibliothèque d’instance par défaut à l’aide des outils R. Requiert un accès administrateur.

    [Installer des packages dans la bibliothèque de l’instance à l’aide des outils R](#bkmk_rInstall)

- Créer une collection de packages pour prendre en charge une installation de plusieurs packages et leurs dépendances partagée.

    [Créer un référentiel de packages à l’aide de miniCRAN](create-a-local-package-repository-using-minicran.md)

### <a name="bkmk_sqlInstall"></a>Installer des packages à l’aide des outils SQL Server

1. Assurez-vous que la fonctionnalité de gestion de bibliothèque externe dans SQL Server 2017 a été activée sur l’instance.

    [Comment activer ou désactiver la gestion des packages](r-package-how-to-enable-or-disable.md)

2. Se connecter au serveur à l’aide d’un compte qui dispose des autorisations nécessaires pour installer de nouveaux packages, à l’aide de l’un des rôles de base de données pris en charge décrites dans cette rubrique : [gestion des packages R pour SQL Server](r-package-management-for-sql-server-r-services.md)

3.  Copiez le fichier compressé qui contient le package R que vous souhaitez installer dans un dossier sur l’ordinateur serveur, tels que votre **utilisateurs** ou **Documents** dossier. Vous ne pouvez pas ajouter un package à partir d’un lecteur réseau ou d’un dossier sur l’ordinateur client. Si vous avez utilisé miniCRAN pour créer un référentiel de packages, copiez le référentiel de packages dans son intégralité à n’importe quel dossier local sur le serveur : autrement dit, pas sur un lecteur réseau.

    Si vous n’avez pas accès aux dossiers sur le serveur, vous pouvez passer le contenu du package au format binaire. Consultez [créer une bibliothèque externe](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) pour obtenir un exemple.

4.  À partir de la base de données où vous souhaitez utiliser le package, exécutez le [créer une bibliothèque externe](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) instruction.

    Pour cet exemple, nous partons du principe que votre compte est autorisé à télécharger de nouveaux packages sur le serveur et de les installer à **partagé** étendue dans la base de données.

    L’instruction suivante ajoute la version de la [zoo](https://cran.r-project.org/web/packages/zoo/index.html) package dans le contexte de base de données en cours, à partir d’un partage de fichiers local.

    ```SQL
    CREATE EXTERNAL LIBRARY zoo
    FROM (CONTENT = 'C:\Temp\RPackages\zoo_1.8-0.zip')
    WITH (LANGUAGE = 'R');
    ```

    Si vous vous connectez à l’aide d’un compte qui est un propriétaire de base de données (membre du rôle dbo), le package est mis à disposition dans **partagé** étendue : autrement dit, il peut être installé par tout utilisateur qui est membre de la `rpkgs-users` rôle.

    Si vous téléchargez le package à l’aide d’un compte qui peut accéder uniquement **privé** étendue, le package peut être installé que par vous.

4.  Pour installer le package dans la bibliothèque par défaut R utilisée par l’instance, exécutez R `library()` commande au sein de la procédure stockée sp_execute_external_script.

    ```SQL
    EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    # load the binaries in zoo
    library(zoo)'
    ```

    En cas de réussite, le **Messages** fenêtre doit signaler un message telles que « package « zoo » a été décompressé et MD5 sommes vérifiée ». Si un package requis est déjà installé, le processus d’installation attache ensuite et charge le package requis.

    > [!NOTE]
    > Si un package requis n’est pas disponible, une erreur est retournée : « il n’existe aucun package appelé \<required_package\>». 
    > 
    > Pour éviter les erreurs, nous vous recommandons de Vérifiez au préalable les dépendances du package, ou miniCRAN permet de collecter tous les packages requis dans un seul fichier compressé avant d’exécuter `CREATE EXTERNAL LIBRARY`.

### <a name="bkmk_rAddPackage"></a>Utiliser R pour installer des packages sur un serveur de gestion de packages est activée

Si vous avez déjà activé la gestion des packages sur l’instance, vous pouvez installer les nouveaux packages R à partir d’un client distant de R, à l’aide des fonctions RevoScaleR pour la gestion des packages.

1. Avant de commencer, assurez-vous que ces conditions sont remplies :

    + Utiliser la dernière version du Client Microsoft R, qui inclut les mises à jour de RevoScale.
    + Gestion des packages a été activée sur l’instance et sur la base de données.
    + Vous avez l’autorisation à un des rôles de gestion de base de données.

2. Répertorier les packages que vous souhaitez installer dans une variable de chaîne.

    ```R
    packageList <- c("e1071")

3. Define a connection string to the instance and database where package management is enabled, and use the connection string to create a SQL Server compute context.

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```

4. Appelez `rxInstallPackages` et de transmettre le contexte de calcul et la variable de chaîne qui contient les noms de package.

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    Si des packages dépendants sont nécessaires, elles sont également téléchargés.
    
    Dans cet exemple, parce que le propriétaire du lot et l’étendue n’a pas été spécifié, le package est installé à l’aide des informations d’identification de l’utilisateur qui effectue la connexion et les packages sont installés à l’aide de l’étendue par défaut pour cet utilisateur.

### <a name="bkmk_rInstall"></a>Installer des packages dans la bibliothèque de l’instance à l’aide des outils R

Vous pouvez utiliser les outils R pour installer de nouveaux packages sur SQL Server 2016 et SQL Server 2017. Toutefois, vous devez être un administrateur pour ce faire.

1.  Si le serveur n’a pas accès à internet, téléchargez les packages à l’avance.

    Nous vous recommandons d’utiliser un référentiel de packages pour préparer des collections de packages en mode hors connexion. Pour plus d’informations, consultez [créer un référentiel de package local à l’aide de miniCRAN](create-a-local-package-repository-using-minicran.md).

2.  Accédez au dossier sur le serveur où sont installées les bibliothèques R pour l’instance.

    > [!IMPORTANT] 
    > Veillez à installer des packages à la bibliothèque par défaut qui est associée à l’instance actuelle. Ne jamais installer de packages vers un répertoire de l’utilisateur. Pour obtenir des instructions sur la localisation de la bibliothèque par défaut, consultez [packages R sont installés avec SQL Server](installing-and-managing-r-packages.md).

    Pour chaque instance sur lequel vous exécutez un package, installez une copie distincte du package. Les packages ne peuvent pas être partagés entre les instances.

4.  Ouvrez une invite de commandes R en tant qu’administrateur.

    Par exemple, si vous utilisez l’invite de commandes Windows, accédez au répertoire où se trouvent les fichiers RTerm.Exe ou RGui.exe. 

    **Instance par défaut**

    SQL Server 2017 :`C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`
    
    SQL Server 2016 :`C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`

    **Instance nommée**

    SQL Server 2017 :`C:\Program files\MSSQL14.<instanceName>\R_SERVICES\bin\x64`
    
    SQL Server 2016 :`C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`

5.  Exécutez la commande R `install.packages` pour installer le package.

    La syntaxe varie selon que le package à partir d’Internet ou d’un fichier zip local. 

    **Installer le package à l’aide d’une connexion internet**

    Par exemple, l’instruction suivante installe le package d’e1071 populaires. Des guillemets doubles sont toujours requis pour le nom du package.

    ```R
    install.packages("e1071", lib = lib.SQL)
    ```

    Lorsque vous êtes invité pour un site miroir, sélectionnez n’importe quel site qui est adapté à votre emplacement.

    Si le package cible dépend de packages supplémentaires, le programme d’installation de R télécharge les dépendances et les installe pour vous automatiquement.

    **Installer manuellement, ou sur un ordinateur sans accès à Internet**

    Si vous envisagez d’installer un package avec des dépendances, téléchargez au préalable les packages nécessaires, puis ajoutez-les au dossier avec les autres fichiers de package compressés. Consultez le [conseils d’installation](#bkmk_tips) section de l’aide sur la préparation des packages.

    À l’invite de commandes R, tapez la commande suivante pour spécifier le chemin d’accès et le nom du package à installer :

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    Cette commande extrait un package R à partir de son fichier zip local, si vous avez enregistré la copie dans le répertoire `C:\Temp\Downloaded packages`et installe le package (avec ses dépendances) dans la bibliothèque R sur l’ordinateur local.

### <a name="bkmk_minicran"></a>Pour installer plusieurs packages à partir d’un référentiel miniCRAN

Le processus global de l’installation des packages à partir d’un référentiel miniCRAN est similaire à l’installation d’un package à partir d’un seul fichier zip. Toutefois, au lieu de télécharger un package individuel dans un format compressé, le référentiel miniCRAN contient le package cible, ainsi que tous les packages requis associés.

1.  Préparer le référentiel miniCRAN et puis copiez le fichier compressé dans un dossier local sur le serveur.

2.  Si vous utilisez T-SQL, un administrateur exécute l’instruction T-SQL `CREATE EXTERNAL LIBRARY` pour télécharger de la collection de package compressé pour la base de données.

    Par exemple, l’instruction suivante fait référence à un référentiel miniCRAN contenant le package randomForest et ses dépendances.

    ```R
    CREATE EXTERNAL LIBRARY randomForest
    FROM (CONTENT = 'C:\Downloads\Rpackages\randomForest_4.6-12.zip')
    WITH (LANGUAGE = 'R');
    ```

3. Pour installer les packages pour une utilisation avec SQL Server, exécutez la commande suivante en tant que partie du code R dans une procédure stockée.
    
    ```SQL
    EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    # install randomForest and its dependencies
    library(randomForest)'
    ```

    En cas de réussite, le **Messages** fenêtre doit signaler un message telles que « package 'randomForest' a été décompressé et les sommes de MD5 vérifié » et « Terminé chaînés d’exécution ».

## <a name="package-installation-tips"></a>Conseils d’installation de package

Cette section fournit des conseils assorties et exemple de code liées à l’installation de package de R sur SQL Server. 

###  <a name="packageVersion"></a>Obtenir la version de package approprié et le format

Il existe plusieurs sources de packages R, les plus connues étant CRAN et Bioconductor. Le site officiel pour le langage R (<https://www.r-project.org/>) répertorie la plupart de ces ressources. De nombreux packages sont publiés sur GitHub, où vous pouvez obtenir le code source. Toutefois, vous pouvez ont reçu des packages R développés par une personne dans votre entreprise.

Quelle que soit la source, vous devez vous assurer que le package que vous souhaitez installer a un format binaire pour la plateforme Windows. Dans le cas contraire, le package téléchargé ne peut pas exécuter dans l’environnement SQL Server.

Avant de télécharger, vous devez également vérifier si le package est compatible avec la version de R est en cours d’exécution dans SQL Server.

### <a name="bkmk_zipPreparation"></a>Télécharger le package en tant que fichier compressé

Pour l’installation sur un serveur sans accès à internet, téléchargez une copie du package dans le format d’un fichier compressé pour l’installation en mode hors connexion. Ne pas décompressez le package.

Par exemple, la procédure suivante décrit pour obtenir la version correcte de la [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) package à partir de Bioconductor, en supposant que de l’ordinateur a accès à internet.

1.  Dans la liste d’ **archives de package** , recherchez la version **binaire Windows** .

2.  Cliquez sur le lien vers le. Fichier ZIP, puis sélectionnez **enregistrer la cible sous**.

3.  Accédez au dossier local dans lequel les packages compressés sont stockés, puis cliquez sur **enregistrer**.

Ce processus crée une copie locale du package. Vous pouvez ensuite installer le package ou copier le package compressé vers un serveur qui n’a pas accès à internet.

Pour plus d’informations sur le contenu du fichier de format zip et comment créer un package R, nous vous recommandons de ce didacticiel, vous pouvez télécharger au format PDF à partir du site du projet R : [création de Packages R](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf).

### <a name="bkmk_packageDependencies"></a>Obtenir les dépendances de package

Packages R dépendent souvent plusieurs packages, certains d'entre eux peuvent être disponibles dans la bibliothèque de R par défaut utilisée par l’instance. Ou, parfois, un package requiert une version différente d’un package dépendant qui est déjà installé.

Si vous avez besoin d’installer plusieurs packages ou souhaitez vous assurer que tous les membres de votre organisation Obtient le type de package approprié et la version, nous recommandons d’utiliser le package miniCRAN pour créer un référentiel local qui peut être partagé entre plusieurs utilisateurs ou ordinateur. Pour plus d’informations, consultez [créer un référentiel de package local à l’aide de miniCRAN](create-a-local-package-repository-using-minicran.md).

### <a name="permissions"></a>Permissions

Si vous êtes un utilisateur expérimenté de R, vous pouvez être habitué à l’installation des packages à partir de la ligne de commande sans autorisations spéciales ou sans les télécharger à l’avance. Toutefois, la plupart des serveurs n’ont pas d’une connexion internet. En outre, l’accès aux partages de fichiers ou de stockage peut-être être limité.

Cette section décrit le différents niveaux d’autorisations requises pour l’installation des packages dans SQL Server 2016 et SQl Server 2017. L’installation peut être réalisée à l’aide des outils R ou SQL Server, mais les processus et les autorisations diffèrent légèrement.

-   SQL Server 2016

    Dans cette version, seul un administrateur sur l’ordinateur peut installer des packages à l’emplacement requis. Les outils R standard vous permet d’installer des packages, mais vous devez exécuter en tant qu’administrateur et utiliser les outils R associés à l’instance.

-   SQL Server 2017

    Cette version fournit de nouvelles fonctionnalités qui permettent à un administrateur de base de données de déléguer l’installation du package pour les utilisateurs. L’administrateur doit activer les fonctionnalités de gestion de package sur chaque instance. Une fois que cette fonctionnalité est activée, l’administrateur peut utiliser des rôles de base de données afin de permettre aux utilisateurs individuels à installer des packages en fonction des besoins ou pour partager des packages sur une base par base de données.

    Pour plus d’informations, consultez [gestion des packages R pour SQL Server](r-package-management-for-sql-server-r-services.md).


> [!IMPORTANT]
> 
> Les utilisateurs expérimentés de R sont habitués à l’installation des packages dans une bibliothèque de l’utilisateur, puis de référencer le package dans le dossier dans le cadre de la solution R, en spécifiant un chemin d’accès de fichier. Toutefois, cette pratique n’est pas pris en charge dans SQL Server. Pour plus d’informations et des solutions de contournement, consultez [comment utiliser des packages dans les bibliothèques utilisateur](packages-installed-in-user-libraries.md).

### <a name="comparing-package-management-methods"></a>Comparaison des méthodes de gestion de package

Cette section compare les méthodes d’installation de package disponibles et répertorie des considérations supplémentaires et des conseils pour vous aider à déterminer une stratégie de gestion et d’installation de package approprié.

#### <a name="using-sql-server-package-management-features"></a>À l’aide des fonctionnalités de gestion de package SQL Server

Si vous activez la gestion des packages, vous installez un package pour une base de données spécifique. Si vous avez besoin d’utiliser un package dans toutes les bases de données où le script R est activé, vous devez l’installer dans chaque base de données.

Toutefois, étant donné que SQL Server gère les informations sur l’utilisateur qui a le droit d’utiliser les packages, il est plus facile de copier des informations sur les utilisateurs et les packages entre des bases de données. Il est également facile de régénérer un ensemble de packages de travail pour un ou plusieurs utilisateurs lors de la restauration d’une base de données, ou lors du déplacement entre des instances.

À l’aide de T-SQL et les fonctions de gestion de packages dans SQL Server 2017 d’est la méthode recommandée chaque fois que vous avez plusieurs utilisateurs de base de données installation ou l’exécution des packages R.

Cette fonctionnalité est disponible à compter de SQL Server 2017.

#### <a name="using-r-tools-to-install-packages-for-the-sql-server-instance"></a>À l’aide des outils R pour installer des packages pour l’instance de SQL Server

Si vous utilisez cette méthode, les packages installés pour l’instance sont disponibles dans une base de données. Toutefois, étant donné que les packages sont installés directement au système de fichiers, ils doivent être gérés en dehors de SQL Server. Les packages ne peuvent pas être sauvegardés ou restaurés. En outre, l’administrateur de base de données doit apprendre à utiliser les outils R.

Toutefois, cette solution est la plus simple si vous êtes l’unique propriétaire de la base de données.

#### <a name="managing-multiple-packages-and-multiple-versions-of-the-same-package"></a>Gestion de plusieurs packages et plusieurs versions du même package

Si vous avez besoin effectuer une installation en mode hors connexion de packages R, configuration d’un référentiel local à l’aide de [miniCRAN](https://mran.revolutionanalytics.com/package/miniCRAN/) vous permet de partager les packages et de gérer les versions disponibles pour une utilisation par l’organisation.

#### <a name="establish-a-single-mirror-site-as-standard"></a>Établir un site miroir unique comme norme

Pour éviter d’avoir à sélectionner un site miroir chaque fois que vous ajoutez un package, vous pouvez configurer votre environnement de développement R afin de toujours utiliser le même référentiel. Pour ce faire, modifiez le fichier de paramètres globaux R, **. Rprofile**et ajoutez la ligne suivante :

`options(repos=structure(c(CRAN="<mirror site URL>")))`

Miroirs CRAN sont répertoriés sur [ce site](https://cran.r-project.org/mirrors.html).

Pour plus d’informations sur les préférences et d’autres fichiers chargés au démarrage du runtime R, exécutez cette commande à partir d’une console R :`?Startup`

#### <a name="know-which-library-you-are-using-for-installation"></a>Connaître la bibliothèque dans laquelle vous utilisez pour l’installation

Si vous avez modifié précédemment l’environnement R sur l’ordinateur, avant d’installer quoi que ce soit, prenez un moment, puis vérifiez que la variable d’environnement R `.libPath` utilise simplement un chemin d’accès.

Ce chemin d’accès doit pointer vers le dossier R_SERVICES pour l’instance. Pour plus d’informations, consultez [packages R sont installés avec SQL Server](installing-and-managing-r-packages.md).

#### <a name="side-by-side-installation-with-r-server"></a>Installation côte à côte avec R Server

Si vous avez installé Microsoft Machine Learning Server (autonome) en plus des Services de SQL Server Machine Learning, votre ordinateur doit disposer des installations séparées de R pour chaque les deux, avec des doublons de tous les outils R et les bibliothèques.

> [!IMPORTANT]
> 
> Les packages qui sont installés à la bibliothèque R_SERVER sont utilisés uniquement par Microsoft R Server et ne sont pas accessibles par SQL Server.
> 
> Veillez à utiliser le `R_SERVICES` bibliothèque lors de l’installation des packages que vous souhaitez utiliser dans SQL Server.
