---
title: Synchronisation de package R du système de fichiers - SQL Server Machine Learning Services
description: Mettre à jour des bibliothèques R sur SQL Server avec des versions plus récentes installées sur le système de fichiers.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5b7141e1fe6256c7a7e21056d82f2d8fc4ad4faf
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53431816"
---
# <a name="r-package-synchronization-for-sql-server"></a>Synchronisation de package R pour SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

La version de RevoScaleR inclus dans SQL Server 2017 inclut la possibilité de synchroniser les collections de packages R entre le système de fichiers et l’instance et de base de données où les packages sont utilisés.

Cette fonctionnalité a été fournie pour le rendre plus facile de sauvegarder des regroupements de package R associés aux bases de données SQL Server. À l’aide de cette fonctionnalité, un administrateur peut restaurer non seulement la base de données, mais les packages R qui ont été utilisés par les scientifiques des données dans cette base de données.

Cet article décrit la fonctionnalité de synchronisation de package et comment utiliser le [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) (fonction) pour effectuer les tâches suivantes :

+ Synchroniser une liste des packages pour une base de données SQL Server entière

+ Synchroniser les packages utilisés par un utilisateur individuel ou par un groupe d’utilisateurs

+ Si un utilisateur accède à un autre serveur SQL Server, vous pouvez effectuer une sauvegarde de base de données de l’utilisateur et restaurez-la sur le nouveau serveur, et les packages pour l’utilisateur seront installés sur le système de fichiers sur le nouveau serveur, comme requis par R.

Par exemple, vous pouvez utiliser la synchronisation de package dans ces scénarios :

+ L’administrateur a restauré une instance de SQL Server vers un nouvel ordinateur et invitent les utilisateurs à se connecter à partir de leurs clients R et exécutez `rxSyncPackages` pour actualiser et restaurer les packages.

+ Vous pensez que d’un package R sur le système de fichiers est endommagé. vous exécutez `rxSyncPackages` sur le serveur SQL Server.

## <a name="requirements"></a>Configuration requise

Avant que vous pouvez utiliser la synchronisation de package, vous devez disposer de la version appropriée de Microsoft R serveur ou Machine Learning. Cette fonctionnalité est fournie dans Microsoft R version 9.1.0). ou version ultérieure. 

Vous devez également activer le [fonctionnalité de gestion des packages](r-package-how-to-enable-or-disable.md) sur le serveur.

### <a name="determine-whether-your-server-supports-package-management"></a>Déterminer si votre serveur prend en charge la gestion des packages

Cette fonctionnalité est disponible dans SQL Server 2017 CTP 2 ou version ultérieure.

