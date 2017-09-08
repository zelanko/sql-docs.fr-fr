---
title: Gestion des packages R pour SQL Server | Documents Microsoft
ms.custom: 
ms.date: 08/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 98c14b05-750e-44f9-8531-1298bf51e8d2
caps.latest.revision: 7
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f19982251b629d12215595685c0633b4c6b61c98
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="r-package-management-for-sql-server"></a>Gestion des packages R pour SQL Server

Cette rubrique décrit les fonctionnalités de gestion de package que vous pouvez utiliser pour gérer les packages R qui sont exécutent sur une instance de SQL Server.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 d’apprentissage automatique Services

## <a name="package-management-using-t-sql"></a>Gestion des packages à l’aide de T-SQL

Vous pouvez continuer à installer des packages R en tant qu’administrateur sur l’ordinateur, si vous disposez des privilèges, et si vous êtes la seule personne à l’aide du serveur pour les tâches d’apprentissage machine.

Toutefois, si vous avez besoin de partager les packages avec d’autres personnes, ou si avez besoin de plusieurs personnes exécuter les tâches de machine learning sur le serveur, il est plus efficace de définir une bibliothèque de package partagé. SQL Server CE prend en charge par le biais des rôles de base de données.

L’administrateur de base de données est responsable de la configuration des rôles et l’ajout d’utilisateurs aux rôles. Via des rôles, l’administrateur de base de données peut contrôler qui a l’autorisation d’ajouter ou supprimer des packages R dans l’environnement SQL Server et que vous pouvez auditer l’installation du package.

### <a name="database-roles-for-package-management"></a>Rôles de base de données pour la gestion des packages

Les nouveaux rôles de base de données suivantes prennent en charge l’installation en toute sécurité et gestion des packages R dans SQL Server :

- `rpkgs-users`: Permet aux utilisateurs d’utiliser tous les packages partagés qui ont été installées par les membres de le `rpkgs-shared` rôle.

- `rpkgs-private`: Fournit l’accès aux packages partagés avec les mêmes autorisations que le `rpkgs-users` rôle. Les membres de ce rôle peuvent également installer, supprimer et utiliser des packages à étendue privée.

-  `rpkgs-shared`: Fournit les mêmes autorisations que le `rpkgs-private` rôle. Les utilisateurs membres de ce rôle peuvent également installer ou supprimer des packages partagés.

- `db_owner`: A les mêmes autorisations que le `rpkgs-shared` rôle. Peut également accorder aux utilisateurs le droit d’installer ou de supprimer des packages partagés et privés.

### <a name="creating-an-external-package-library-using-t-sql"></a>Création d’une bibliothèque de lot externe à l’aide de T-SQL

En outre, SQL Server 2017 prend en charge l’instruction T-SQL, **créer une bibliothèque externe**pour prendre en charge la gestion par l’administrateur de base de données de bibliothèques externes. Actuellement, vous pouvez utiliser cette instruction pour créer des bibliothèques Windows pour R. plus prise en charge est prévue dans l’avenir pour les packages de Python et pour les paquets écrits pour l’exécution sur d’autres plateformes, tels que Linux.

