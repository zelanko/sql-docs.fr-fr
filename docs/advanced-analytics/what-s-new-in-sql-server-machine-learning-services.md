---
title: Nouveautés
description: Nouvelles annonces de fonctionnalités pour chaque version de SQL Server 2016 R services, R Server SQL Server Machine Learning Services.
ms.date: 07/31/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9d63aac9c91919a2b4e3296f29e939c8cd09ad76
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715307"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>Nouveautés de SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Des fonctionnalités d’apprentissage automatique sont ajoutées à SQL Server dans chaque version, car nous continuons à développer, étendre et approfondir l’intégration entre la plateforme de données, l’analytique avancée et la science des données. 

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2019-preview"></a>Nouveautés de SQL Server version préliminaire 2019

Cette version ajoute les fonctionnalités les plus demandées pour les opérations R et Python Machine Learning dans SQL Server. Pour plus d’informations sur toutes les fonctionnalités de cette version, consultez [What’s New in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md) and [release Notes for SQL Server 2019](../sql-server/sql-server-ver15-release-notes.md).

> [!NOTE]
> Pour obtenir la documentation sur les nouveautés de Java dans SQL Server 2019, consultez les [nouvelles extensions de langages de SQL Server](https://docs.microsoft.com/sql/language-extensions/language-extensions-whats-new) .

| Libérer | Mise à jour des fonctionnalités |
|---------|----------------|
| CTP 3.2 | Aucune modification. |
| CTP 3.1 | Aucune modification. |
| CTP 3.0 | Aucune modification. |
| CTP 2,5 | Aucune modification. |
| CTP 2.4 | Prise en charge de Linux pour [Create External Library (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) pour R et Python. |
| CTP 2.3 | Sur Windows uniquement, le code Python est accessible dans une bibliothèque externe à l’aide de l’instruction [Create External Library (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) . |
| CTP 2.2 | Aucune modification. |
| CTP 2.1 | Aucune modification. |
| CTP 2.0 | Prise en charge de la plateforme Linux pour R et Python Machine Learning. Prise en main de l' [installation SQL Server machine learning services sur Linux](../linux/sql-server-linux-setup-machine-learning.md). |
|  | Le [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) introduit deux nouveaux paramètres qui vous permettent de générer facilement plusieurs modèles à partir de données partitionnées. Pour plus d’informations, consultez ce didacticiel, [créer des modèles basés sur des partitions dans R](tutorials/r-tutorial-create-models-per-partition.md). |
|   | La prise en charge des clusters de basculement est désormais prise en charge sur Windows et Linux, en supposant SQL Server Launchpad service est démarré sur tous les nœuds. Pour plus d’informations, consultez [SQL Server l’installation](../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)d’un cluster de basculement. |

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2017"></a>Nouveautés de SQL Server 2017

Cette version ajoute la [prise en charge de Python et les algorithmes de machine learning de pointe](https://cloudblogs.microsoft.com/sqlserver/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/). Renommée pour refléter la nouvelle étendue, SQL Server 2017 marque l’introduction de [SQL Server machine learning services (dans la base de données)](what-is-sql-server-machine-learning.md), avec prise en charge linguistique pour Python et R. 

Pour plus d’informations sur les annonces de fonctionnalités, consultez [Nouveautés de SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

### <a name="r-enhancements"></a>Améliorations de R

Le composant R de SQL Server Machine Learning Services est la nouvelle génération de SQL Server 2016 R services, avec les versions mises à jour de base R, RevoScaler et d’autres packages.

Les nouvelles fonctionnalités de R incluent la [**gestion des packages**](r/install-additional-r-packages-on-sql-server.md), avec les points suivants: 

+ Les rôles de base de données aident les DBA à gérer les packages et à affecter des autorisations pour l’installation du package.
+ [Créer une bibliothèque externe](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) permet aux administrateurs de bases de connaissances de gérer les packages dans le langage T-SQL familier.
+ Les fonctions [RevoScaleR](r/use-revoscaler-to-manage-r-packages.md) permettent d’installer, de supprimer ou de répertorier les packages détenus par les utilisateurs. Pour plus d’informations, consultez [comment utiliser les fonctions RevoScaleR pour rechercher ou installer des packages R sur SQL Server](r/use-revoscaler-to-manage-r-packages.md).

### <a name="r-libraries"></a>Bibliothèques R

| Package | Description |
|---------|-------------|
| [**MicrosoftML**](r/ref-r-microsoftml.md) | Dans cette version, MicrosoftML est inclus dans une installation R par défaut, ce qui élimine l’étape de mise à niveau requise dans le précédent SQL Server les services R 2016. MicrosoftML fournit des algorithmes de Machine Learning et des transformations de données de pointe qui peuvent être mis à l’échelle ou exécutés dans des contextes de calcul distants. Les algorithmes incluent des réseaux neuronaux profonds personnalisables, des arbres de décision rapide et des forêts de décision, la régression linéaire et la régression logistique.  |

### <a name="python-integration-for-in-database-analytics"></a>Intégration de Python pour l’analyse en base de données

Python est un langage qui offre une grande flexibilité et une grande puissance pour un large éventail de tâches de Machine Learning. Les bibliothèques Open source pour Python incluent plusieurs plateformes pour les réseaux neuronaux personnalisables, ainsi que des bibliothèques populaires pour le traitement en langage naturel. 

Étant donné que Python est intégré au moteur de base de données, vous pouvez conserver les analyses proches des données et éliminer les coûts et les risques de sécurité liés au déplacement des données. Vous pouvez déployer des solutions Machine Learning basées sur Python à l’aide d’outils tels que Visual Studio. Vos applications de production peuvent se procurer des prédictions, des modèles ou des visuels à partir du runtime python 3,5 à l’aide de SQL Server méthodes d’accès aux données.

L’intégration T-SQL et Python est prise en charge via la procédure stockée système [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) . Vous pouvez appeler n’importe quel code Python à l’aide de cette procédure stockée. Le code s’exécute dans une architecture sécurisée et double qui permet le déploiement de modèles et de scripts Python à l’échelle de l’entreprise, pouvant être appelé à partir d’une application à l’aide d’une procédure stockée simple. Des gains de performances supplémentaires sont réalisés en diffusant des données de SQL vers des processus Python et une parallélisation de sonnerie MPI.

Vous pouvez utiliser la fonction [PREDICTION](../t-sql/queries/predict-transact-sql.md) T-SQL pour effectuer un calcul de [score natif](sql-native-scoring.md) sur un modèle pré-formé qui a déjà été enregistré au format binaire requis.

### <a name="python-libraries"></a>Bibliothèques python

| Package | Description |
|---------|-------------|
|[**revoscalepy**](python/ref-py-revoscalepy.md)| Équivalent python de RevoScaleR. Vous pouvez créer des modèles Python pour les régressions linéaires et logistiques, les arbres de décision, les arbres amplifiés et les forêts aléatoires, tous les parallèles et capables d’être exécutés dans des contextes de calcul distants. Ce package prend en charge l’utilisation de plusieurs sources de données et de contextes de calcul distants. Le chercheur ou le développeur de données peut exécuter du code Python sur un SQL Server distant pour explorer des données ou créer des modèles sans déplacer les données. |
|[**microsoftml**](python/ref-py-microsoftml.md) |Équivalent python du package R MicrosoftML. |

### <a name="pre-trained-models"></a>Modèles dont l’apprentissage a déjà été effectué

Des [**modèles**](install/sql-pretrained-models-install.md) préformés sont disponibles pour Python et R. Utilisez ces modèles pour la reconnaissance d’images et l’analyse des sentiments positifs-négatifs pour générer des prédictions sur vos propres données. 

### <a name="standalone-server-as-a-shared-feature-in-sql-server-setup"></a>Serveur autonome en tant que fonctionnalité partagée dans le programme d’installation de SQL Server

Cette version ajoute également [SQL Server machine learning Server (autonome)](r/r-server-standalone.md), un serveur de science des données entièrement indépendant, prenant en charge l’analyse statistique et prédictive dans R et Python. Comme avec R services, ce serveur est la prochaine version de SQL Server 2016 R Server (autonome). Avec le serveur autonome, vous pouvez distribuer et mettre à l’échelle des solutions R ou python sans dépendances sur SQL Server.
::: moniker-end

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2016"></a>Nouveautés de SQL Server 2016

Cette version a introduit les fonctionnalités de Machine Learning dans SQL Server par le biais de **SQL Server 2016 R services**, un moteur d’analyse en base de données pour le traitement des scripts R sur les données résidentes au sein d’une instance du moteur de base de données.

En outre, **SQL Server 2016 R Server (autonome)** a été publié comme un moyen d’installer R Server sur un serveur Windows. Initialement, SQL Server installation a fourni la seule façon d’installer R Server pour Windows. Dans les versions ultérieures, les développeurs et les chercheurs de données qui souhaitaient R Server sur Windows pouvaient utiliser un autre programme d’installation autonome pour atteindre le même objectif. Le serveur autonome dans SQL Server est fonctionnellement équivalent au produit serveur autonome, [Microsoft R Server pour Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

Pour plus d’informations sur les annonces de fonctionnalités, consultez [Nouveautés de SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md).

| Libérer |Mise à jour des fonctionnalités |
|---------|----------------|
| Ajouts CU | La [**notation en temps réel**](real-time-scoring.md) repose sur les C++ bibliothèques natives pour lire un modèle stocké dans un format binaire optimisé, puis générer des prédictions sans devoir appeler le runtime R. Cela rend les opérations de notation beaucoup plus rapides. Avec l’évaluation en temps réel, vous pouvez exécuter une procédure stockée ou effectuer des scores en temps réel à partir du code R. La notation en temps réel est également disponible pour SQL Server 2016, si l’instance est mise à niveau vers la dernière version [!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]de. |
| Version initiale | [**Intégration R pour l’analytique dans la base de données**](r/sql-server-r-services.md). <br/><br/> Packages r pour appeler des fonctions R dans T-SQL, et vice versa. Les fonctions RevoScaleR fournissent des analyses R à l’échelle en segmentant les données en parties de composants, en coordonnant et en gérant le traitement distribué et en agrégeant les résultats. Dans SQL Server R 2016 R services (en base de données), le moteur RevoScaleR est intégré à une instance du moteur de base de données, en saumure les données et l’analyse dans le même contexte de traitement. <br/><br/>Intégration T-SQL et R par le biais de [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). Vous pouvez appeler n’importe quel code R à l’aide de cette procédure stockée. Cette infrastructure sécurisée permet un déploiement à l’échelle de l’entreprise des modèles et des scripts RN qui peuvent être appelés à partir d’une application à l’aide d’une procédure stockée simple. Des gains de performances supplémentaires sont obtenus en diffusant des données de SQL vers des processus R et une parallélisation de sonnerie MPI. <br/><br/>Vous pouvez utiliser la fonction [PREDICTION](../t-sql/queries/predict-transact-sql.md) T-SQL pour effectuer un calcul de [score natif](sql-native-scoring.md) sur un modèle pré-formé qui a déjà été enregistré au format binaire requis.|

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="linux-support"></a>Support Linux

SQL Server 2019 ajoute la prise en charge Linux pour R et Python quand vous installez les packages Machine Learning avec une instance du moteur de base de données. Pour plus d’informations, consultez [installer SQL Server machine learning services sur Linux](../linux/sql-server-linux-setup-machine-learning.md).

Sur Linux, SQL Server 2017 ne dispose pas de l’intégration R ou python, mais vous pouvez utiliser le [score natif](sql-native-scoring.md) sur Linux, car cette fonctionnalité est disponible via la [prédiction](../t-sql/queries/predict-transact-sql.md) T-SQL, qui s’exécute sur Linux. Le score natif permet une notation à hautes performances à partir d’un modèle préformé, sans appeler ou même exiger un Runtime R.
::: moniker-end

<a name="azure-sql-database-roadmap"></a>

## <a name="machine-learning-services-in-azure-sql-database"></a>Machine Learning Services dans Azure SQL Database

Machine Learning Services dans Azure SQL Database est en version préliminaire publique. Pour plus d’informations, consultez [Azure SQL Database machine learning services (version préliminaire)](https://docs.microsoft.com/azure/sql-database/sql-database-machine-learning-services-overview).

## <a name="next-steps"></a>Étapes suivantes

+ [Installer SQL Server Machine Learning Services (dans la base de données)](install/sql-machine-learning-services-windows-install.md)
+ [Didacticiels et exemples de machine learning](tutorials/machine-learning-services-tutorials.md)
