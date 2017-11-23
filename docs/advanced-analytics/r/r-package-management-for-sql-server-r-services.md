---
title: Gestion des packages R pour SQL Server | Documents Microsoft
ms.custom: 
ms.date: 10/09/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 98c14b05-750e-44f9-8531-1298bf51e8d2
caps.latest.revision: "7"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: d53965dd5e931eb4290031ed2023cdb78ee74283
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="r-package-management-for-sql-server"></a>Gestion des packages R pour SQL Server

Cet article décrit les fonctionnalités pour la gestion des packages R dans SQL Server 2017 et SQL Server 2016.

+ Modifications dans les méthodes d’installation du package R entre 2016 et 2017
+ Méthodes recommandées pour la gestion des packages R
+ Nouveaux rôles de base de données pour la gestion des packages dans SQL Server 2017
+ Nouvelle instruction T-SQL pour la gestion des packages dans SQL Server 2017

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 d’apprentissage automatique Services

## <a name="differences-in-package-management-between-sql-server-2016-and-sql-server-2017"></a>Différences de gestion des packages SQL Server 2016 et SQL Server 2017

Dans **SQL Server 2017**, vous pouvez activer la gestion des packages au niveau de l’instance et gérer les autorisations utilisateur pour ajouter ou utiliser des packages au niveau de la base de données.

Cela nécessite que l’administrateur de base de données activer la fonctionnalité de gestion de package en exécutant un script qui crée les objets de base de données nécessaires. Pour plus d’informations, consultez [comment activer la gestion des packages R](r-package-how-to-enable-or-disable.md).

Dans **SQL Server 2016**, un administrateur doit installer des packages R dans la bibliothèque R associée à l’instance. Tous les utilisateurs dans l’instance en cours d’exécution du code R utilisent ces packages. Code R en cours d’exécution dans SQL server ne peut pas utiliser les packages installés dans les bibliothèques de l’utilisateur. Toutefois, l’administrateur peut accorder des utilisateurs individuels à la capacité d’exécuter des scripts R dans une base de données spécifique.

**Résumé des avantages et des différences**

+ Si vous utilisez une Machine Learning Services dans SQL Server 2017, vous pouvez gérer et installer des packages R à l’aide de la méthode traditionnelle, basée sur les outils R, ou en utilisant les nouveaux rôles de base de données et les instructions T-SQL.

+ Nous vous recommandons de que la dernière méthode, car elle fournit un contrôle plus affiné par les administrateurs, couplée avec davantage de liberté pour les utilisateurs. Par exemple, les utilisateurs peuvent installer leurs propres packages, soit à l’aide d’une procédure stockée ou via le code R et des packages de partage avec d’autres utilisateurs. 

    Packages peuvent être limités à une base de données, et chaque utilisateur obtienne un bac à sable package isolé, il est plus facile à installer des versions différentes du même package R. Vous pouvez également facilement copier ou déplacer des utilisateurs et leurs packages entre bases de données. 

+ Utilisation de la fonctionnalité de gestion de package dans SQL Server ainsi que les opérations de sauvegarde et de restauration est beaucoup plus facile. Lorsque vous migrez votre base de données vers un nouveau serveur, vous pouvez utiliser la fonction de synchronisation de package pour lecture d’une liste de tous vos packages et de les installer dans une base de données sur le nouveau serveur.

+ Il peut s’avérer plus pratique d’installer des packages R en tant qu’administrateur sur l’ordinateur, à l’aide des outils R traditionnels, si vous êtes la seule personne à l’aide du serveur pour les tâches d’apprentissage machine.

+ Si vous utilisez SQL Server 2016 R Services, vous devez continuer à installer des packages R utilisées par l’instance à l’aide des outils R > Veillez à utiliser la bibliothèque R associée à l’instance.

Les sections suivantes fournissent plus de détails sur la gestion des packages est effectuée à l’aide de ces deux options.

## <a name="r-package-management-using-t-sql"></a>Gestion des packages R à l’aide de T-SQL

SQL Server 2017 inclut de nouvelles instructions T-SQL qui donnent l’administrateur de mieux contrôler les packages R au niveau de la base de données. En même temps, l’administrateur peut donner aux utilisateurs la possibilité d’installer les packages, ils ont besoin et les partagent avec d’autres.

Si vous devez partager les packages avec d’autres, ou si plusieurs personnes doivent exécuter les tâches de machine learning sur le serveur, nous vous recommandons d’activer la gestion des packages, affecter des utilisateurs aux rôles de base de données et télécharger des packages afin que les utilisateurs peuvent les partager.

Gestion des packages dans SQL Server 2017 s’appuie sur ces nouveaux objets de base de données et des fonctionnalités :

