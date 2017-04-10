---
title: "Gestion des packages R pour SQL Server R Services | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 98c14b05-750e-44f9-8531-1298bf51e8d2
caps.latest.revision: 7
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 7
---
# Gestion des packages R pour SQL Server R Services
Pour simplifier la gestion des packages R qui s’exécutent sur une instance de SQL Server, le package **RevoScaleR** inclut désormais des fonctions permettant de prendre en charge l’installation et la gestion des packages R. 

Cette nouvelle fonctionnalité prend en charge plusieurs scénarios :

- Les spécialistes des données peuvent installer un package R nécessaire sur SQL Server sans disposer d’un accès administratif à l’ordinateur SQL Server. Les packages sont installés individuellement sur chaque base de données.
- Il est très facile de partager les packages avec d’autres utilisateurs. Il vous suffit d’établir un dépôt de packages local et de faire en sorte que chaque spécialiste des données installe les packages sur chaque base de données.
- L’administrateur de base de données n’a pas besoin d’apprendre à exécuter des commandes R, ni de comprendre les dépendances des packages. Il utilise des rôles de base de données pour déterminer quels utilisateurs SQL Server sont autorisés à installer, désinstaller ou utiliser des packages.
 
**Fonctionnement**

* L’administrateur de base de données est responsable de la configuration des rôles et de l’ajout des utilisateurs aux rôles, afin de contrôler qui a l’autorisation d’ajouter ou de supprimer des packages R dans l’environnement SQL Server.
* Si vous êtes autorisé à installer des packages, vous exécutez l’une des fonctions de la gestion des packages à partir de votre code R et vous spécifiez le contexte de calcul où les packages doivent être ajoutés ou supprimés. Le contexte de calcul peut être votre ordinateur local ou une base de données sur l’instance de SQL Server. 
* Si l’appel pour installer des packages est exécuté sur SQL Server, vos informations d’identification déterminent si l’opération peut être effectuée sur le serveur. 
- Les fonctions d’installation de package vérifient les dépendances et garantissent que tous les packages associés peuvent être installés sur SQL Server, tout comme l’installation des packages R dans le contexte de calcul local.
- La fonction qui désinstalle les packages calcule également les dépendances et garantit la suppression des packages qui ne sont plus utilisés par d’autres packages sur SQL Server, afin de libérer les ressources.
- Chaque spécialiste des données peut installer des packages privés qui ne sont visibles par personne d’autre, ce qui lui procure un bac à sable (sandbox) isolé pour travailler avec ses propres packages R.
-  Comme les packages peuvent avoir pour étendue une base de données et que chaque utilisateur obtient un bac à sable (sandbox) de packages isolé dans chaque base de données, il est plus facile d’installer et d’utiliser différentes versions du même package R. 

> [!NOTE]
> Pour l’instant, cette fonctionnalité est publiée pour être utilisée uniquement avec [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]. 

## <a name="database-roles-and-database-scoping"></a>Rôles de base de données et étendue de base de données

Les nouvelles fonctions de la gestion des packages fournissent deux étendues pour l’installation et l’utilisation des packages dans SQL Server sur une base de données :

- **Étendue partagée**

  *Étendue partagée* signifie que les utilisateurs qui disposent de l’autorisation pour le rôle à étendue partagée (**rpkgs-shared**) peuvent installer et désinstaller des packages dans une base de données spécifiée. Un package installé dans une bibliothèque à étendue partagée peut être utilisé par d’autres utilisateurs de la base de données sur SQL Server, à condition que ces utilisateurs soient autorisés à utiliser les packages R installés. 

- **Étendue privée** 

  *Étendue privée* signifie que les utilisateurs qui sont membres du rôle à étendue privée (**rpkgs-private**) peuvent installer ou désinstaller des packages dans un emplacement de bibliothèque privé défini pour chaque utilisateur. Ainsi, les packages installés dans l’étendue privée sont utilisables uniquement par l’utilisateur qui les a installés. Autrement dit, un utilisateur sur SQL Server ne peut pas utiliser des packages privés qui ont été installés par un autre utilisateur. 

