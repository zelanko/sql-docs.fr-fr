---
title: Synchronisation des package R pour SQL Server | Documents Microsoft
ms.custom: 
ms.date: 10/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: ed7dbf99b0f492b5ca8879bb67a7256fdfae3306
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---

# <a name="r-package-synchronization-for-sql-server"></a>Synchronisation des package R pour SQL Server

SQL Server 2017 inclut la possibilité de synchroniser les collections de packages R entre le système de fichiers et l’instance et de base de données où les packages sont utilisés.
Cette fonctionnalité a été fournie pour le rendre plus facile de sauvegarder des regroupements de package de R associés aux bases de données SQL Server. À l’aide de cette fonctionnalité, un administrateur peut le restaurer non seulement de la base de données, mais tous les packages R qui ont été utilisés par les spécialistes de données dans cette base de données.

Cette rubrique décrit la fonctionnalité de synchronisation de package et comment utiliser le [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages) (fonction) pour effectuer les tâches suivantes :

+ Synchroniser une liste des packages pour un ensemble de base de données SQL Server

+ Synchroniser les packages utilisés par un utilisateur individuel, ou par un groupe d’utilisateurs

+ Si un utilisateur se déplace vers un autre serveur SQL Server, vous pouvez effectuer une sauvegarde de base de données de l’utilisateur et restaurez-la sur le nouveau serveur, et les packages de l’utilisateur seront installés sur le système de fichiers sur le nouveau serveur, comme requis par R.

Par exemple, vous pouvez utiliser la synchronisation de package dans ces scénarios :

+ L’administrateur a restauré une instance de SQL Server à un nouvel ordinateur et demande aux utilisateurs de se connecter à partir de leurs clients R et exécuter `rxSyncPackages` pour actualiser et restaurer les packages.

+ Vous pensez que d’un package de R sur le système de fichiers est endommagé, vous exécuter `rxSyncPackages` sur le serveur SQL Server.

## <a name="requirements"></a>Spécifications

Avant que vous pouvez utiliser la synchronisation de package, vous devez avoir la version appropriée de Microsoft R et vous avez activé la fonctionnalité de base de données associée.

### <a name="determine-whether-your-server-supports-package-management"></a>Déterminer si votre serveur prend en charge la gestion des packages

Cette fonctionnalité est disponible dans SQL Server 2017 CTP 2 ou version ultérieure.