+ Nouveaux rôles de base de données, pour la gestion d’utilisation et accès au package
+ Portée de package distinct partagés et des packages privés
+ Instruction de créer une bibliothèque externe, pour télécharger les nouvelles bibliothèques de code dans le serveur
+ Contexte de calcul de nouvelles fonctions R dans RevoScaleR, pour prendre en charge l’installation des packages dans SQL Server
+ Synchronisation de package, pour garantir une sauvegarde et restauration des packages

### <a name="database-roles-for-package-management"></a>Rôles de base de données pour la gestion des packages

L’administrateur de base de données doit créer les rôles utilisés pour la gestion de package en exécutant un script comme décrit ici : [activer ou désactiver la gestion des packages](r-package-how-to-enable-or-disable.md).

Après avoir exécuté ce script, vous devez voir les nouveaux rôles de base de données suivantes :

+ `rpkgs-users`: Les membres de ce rôle peuvent utiliser n’importe quel package partagé qui a été installé par un autre `rpkgs-shared` membre de rôle.

+ `rpkgs-private`: Les membres de ce rôle ont accès aux packages partagés, avec les mêmes autorisations que les membres de le `rpkgs-users` rôle. Membres de ce rôle peuvent également installer, supprimer et utiliser des packages en privé étendues.

+ `rpkgs-shared`: Les membres de ce rôle ont les mêmes autorisations que les membres de le `rpkgs-private` rôle. En outre, les membres de ce rôle peuvent installer ou supprimer des packages partagés.

+ `db_owner`: Les membres de ce rôle ont les mêmes autorisations que les membres de le `rpkgs-shared` rôle. En outre, les membres de ce rôle peuvent **accorder** autres utilisateurs la possibilité d’installer ou supprimer les deux partagée et les packages privés.

L’administrateur ajoute les utilisateurs aux rôles sur une base par base de données, pour contrôler la capacité de l’utilisateur à installer des packages.

### <a name="package-scope"></a>Portée de package

Les nouvelles fonctionnalités de gestion de package distinguent les packages en ils sont privés, ou peuvent être partagés par plusieurs utilisateurs.

+ **Étendue partagée**

    *Étendue partagée* signifie que les utilisateurs qui ont reçu l’autorisation pour le rôle de portée partagée (`rpkgs-shared`) peuvent installer et désinstaller des packages à une base de données spécifiée. Un package installé dans une bibliothèque à étendue partagée peut être utilisé par d’autres utilisateurs de la base de données sur SQL Server, à condition que ces utilisateurs soient autorisés à utiliser les packages R installés.

+ **Étendue privée**

    *Portée privée* signifie que les utilisateurs qui disposent de l’appartenance au rôle de portée privée (`rpkgs-private`) peut installer ou désinstaller des packages dans un emplacement de bibliothèque privée défini par l’utilisateur. Ainsi, les packages installés dans l’étendue privée sont utilisables uniquement par l’utilisateur qui les a installés. Autrement dit, un utilisateur sur SQL Server ne peut pas utiliser des packages privés qui ont été installés par un autre utilisateur.

Ces modèles d’étendue *partagée* et *privée* peuvent être combinés pour développer des systèmes sécurisés personnalisés pour le déploiement et la gestion des packages sur SQL Server.

Par exemple, à l’aide d’une étendue partagée, le responsable d’un groupe de spécialistes des données peut être autorisé à installer des packages, lesquels peuvent ensuite être utilisés par tous les autres utilisateurs ou spécialistes des données dans la même instance de SQL Server.

Un autre scénario peut nécessiter un meilleur isolement entre les utilisateurs ou l’utilisation de différentes versions des packages. Dans ce cas, l’étendue privée peut être utilisée pour accorder des autorisations individuelles aux spécialistes des données qui seraient responsables de l’installation et de l’utilisation uniquement des packages dont ils ont besoin. Les packages étant installés utilisateur par utilisateur, les packages installés par un utilisateur n’affectent pas le travail des autres utilisateurs qui utilisent la même base de données SQL Server.

### <a name="create-external-library"></a>CRÉER UNE BIBLIOTHÈQUE EXTERNE

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

Pour voir des exemples d’installation à l’aide de R et T-SQL, consultez [installer des packages supplémentaires sur SQL Server](install-additional-r-packages-on-sql-server.md).

### <a name="new-r-functions-for-package-installation"></a>Nouvelles fonctions R pour l’installation du package

Une fois que les rôles de base de données pour la gestion des packages ont été activées, les utilisateurs peuvent également utiliser des fonctions nouvelles dans [ **RevoScaleR** ](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) à installer des packages sur l’instance spécifiée en tant que le contexte de calcul de SQL Server.

+ Le chercheur de données peut installer des packages R nécessaires sur SQL Server sans avoir un accès direct à l’ordinateur SQL Server.

