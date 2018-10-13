---
title: Gérer et intégrer des charges de travail machine learning dans SQL Server | Microsoft Docs
description: Comme un DBA SQL Server, passez en revue les tâches d’administration pour le déploiement d’un sous-système de R et Python sur une instance du moteur de base de données d’apprentissage.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c921b89dc3f6928ccbfc3f9fc727015dadc05b7b
ms.sourcegitcommit: fc6a6eedcea2d98c93e33d39c1cecd99fbc9a155
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49169079"
---
# <a name="manage-and-integrate-machine-learning-workloads-on-sql-server"></a>Gérer et intégrer des charges de travail machine learning sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article est pour les administrateurs de base de données de SQL Server qui sont responsables du déploiement d’une infrastructure de science des données efficace sur une ressource de serveur prenant en charge de plusieurs charges de travail. Il encadre l’espace de problème d’administration relatives à la gestion de R et Python code d’exécution sur SQL Server. 

## <a name="what-is-feature-integration"></a>Quelle est la fonctionnalité d’intégration

Apprentissage de R et Python est fourni par [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) en tant qu’extension à une instance du moteur de base de données. L’intégration est principalement par le biais de la couche de sécurité et le langage de définition de données résumées comme suit :

+ Les procédures stockées sont équipés de la capacité à accepter de R et Python code comme paramètres d’entrée. Les développeurs et chercheurs de données peuvent utiliser un [procédure stockée système](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql?view=sql-server-2017) ou créer une procédure personnalisée qui encapsule leur code.
+ Fonctions T-SQL (à savoir, [PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)) qui peut consommer un modèle de données précédemment formée. Cette fonctionnalité est disponible via T-SQL. Par conséquent, elle peut appelée sur un système qui n’a pas spécifiquement les extensions installées d’apprentissage.
+ Les connexions de base de données existantes et les autorisations en fonction du rôle couvrent les scripts appelé par l’utilisateur utilisant ces mêmes données. En règle générale, si les utilisateurs ne peuvent pas accéder aux données via une requête, ils ne peuvent pas y accéder via un script soit.

## <a name="feature-availability"></a>Disponibilité des fonctionnalités

Intégration de R et Python devient disponible via une série d’étapes. Le premier est le programme d’installation, lorsque vous [ou ajoutez le **Machine Learning Services** ](../install/sql-machine-learning-services-windows-install.md) fonctionnalité à une instance du moteur de base de données. Comme une étape ultérieure, vous devez activer les scripts externes sur l’instance du moteur de base de données (il est désactivé par défaut).

À ce stade, seuls les administrateurs de base de données ont des autorisations complètes pour créer et exécuter des scripts externes, ajouter ou supprimer des packages et créer des procédures stockées et autres objets.

Tous les autres utilisateurs doivent être l’autorisation EXECUTE ANY EXTERNAL SCRIPT. Supplémentaires [les autorisations de base de données standard](../security/user-permission.md) déterminer si les utilisateurs peuvent créer des objets, exécuter des scripts, utiliser des modèles sérialisés et formés et ainsi de suite. 

## <a name="resource-allocation"></a>Allocation de ressources

Les procédures stockées et des requêtes T-SQL qui appellent le traitement externe utilisent les ressources disponibles pour le pool de ressources par défaut. Dans le cadre de la configuration par défaut, les processus externes tels que les sessions R et Python sont autorisés jusqu'à 20 % de la mémoire totale sur le système hôte. 

Si vous souhaitez réajuster les ressources, vous pouvez modifier le pool par défaut, avec un effet correspondant sur les charges de travail machine learning en cours d’exécution sur ce système.

Une autre option consiste à créer un pool de ressources externes personnalisés pour capturer les sessions provenant des programmes spécifiques, les ordinateurs hôtes ou les activités qui se produisent pendant l’intervalle de temps spécifique. Pour plus d’informations, consultez [gouvernance des ressources pour modifier les niveaux de ressources pour l’exécution de R et Python](../administration/resource-governance.md) et [comment créer un pool de ressources](../administration/how-to-create-a-resource-pool.md) pour obtenir des instructions pas à pas.

## <a name="isolation-and-containment"></a>Isolation et relation contenant-contenu

L’architecture de traitement est conçu pour isoler des scripts externes du traitement de moteur de base. Les scripts R et Python s’exécutent en tant que processus distincts, sous les comptes de travail local. Dans le Gestionnaire des tâches, vous pouvez surveiller les processus R et Python, l’exécution sous un compte d’utilisateur local à faibles privilèges, distinct à partir du compte de service SQL Server. 

Exécution des processus R et Python dans des comptes à faibles privilèges présente les avantages suivants :

+ Isole les processus de moteur de base à partir de sessions R et Python, que vous pouvez arrêter un processus R ou Python sans affecter les opérations de base de données principales. 

+ Réduit les privilèges des processus de runtime de script externe sur l’ordinateur hôte.

Comptes de privilèges sont créés pendant l’installation et placés dans un Windows *pool de comptes d’utilisateur* appelé **SQLRUserGroup**. Par défaut, ce groupe est autorisé à utiliser des exécutables, des bibliothèques et des jeux de données intégrées dans le dossier de programme pour R et Python sous SQL Server. 