Pour plus d’informations, consultez [créer une bibliothèque externe](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="package-management-using-r"></a>Gestion des packages à l’aide de R

Le **RevoScaleR** package inclut désormais des fonctions pour prendre en charge d’installation plus facile et la gestion des packages R. Ces nouvelles fonctions, combinées avec des rôles de base de données pour la gestion des packages, prend en charge ces scénarios :

- Le chercheur de données peut installer des packages R nécessaires sur SQL Server sans avoir un accès administratif à l’ordinateur SQL Server.
- Les packages sont installés sur une base de chaque base de données, et lorsque la base de données est déplacée, les packages se déplacent avec lui.
- Il est plus facile de partager les packages avec d’autres utilisateurs. Si vous configurez un référentiel de packages local, chaque chercheur de données peut utiliser le référentiel pour installer des packages à sa propre base de données.
- L’administrateur de base de données sans devoir apprendre à exécuter des commandes R et n’a pas besoin de suivre les dépendances de package complexe.
- L’administrateur peut utiliser des rôles de base de données familière pour contrôler les utilisateurs de SQL Server sont autorisés à installer, désinstaller ou utiliser des packages.

### <a name="r-package-management-functions"></a>Fonctions de gestion de package de R

Les fonctions de gestion de package suivantes sont fournies dans RevoScaleR, pour l’installation et la suppression de packages dans un contexte de calcul spécifié :

+ [rxInstalledPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstalledpackages): rechercher des informations sur les packages installés dans le contexte de calcul spécifiée.

+ [rxInstallPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstallpackages): installer des packages dans un contexte de calcul, à partir d’un référentiel spécifié, ou en lisant enregistrés localement compressés des packages.

+ [rxRemovePackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxremovepackages): supprimer les packages installés à partir d’un contexte de calcul.

+ [rxFindPackage](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxfindpackage): obtenir le chemin d’accès pour un ou plusieurs packages dans le contexte de calcul spécifiée.

+ [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages): copie d’une package de bibliothèque entre le système de fichiers et les bases de données dans les contextes de calcul spécifiée.

+ [rxSqlLibPaths](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqllibpaths): obtenir le chemin de recherche pour les arborescences de bibliothèque pour les packages lors de l’exécution à l’intérieur de SQL Server.

Ces packages sont également inclus par défaut dans SQL Server 2017. Vous pouvez ajouter les packages à une instance de SQL Server 2016 si vous mettez à niveau l’instance à utiliser au moins Microsoft R 9.0.1. Pour plus d’informations, consultez [à l’aide de SqlBindR.exe pour mettre à niveau R](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

Pour plus d’informations sur ces fonctions, consultez les pages de référence de fonction RevoScaleR : (https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)

## <a name="how-package-management-works"></a>Fonctionne de la gestion des packages

Si vous êtes autorisé à installer des packages, vous exécutez l’une des fonctions de la gestion des packages à partir de votre code R et vous spécifiez le contexte de calcul où les packages doivent être ajoutés ou supprimés. Le contexte de calcul peut être votre ordinateur local ou une base de données sur l’instance de SQL Server. Si l’appel pour installer des packages est exécuté sur SQL Server, vos informations d’identification déterminent si l’opération peut être effectuée sur le serveur. Les fonctions d’installation de package vérifient les dépendances et garantissent que tous les packages associés peuvent être installés sur SQL Server, tout comme l’installation des packages R dans le contexte de calcul local. La fonction qui désinstalle les packages calcule également les dépendances et garantit la suppression des packages qui ne sont plus utilisés par d’autres packages sur SQL Server, afin de libérer les ressources.

Chaque chercheur de données peut installer des packages privés qui ne sont pas visibles à d’autres personnes, création d’un bac à sable privé pour les packages R. Packages peuvent être limités à une base de données et chaque utilisateur obtienne un bac à sable package isolé dans chaque base de données, il est plus facile à installer des versions différentes du même package R.

Si vous migrez votre base de données vers un nouveau serveur, vous pouvez utiliser la fonction de synchronisation de package pour lecture d’une liste de tous vos packages et de les installer dans une base de données sur le nouveau serveur.

> [!NOTE]
> 
> Les fonctions R pour la gestion des packages sont fournies à partir de Microsoft R Server 9.0.1. Si vous ne trouvez pas les fonctions dans RevoScaleR, vous devrez probablement mettre à niveau vers la version la plus récente.

### <a name="bkmk_scope"></a>Étendue des packages par rôle

Les nouvelles fonctions de la gestion des packages fournissent deux étendues pour l’installation et l’utilisation des packages dans SQL Server sur une base de données :

- **Étendue partagée**

  *Étendue partagée* signifie que les utilisateurs qui ont reçu l’autorisation pour le rôle de portée partagée (`rpkgs-shared`) peuvent installer et désinstaller des packages à une base de données spécifiée. Un package installé dans une bibliothèque à étendue partagée peut être utilisé par d’autres utilisateurs de la base de données sur SQL Server, à condition que ces utilisateurs soient autorisés à utiliser les packages R installés.

- **Étendue privée**

  *Portée privée* signifie que les utilisateurs qui disposent de l’appartenance au rôle de portée privée (`rpkgs-private`) peut installer ou désinstaller des packages dans un emplacement de bibliothèque privée défini par l’utilisateur. Ainsi, les packages installés dans l’étendue privée sont utilisables uniquement par l’utilisateur qui les a installés. Autrement dit, un utilisateur sur SQL Server ne peut pas utiliser des packages privés qui ont été installés par un autre utilisateur.

Ces modèles d’étendue *partagée* et *privée* peuvent être combinés pour développer des systèmes sécurisés personnalisés pour le déploiement et la gestion des packages sur SQL Server.

Par exemple, à l’aide d’une étendue partagée, le responsable d’un groupe de spécialistes des données peut être autorisé à installer des packages, lesquels peuvent ensuite être utilisés par tous les autres utilisateurs ou spécialistes des données dans la même instance de SQL Server.

Un autre scénario peut nécessiter un meilleur isolement entre les utilisateurs ou l’utilisation de différentes versions des packages. Dans ce cas, l’étendue privée peut être utilisée pour accorder des autorisations individuelles aux spécialistes des données qui seraient responsables de l’installation et de l’utilisation uniquement des packages dont ils ont besoin. Les packages étant installés utilisateur par utilisateur, les packages installés par un utilisateur n’affectent pas le travail des autres utilisateurs qui utilisent la même base de données SQL Server.

### <a name="synchronizing-r-package-libraries"></a>Synchronisation des bibliothèques de package de R

La version 2.0 du CTP de SQL Server 2017 (et la version d’avril 2017 de Microsoft R Server) inclut les nouvelles fonctions R pour *synchronisation packages*.

Synchronisation des package signifie que le moteur de base de données effectue le suivi des packages qui sont utilisés par un propriétaire spécifique et un groupe et peuvent d’écrire ces packages au système de fichiers si nécessaire. Vous pouvez utiliser la synchronisation de package dans ces scénarios :

+ Vous voulez déplacer des packages R entre des instances de SQL Server
+ Vous devez réinstaller les packages d’un utilisateur spécifique ou un groupe après la restauration d’une base de données

Pour plus d’informations, consultez [rxSyncPackages](../r/package-install-uninstall-and-sync.md).

## <a name="examples"></a>Exemples

Ces exemples illustrent l’utilisation de base pour les fonctions de gestion de package. Pour exécuter ces commandes requiert que vous êtes autorisé à exécuter des commandes R sur l’instance.

+ Lors de l’exécution à partir d’un terminal de R à distance, vous créez un objet de contexte de calcul en spécifiant une instance de SQL Server et exécutez sur les fonctions, en passant le contexte de calcul en tant qu’argument.

+ Pour exécuter des fonctions de gestion de package à partir d’une procédure stockée, vous devez les encapsuler dans un appel à `sp_execute_external_script`.

### <a name="package-scoping"></a>Portée de package

Cet exemple vérifie pour les packages qui ont été installés sur l’instance `myServer`, dans la base de données `TestDB`. Gestion des packages est étendue à une base de données spécifique et un utilisateur. Si l’utilisateur n’est pas spécifié, l’utilisateur qui exécute l’appel de contexte de calcul est supposé. Pour plus d’informations, consultez [Scoping de packages par rôle](#bkmk_scope).

```R
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;");
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerCompute);
```

### <a name="get-package-location-on-a-remote-sql-server-compute-context"></a>Obtenir l’emplacement du package sur un contexte de calcul de SQL Server à distance

Cet exemple obtient le chemin du package **RevoScaleR** sur le contexte de calcul *sqlServer*.

  ```R
  sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerL)
  ```

### <a name="get-locations-for-multiple-packages"></a>Obtenir les emplacements de plusieurs packages

L’exemple suivant obtient les chemins des packages **RevoScaleR** et **lattice** sur le contexte de calcul *sqlServer*. Pour obtenir plus d’informations sur plusieurs packages, passez un vecteur de chaînes contenant les noms de package.

  ```R
  packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlServer)
  ```

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

### <a name="get-package-versions-on-a-remote-compute-context"></a>Obtenir des versions de package sur un contexte de calcul à distance

Exécutez cette commande à partir d’une console R pour obtenir le numéro de build et les numéros de version des packages installés dans le contexte de calcul, *sqlServer*.

  ```R
  sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

### <a name="install-a-package-on-sql-server"></a>Installer un package sur SQL Server

Cet exemple installe le package **ggplot2** et ses dépendances dans le contexte de calcul *sqlServer*.

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

### <a name="package-synchronization"></a>Synchronisation de package

L’exemple suivant synchronise les packages installés dans le système de fichiers avec la liste des packages gérés dans la base de données. Si certains packages sont manquants, ils sont installés dans le système de fichiers.

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

## <a name="next-steps"></a>Étapes suivantes

[Comment activer ou désactiver la gestion des packages R](../r/r-package-how-to-enable-or-disable.md)