Étant donné que cette fonctionnalité utilise les fonctions R dans Microsoft R version 9.1.0, vous pouvez ajouter cette fonctionnalité à une instance de SQL Server 2016 par la mise à niveau de l’instance pour utiliser la dernière version de Microsoft R. Pour plus d’informations, consultez [SqlBindR.exe utilisé pour mettre à niveau SQL Server R Services](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="enable-the-package-management-feature"></a>Activer la fonctionnalité de gestion de package

Pour utiliser la synchronisation de package requiert l’activation de nouvelles fonctionnalités de gestion de package sur l’instance de SQL Server et sur des bases de données utilisés pour exécuter les tâches R.

1. L’administrateur du serveur Active la fonctionnalité de l’instance de SQL Server.
2. Pour chaque base de données, l’administrateur accorde aux utilisateurs la possibilité d’installer ou de partager des packages R.

Dans ce cas, les informations sur les utilisateurs et les packages qu’ils ont installé sont stockées dans l’instance de SQL Server. Ces informations peuvent ensuite être appliquées pour mettre à jour les packages R dans le système de fichiers.

Lorsque vous ajoutez un nouveau package à l’aide des fonctions de gestion de package, les deux enregistrements dans SQL Server et le système de fichiers sont mis à jour.

> [!NOTE]
> Vous ne pouvez pas utiliser la synchronisation du package si vous avez installé les packages R la méthode traditionnelle, à l’aide des outils R pour installer des packages directement dans le système de fichiers.
### <a name="permissions"></a>Permissions

+ La personne qui exécute la fonction de synchronisation du package doit être une entité sur l’instance de SQL Server et de la base de données qui se trouvent les packages de sécurité.

+ L’appelant de la fonction doit être un membre d’un de ces rôles de gestion de package : **partagé rpkgs** ou **rpkgs-privée**.

+ Pour synchroniser les packages marqués comme **partagé**, la personne qui exécute la fonction doit être membre la **rpkgs partagé** rôle et les packages sont déplacés doivent avoir été installé dans une bibliothèque partagée étendue.

+ Pour synchroniser les packages marqués comme **privé**, soit le propriétaire du package ou l’administrateur doit exécuter la fonction et les packages doivent être privées.

+ Pour synchroniser des packages pour le compte d’autres utilisateurs, le propriétaire doit être un membre de la **db_owner** rôle de base de données.

## <a name="how-package-synchronization-works"></a>Comment fonctionne la synchronisation de package

Pour utiliser la synchronisation de package, appelez [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages), qui est une nouvelle fonction dans [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler). Vous pouvez appeler cette fonction à partir de SQL Server à l’aide de sp_execute_external_script, ou vous pouvez exécuter à partir d’un client distant de R et spécifier le contexte de calcul de SQL Server. 

Étant donné que les packages sont gérés au niveau de la base de données, pour chaque appel à `rxSyncPackages`, vous devez spécifier une instance de SQL Server et base de données, puis sur liste des packages, ou spécifier la portée de package.

1. Créer le contexte de calcul de SQL Server à l’aide de la `RxInSqlServer` (fonction). Si vous ne spécifiez pas un contexte de calcul, le contexte de calcul actuel est utilisé.

2. Indiquez le nom d’une base de données sur l’instance dans le contexte de calcul spécifiée. Les packages sont gérés par la base de données.

3. Répertorier les packages à synchroniser.

4.  Vous pouvez également utiliser le *étendue* argument afin d’indiquer si vous synchronisez des packages pour un seul utilisateur ou pour un groupe d’utilisateurs. Si vous exécutez la fonction sans spécifier soit **privé** ou **partagé** étendue, l’ensemble des packages disponibles pour toutes les étendues et les utilisateurs seront copiés.

Si la commande s’exécute correctement, les packages existants dans le système de fichiers sont ajoutés à la base de données avec l’étendue spécifiée et le propriétaire. Si le système de fichiers est endommagé, les packages sont restaurés en fonction de la liste mis à jour dans la base de données.

### <a name="example-1-synchronize-all-package-by-database"></a>Exemple 1. Synchroniser tous les packages par base de données

Cet exemple obtient tous les packages installés dans la base de données [TestDB]. Aucun propriétaire n’étant spécifique, la liste inclut tous les packages qui ont été installés pour les étendues privés et partagés.

```R
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

### <a name="example-2-restrict-synchronized-packages-by-scope"></a>Exemple 2. Limiter les packages synchronisés par l’étendue

Les exemples suivants synchroniser uniquement les packages dans l’étendue spécifiée.

```R
#Shared scope
rxSyncPackages(computeContext=computeContext, scope="shared", verbose=TRUE)

#Private scope
rxSyncPackages(computeContext=computeContext, scope="private", verbose=TRUE)
```

### <a name="example-3-restrict-synchronized-packages-by-owner"></a>Exemple 3. Limiter les packages synchronisés par propriétaire

L’exemple suivant montre comment obtenir uniquement les packages qui ont été installés pour un utilisateur spécifique. Dans cet exemple, l’utilisateur est identifié par le nom de connexion SQL, *user1*.

```R
rxSyncPackages(computeContext=computeContext, scope="private", owner = "user1", verbose=TRUE))
```

### <a name="example-4-restrict-synchronized-packages-by-owner"></a>Exemple 4. Limiter les packages synchronisés par propriétaire

L’exemple suivant synchronise les packages installés dans le système de fichiers avec la liste des packages gérés dans la base de données. Si un package est manquant, il est installé dans le système de fichiers.

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

## <a name="related-resources"></a>Ressources connexes

[Gestion des packages R pour SQL Server](r-package-management-for-sql-server-r-services.md)

