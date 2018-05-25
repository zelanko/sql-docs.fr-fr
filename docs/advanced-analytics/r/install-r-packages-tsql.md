---
title: T-SQL (créer une bibliothèque externe) permet d’installer des packages R sur SQL Server Machine Learning Services | Documents Microsoft
description: Ajouter de nouveaux packages R à SQL Server 2017 Machine Learning Services (de-de base de données)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/20/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: bbc1adf4868cbfbd02afe5cae3a38fd6223e2d4d
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2018
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server-2017-machine-learning-services"></a>T-SQL (créer une bibliothèque externe) permet d’installer des packages R sur SQL Server 2017 Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit comment installer de nouveaux packages R à une instance de SQL Server où l’apprentissage automatique est activé. Il existe plusieurs approches sélectionnables. Cette approche convient le mieux pour les administrateurs de serveur qui ne sont pas familiarisés avec R.

**S’applique à :**  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Le [créer une bibliothèque externe](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) instruction permet d’ajouter un package ou un ensemble de packages à une base de données spécifique ou à une instance sans exécuter R ou directement le code Python. Toutefois, cette méthode requiert la préparation du package et les autorisations de base de données supplémentaires.

+ Tous les packages doivent être disponibles en tant qu’un fichier zip local, plutôt que téléchargement à la demande à partir d’internet.

+ Toutes les dépendances doivent être identifiés par le nom et la version et inclus dans le fichier zip. L’instruction échoue si les packages nécessaires ne sont pas disponibles, notamment les dépendances de package en aval. 

+ Vous devez disposer des autorisations nécessaires sur la base de données. Pour plus d’informations, consultez [créer une bibliothèque externe](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="download-packages-in-archive-format"></a>Télécharger les packages au format d’archive

Si vous installez un package unique, téléchargez le package au format compressé.

Si le package requiert tous les autres packages, vous devez vérifier que les packages nécessaires sont disponibles. Vous pouvez utiliser miniCRAN pour analyser le package cible et d’identifier toutes ses dépendances. Nous vous recommandons d’utiliser [ **miniCRAN** ](create-a-local-package-repository-using-minicran.md) ou [ **igraph** ](http://igraph.org/r/) pour l’analyse des dépendances de packages. L’installation d’une version incorrecte du package ou de la dépendance de package peut se produire l’instruction échoue. 

## <a name="copy-the-file-to-a-local-folder"></a>Copiez le fichier dans un dossier local

Copiez le fichier compressé qui contient tous les packages vers un dossier local sur le serveur. Si vous n’avez pas de l’accès au système de fichiers sur le serveur, vous pouvez également passer un package complet en tant que variable, à l’aide d’un format binaire. Pour plus d’informations, consultez [créer une bibliothèque externe](../../t-sql/statements/create-external-library-transact-sql.md).

## <a name="run-the-statement-to-upload-packages"></a>Exécutez l’instruction pour télécharger des packages

Ouvrir un **requête** fenêtre, à l’aide d’un compte avec des privilèges d’administrateur.

Exécutez l’instruction T-SQL `CREATE EXTERNAL LIBRARY` pour télécharger de la collection de package compressé pour la base de données.

    For example, the following statement names as the package source a miniCRAN repository containing the **randomForest** package, together with its dependencies. 

    ```R
    CREATE EXTERNAL LIBRARY randomForest
    FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
    WITH (LANGUAGE = 'R');
    ```

    You cannot use an arbitrary name; the external library name must have the same name that you expect to use when loading or calling the package.

## <a name="verify-package-installation"></a>Vérifier l’installation du package

Si la bibliothèque est créée avec succès, vous pouvez exécuter le package dans SQL Server, en l’appelant à l’intérieur d’une procédure stockée.
    
    ```SQL
    EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    library(randomForest)'
    ```

