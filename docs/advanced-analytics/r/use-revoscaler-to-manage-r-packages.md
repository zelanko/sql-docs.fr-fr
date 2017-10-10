---
title: Comment utiliser les fonctions RevoScaleR pour rechercher ou installer R packages SQL Server | Documents Microsoft
ms.custom: 
ms.date: 09/29/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 
caps.latest.revision: 1
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 59f13d7c65818b49025f8578068b348c650e98c2
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>Comment utiliser les fonctions RevoScaleR pour rechercher ou installer des packages R sur SQL Server

Version de Microsoft R Server 9.0.1 a introduit de nouvelles fonctions RevoScaleR que prise en charge de l’utilisation d’installé les packages dans un contexte de calcul de SQL Server. Ces nouvelles fonctions facilitent un chercheur de données exécuter le code R dans SQL Server sans un accès direct au serveur.

Chaque chercheur de données peut installer des packages privés qui ne sont pas visibles à d’autres personnes. Packages peuvent être limités à une base de données et chaque utilisateur obtienne un bac à sable package isolé dans chaque base de données, il est plus facile à installer des versions différentes du même package R.

Si vous migrez votre base de données vers un nouveau serveur, vous pouvez également utiliser la fonction de synchronisation de package pour lecture d’une liste de tous vos packages et de les installer dans une base de données sur le nouveau serveur.

Cet article décrit ces fonctions et fournit des exemples d’utilisation de la fonction.

## <a name="requirements"></a>Spécifications

+ Pour exécuter ces fonctions, vous devez disposer de l’autorisation d’exécuter des commandes R sur l’instance.

+ Si vous ne spécifiez pas un nom d’utilisateur et un mot de passe lorsque vous créez le contexte de calcul, l’identité de l’utilisateur qui exécute le code R est utilisée.

+ Lorsque vous utilisez ces fonctions à partir d’un client distant de R, vous devez créer un objet de contexte de calcul en premier lieu, à l’aide de la fonction RxInSQLServer. Par la suite, pour chaque fonction de gestion de package que vous utilisez, transmettre le contexte de calcul en tant qu’argument.

+ Il est possible d’exécuter des fonctions de gestion de package à l’aide de `sp_execute_external_script`. Lorsque vous procédez ainsi, la fonction est exécutée en utilisant le contexte de sécurité de l’appelant de la procédure stockée.

## <a name="list-of-package-management-functions"></a>Liste des fonctions de gestion de package

Les fonctions de gestion de package suivantes sont fournies dans RevoScaleR, pour l’installation et la suppression de packages dans un contexte de calcul spécifié :

+ [rxInstalledPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstalledpackages): rechercher des informations sur les packages installés dans le contexte de calcul spécifiée.

+ [rxInstallPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstallpackages): installer des packages dans un contexte de calcul, à partir d’un référentiel spécifié, ou en lisant enregistrés localement compressés des packages.

+ [rxRemovePackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxremovepackages): supprimer les packages installés à partir d’un contexte de calcul.

+ [rxFindPackage](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxfindpackage): obtenir le chemin d’accès pour un ou plusieurs packages dans le contexte de calcul spécifiée.

+ [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages): copie d’une package de bibliothèque entre le système de fichiers et les bases de données dans les contextes de calcul spécifiée.

+ [rxSqlLibPaths](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqllibpaths): obtenir le chemin de recherche pour les arborescences de bibliothèque pour les packages lors de l’exécution à l’intérieur de SQL Server.

Ces packages sont inclus par défaut dans SQL Server 2017. Pour plus d’informations sur ces fonctions, consultez les pages de référence de fonction RevoScaleR : (https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)

> [!NOTE]
> Des fonctions de gestion des packages R sont disponibles à compter de Microsoft R Server 9.0.1. Si vous ne trouvez pas les fonctions dans RevoScaleR, vous devrez probablement mettre à niveau vers la version la plus récente. 
## <a name="examples"></a>Exemples

Cette section contient des exemples montrant comment utiliser les fonctions de gestion de package avec une instance de SQL Server ou de la base de données. 

+ Les fonctions d’installation de package vérifient les dépendances et garantissent que tous les packages associés peuvent être installés sur SQL Server, tout comme l’installation des packages R dans le contexte de calcul local.

+ La fonction qui _désinstalle_ packages également calcule les dépendances et garantit que les packages qui ne sont plus utilisés par d’autres packages sur SQL Server sont supprimés pour libérer des ressources.

+ Vous pouvez utiliser une combinaison d’utilisateurs et de portée pour rechercher les packages ou d’ajouter des packages à une base de données :

    + Dans les packages **étendue partagée** peuvent être installées par les utilisateurs appartenant à la `rpkgs-shared` rôle dans une base de données spécifiée. Tous les utilisateurs de ce rôle peuvent désinstaller des packages partagés.
    + Dans les packages **portée privée** peut être installé par tout utilisateur appartenant à la `rpkgs-private` rôle dans une base de données. Toutefois, les utilisateurs peuvent voir et désinstaller uniquement leurs propres packages.
    + Les propriétaires de base de données peuvent fonctionner avec des packages partagés ou privés.

