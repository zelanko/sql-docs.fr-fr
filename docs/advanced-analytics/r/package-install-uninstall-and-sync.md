---
title: "Package d’installation, la désinstallation et la synchronisation | Documents Microsoft"
ms.custom: 
ms.date: 04/12/2017
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
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 959282395d178a090a3d447769ced4dca8882f89
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---

# <a name="r-package-synchronization-for-sql-server"></a>Synchronisation des Package R pour SQL Server

SQL Server 2017 CTP 2.0 comprend une nouvelle fonction pour la synchronisation des packages R, pour prendre en charge sauvegarder et restaurer des regroupements de package de R associés aux bases de données SQL Server. Cette fonctionnalité permet de vous assurer que les ensembles complexes de packages R créés par les utilisateurs ne sont pas perdues et peuvent être facilement restaurées.  

Cette rubrique décrit ce que fait la fonctionnalité de synchronisation de package et comment utiliser le `rxSyncPackages()` (fonction) pour effectuer les tâches suivantes :

+  Synchroniser une liste des packages pour un ensemble de base de données SQL Server
+  Synchroniser les packages utilisés par un utilisateur individuel, ou par un groupe d’utilisateurs

> [!NOTE]
> Cette fonction est fournie comme une partie d’un logiciel en version préliminaire et est susceptible de changer avant la version finale.

## <a name="what-is-package-synchronization"></a>Quelle est la synchronisation du Package 

Synchronisation de package est une nouvelle fonctionnalité qui fonctionne en particulier avec SQL Server les contextes de calcul. Il est conçu pour obtenir la liste des packages R sont installés sur une base de données, pour un utilisateur particulier ou un groupe, et vous assurer que les packages répertoriés dans la correspondance de système de fichiers celles figurant dans la base de données. 

Cela est utile si vous avez besoin déplacer une base de données utilisateur et de déplacer les packages, ainsi que la base de données. Vous pouvez également utiliser la synchronisation du package lorsque vous sauvegardez et restaurez une base de données SQL Server utilisée pour les travaux R.

Synchronisation de package utilise une nouvelle fonction, `rxSyncPackages()`. Pour synchroniser la liste des packages, vous ouvrez une invite de commandes R, passez le contexte de calcul qui définit l’instance et la base de données que vous souhaitez utiliser, puis une portée de package ou un nom d’utilisateur ou de propriétaire. 

### <a name="how-packages-are-managed-in-r-and-sql-server"></a>Comment sont gérées les packages dans R et SQL Server

En règle générale, lorsque vous exécutez des scripts R à l’aide des outils R standard, les packages R sont installés sur le système de fichiers. Si plusieurs personnes utilisent les R sur le même ordinateur, il peut être le nombre de copies des packages mêmes, dans des dossiers différents ou dans des bibliothèques de l’autre utilisateur.

Toutefois, pour utiliser un package R à partir de SQL Server, le package doit être installé dans la bibliothèque R par défaut qui est associée à l’instance. Un ordinateur de serveur peut héberger plusieurs instances de SQL Server avec R activé, et dans ce cas, chaque instance peut avoir un ensemble distinct de packages R. 

L’administrateur de base de données est responsable de l’installation des packages sur l’instance. Toutefois, avec les bibliothèques de gestion de package, l’administrateur peut déléguer cette responsabilité pour les utilisateurs. 

+ Pour chaque base de données, l’administrateur peut donner aux utilisateurs la possibilité de librement installer les packages R que dont ils ont besoin. Ce mécanisme permet de s’assurer que plusieurs utilisateurs peuvent installer les différentes versions des packages R sans provoquer de conflits pour d’autres utilisateurs de l’ordinateur SQL Server. Chaque utilisateur peut installer des packages pour leur propre usage, à l’aide d’un emplacement de système de fichiers marqué comme **privé**, s’ils appartiennent au rôle de base de données **rpkgs-privée**.

+ L’administrateur peut configurer un groupe d’utilisateurs du package sur une base de données et installer des packages qui sont partagées par tous les utilisateurs dans le groupe. Les packages peuvent être partagées entre les membres du rôle de base de données **rpkgs partagé**. Ces utilisateurs peuvent également installer des packages aux emplacements de portée privée. 

### <a name="goal-of-package-synchronization"></a>Objectif de la synchronisation de package

Si une base de données sur un serveur est perdue ou doit être déplacée à l’aide de synchronisation de package, vous pouvez restaurer des ensembles de packages spécifiques à une base de données, un utilisateur ou un groupe. 

Les informations sur les utilisateurs et les packages qu’ils ont installé sont stockées dans l’instance de SQL Server et sont utilisées pour mettre à jour les packages dans le système de fichiers. Lorsque vous ajoutez un nouveau package à l’aide des fonctions de gestion de package, les deux enregistrements dans SQL Server et le système de fichiers sont mis à jour. Par conséquent, si un utilisateur se déplace vers un autre serveur SQL Server, vous pouvez effectuer une sauvegarde de base de données de travail de l’utilisateur et restaurez-la sur le nouveau serveur, et les packages de l’utilisateur seront installés sur le système de fichiers sur le nouveau serveur, comme requis par R.


