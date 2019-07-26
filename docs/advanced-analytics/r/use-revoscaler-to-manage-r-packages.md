---
title: Comment utiliser les fonctions RevoScaleR pour rechercher ou installer des packages R
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: e5cd2f55559671b1e3f3d2004c4865b8bac8aa42
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469888"
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>Comment utiliser les fonctions RevoScaleR pour rechercher ou installer des packages R sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

RevoScaleR 9.0.1 et versions ultérieures incluent des fonctions de gestion des packages R SQL Server un contexte de calcul. Ces fonctions peuvent être utilisées par des non-administrateurs distants pour installer des packages sur SQL Server sans accès direct au serveur.

SQL Server 2017 Machine Learning Services contient déjà une version plus récente de RevoScaleR. SQL Server 2016 R services les clients doivent effectuer une [mise à niveau de composant](../install/upgrade-r-and-python.md) pour obtenir les fonctions de gestion des packages RevoScaleR. Pour obtenir des instructions sur la récupération de la version et du contenu d’un package, consultez [obtenir des informations](../package-management/installed-package-information.md)sur le package.

## <a name="revoscaler-functions-for-package-management"></a>Fonctions RevoScaleR pour la gestion des packages

Le tableau suivant décrit les fonctions utilisées pour l’installation et la gestion des packages R.

| Fonction | Description |
|----------|-------------|
| [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) | Déterminez le chemin d’accès de la bibliothèque d’instances sur la SQL Server distante. |
| [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage) | Obtient le chemin d’accès d’un ou plusieurs packages sur le SQL Server distant. |
| [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) | Appelez cette fonction à partir d’un client R distant pour installer des packages dans un contexte de calcul SQL Server, soit à partir d’un référentiel spécifié, soit en lisant des packages Zippés enregistrés localement. Cette fonction vérifie les dépendances et s’assure que tous les packages associés peuvent être installés sur SQL Server, tout comme l’installation du package R dans le contexte de calcul local. Pour utiliser cette option, vous devez avoir activé la gestion des packages sur le serveur et la base de données. Les environnements client et serveur doivent avoir la même version de RevoScaleR. |
| [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages) | Obtient la liste des packages installés dans le contexte de calcul spécifié. |
| [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) | Copier les informations relatives à une bibliothèque de packages entre le système de fichiers et la base de données, pour le contexte de calcul spécifié. |
| [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages) | Supprime les packages d’un contexte de calcul spécifié. Il calcule également les dépendances et garantit que les packages qui ne sont plus utilisés par d’autres packages sur SQL Server sont supprimés, pour libérer des ressources. |

## <a name="prerequisites"></a>Prérequis

+ [Activer la gestion des packages R distants sur SQL Server](r-package-how-to-enable-or-disable.md)

+ Les versions de RevoScaleR doivent être identiques sur les environnements client et serveur. Pour plus d’informations, consultez [obtenir des informations sur le package](../package-management/installed-package-information.md).

+ Autorisation de se connecter au serveur et à une base de données, et d’exécuter des commandes R. Vous devez être membre d’un rôle de base de données qui vous permet d’installer des packages sur l’instance et la base de données spécifiées.

+ Les packages dans l' **étendue partagée** peuvent être installés par des utilisateurs `rpkgs-shared` appartenant au rôle dans une base de données spécifiée. Tous les utilisateurs de ce rôle peuvent désinstaller des packages partagés.

+ Les packages dans l' **étendue privée** peuvent être installés par tout utilisateur appartenant `rpkgs-private` au rôle dans une base de données. Toutefois, les utilisateurs peuvent voir et désinstaller uniquement leurs propres packages.

+ Les propriétaires de bases de données peuvent utiliser des packages partagés ou privés.

## <a name="client-connections"></a>Connexions client