Ces modèles d’étendue *partagée* et *privée* peuvent être combinés pour développer des systèmes sécurisés personnalisés pour le déploiement et la gestion des packages sur SQL Server. 

Par exemple, à l’aide d’une étendue partagée, le responsable d’un groupe de spécialistes des données peut être autorisé à installer des packages, lesquels peuvent ensuite être utilisés par tous les autres utilisateurs ou spécialistes des données dans la même instance de SQL Server. 

Un autre scénario peut nécessiter un meilleur isolement entre les utilisateurs ou l’utilisation de différentes versions des packages. Dans ce cas, l’étendue privée peut être utilisée pour accorder des autorisations individuelles aux spécialistes des données qui seraient responsables de l’installation et de l’utilisation uniquement des packages dont ils ont besoin. Les packages étant installés utilisateur par utilisateur, les packages installés par un utilisateur n’affectent pas le travail des autres utilisateurs qui utilisent la même base de données SQL Server. 

### <a name="database-roles-for-package-management"></a>Rôles de base de données pour la gestion des packages

Les nouveaux rôles de base de données suivants prennent en charge l’installation et la gestion sécurisées des packages pour SQL R Services : 

- **rpkgs-users** Permet aux utilisateurs d’employer tous les packages partagés qui ont été installés par des membres du rôle **rpkgs-shared**.

- **rpkgs-private**Fournit l’accès aux packages partagés avec les mêmes autorisations que le rôle **rpkgs-users**. Les membres de ce rôle peuvent également installer, supprimer et utiliser des packages à étendue privée.

-  **rpkgs-shared** Fournit les mêmes autorisations que le rôle **rpkgs-private**. Les utilisateurs membres de ce rôle peuvent également installer ou supprimer des packages partagés. 
 
- **db_owner** A les mêmes autorisations que le rôle **rpkgs-shared**. Peut également accorder aux utilisateurs le droit d’installer ou de supprimer des packages partagés et privés.



## <a name="new-package-management-functions"></a>Nouvelles fonctions de la gestion des packages


+ `rxInstalledPackages` : Recherchez des informations sur les packages installés dans le contexte de calcul spécifié.

+ `rxInstallPackages` : Installez des packages dans un contexte de calcul à partir d’un dépôt spécifié ou en lisant des packages compressés enregistrés localement.

+ `rxRemovePackages` : Supprimez des packages installés à partir d’un contexte de calcul.

+ `rxFindPackage` : Obtenez le chemin d’un ou plusieurs packages dans le contexte de calcul spécifié.

+ `rxSqlLibPaths` : Obtenez le chemin de recherche des arborescences de bibliothèque pour des packages pendant l’exécution dans SQL Server.

## <a name="examples"></a>Exemples

### <a name="get-package-location-on-sql-server-compute-context"></a>Obtenir l’emplacement d’un package sur le contexte de calcul SQL Server

Cet exemple obtient le chemin du package **RevoScaleR** sur le contexte de calcul *sqlServer*.

  ```R
  sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlServerL)
  ```
  
  ### <a name="get-locations-for-multiple-packages"></a>Obtenir les emplacements de plusieurs packages

L’exemple suivant obtient les chemins des packages **RevoScaleR** et **lattice** sur le contexte de calcul *sqlServer*. Lors de la recherche d’informations sur plusieurs packages, passez un vecteur de chaînes contenant les noms des packages.

  ```R
  packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlServer)
  ```



### <a name="list-packages-in-specified-compute-context"></a>Énumérer les packages dans le contexte de calcul spécifié

Cet exemple énumère et affiche dans la console tous les packages installés dans le contexte de calcul *sqlServer*.

  ```R
  myPackages <- rxInstalledPackages(computeContext = sqlServer) 
  myPackages
  ```

### <a name="get-package-versions"></a>Obtenir des versions de packages

Cet exemple obtient le numéro de build et les numéros de version d’un package installé sur le contexte de calcul *sqlServer*.

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

## <a name="see-also"></a>Voir aussi

[Guide pratique pour activer ou désactiver la gestion des packages R](../../advanced-analytics/r-services/how-to-enable-or-disable-r-package-management.md)