---
title: Gérer et intégrer des charges de travail Machine Learning
description: En tant que SQL Server DBA, passez en revue les tâches d’administration pour le déploiement d’un sous-système Machine Learning R et Python sur une instance du moteur de base de données.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2677b48daf253a85f2b74078bdad7de65e37d572
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715048"
---
# <a name="manage-and-integrate-machine-learning-workloads-on-sql-server"></a>Gérer et intégrer des charges de travail de Machine Learning sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article est destiné aux administrateurs de base de données SQL Server chargés de déployer une infrastructure de science des données efficace sur une ressource de serveur prenant en charge plusieurs charges de travail. Il encadre l’espace de problème administratif en rapport avec la gestion de l’exécution de code R et Python sur SQL Server. 

## <a name="what-is-feature-integration"></a>Qu’est-ce que l’intégration des fonctionnalités?

R et Python Machine Learning sont fournis par [SQL Server machine learning services](../what-is-sql-server-machine-learning.md) en tant qu’extension d’une instance de moteur de base de données. L’intégration s’effectue principalement via la couche de sécurité et le langage de définition de données, résumé comme suit:

+ Les procédures stockées sont équipées de la possibilité d’accepter du code R et Python en tant que paramètres d’entrée. Les développeurs et les chercheurs de données peuvent utiliser une [procédure stockée système](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql?view=sql-server-2017) ou créer une procédure personnalisée qui encapsule leur code.
+ Fonctions T-SQL (à savoir, [Predict](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)) qui peuvent consommer un modèle de données déjà formé. Cette fonctionnalité est disponible via T-SQL. Par conséquent, il peut être appelé sur un système qui n’a pas les extensions Machine Learning installées.
+ Les connexions de base de données existantes et les autorisations basées sur les rôles couvrent les scripts appelés par l’utilisateur qui utilisent ces mêmes données. En règle générale, si les utilisateurs ne peuvent pas accéder aux données par le biais d’une requête, ils ne peuvent pas non plus y accéder par le biais d’un script.

## <a name="feature-availability"></a>Disponibilité des fonctionnalités

L’intégration de R et Python est disponible en une succession d’étapes. La première est la configuration, lorsque vous [incluez ou ajoutez la fonctionnalité **machine learning services** ](../install/sql-machine-learning-services-windows-install.md) à une instance du moteur de base de données. À l’étape suivante, vous devez activer les scripts externes sur l’instance du moteur de base de données (elle est désactivée par défaut).

À ce stade, seuls les administrateurs de base de données disposent de l’autorisation totale pour créer et exécuter des scripts externes, ajouter ou supprimer des packages, et créer des procédures stockées et d’autres objets.

Tous les autres utilisateurs doivent disposer de l’autorisation exécuter une SCRIPT externe. Des [autorisations de base de données standard](../security/user-permission.md) supplémentaires déterminent si les utilisateurs peuvent créer des objets, exécuter des scripts, utiliser des modèles sérialisés et formés, et ainsi de suite. 

## <a name="resource-allocation"></a>Allocation des ressources

Les procédures stockées et les requêtes T-SQL qui appellent le traitement externe utilisent les ressources disponibles pour le pool de ressources par défaut. Dans le cadre de la configuration par défaut, les processus externes tels que les sessions R et Python sont autorisés jusqu’à 20% de la mémoire totale sur le système hôte. 

Si vous souhaitez réajuster la réapprovisionnement, vous pouvez modifier le pool par défaut, avec l’effet correspondant sur Machine Learning charges de travail en cours d’exécution sur ce système.

Une autre option consiste à créer un pool de ressources externes personnalisé pour capturer les sessions provenant de programmes, d’hôtes ou d’activités spécifiques qui se produisent pendant des intervalles de temps spécifiques. Pour plus d’informations, consultez [gouvernance des ressources pour modifier les niveaux de ressources pour l’exécution de R et Python](../administration/resource-governance.md) et [comment créer un pool de ressources](../administration/how-to-create-a-resource-pool.md) pour obtenir des instructions pas à pas.

## <a name="isolation-and-containment"></a>Isolation et relation contenant-contenu

L’architecture de traitement est conçue pour isoler les scripts externes du traitement du moteur principal. Les scripts R et Python s’exécutent en tant que processus distincts, sous comptes Worker locaux. Dans le gestionnaire des tâches, vous pouvez surveiller les processus R et Python, s’exécutant sous un compte d’utilisateur local à faibles privilèges, distinct du compte de service SQL Server. 

L’exécution de processus R et Python dans des comptes à privilèges faibles offre les avantages suivants:

+ Isole les processus du moteur principal des sessions R et Python vous pouvez mettre fin à un processus R ou python sans affecter les opérations de base de données principales. 

+ Réduit les privilèges des processus d’exécution de script externe sur l’ordinateur hôte.

Les comptes avec des privilèges minimaux sont créés lors de l’installation et placés dans un *pool de comptes d’utilisateurs* Windows appelé **SQLRUserGroup**. Par défaut, ce groupe est autorisé à utiliser des fichiers exécutables, des bibliothèques et des datasets intégrés dans le dossier de programme pour R et Python sous SQL Server. 

En tant qu’administrateur de bases de données, vous pouvez utiliser SQL Server la sécurité des données pour spécifier qui est autorisé à exécuter des scripts, et les données utilisées dans les travaux sont gérées sous les mêmes rôles de sécurité qui contrôlent l’accès via les requêtes T-SQL. En tant qu’administrateur système, vous pouvez refuser explicitement l’accès **SQLRUserGroup** aux données sensibles sur le serveur local en créant des listes de contrôle d’accès.

