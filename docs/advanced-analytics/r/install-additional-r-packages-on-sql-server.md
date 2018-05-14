---
title: Installer de nouveaux packages R sur SQL Server Machine Learning Services | Documents Microsoft
description: Ajouter de nouveaux packages R pour SQL Server 2016 R Services ou SQL Server 2017 Machine Learning Services (de-de base de données)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/10/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 1106d0f1505f29a3b54f9fc036fcaf28b8715b75
ms.sourcegitcommit: feff98b3094a42f345a0dc8a31598b578c312b38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2018
---
# <a name="install-new-r-packages-on-sql-server"></a>Installer de nouveaux packages R sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit comment installer de nouveaux packages R à une instance de SQL Server où l’apprentissage automatique est activé. Il existe plusieurs méthodes pour l’installation de nouveaux packages R, selon la version de SQL Server que vous avez et indique si le serveur possède une connexion internet.

## <a name="bkmk_rInstall"></a> Installer des packages R via une connexion Internet

Vous pouvez utiliser les outils R standard pour installer de nouveaux packages sur une instance de SQL Server 2016 ou SQL Server 2017, en fournissant l’ordinateur a un port ouvert 80 et dispose de droits d’administrateur.

> [!IMPORTANT] 
> Veillez à installer des packages à la bibliothèque par défaut qui est associée à l’instance actuelle. Ne jamais installer de packages vers un répertoire de l’utilisateur.

Cette procédure utilise RGui, mais vous pouvez utiliser RTerm ou tout autre R de ligne de commande outil qui prend en charge l’accès avec élévation de privilèges.

### <a name="install-a-package-using-rgui"></a>Installer un package à l’aide de RGui

1. [Déterminer l’emplacement de la bibliothèque de l’instance](installing-and-managing-r-packages.md). Accédez au dossier où sont installés les outils R. Par exemple, le chemin d’accès par défaut pour une instance par défaut de SQL Server 2017 est comme suit : `C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`

1. RGui.exe d’avec le bouton droit, puis sélectionnez **exécuter en tant qu’administrateur**. Si vous n’avez pas les autorisations requises, contactez l’administrateur de base de données et fournir une liste des packages que vous avez besoin.

1. À partir de la ligne de commande, si vous connaissez le nom du package, vous pouvez taper : `install.packages("the_package-name")` des guillemets doubles sont requises pour le nom du package.

1. Lorsque vous êtes invité pour un site miroir, sélectionnez n’importe quel site qui est adapté à votre emplacement.

Si le package cible dépend de packages supplémentaires, le programme d’installation de R télécharge les dépendances et les installe pour vous automatiquement.

Si vous avez plusieurs instances de SQL Server, tels que les instances côte à côte de SQL Server 2016 R Services et SQL Server 2017 Machine Learning Services, exécutez installation séparément pour chaque instance si vous souhaitez utiliser le package dans les deux contextes. Les packages ne peuvent pas être partagés entre les instances.

## <a name = "bkmk_offlineInstall"></a> Installation hors connexion à l’aide des outils R

Si le serveur n’a pas accès à internet, des étapes supplémentaires sont requises pour préparer les packages. Pour installer des packages R sur un serveur qui n’a pas accès à internet, vous devez :

+ Analyser les dépendances à l’avance.
+ Téléchargez le package cible sur un ordinateur connecté à Internet.
+ Télécharger tous les packages requis sur le même ordinateur et placer tous les packages dans une archive de package unique.
+ Code postal de l’archive si elle n’est pas déjà dans un format compressé.
+ Copiez l’archive de package vers un emplacement sur le serveur.
+ Installez le package cible en spécifiant le fichier d’archive en tant que source.

