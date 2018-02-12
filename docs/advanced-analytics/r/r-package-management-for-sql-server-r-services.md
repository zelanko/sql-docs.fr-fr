---
title: Gestion des packages R pour SQL Server | Documents Microsoft
ms.custom: 
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 98c14b05-750e-44f9-8531-1298bf51e8d2
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: f40bc2a4f17914423eeea944a45c79ae3d259a76
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2018
---
# <a name="r-package-management-for-sql-server"></a>Gestion des packages R pour SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit les fonctionnalités pour la gestion des packages R dans SQL Server 2017 et dans SQL Server 2016.

+ Méthodes recommandées pour la gestion des packages R 
+ Modifications apportées à la gestion des packages entre SQL Server 2016 et 2017

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 d’apprentissage automatique Services

## <a name="recommended-methods-for-package-management"></a>Méthodes recommandées pour la gestion des packages

Dans SQL Server 2016 et SQL Server 2017, un administrateur de l’ordinateur peut installer des packages pour chaque instance où l’apprentissage a été activée. 

Les packages sont installés dans le système de fichiers à l’aide des bibliothèques de l’instance et ne peut pas être partagés entre les instances. Il s’agit actuellement de la méthode recommandée pour SQL Server 2016 et SQL Server 2017.

+ [Installer des packages R supplémentaires sur SQL Server](install-additional-r-packages-on-sql-server.md)
+ [Identifier les packages installés sur SQL Server](determine-which-packages-are-installed-on-sql-server.md)

En outre, si vous avez **dbo** l’appartenance au rôle sur une instance de SQL Server où l’apprentissage a été activée, vous pouvez installer des packages R à partir d’un client distant, à l’aide des nouvelles fonctions dans RevoScaleR.