Vous pouvez ajouter cette fonctionnalité à une instance de SQL Server 2016 en mettant à niveau l’instance pour utiliser la dernière version de Microsoft R. Pour plus d’informations, consultez [utiliser SqlBindR.exe pour mettre à niveau de SQL Server R Services](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="enable-the-package-management-feature"></a>Activer la fonctionnalité de gestion de package

Pour utiliser la synchronisation de package nécessite que la nouvelle fonctionnalité de gestion de package sur l’instance de SQL Server et sur les bases de données individuelles. Pour plus d’informations, consultez [activer ou désactiver la gestion des packages pour SQL Server](r-package-how-to-enable-or-disable.md).

1. L’administrateur du serveur Active la fonctionnalité pour l’instance de SQL Server.
2. Pour chaque base de données, l’administrateur accorde aux utilisateurs individuels la possibilité d’installer ou partagez des packages R, à l’aide de rôles de base de données.

Dans ce cas, vous pouvez utiliser les fonctions RevoScaleR, tel que [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) à installer des packages dans une base de données.  Informations sur les utilisateurs et les packages qu’ils peuvent utiliser sont stockées dans l’instance de SQL Server. 

Chaque fois que vous ajoutez un nouveau package en utilisant les fonctions de gestion de package, les deux enregistrements dans SQL Server et le système de fichiers sont mis à jour. Ces informations peuvent être utilisées pour restaurer les informations de package pour la base de données entière.

### <a name="permissions"></a>Autorisations

+ La personne qui exécute la fonction de synchronisation de package doit être un principal de sécurité sur l’instance de SQL Server et de la base de données qui se trouvent les packages.

+ L’appelant de la fonction doit être un membre d’un de ces rôles de gestion de package : **rpkgs-shared** ou **rpkgs-private**.

+ Pour synchroniser les packages marqués comme **partagé**, la personne qui exécute la fonction doit être membre du **rpkgs-shared** rôle et les packages sont déplacés doivent avoir été installé à un partage bibliothèque de l’étendue.

+ Pour synchroniser les packages marqués comme **privé**, soit le propriétaire du package ou l’administrateur doit exécuter la fonction et les packages doivent être privées.

+ Pour synchroniser des packages pour le compte d’autres utilisateurs, le propriétaire doit être b membre de la **db_owner** rôle de base de données.

## <a name="how-package-synchronization-works"></a>Comment fonctionne la synchronisation de package

Pour utiliser la synchronisation de package, appelez [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages), qui est une nouvelle fonction dans [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler). 

Pour chaque appel à `rxSyncPackages`, vous devez spécifier une instance de SQL Server et la base de données. Puis, répertorier les packages à synchroniser, ou spécifier la portée du package.

1. Créer le contexte de calcul de SQL Server à l’aide de la `RxInSqlServer` (fonction). Si vous ne spécifiez pas un contexte de calcul, le contexte de calcul actuel est utilisé.

2. Indiquez le nom d’une base de données sur l’instance dans le contexte de calcul spécifié. Les packages sont synchronisés par base de données.

3. Spécifier les packages à synchroniser à l’aide de l’argument d’étendue.

    Si vous utilisez **privé** étendue, uniquement les packages détenus par le propriétaire spécifié sont synchronisés. Si vous spécifiez **partagé** étendue, tous les packages non privée dans la base de données sont synchronisées. 
    
    Si vous exécutez la fonction sans spécifier soit **privé** ou **partagé** étendue, tous les packages sont synchronisés.

4. Si la commande réussite, les packages existants dans le système de fichiers sont ajoutés à la base de données, avec la portée spécifiée et le propriétaire.

    Si le système de fichiers est endommagé, les packages sont restaurés en fonction de la liste maintenue dans la base de données.

    Si la fonctionnalité de gestion de package n’est pas disponible sur la base de données cible, une erreur est générée : « La fonctionnalité de gestion de package n’est pas activée sur le serveur SQL Server ou la version est trop ancienne »

### <a name="example-1-synchronize-all-package-by-database"></a>Exemple 1. Synchroniser tous les packages par base de données

Cet exemple obtient de nouveaux packages à partir du système de fichiers local et installe les packages dans la base de données [TestDB]. Aucun propriétaire n’étant spécifique, la liste inclut tous les packages qui ont été installés pour les étendues privés et partagés.

```R
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

### <a name="example-2-restrict-synchronized-packages-by-scope"></a>Exemple 2. Restreindre les packages synchronisés par étendue

Les exemples suivants synchroniser uniquement les packages dans la portée spécifiée.

```R
#Shared scope
rxSyncPackages(computeContext=computeContext, scope="shared", verbose=TRUE)

#Private scope
rxSyncPackages(computeContext=computeContext, scope="private", verbose=TRUE)
```

### <a name="example-3-restrict-synchronized-packages-by-owner"></a>Exemple 3. Restreindre les packages synchronisés par propriétaire

L’exemple suivant montre comment synchroniser uniquement les packages qui ont été installés pour un utilisateur spécifique. Dans cet exemple, l’utilisateur est identifié par le nom de connexion SQL, *user1*.

```R
rxSyncPackages(computeContext=computeContext, scope="private", owner = "user1", verbose=TRUE))
```

## <a name="related-resources"></a>Ressources connexes

[Gestion des packages R pour SQL Server](install-additional-r-packages-on-sql-server.md)