+ Un utilisateur peut installer un package et le partager avec d’autres, en installant le package avec la portée partagée. Ensuite, les utilisateurs autorisés de la même base de données SQL Server peuvent accéder au package.

+ Les utilisateurs peuvent installer des packages privés qui ne sont pas visibles à d’autres personnes, de création d’un bac à sable privé pour les packages R.

Les fonctions de gestion de package suivantes sont fournies dans RevoScaleR, pour l’installation et la suppression de packages dans un contexte de calcul spécifié :

-   [rxInstalledPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstalledpackages): rechercher des informations sur les packages installés dans le contexte de calcul spécifiée.

-   [rxInstallPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstallpackages): installer des packages dans un contexte de calcul, à partir d’un référentiel spécifié, ou en lisant enregistrés localement compressés des packages.

-   [rxRemovePackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxremovepackages): supprimer les packages installés à partir d’un contexte de calcul.

-   [rxFindPackage](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxfindpackage): obtenir le chemin d’accès pour un ou plusieurs packages dans le contexte de calcul spécifiée.

-   [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages): copie d’une package de bibliothèque entre le système de fichiers et les bases de données dans les contextes de calcul spécifiée.

-   [rxSqlLibPaths](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqllibpaths): obtenir le chemin de recherche pour les arborescences de bibliothèque pour les packages lors de l’exécution à l’intérieur de SQL Server.

Pour utiliser ces fonctions, connectez-vous à une instance de SQL Server sur lequel vous disposez des autorisations nécessaires, à l’aide d’un contexte de calcul de SQL Server. Lorsque vous vous connectez, vos informations d’identification déterminent si l’opération peut être effectuée sur le serveur.

Les fonctions d’installation de package vérifient les dépendances et garantissent que tous les packages associés peuvent être installés sur SQL Server, tout comme l’installation des packages R dans le contexte de calcul local. La fonction qui désinstalle les packages calcule également les dépendances et garantit la suppression des packages qui ne sont plus utilisés par d’autres packages sur SQL Server, afin de libérer les ressources.

> [!NOTE]
> 
> Ces nouvelles fonctions sont incluses par défaut dans SQL Server 2017. Vous pouvez mettre à jour votre version de RevoScaleR pour obtenir ces fonctions en mettant à niveau l’instance pour utiliser une version ultérieure de Microsoft R Server, telles que Microsoft R Server 9.0.1.
> 
> Pour plus d’informations, consultez [à l’aide de SqlBindR.exe à upgradeR](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="synchronization-of-r-package-libraries"></a>Synchronisation des bibliothèques de package de R

La version 2.0 du CTP de SQL Server 2017 (et la version d’avril 2017 de Microsoft R Server) inclut les nouvelles fonctions R pour *synchronisation packages*.

Synchronisation des package signifie que le moteur de base de données effectue le suivi des packages qui sont utilisés par un propriétaire spécifique et un groupe et peuvent d’écrire ces packages au système de fichiers si nécessaire. Vous pouvez utiliser la synchronisation de package dans ces scénarios :

+ Vous voulez déplacer des packages R entre des instances de SQL Server.
+ Vous devez réinstaller les packages d’un utilisateur spécifique ou un groupe après la restauration d’une base de données.

Pour plus d’informations sur la façon d’activer et utiliser cette fonctionnalité, consultez [synchronisation des package R pour SQL Server](package-install-uninstall-and-sync.md).

## <a name="r-package-management-using-traditional-r-tools"></a>Gestion des packages R à l’aide des outils traditionnels R

La méthode traditionnelle de la gestion des packages R sur une instance consiste à installer et la liste des packages à l’aide des commandes et outils R. 

+ Cette option peut être la seule option si vous utilisez le des premières versions de SQL Server 2016.  
+ Cette option peut également être pratique si vous êtes le seul utilisateur de packages R et avez un accès administratif au serveur.
+ Pour faciliter la gestion des versions de package de R, vous pouvez utiliser [miniCRAN](create-a-local-package-repository-using-minicran.md) pour créer un référentiel local et de les partager entre les instances.

Pour plus d’informations, consultez les articles suivants :

+ [Installer des packages R supplémentaires sur SQL Server](install-additional-r-packages-on-sql-server.md)
+ [Identifier les packages installés sur SQL Server](determine-which-packages-are-installed-on-sql-server.md)

Pour SQL Server 2017, nous vous recommandons d’utiliser créer une bibliothèque externe et les rôles de base de données fournit pour gérer les utilisateurs et leurs packages R.

## <a name="next-steps"></a>Étapes suivantes

[Comment activer ou désactiver la gestion des packages R](../r/r-package-how-to-enable-or-disable.md)