> [!IMPORTANT] 
> > Assurez-vous que vous analysez toutes les dépendances et télécharger **tous les** requis packages **avant** début de l’installation. Nous vous recommandons de [miniCRAN](https://mran.microsoft.com/package/miniCRAN) pour ce processus. Ce package de R utilise une liste des packages que vous souhaitez installer, analyse des dépendances et obtient tous les fichiers pour vous. miniCRAN crée ensuite un référentiel unique que vous pouvez copier sur l’ordinateur serveur.
> 
> Pour plus d’informations, consultez [créer un référentiel de package local à l’aide de miniCRAN](create-a-local-package-repository-using-minicran.md)

Cette procédure suppose que vous avez préparé tous les packages que vous avez besoin, dans un format compressé et que vous êtes prêt à les copier sur le serveur.

1. Copie le package compressé de fichiers, ou pour plusieurs packages, le référentiel complet qui contient tous les packages compressés format, à un emplacement accessible au serveur.

2. Ouvrez le dossier sur le serveur où sont installés les outils R pour l’instance. Par exemple, si vous utilisez l’invite de commandes Windows sur un système avec SQL Server 2016 R Services, basculez vers `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`.

3. Avec le bouton droit sur RGui ou RTerm et sélectionnez **exécuter en tant qu’administrateur**.

4. Exécutez la commande R `install.packages` et spécifiez le package ou le nom du référentiel et l’emplacement des fichiers compressés.

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    Cette commande extrait le package R `mynewpackage` à partir de son fichier zip local, si vous avez enregistré la copie dans le répertoire `C:\Temp\Downloaded packages`, puis installe le package sur l’ordinateur local. Si le package possède des dépendances, le programme d’installation vérifie pour les packages existants dans la bibliothèque. Si vous avez créé un référentiel qui inclut les dépendances, le programme d’installation installe les packages requis ainsi.

    Si tous les packages requis ne sont pas présents dans la bibliothèque de l’instance et ne peut pas être trouvés dans les fichiers, l’installation du package cible échoue.

## <a name="bkmk_createlibrary"></a> Utiliser créer une bibliothèque externe

**S’applique à :**  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Le [créer une bibliothèque externe](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) instruction permet d’ajouter un package ou un ensemble de packages à une base de données spécifique ou à une instance sans exécuter R ou directement le code Python. Toutefois, cette méthode requiert la préparation du package et les autorisations de base de données supplémentaires.

+ Tous les packages doivent être disponibles en tant qu’un fichier zip local, plutôt que téléchargement à la demande à partir d’internet.

    Si vous n’avez pas de l’accès au système de fichiers sur le serveur, vous pouvez également passer un package complet en tant que variable, à l’aide d’un format binaire. Pour plus d’informations, consultez [créer une bibliothèque externe](../../t-sql/statements/create-external-library-transact-sql.md).

+ Toutes les dépendances doivent être identifiés par le nom et la version et inclus dans le fichier zip. L’instruction échoue si les packages nécessaires ne sont pas disponibles, notamment les dépendances de package en aval. Nous vous recommandons d’utiliser **miniCRAN** ou **igraph** pour l’analyse des dépendances de packages. L’installation d’une version incorrecte du package ou de la dépendance de package peut se produire l’instruction échoue. 

+ Vous devez disposer des autorisations nécessaires sur la base de données. Pour plus d’informations, consultez [créer une bibliothèque externe](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

### <a name="prepare-the-packages-in-archive-format"></a>Préparer les packages au format d’archive

1. Si vous installez un package unique, téléchargez le package au format compressé. 

2. Si le package requiert tous les autres packages, vous devez vérifier que les packages nécessaires sont disponibles. Vous pouvez utiliser miniCRAN pour analyser le package cible et d’identifier toutes ses dépendances. 

3. Copier les fichiers ou un référentiel miniCRAN contenant tous les packages vers un dossier local sur le serveur.

4. Ouvrir un **requête** fenêtre, à l’aide d’un compte avec des privilèges d’administrateur.

5. Exécutez l’instruction T-SQL `CREATE EXTERNAL LIBRARY` pour télécharger de la collection de package compressé pour la base de données.

    Par exemple, l’instruction suivante noms comme source du package d’un référentiel de miniCRAN contenant le **randomForest** package, ainsi que de ses dépendances. 

    ```R
    CREATE EXTERNAL LIBRARY randomForest
    FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
    WITH (LANGUAGE = 'R');
    ```

    Vous ne pouvez pas utiliser un nom arbitraire ; le nom de bibliothèque externe doit avoir le même nom que vous utiliserez lors du chargement ou de l’appel.

6. Si la bibliothèque est créée avec succès, vous pouvez exécuter le package dans SQL Server, en l’appelant à l’intérieur d’une procédure stockée.
    
    ```SQL
    EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    library(randomForest)'
    ```

## <a name="tips-for-package-installation"></a>Conseils pour l’installation du package

Cette section fournit des conseils assorties et questions courantes liées à l’installation du package R dans SQL Server.

###  <a name="packageVersion"></a> Obtenir la version de package approprié et le format

Il existe plusieurs sources de packages R, tels que le CRAN et Bioconductor. Le site officiel du langage R (<https://www.r-project.org/>) répertorie la plupart de ces ressources. De nombreux packages sont publiés sur GitHub, où vous pouvez obtenir le code source. Enfin, vous pouvez ont reçu des packages R développés par une personne dans votre entreprise, ou vous avez un package personnalisé que vous avez écrit.

Quelle que soit la source, avant d’installer le package, assurez-vous que vous avez obtenu le format binaire pour la plateforme Windows. 

### <a name="bkmk_zipPreparation"></a> Télécharger le package comme un fichier compressé

Pour l’installation sur un serveur sans accès à internet, vous devez télécharger une copie du package dans le format d’un fichier compressé pour l’installation en mode hors connexion. **Ne pas décompressez le package.**

Par exemple, la procédure suivante décrit pour obtenir la version correcte de la [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) package à partir de Bioconductor, en supposant que de l’ordinateur a accès à internet.

1.  Dans la liste d’ **archives de package** , recherchez la version **binaire Windows** .

2.  Cliquez sur le lien vers le. Fichier ZIP, puis sélectionnez **enregistrer la cible sous**.

3.  Accédez au dossier local dans lequel les packages compressés sont stockés, puis cliquez sur **enregistrer**.

    Ce processus crée une copie locale du package. 

4. Si vous obtenez une erreur de téléchargement, essayez un site miroir différent.

5. Une fois que l’archive de package a été téléchargé, vous pouvez installer le package, ou copier le package compressé vers un serveur qui n’a pas accès à internet.

> [!TIP]
> Si par inadvertance, vous installez le package au lieu de télécharger les fichiers binaires, une copie du fichier ZIP téléchargé est également enregistrée sur votre ordinateur. Surveiller les messages d’état que le package est installé pour déterminer l’emplacement du fichier. Vous pouvez copier ce fichier sur le serveur qui n’a pas accès à internet.
> 
> Toutefois, lorsque vous obtenez des packages à l’aide de cette méthode, les dépendances ne sont pas inclus. 

### <a name="bkmk_packageDependencies"></a> Obtenir les packages requis

Packages R dépendent souvent plusieurs packages, certains d'entre eux peuvent être disponibles dans la bibliothèque de R par défaut utilisée par l’instance. Parfois, un package requiert une version différente d’un package dépendant qui est déjà installé.

Si vous avez besoin d’installer plusieurs packages ou souhaitez vous assurer que tous les membres de votre organisation Obtient le type de package approprié et la version, nous vous recommandons d’utiliser le [miniCRAN](https://mran.microsoft.com/package/miniCRAN) package pour analyser la chaîne de dépendance terminée. minicRAN crée un référentiel local qui peut être partagé entre plusieurs utilisateurs ou ordinateurs. Pour plus d’informations, consultez [créer un référentiel de package local à l’aide de miniCRAN](create-a-local-package-repository-using-minicran.md).


### <a name="know-which-library-you-are-installing-to-and-which-packages-are-already-installed"></a>Connaître la bibliothèque dans laquelle vous effectuez l’installation et lesquelles packages sont déjà installés.

Si vous avez modifié précédemment l’environnement R sur l’ordinateur, avant d’installer quoi que ce soit, prenez un moment, puis vérifiez que la variable d’environnement R `.libPath` utilise simplement un chemin d’accès.

Ce chemin d’accès doit pointer vers le dossier R_SERVICES pour l’instance. Pour plus d’informations, notamment la façon de déterminer les packages qui sont déjà installés, consultez [packages R sont installés avec SQL Server](installing-and-managing-r-packages.md).

### <a name="side-by-side-installation-with-standalone-r-or-python-servers"></a>Installation côte à côte avec Standalone R ou les serveurs de Python

Si vous avez installé SQL Server 2017 Microsoft Machine Learning Server (autonome) ou SQL Server 2016 R Server (autonome) en plus de l’analytique dans base de données (SQL Server 2017 Machine Learning Services et SQL Server 2016 R Services), votre ordinateur a Séparez les installations de R pour chacune, avec des doublons de tous les outils R et les bibliothèques.

Les packages qui sont installés à la bibliothèque R_SERVER sont utilisés uniquement par un serveur autonome et ne sont pas accessibles par une instance de SQL Server (de-de base de données). Utilisez toujours le `R_SERVICES` bibliothèque lors de l’installation des packages que vous souhaitez utiliser dans la base de données sur SQL Server.