### <a name="supported-versions"></a>Versions prises en charge

Cette fonction est incluse dans SQL Server 2017 CTP 2.0.

Cette fonction fait partie de Microsoft R version 9.1.0, vous pouvez ajouter cette fonctionnalité à une instance de SQL Server 2016 par la mise à niveau de l’instance pour utiliser la dernière version de Microsoft R. Pour plus d’informations, consultez [SqlBindR.exe utilisé pour mettre à niveau SQL Server R Services](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="to-synchronize-packages"></a>Pour synchroniser des Packages

Vous appelez `rxSyncPackages` après restauration d’une instance de SQL Server à un nouvel ordinateur, ou si un R le package sur le système de fichiers est considérée comme endommagée.

Si la commande s’exécute correctement, les packages existants dans le système de fichiers sont ajoutés à la base de données, la portée et le propriétaire spécifié. Si le système de fichiers est endommagé, les packages sont restred en fonction de la liste mis à jour dans la base de données.

### <a name="syntax"></a>Syntaxe
`rxSyncPackages(computeContext = rxGetOption("computeContext"),  scope = c("shared", "private"), owner = c(), verbose = getOption("verbose"))`

+ Contexte de calcul

    Définir un contexte de calcul de SQL Server, consistant en une instance et les packages de la synchronisation de la base de données. Créer le contexte de SQL Server à l’aide de la `RxInSqlServer` (fonction). Si vous ne spécifiez pas un contexte de calcul, le contexte de calcul actuel est utilisé. 

+ Portée

  Indiquer si vous installez des packages pour un seul utilisateur ou pour un groupe d’utilisateurs : 

    + **privé** l’opération inclura uniquement les packages qui ont été installés pour une utilisation par un propriétaire spécifié.
    + **partagé** l’oepration inclura tous les packages installés pour un groupe d’utilisateurs. 

  Si vous exécutez la fonction sans spécifier d’étendue privé ou partagé, les deux étendues sont appliquées. Par conséquent, l’ensemble des packages disponibles pour toutes les étendues et les utilisateurs est copié.

+ Propriétaire 

    Spécifiez le propriétaire des packages à synchroniser. Le nom du propriétaire doit être un utilisateur de base de données SQL valide. Si vous laissez vide, le nom d’utilisateur de connexion SQL spécifiée dans la connexion est utilisé.


### <a name="requirements"></a>Spécifications

+ La personne qui exécute la fonction doit être une entité de sécurité sur l’instance de SQL Server et la base de données qui se trouvent les packages et doit être un membre d’un rôle de gestion de package : **partagé rpkgs** ou **rpkgs-privée** 
  + Pour synchroniser les packages marqués comme **partagé**, la personne qui exécute la fonction doit être membre la **rpkgs partagé** rôle et les packages sont déplacés doivent avoir été installé dans une bibliothèque partagée étendue.
  + Pour synchroniser de des packages marqués comme **privé**, soit le propriétaire du package ou l’administrateur doit exécuter la fonction et les packages doivent être privées.
+ **les utilisateurs du rpkgs** -membres de ce rôle peuvent exécuter le code qui utilise des packages installés sur l’instance de SQL Server, mais ne peut pas installer ou synchroniser des packages.
+ Pour synchroniser des packages pour le compte d’autres utilisateurs, le propriétaire doit être un membre de la **db_owner** rôle de base de données.

## <a name="examples"></a>Exemples

Les exemples suivants créer une connexion à une instance spécifique de SQL Server, spécifient une base de données, puis spécifient un ensemble de packages à synchroniser. 

Lors de l’appel à `rxSyncPackages` est effectuée, le package de listes sont synchronisés entre le système de fichiers et de la base de données. 

### <a name="synchronize-all-by-database"></a>Synchroniser tous par base de données

Cet exemple obtient tous les packages installés dans la base de données [TestDB]. Aucun propriétaire n’étant spécifique, la liste inclut tous les packages qui ont été installés pour les étendues privés et partagés.

```R
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

### <a name="restrict-synchronized-packages-by-scope"></a>Limiter les packages synchronisés par l’étendue 

Le synchroniser exemples suivant uniquement les packages dans l’étendue partagé ou privé.

**Étendue partagée**

```R
rxSyncPackages(computeContext=computeContext, scope="shared", verbose=TRUE)
```

**Étendue privée**

```R
rxSyncPackages(computeContext=computeContext, scope="private", verbose=TRUE)
```

### <a name="restrict-synchronized-packages-by-owner"></a>Limiter les packages synchronisés par propriétaire 

L’exemple suivant montre comment obtenir uniquement les packages qui ont été installés pour un utilisateur spécifique. Dans cet exemple, l’utilisateur est identifié par le nom de connexion SQL, *user1*.

```R
rxSyncPackages(computeContext=computeContext, scope="private", owner = "user1", verbose=TRUE))
```

## <a name="see-also"></a>Voir aussi

[Gestion des packages R pour SQL Server](../r/r-package-management-for-sql-server-r-services.md)