Une station de travail cliente peut être [Microsoft R client](https://docs.microsoft.com/machine-learning-server/r-client/install-on-windows) ou [Microsoft machine learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) (les scientifiques de données utilisent souvent l’édition Developer gratuite) sur le même réseau.

Lors de l’appel de fonctions de gestion de package à partir d’un client R distant, vous devez d’abord créer un objet de contexte de calcul à l’aide de la fonction [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) . Par la suite, pour chaque fonction de gestion de package que vous utilisez, transmettez le contexte de calcul en tant qu’argument.

L’identité de l’utilisateur est généralement spécifiée lors de la définition du contexte de calcul. Si vous ne spécifiez pas de nom d’utilisateur et de mot de passe lors de la création du contexte de calcul, l’identité de l’utilisateur qui exécute le code R est utilisée.

1. À partir d’une ligne de commande R, définissez une chaîne de connexion à l’instance et à la base de données.
2. Utilisez le constructeur [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) pour définir un contexte de calcul SQL Server à l’aide de la chaîne de connexion.

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```
3. Créez une liste des packages que vous souhaitez installer et enregistrez la liste dans une variable de chaîne.

    ```R
    packageList <- c("e1071", "mice")
    ```

4. Appelez [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) et transmettez le contexte de calcul et la variable de chaîne contenant les noms des packages.

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    Si des packages dépendants sont requis, ils sont également installés, en supposant qu’une connexion Internet est disponible sur le client.
    
    Les packages sont installés à l’aide des informations d’identification de l’utilisateur qui effectue la connexion, dans l’étendue par défaut pour cet utilisateur.

## <a name="call-package-management-functions-in-stored-procedures"></a>Appeler des fonctions de gestion des packages dans des procédures stockées

Vous pouvez exécuter des fonctions de gestion `sp_execute_external_script`des packages dans. Dans ce cas, la fonction est exécutée à l’aide du contexte de sécurité de l’appelant de la procédure stockée.

## <a name="examples"></a>Exemples

Cette section fournit des exemples d’utilisation de ces fonctions à partir d’un client distant lors de la connexion à une instance ou une base de données SQL Server en tant que contexte de calcul.

Pour tous les exemples, vous devez fournir une chaîne de connexion ou un contexte de calcul qui requiert une chaîne de connexion. Cet exemple fournit un moyen de créer un contexte de calcul pour SQL Server:

```R
instance_name <- "computer-name/instance-name";
database_name <- "TestDB";
sqlWait= TRUE;
sqlConsoleOutput <- TRUE;
connString <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
sqlcc <- RxInSqlServer(connectionString = connString, wait = sqlWait, consoleOutput = sqlConsoleOutput, numTasks = 4);
```

Selon l’emplacement du serveur et le modèle de sécurité, vous devrez peut-être fournir un domaine et une spécification de sous-réseau dans la chaîne de connexion, ou utiliser une connexion SQL. Exemple :

```R
connStr <- "Driver=SQL Server;Server=myserver.financeweb.contoso.com;Database=Finance;Uid=RUser1;Pwd=RUserPassword"
```

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>Obtenir le chemin d’accès au package sur un contexte de calcul SQL Server distant

Cet exemple obtient le chemin d’accès pour le package **RevoScaleR** dans le contexte de `sqlcc`calcul,.

```R
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlcc)
print(sqlPackagePaths)
```

**Résultats**

«C:/Program Files/Microsoft SQL Server/MSSQL14. MSSQLSERVER/R_SERVICES/Library/RevoScaleR»

> [!TIP]
> Si vous avez activé l’option pour afficher la sortie de la console SQL, vous pouvez obtenir des messages d’état de la `print` fonction qui précède l’instruction. Une fois que vous avez terminé de tester votre `consoleOutput` code, affectez à la valeur false dans le constructeur de contexte de calcul pour éliminer les messages.

### <a name="get-locations-for-multiple-packages"></a>Obtenir les emplacements de plusieurs packages

L’exemple suivant obtient les chemins d’accès pour les packages **RevoScaleR** et **treillis** , sur le contexte de `sqlcc`calcul,. Pour obtenir des informations sur plusieurs packages, transmettez un vecteur de chaîne contenant les noms des packages.

```R
packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlcc)
print(packagePaths)
```

### <a name="get-package-versions-on-a-remote-compute-context"></a>Obtenir des versions de package sur un contexte de calcul distant

Exécutez cette commande à partir d’une console R pour obtenir le numéro de build et les numéros de version des packages installés sur le contexte de calcul *sqlServer*.

```R
sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

**Résultats**

```text
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/RevoScaleR"

[2] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/lattice"
```

### <a name="install-a-package-on-sql-server"></a>Installer un package sur SQL Server

Cet exemple installe le package de **prévision** et ses dépendances dans le contexte de calcul.

  ```R
  pkgs <- c("forecast")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="remove-a-package-from-sql-server"></a>Supprimer un package de SQL Server

Cet exemple supprime le package de **prévision** et ses dépendances du contexte de calcul.

  ```R
  pkgs <- c("forecast")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="synchronize-packages-between-database-and-file-system"></a>Synchroniser les packages entre la base de données et le système de fichiers

L’exemple suivant vérifie la base de données **TestDB**et détermine si tous les packages sont installés dans le système de fichiers. Si certains packages sont manquants, ils sont installés dans le système de fichiers.

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

La synchronisation des packages fonctionne pour chaque base de données et par utilisateur. Pour plus d’informations, consultez [synchronisation des packages R pour SQL Server](../r/package-install-uninstall-and-sync.md).

### <a name="use-a-stored-procedure-to-list-packages-in-sql-server"></a>Utilisez une procédure stockée pour répertorier les packages dans SQL Server

Exécutez cette commande à partir de Management Studio ou d’un autre outil qui prend en charge T-SQL, pour obtenir la liste des packages installés `rxInstalledPackages` sur l’instance actuelle, à l’aide de dans une procédure stockée.

```sql
EXEC sp_execute_external_script 
  @language=N'R', 
  @script=N'
    myPackages <- rxInstalledPackages();
    OutputDataSet <- as.data.frame(myPackages);
    '
```

La `rxSqlLibPaths` fonction peut être utilisée pour déterminer la bibliothèque active utilisée par SQL Server machine learning services. Ce script peut retourner uniquement le chemin d’accès de la bibliothèque pour le serveur actuel. 

```sql
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

## <a name="see-also"></a>Voir aussi

+ [Activer la gestion de packages R à distance](r-package-how-to-enable-or-disable.md)
+ [Synchroniser des packages R](package-install-uninstall-and-sync.md)
+ [Conseils pour l’installation de packages R](packages-installed-in-user-libraries.md)
+ [Packages par défaut](../package-management/default-packages.md)