**À partir du code R**

Si vous êtes autorisé à installer des packages, exécutez l’une du package de fonctions de gestion à partir de votre client de R et spécifier le contexte de calcul où les packages doivent être ajoutés ou supprimés.  Le contexte de calcul peut être votre ordinateur local ou une base de données sur l’instance de SQL Server. Vos informations d’identification déterminent si l’opération peut être effectuée sur le serveur.

**À partir de Transact-SQL**

Pour exécuter des fonctions de gestion de package à partir d’une procédure stockée, les encapsuler dans un appel à `sp_execute_external_script`.

### <a name="get-list-of-packages-in-a-sql-server-compute-context"></a>Obtenir la liste des packages dans un contexte de calcul de SQL Server

Cet exemple vérifie pour les packages qui ont été installés sur l’instance `myServer`, dans la base de données `TestDB`. Gestion des packages est étendue à une base de données spécifique et un utilisateur. Si l’utilisateur n’est pas spécifié, l’utilisateur qui exécute l’appel de contexte de calcul est supposé. Pour plus d’informations, consultez [Scoping de packages par rôle](#bkmk_scope).

```R
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;");
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerCompute);
```

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>Obtenir le chemin d’accès du package sur un contexte de calcul de SQL Server à distance

Cet exemple obtient le chemin du package **RevoScaleR** sur le contexte de calcul *sqlServer*.

  ```R
  sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerL)
  ```

### <a name="get-locations-for-multiple-packages"></a>Obtenir les emplacements de plusieurs packages

L’exemple suivant obtient les chemins des packages **RevoScaleR** et **lattice** sur le contexte de calcul *sqlServer*. Pour obtenir plus d’informations sur plusieurs packages, passez un vecteur de chaînes contenant les noms de package.

  ```R
  packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlServer)
  ```


### <a name="get-package-versions-on-a-remote-compute-context"></a>Obtenir des versions de package sur un contexte de calcul à distance

Exécutez cette commande à partir d’une console R pour obtenir le numéro de build et les numéros de version des packages installés dans le contexte de calcul, *sqlServer*.

  ```R
  sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

### <a name="install-a-package-on-sql-server"></a>Installer un package sur SQL Server

Cet exemple installe le **prévision** package et ses dépendances dans le contexte de calcul, *sqlServer*.

  ```R
  pkgs <- c("ggplot2")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlServer)
  ```

### <a name="remove-a-package-from-sql-server"></a>Supprimer un package de SQL Server

Cet exemple supprime le package **ggplot2** et ses dépendances du contexte de calcul *sqlServer*.

  ```R
  pkgs <- c("ggplot2")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlServer)
  ```

### <a name="synchronize-packages-between-database-and-file-system"></a>Synchroniser des packages entre le système de fichiers et de la base de données

L’exemple suivant vérifie la base de données **TestDB**et détermine si tous les packages sont installés dans le système de fichiers. Si certains packages sont manquants, ils sont installés dans le système de fichiers.

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

Fonctionnement de la synchronisation du package sur un par base de données et par utilisateur. Pour plus d’informations, consultez [synchronisation des package R pour SQL Server](../r/package-install-uninstall-and-sync.md).

### <a name="use-a-stored-procedure-to-list-packages-in-sql-server"></a>Utiliser une procédure stockée pour répertorier les packages dans SQL Server

Exécutez cette commande à partir de Management Studio ou un autre outil qui prend en charge T-SQL pour obtenir la liste des packages installés sur l’instance actuelle, à l’aide de `rxInstalledPackages` dans une procédure stockée.

```SQL
EXEC sp_execute_external_script 
  @language=N'R', 
  @script=N'
    myPackages <- rxInstalledPackages();
    OutputDataSet <- as.data.frame(myPackages);
    '
```

Le `rxSqlLibPaths` fonction peut être utilisée pour déterminer la bibliothèque active utilisée par les Services de SQL Server Machine Learning. Ce script peut retourner uniquement le chemin de bibliothèque pour le serveur actif. 

```SQL
declare @instance_name nvarchar(100) = @@SERVERNAME, @database_name nvarchar(128) = db_name();
exec sp_execute_external_script 
  @language = N'R',
  @script = N'
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    .libPaths(rxSqlLibPaths(connStr));
    print(.libPaths());
  ', 
  @input_data_1 = N'', 
  @params = N'@instance_name nvarchar(100), @database_name nvarchar(128)',
  @instance_name = @instance_name, 
  @database_name = @database_name;
```