Comme un DBA, sécurité des données de SQL Server vous permet de spécifier qui est autorisé à exécuter des scripts, et que les données utilisées dans les travaux sont gérées sous les mêmes rôles de sécurité qui contrôlent accéder via des requêtes T-SQL. En tant qu’un administrateur système, vous pouvez refuser explicitement le **SQLRUserGroup** accès aux données sensibles sur le serveur local en créant des ACL.

>[!NOTE]
> Par défaut, le **SQLRUserGroup** n’a pas d’une connexion ou les autorisations dans SQL Server lui-même. Comptes de travail doivent ont besoin d’une connexion pour accéder aux données, vous devez la créer vous-même. Un scénario qui appelle spécifiquement pour la création d’une connexion consiste à prendre en charge des demandes à partir d’un script dans l’exécution, pour des opérations sur l’instance du moteur de base de données ou des données lors de l’identité de l’utilisateur est un utilisateur de Windows et la chaîne de connexion spécifie un utilisateur approuvé. Pour plus d’informations, consultez [SQLRUserGroup d’ajouter en tant qu’un utilisateur de base de données](../../advanced-analytics/security/add-sqlrusergroup-to-database.md).

## <a name="disable-script-execution"></a>Désactiver l’exécution du script

En cas de perte de contrôle de scripts, vous pouvez désactiver toute l’exécution du script, en inversant les étapes précédemment entrepris pour permettre l’exécution du script externe en premier lieu.

1. Dans SQL Server Management Studio ou un autre outil de requête, exécutez cette commande pour définir `external scripts enabled` à 0 ou FALSE.

    ```sql
    EXEC sp_configure  'external scripts enabled', 0
    RECONFIGURE WITH OVERRIDE
    ```
2. Redémarrez le service de moteur de base de données.

Une fois que vous résolvez le problème, pensez à activer de nouveau l’exécution du script sur l’instance si vous souhaitez reprendre R et Python de script prend en charge sur l’instance du moteur de base de données. Pour plus d’informations, consultez [activer l’exécution du script](../install/sql-machine-learning-services-windows-install.md#enable-script-execution)

## <a name="extend-functionality"></a>Étendre les fonctionnalités

Science des données présente souvent la nouvelle configuration requise pour le déploiement de package et l’administration. Pour un scientifique des données, il est courant de tirer parti des packages tiers et open source dans des solutions personnalisées. Certaines de ces packages ont des dépendances sur d’autres packages, auquel cas vous devrez peut-être évaluer et d’installer plusieurs packages afin d’atteindre votre objectif.

En tant qu’un administrateur responsable d’une ressource de serveur, le déploiement des packages R et Python arbitraires sur un serveur de production représente un défi d’inconnu. Avant d’ajouter des packages, vous devez évaluer si la fonctionnalité fournie par le package externe est réellement nécessaire, avec aucun équivalent dans intégrés [langage R](r-libraries-and-data-types.md) et [bibliothèques Python](../python/python-libraries-and-data-types.md) installé Installation de SQL Server. 

Comme alternative à l’installation du serveur package, un spécialiste des données peuvent être en mesure de [générer et exécuter des solutions sur une station de travail externe](../r/set-up-a-data-science-client.md), récupération de données à partir de SQL Server, mais avec toutes les analyses exécutées localement sur la station de travail au lieu de sur le serveur lui-même. 

Si vous déterminez par la suite que les fonctions de bibliothèque externe sont nécessaires et ne présentent pas de risque pour les opérations du serveur ou l’ensemble des données, vous pouvez choisir à partir de plusieurs méthodologies pour ajouter des packages. Dans la plupart des cas, les droits d’administrateur sont requis pour ajouter des packages à SQL Server. Pour plus d’informations, consultez [packages d’installation de Python dans SQL Server](../python/install-additional-python-packages-on-sql-server.md) et [installer des packages R dans SQL Server](install-additional-r-packages-on-sql-server.md).

> [!NOTE]
> Pour les packages R, les droits d’administrateur de serveur ne sont pas spécialement requis pour l’installation du package si vous utilisez d’autres méthodes. Consultez [installer des packages R dans SQL Server](install-additional-r-packages-on-sql-server.md) pour plus d’informations.

## <a name="next-steps"></a>Étapes suivantes

+ Passez en revue les concepts et les composants de la [architecture d’extensibilité](../concepts/extensibility-framework.md) et [sécurité](../concepts/security.md) pour plus d’informations.

+ Dans le cadre de l’installation de fonctionnalités, vous peut-être déjà familiarisé avec l’utilisateur final de données de contrôle d’accès, mais dans le cas contraire, consultez [accorder des autorisations d’utilisateur à l’apprentissage de SQL Server](../security/user-permission.md) pour plus d’informations. 

+ Découvrez comment ajuster les ressources système pour les charges de travail d’apprentissage calculs intensifs. Pour plus d’informations, consultez [comment créer un pool de ressources](../administration/how-to-create-a-resource-pool.md).
