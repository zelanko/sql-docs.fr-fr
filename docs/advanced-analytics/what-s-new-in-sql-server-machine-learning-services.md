---
title: Nouveautés - SQL Server Machine Learning Services | Microsoft Docs
description: Nouvelles annonces de fonctionnalité pour chaque version de SQL Server 2016 R Services, R Server, SQL Server 2017 Machine Learning Services.
ms.date: 05/22/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: f7b7daefb0f5e9514372fadd9377b05c84784e34
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67140273"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>Quelles sont les nouveautés dans SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Fonctionnalités d’apprentissage automatique sont ajoutées à SQL Server dans chaque version que nous continuons à développer, étendre et approfondir l’intégration entre la plateforme de données, analytique avancée et science des données. 

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2019-preview"></a>Nouveautés de la version préliminaire de SQL Server 2019

Cette version ajoute les fonctionnalités les plus demandées pour les opérations d’apprentissage machine R et Python dans SQL Server. Pour plus d’informations sur toutes les fonctionnalités dans cette version, consultez [What ' s New in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md) et [Release Notes for SQL Server 2019](../sql-server/sql-server-ver15-release-notes.md).

> [!NOTE]
> Pour les nouveautés nouvelle documentation sur Java dans SQL Server 2019, consultez le [Nouveautés Extensions en langage SQL Server ?](https://docs.microsoft.com/sql/language-extensions/language-extensions-whats-new)

| Version | Mise à jour de fonctionnalité |
|---------|----------------|
| CTP 3.0 | Aucune modification. |
| CTP 2.5 | Aucune modification. |
| CTP 2.4 | Prise en charge de Linux pour [CREATE EXTERNAL LIBRARY (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) pour R et Python. |
| CTP 2.3 | Sur Windows, le code Python sont accessibles dans une bibliothèque externe à l’aide de la [CREATE EXTERNAL LIBRARY (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) instruction. |
| CTP 2.2 | Aucune modification. |
| CTP 2.1 | Aucune modification. |
| CTP 2.0 | Prise en charge des plates-formes de Linux pour l’apprentissage de R et Python. Prise en main [installer SQL Server Machine Learning Services sur Linux](../linux/sql-server-linux-setup-machine-learning.md). |
|  | Le [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) introduit deux nouveaux paramètres qui vous permettent de facilement générer plusieurs modèles à partir de données partitionnées. En savoir plus dans ce didacticiel, [créer des modèles basés sur une partition dans R](tutorials/r-tutorial-create-models-per-partition.md). |
|   | Prise en charge du cluster de basculement est maintenant pris en charge sur Windows et Linux, en supposant que le service Launchpad SQL Server est démarré sur tous les nœuds. Pour plus d’informations, consultez [installation de cluster de basculement SQL Server](../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md). |

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2017"></a>Nouveautés de SQL Server 2017

Cette version ajoute [prise en charge de Python et les algorithmes d’apprentissage leader du secteur](https://cloudblogs.microsoft.com/sqlserver/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/). Renommé pour refléter la nouvelle étendue, SQL Server 2017 marque l’introduction de [SQL Server Machine Learning Services (en base de données)](what-is-sql-server-machine-learning.md), avec prise en charge linguistique pour Python et R. 

Pour la fonctionnalité annonces global, consultez [What ' s New in SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

### <a name="r-enhancements"></a>Améliorations de R

Le composant de R de SQL Server 2017 Machine Learning Services est la nouvelle génération de SQL Server 2016 R Services, avec des versions mises à jour de base R, RevoScaler et autres packages.

Les nouvelles fonctionnalités pour R incluent [ **gestion des packages**](r/install-additional-r-packages-on-sql-server.md), avec les points importants suivants : 

+ Rôles de base de données aider les administrateurs à gérer les packages et affecter des autorisations pour l’installation du package.
+ [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) DBA permet de gérer les packages dans le langage T-SQL familier.
+ [RevoScaleR](r/use-revoscaler-to-manage-r-packages.md) fonctions aider à installer, supprimer ou répertorier les packages détenus par les utilisateurs. Pour plus d’informations, consultez [comment utiliser les fonctions RevoScaleR pour rechercher ou installer R packages sur SQL Server](r/use-revoscaler-to-manage-r-packages.md).

### <a name="r-libraries"></a>Bibliothèques R

| Package | Description |
|---------|-------------|
| [**MicrosoftML**](r/ref-r-microsoftml.md) | Dans cette version, MicrosoftML est inclus dans une installation de R par défaut, éliminant l’étape de mise à niveau requise dans la précédente SQL Server 2016 R Services. MicrosoftML offre de pointe d’apprentissage algorithmes et les transformations de données qui peuvent être mis à l’échelle ou exécuter dans des contextes de calcul à distance. Les algorithmes sont personnalisables des réseaux neuronaux profonds, des arbres de décision et les forêts de décision, régression linéaire et régression logistique.  |

### <a name="python-integration-for-in-database-analytics"></a>Intégration de Python pour la base de données analytique

Python est un langage qui offre une grande souplesse et puissance pour diverses tâches d’apprentissage. Bibliothèques Open source pour Python incluent plusieurs plateformes pour les réseaux neuronaux personnalisables, ainsi que des bibliothèques populaires pour le traitement en langage naturel. À présent, ce langage largement utilisé est pris en charge dans SQL Server 2017 Machine Learning.

Étant donné que Python est intégré avec le moteur de base de données, vous pouvez conserver analytique proche des données et éliminer les coûts et les risques de sécurité associés au transfert de données. Vous pouvez déployer des solutions machine learning basées sur Python à l’aide des outils tels que Visual Studio. Vos applications de production peuvent obtenir des prédictions, modèles, ou les méthodes d’accéder aux éléments visuels à partir de l’exécution de Python 3.5 à l’aide de données SQL Server.

Intégration de T-SQL et Python est pris en charge par le biais du [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) procédure stockée système. Vous pouvez appeler n’importe quel code Python à l’aide de cette procédure stockée. Code s’exécute dans une architecture double sécurisée, qui permet le déploiement d’entreprise de modèles de Python et des scripts pouvant être appelés à partir d’une application à l’aide d’une procédure stockée simple. Gains de performances supplémentaires sont réalisés par les données de diffusion en continu à partir de SQL aux processus de Python et de parallélisation des anneaux MPI.

Vous pouvez utiliser le code T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) (fonction) pour effectuer [notation native](sql-native-scoring.md) sur un modèle préentraîné qui a été précédemment enregistré dans le format binaire requis.

### <a name="python-libraries"></a>Bibliothèques Python

| Package | Description |
|---------|-------------|
|[**revoscalepy**](python/ref-py-revoscalepy.md)| Équivalent Python de RevoScaleR. Vous pouvez créer des modèles de Python pour régressions linéaires et logistiques, arbres de décision, arbres amplifiés et forêts aléatoires, tout parallélisme et capables d’en cours d’exécution dans des contextes de calcul à distance. Ce package prend en charge l’utilisation de plusieurs sources de données et des contextes de calcul distants. Le spécialiste des données ou le développeur peut exécuter du code Python sur un serveur SQL distant, pour Explorer les données ou de créer des modèles sans déplacement de données. |
|[**microsoftml**](python/ref-py-microsoftml.md) |Python équivalent du package MicrosoftML R. |

### <a name="pre-trained-models"></a>Modèles dont l’apprentissage a déjà été effectué

[**Modèles préentraînés** ](install/sql-pretrained-models-install.md) sont disponibles pour Python et R. utilisent ces modèles pour la reconnaissance d’images et d’analyse d’opinions positive négative, pour générer des prédictions sur vos propres données. 

### <a name="standalone-server-as-a-shared-feature-in-sql-server-setup"></a>Serveur autonome comme une fonctionnalité partagée dans le programme d’installation de SQL Server

Cette version ajoute également [SQL Server Machine Learning Server (autonome)](r/r-server-standalone.md), un serveur de science des données totalement indépendante, prenant en charge d’analytique prédictive et statistiques dans R et Python. Comme avec R Services, ce serveur est la prochaine version de SQL Server 2016 R Server (autonome). Avec le serveur autonome, vous pouvez distribuer et mettre à l’échelle des solutions R ou Python sans dépendances sur SQL Server.
::: moniker-end

## <a name="new-in-sql-server-2016"></a>Nouveautés de SQL Server 2016

Cette version introduite fonctionnalités machine learning dans SQL Server via **SQL Server 2016 R Services**, un moteur de base de données analytique pour le script de traitement R sur les données résidentes dans une instance du moteur de base de données.

En outre, **SQL Server 2016 R Server (autonome)** a été publié comme un moyen d’installer R Server sur un serveur Windows. Le programme d’installation de SQL Server fournies au départ, la seule façon d’installer R Server pour Windows. Dans les versions ultérieures, les développeurs et scientifiques des données qui souhaitaient R Server sur Windows peuvent utiliser un autre programme d’installation autonome pour atteindre le même objectif. Le serveur autonome dans SQL Server est fonctionnellement équivalent au produit serveur autonome, [Microsoft R Server pour Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

Pour la fonctionnalité annonces global, consultez [What ' s New in SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md).

| Version |Mise à jour de fonctionnalité |
|---------|----------------|
| Ajouts CU | [**Calcul de score en temps réel** ](real-time-scoring.md) s’appuie sur les bibliothèques C++ natives pour lire un modèle stocké dans un format binaire optimisé, puis générer des prédictions sans avoir à appeler le runtime R. Cela rend les opérations de notation beaucoup plus rapides. Avec la notation en temps réel, vous pouvez exécuter une procédure stockée ou exécuter une notation en temps réel à partir de code R. Calcul de score en temps réel est également disponible pour SQL Server 2016, si l’instance est mis à niveau vers la dernière version de [!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]. |
| Version initiale | [**Intégration de R pour la base de données analytique**](r/sql-server-r-services.md). <br/><br/> Packages R pour R appelant les fonctions dans T-SQL et vice versa. Fonctions RevoScaleR fournissent analytique R à l’échelle en divisant les données en composants, la coordination et la gestion distribuée de traitement et l’agrégation des résultats. Dans SQL Server 2016 R Services (en base de données), le moteur de RevoScaleR est intégré à une instance du moteur de base de données, chambres data et analytique ensemble dans le même contexte de traitement. <br/><br/>Intégration de T-SQL et R via [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). Vous pouvez appeler n’importe quel code R à l’aide de cette procédure stockée. Cette infrastructure sécurisée permet le déploiement d’entreprise des modèles de Rn et des scripts qui peuvent être appelées à partir d’une application à l’aide d’une procédure stockée simple. Gains de performances supplémentaires sont réalisés par les données de diffusion en continu à partir de SQL pour les processus R et la parallélisation des anneaux MPI. <br/><br/>Vous pouvez utiliser le code T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) (fonction) pour effectuer [notation native](sql-native-scoring.md) sur un modèle préentraîné qui a été précédemment enregistré dans le format binaire requis.|

## <a name="linux-support-roadmap"></a>Feuille de route de prise en charge de Linux

SQL Server 2019 CTP 2.3 ajoute la prise en charge de Linux pour R et Python lorsque vous installez les packages avec une instance du moteur de base de données d’apprentissage. Pour plus d’informations, consultez [installer SQL Server Machine Learning Services sur Linux](../linux/sql-server-linux-setup-machine-learning.md).

Sur Linux, SQL Server 2017 n’a pas d’intégration de R ou Python, mais vous pouvez utiliser [notation Native](sql-native-scoring.md) sur Linux, car cette fonctionnalité est disponible via T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md), qui s’exécute sur Linux. Notation native permet la notation de hautes performances à partir d’un modèle préformé, sans appeler ou même nécessiter un runtime R.

<a name="azure-sql-database-roadmap"></a>

## <a name="machine-learning-services-in-azure-sql-database"></a>Machine Learning Services dans la base de données SQL Azure

Machine Learning Services (avec R) dans la base de données SQL Azure est en version préliminaire publique. Pour plus d’informations, consultez [base de données de SQL Azure Machine Learning Services avec R (version préliminaire)](https://docs.microsoft.com/azure/sql-database/sql-database-machine-learning-services-overview).

## <a name="next-steps"></a>Étapes suivantes

+ [Installation de SQL Server 2017 Machine Learning Services (en base de données)](install/sql-machine-learning-services-windows-install.md)
+ [Exemples et didacticiels de machine learning](tutorials/machine-learning-services-tutorials.md)