+ [Nouvelles fonctions R pour l’installation du package](#bkmk_remoteInstall)

### <a name="installation-on-servers-with-no-internet-access"></a>Installation sur des serveurs sans accès à Internet

Pour le rendre plus facile de déterminer les versions de package de R requises et fournir toutes les dépendances de package, vous pouvez utiliser [miniCRAN](https://mran.microsoft.com/package/miniCRAN). Ce package de R prend une liste des packages de la cible et crée un référentiel local qui contient les packages de la cible, ainsi que toutes leurs dépendances, dans un format compressé. Vous pouvez ensuite qui copie sur le serveur en mode hors connexion, ou partager l’espace de stockage entre plusieurs instances.

Pour plus d’informations, consultez [créer un référentiel de package local à l’aide de miniCRAN](create-a-local-package-repository-using-minicran.md).

### <a name="python-packages"></a>Packages de Python

Installation de nouveaux packages Python suit les mêmes instructions : 

+ Passez en revue les packages Python à l’avance pour déterminer la compatibilité avec la version actuelle de Python
+ Évaluer l’adéquation du package Python pour un environnement SQL Server renforcé
+ Utilisez les outils Python pour installer des packages en tant qu’administrateur
+ Installer les packages qui s’exécutent dans le contexte uniquement dans la bibliothèque de l’instance de SQL Server. 
+ Si vous utilisez plusieurs environnements de test, production, etc., assurez-vous que la même version du package Python est installée dans la bibliothèque de l’instance.

Pour les étapes d’installation, consultez [installer de nouveaux packages Python sur SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="features-for-package-management-in-sql-server-2016-and-sql-server-2017"></a>Fonctionnalités de gestion des packages dans SQL Server 2016 et SQL Server 2017

SQL Server 2017 ajouté de nouvelles fonctionnalités pour prendre en charge de faciliter la gestion des packages R (et Python) par les administrateurs de base de données. Ces nouvelles fonctionnalités sont les suivantes :

+ La possibilité d’installer ou de gestion des bibliothèques de package à l’aide de T-SQL
+ Gestion des autorisations utilisateur au niveau de la base de données via des rôles de base de données. 

Dans les versions ultérieures, ces fonctionnalités doivent fournir la principale méthode pour la gestion des packages par les administrateurs de base de données et le rendre plus facilement les chercheurs de données installer les bibliothèques que dont ils ont besoin.

En près en même temps, Microsoft R Server et serveur de Machine Learning ajouté nouvelles fonctions R pour le rendre plus facile à installer et partager des packages dans un contexte de calcul de SQL Server. Ces fonctions fonctionnent indépendamment les fonctionnalités de SQL Server basées sur T-SQL et sont destinées à être exécuté à partir d’un client distant de R.

Cette section fournit une vue d’ensemble de ces fonctionnalités.

### <a name="bkmk_remoteInstall"></a>Nouvelles fonctions RevoScaleR pour l’installation du package 

Utilisateurs avec une version récente du serveur de R ou Machine Learning peuvent également utiliser des fonctions nouvelles dans [ **RevoScaleR** ](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) à installer des packages sur une instance spécifiée en tant que le contexte de calcul de SQL Server.

+ Le chercheur de données peut installer des packages R nécessaires sur SQL Server sans avoir un accès direct à l’ordinateur SQL Server. Toutefois, l’utilisateur doit être membre du propriétaire de la base de données (**dbo**) rôle.

+ L’utilisateur peut partager des packages avec d’autres, en installant les packages avec une portée partagée. Les utilisateurs autorisés de la même base de données SQL Server peuvent accéder au package.

+ Les utilisateurs peuvent installer des packages privés qui ne sont pas visibles à d’autres personnes, de création d’un bac à sable privé pour les packages R.

+ Synchronisation de package permet une sauvegarde et restauration des packages

#### <a name="package-installation-functions"></a>Fonctions d’installation de package

Les fonctions de gestion de package suivantes sont fournies dans RevoScaleR, pour l’installation et la suppression de packages dans un contexte de calcul spécifié :

-   [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages): rechercher des informations sur les packages installés dans le contexte de calcul spécifiée.

-   [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages): installer des packages dans un contexte de calcul, à partir d’un référentiel spécifié, ou en lisant enregistrés localement compressés des packages.

-   [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages): supprimer les packages installés à partir d’un contexte de calcul.

-   [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage): obtenir le chemin d’accès pour un ou plusieurs packages dans le contexte de calcul spécifiée.

-   [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages): copie d’une package de bibliothèque entre le système de fichiers et les bases de données dans les contextes de calcul spécifiée.

-   [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths): obtenir le chemin de recherche pour les arborescences de bibliothèque pour les packages lors de l’exécution à l’intérieur de SQL Server.

Pour utiliser ces fonctions, connectez-vous à une instance de SQL Server sur lequel vous disposez des autorisations nécessaires, à l’aide d’un contexte de calcul de SQL Server. 

> [!IMPORTANT]
> Les informations d’identification que vous utilisez dans la connexion de déterminent si l’opération peut être effectuée sur le serveur.

Ces fonctions d’installation de package, vérifiez les dépendances et vous assurer que tous les packages associés peuvent être installés dans SQL Server, tout comme l’installation du package R dans le contexte de calcul local. La fonction qui désinstalle les packages calcule également les dépendances et garantit la suppression des packages qui ne sont plus utilisés par d’autres packages sur SQL Server, afin de libérer les ressources.

Ces nouvelles fonctions sont incluses dans la version de RevoScaleR est installé dans SQL Server 2017. Vous pouvez également obtenir ces fonctions en [mise à niveau de l’instance de SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md) à utiliser une version récente de [Microsoft R Server ou serveur de Machine Learning](https://docs.microsoft.com/machine-learning-server/rebranding-microsoft-r-server). Requiert la version 9.0.1 ou version ultérieure.

#### <a name="package-synchronization-functions"></a>Empaqueter des fonctions de synchronisation

Synchronisation de package est une nouvelle fonctionnalité pour les packages R uniquement. Le moteur de base de données suit les packages qui sont utilisés par un propriétaire spécifique et un groupe et peuvent d’écrire ces packages au système de fichiers si nécessaire. En règle générale, vous utiliseriez la synchronisation de package dans ces scénarios :

+ Vous voulez déplacer des packages R entre des instances de SQL Server.
+ Vous devez réinstaller les packages d’un utilisateur spécifique ou un groupe après la restauration d’une base de données.

Pour plus d’informations sur la façon d’activer et utiliser cette fonctionnalité, consultez [synchronisation des package R pour SQL Server](package-install-uninstall-and-sync.md).

### <a name="package-management-using-t-sql"></a>Gestion des packages à l’aide de T-SQL

SQL Server 2017 ajouté de nouvelles instructions T-SQL pour accorder à l’administrateur de mieux contrôler les packages R au niveau de la base de données. L’administrateur ne doit pas avoir apprendre à utiliser R ou les outils Python, mais au lieu de cela doit être en mesure de permettre aux utilisateurs de R ou Python pour installer les packages, ils ont besoin et les partagent avec d’autres utilisateurs.

Cette fonctionnalité est destinée à faciliter la gestion de la collaboration et la version dans les environnements multi-utilisateurs : par exemple :

+ Vous souhaitez partager les packages que vous avez développés avec d’autres personnes de votre équipe.
+ Plusieurs analystes travaillent dans la même base de données et avez besoin d’utiliser des versions différentes du même package.
+ Vous voulez déplacer des packages et leurs autorisations en même temps que vous déplacez une base de données, ou lorsque vous effectuez la sauvegarde et les opérations de restauration.

Gestion des packages dans SQL Server 2017 s’appuie sur ces nouveaux objets de base de données et des fonctionnalités :

+ [Nouveaux rôles de base de données](#bkmk_roles), pour la gestion des accès de package et utiliser
+ [CRÉER une bibliothèque externe](#bkmk_createExternalLibrary) instruction, pour télécharger les bibliothèques de package vers le serveur

L’utilisation de ces fonctionnalités nécessite une préparation supplémentaire à l’instance et le niveau de la base de données : 

+  L’administrateur de base de données doit explicitement activer la fonctionnalité de gestion de package en exécutant un script qui crée les objets de base de données nécessaires. Pour plus d’informations, consultez [comment activer la gestion des packages R](r-package-how-to-enable-or-disable.md).

+ Les utilisateurs doivent être affectées aux rôles à un niveau de base de données. Ces rôles de donnent aux utilisateurs la possibilité d’installer des packages partagés ou privés.

+ Bibliothèques de package peuvent être installés à l’aide de la nouvelle instruction T-SQL, créez une bibliothèque externe. Toutefois, toutes les dépendances de package doivent être préparés à l’avance et installés dans le cadre d’un seul fichier zip.

> [!NOTE]
> Bien que les fonctionnalités décrites ici sont entièrement fonctionnelles à ce stade, les versions ultérieures contiennent des améliorations supplémentaires pour le rendre plus facile de préparer des bibliothèques de package et de gérer les dépendances. Si vous êtes familiarisé avec l’installation du package R, nous vous conseillons de continuer à utiliser les outils R pour l’instant.

#### <a name="bkmk_createExternalLibrary"></a>CRÉER UNE BIBLIOTHÈQUE EXTERNE 

Le [créer une bibliothèque externe](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) est une nouvelle instruction T-SQL introduite dans 2017 du serveur SQL pour aider l’administrateur de base de données à utiliser avec les packages sans avoir aux outils utilisateur R. 

Vous utilisez la **créer une bibliothèque externe** instruction pour charger des bibliothèques externes à une instance au format de fichier compressé. Les utilisateurs autorisés peuvent ensuite accéder aux bibliothèques et les installer pour leur propre usage.

Par exemple, vous pouvez créer plusieurs copies de votre projet R, chacun pour une autre version. Les télécharger en tant que bibliothèques distincts vous permet de préserver la confidentialité de certaines versions et partager certaines versions avec d’autres utilisateurs.

Une « bibliothèque » est en fait une collection de packages externes que vous souhaitez rendre disponibles aux utilisateurs sous un nom unique. Par exemple, vous pouvez publier les caractères suivants à SQL Server comme une bibliothèque externe :

+ Un seul package R que vous avez écrit, sans dépendances
+ Un package que vous souhaitez installer et les dépendances requises pour l’installation
+ Une collection de packages R associés à une tâche spécifique ou d’un projet, avec leurs dépendances

Le nom de la bibliothèque est de gérer le package ou une collection de packages dans SQL Server et peut être indépendant des packages qui sont installés. Toutefois, les noms de bibliothèque doivent être uniques dans une instance.

Pour utiliser cette instruction, la fonctionnalité de gestion de package doit avoir été activée sur l’instance. Pour plus d’informations, consultez [créer une bibliothèque externe](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

> [!NOTE]
> Actuellement, vous pouvez utiliser cette instruction pour créer uniquement les bibliothèques Windows pour la prise en charge de r est prévue dans l’avenir pour les packages de Python et des packages qui s’exécutent sur d’autres plateformes, tels que Linux.

Une fois que la bibliothèque externe ont été téléchargée vers le serveur, vous devez l’installer à la bibliothèque de package de R associée à l’instance. Il existe plusieurs manières de procéder :

+ Exécutez la commande R standard `install.packages` dans sp_execute_external_script. Veillez à vous connecter à l’aide d’un compte qui dispose des autorisations nécessaires pour installer des packages.

+ Connectez-vous à SQL Server à partir d’un client distant de R et exécutez [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) dans le contexte de calcul de SQL Server. Là encore, vous devez disposer des autorisations pour installer les packages dans une étendue privée ou partagée pour ce faire.

Pour garantir que toutes les dépendances de package sont fournies, nous vous recommandons d’utiliser [miniCRAN](create-a-local-package-repository-using-minicran.md) pour créer un référentiel local. Vous pouvez ensuite utiliser ce fichier compressé pour installer le package cible et ses dépendances.

#### <a name="bkmk_roles"></a>Rôles de base de données pour la gestion des packages 

Les nouveaux rôles fournis dans SQL Server pour la gestion des packages ne sont pas inclus par défaut, même dans les cas où l’apprentissage a été installé et activé. Vous devez ajouter les rôles en exécutant un script comme décrit ici : [activer ou désactiver la gestion des packages](r-package-how-to-enable-or-disable.md).

Après avoir exécuté ce script, vous devez voir les nouveaux rôles de base de données suivantes :

+ `rpkgs-users`: Les membres de ce rôle peuvent utiliser n’importe quel package partagé qui a été installé par un autre `rpkgs-shared` membre de rôle.

+ `rpkgs-private`: Les membres de ce rôle ont accès aux packages partagés, avec les mêmes autorisations que les membres de le `rpkgs-users` rôle. Membres de ce rôle peuvent également installer, supprimer et utiliser des packages en privé étendues.

+ `rpkgs-shared`: Les membres de ce rôle ont les mêmes autorisations que les membres de le `rpkgs-private` rôle. En outre, les membres de ce rôle peuvent installer ou supprimer des packages partagés.

+ `db_owner`: Les membres de ce rôle ont les mêmes autorisations que les membres de le `rpkgs-shared` rôle. En outre, les membres de ce rôle peuvent **accorder** autres utilisateurs la possibilité d’installer ou supprimer les deux partagée et les packages privés.

L’administrateur peut ajouter des utilisateurs aux rôles sur une base par base de données.



## <a name="next-steps"></a>Étapes suivantes

[Gestion des packages pour l’apprentissage de SQL Server](r-package-management-for-sql-server-r-services.md)