>[!NOTE]
> Par défaut, **SQLRUserGroup** n’a pas de connexion ou d’autorisations dans SQL Server lui-même. Si les comptes de travail nécessitent une connexion pour l’accès aux données, vous devez le créer vous-même. Un scénario qui appelle spécifiquement la création d’une connexion consiste à prendre en charge les demandes d’un script en cours d’exécution, pour les données ou les opérations sur l’instance du moteur de base de données, lorsque l’identité de l’utilisateur est un utilisateur Windows et que la chaîne de connexion spécifie un utilisateur approuvé. Pour plus d’informations, consultez [Ajouter SQLRUserGroup en tant qu’utilisateur de base de données](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md).

## <a name="disable-script-execution"></a>Désactiver l’exécution du script

En cas d’inversion de scripts, vous pouvez désactiver toutes les exécutions de script, en inversant les étapes effectuées précédemment pour activer l’exécution de scripts externes en premier lieu.

1. Dans SQL Server Management Studio ou un autre outil de requête, exécutez cette commande `external scripts enabled` pour définir sur 0 ou false.

    ```sql
    EXEC sp_configure  'external scripts enabled', 0
    RECONFIGURE WITH OVERRIDE
    ```
2. Redémarrez le service moteur de base de données.

Une fois que vous avez résolu le problème, n’oubliez pas de réactiver l’exécution du script sur l’instance si vous souhaitez reprendre la prise en charge des scripts R et Python sur l’instance du moteur de base de données. Pour plus d’informations, consultez [activer l’exécution de scripts](../install/sql-machine-learning-services-windows-install.md#enable-script-execution)

## <a name="extend-functionality"></a>Étendre les fonctionnalités

La science des données introduit souvent de nouvelles exigences en matière de déploiement et d’administration de packages. Pour un scientifique des données, il est courant de tirer parti des packages Open source et tiers dans des solutions personnalisées. Certains de ces packages auront des dépendances avec d’autres packages, auquel cas vous devrez peut-être évaluer et installer plusieurs packages pour atteindre votre objectif.

En tant qu’administrateur de bases de connaissances de serveur, le déploiement de packages R et Python arbitraires sur un serveur de production représente une question inconnue. Avant d’ajouter des packages, vous devez déterminer si la fonctionnalité fournie par le package externe est véritablement requise, sans équivalent dans le [langage R](r-libraries-and-data-types.md) intégré et les [bibliothèques python](../python/python-libraries-and-data-types.md) installées par SQL Server installation. 

En guise d’alternative à l’installation du package serveur, un scientifique des données peut être en mesure de [créer et d’exécuter des solutions sur une station de travail externe](../r/set-up-a-data-science-client.md), de récupérer des données à partir de SQL Server, mais avec une analyse effectuée localement sur la station de travail plutôt que sur le serveur. automatiquement. 

Si, par la suite, vous déterminez que les fonctions de la bibliothèque externe sont nécessaires et ne présentent pas de risque pour l’ensemble des opérations ou des données du serveur, vous pouvez choisir parmi plusieurs méthodologies pour ajouter des packages. Dans la plupart des cas, des droits d’administrateur sont nécessaires pour ajouter des packages à SQL Server. Pour plus d’informations, consultez [installer des packages python dans SQL Server](../python/install-additional-python-packages-on-sql-server.md) et [installer des packages R dans SQL Server](install-additional-r-packages-on-sql-server.md).

> [!NOTE]
> Pour les packages R, les droits d’administrateur de serveur ne sont pas spécifiquement requis pour l’installation du package si vous utilisez d’autres méthodes. Pour plus d’informations, consultez [installer des packages R dans SQL Server](install-additional-r-packages-on-sql-server.md) .

## <a name="monitoring-script-execution"></a>Analyse de l’exécution des scripts

Les scripts R et Python qui s' [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] exécutent dans sont [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] démarrés par l’interface. Toutefois, le Launchpad n’est pas régi par les ressources et n’est pas surveillé séparément, car il s’agit d’un service sécurisé fourni par Microsoft qui gère les ressources de manière appropriée.

Les scripts externes qui s’exécutent sous le service Launchpad sont gérés à l’aide de l' [objet de traitement Windows](/windows/desktop/ProcThread/job-objects). Avec un objet de traitement, des groupes de processus peuvent être gérés en tant qu’unité. Chaque objet de traitement est hiérarchique et contrôle les attributs de tous les processus qui lui sont associés. Les opérations effectuées sur un objet de traitement affectent tous les processus associés à cet objet.

Par conséquent, si vous avez besoin de mettre fin à une tâche associée à un objet, sachez que tous les processus connexes seront également arrêtés. Si vous exécutez un script R qui est affecté à un objet de traitement Windows et que ce script exécute un travail ODBC qui doit être arrêté, le processus de script R parent est également arrêté.

Si vous démarrez un script externe qui utilise le traitement parallèle, un seul objet de traitement Windows gère tous les processus enfants parallèles.

Pour déterminer si un processus s’exécute dans un travail, utilisez la fonction `IsProcessInJob`.

## <a name="next-steps"></a>Étapes suivantes

+ Passez en revue les concepts et les composants de l' [architecture d’extensibilité](../concepts/extensibility-framework.md) et la [sécurité](../concepts/security.md) pour plus d’informations.

+ Dans le cadre de l’installation des fonctionnalités, vous êtes peut-être déjà familiarisé avec le contrôle d’accès aux données de l’utilisateur final, mais dans le cas contraire, consultez [accorder des autorisations utilisateur à SQL Server machine learning](../security/user-permission.md) pour plus d’informations. 

+ Découvrez comment ajuster les ressources système pour les charges de travail Machine Learning nécessitant beaucoup de calculs. Pour plus d’informations, voir [How to Create a Resource pool](../administration/how-to-create-a-resource-pool.md).
