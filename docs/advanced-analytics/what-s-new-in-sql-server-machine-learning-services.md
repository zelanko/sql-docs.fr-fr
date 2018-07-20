---
title: Ce que&#39;s Nouveautés de SQL Server Machine Learning Services | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/02/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: bf56d52823727609d713639d534e277be57caaef
ms.sourcegitcommit: c37da15581fb34250d426a8d661f6d0d64f9b54c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39174806"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>Quelles sont les nouveautés dans SQL Server Machine Learning Services 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Fonctionnalités d’apprentissage automatique sont ajoutées à SQL Server dans chaque version que nous continuons à développer, étendre et approfondir l’intégration entre la plateforme de données et la science des données, analytique et vous souhaitez implémenter sur vos données d’apprentissage supervisé. 

## <a name="new-in-sql-server-2017"></a>Nouveautés de SQL Server 2017

Cette version ajouté la prise en charge de Python et les algorithmes d’apprentissage leader du secteur. Renommé pour refléter la nouvelle étendue, SQL Server 2017 marqué l’introduction de **SQL Server Machine Learning Services (en base de données)**, avec prise en charge linguistique pour Python et R. 

Cette version introduite également **SQL Server Machine Learning Server (autonome)**, entièrement indépendante de SQL Server, pour les charges de travail R et Python que vous souhaitez exécuter sur un système dédié. Avec le serveur autonome, vous pouvez distribuer et mettre à l’échelle des solutions R ou Python sans utiliser de SQL Server.

| Version | Mise à jour de fonctionnalité |
|---------|----------------|
| CU 6 | Correctifs de bogues et actualisation du package, mais pas de fonctionnalités nouvelles annonces. Correctifs principaux comprennent la prise en charge pour les types de données DateTime dans la requête SPEES pour Python et les messages d’erreur améliorés dans microsoftml lorsque modèles préentraînés sont manquantes. |
| CU 5 | Correctifs de bogues et actualisation du package, mais pas de fonctionnalités nouvelles annonces. Correctifs incluent des améliorations pour transformer les fonctions et variables dans revoscalepy, correction des erreurs long chemin d’accès relatif dans rxInstallPackages, résolution des connexions dans un bouclage pour RxExec rx_exec fonctions et les révisions des messages d’avertissement. |
| CU 4 | Correctifs de bogues et actualisation du package, mais pas de fonctionnalités nouvelles annonces. |
| CU 3 | Sérialisation dans revoscalepy, de modèle de Python à l’aide de la [rx_serialize_model fonction](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model).<br/><br/>[Notation native](sql-native-scoring.md) ainsi que des améliorations apportées aux [de score en temps réel](real-time-scoring.md). Pour calculer les scores dans base de données, le débit est un million de lignes par seconde à l’aide des modèles R. Dans cette mise à jour, de notation en temps réel et la notation native offrent de meilleures performances dans la ligne unique et la notation par lot. Natif notation utilise une fonction T-SQL pour l’évaluation rapide qui peut être exécutée sur n’importe quelle édition de SQL Server, même sur Linux. La fonction ne requiert aucune installation de R ou une configuration supplémentaire. Cela signifie que vous pouvez former un modèle à un autre emplacement, enregistrez-le dans SQL Server et puis effectuer l’évaluation sans jamais appeler R. Pour plus d’informations sur les méthodologies de score, consultez [comment effectuer le calcul de score en temps réel ou la notation native](r/how-to-do-realtime-scoring.md). |
| CU 2 | Correctifs de bogues et actualisation du package, mais pas de fonctionnalités nouvelles annonces. |
| CU 1 | Dans revoscalepy, ajoute rx_create_col_info pour retourner des informations de schéma à partir d’une source de données SQL Server, qui est similaire à [rxCreateColInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcreatecolinfo) pour R. <br/><br/>Améliorations apportées aux [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) pour prendre en charge les scénarios parallèles à l’aide de la `RxLocalParallel` contexte de calcul.|
| Version initiale |[**Intégration de Python pour la base de données analytique**](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/) <br/><br/>Le [revoscalepy](python/what-is-revoscalepy.md) package est l’équivalent de Python de RevoScaleR. Vous pouvez créer des modèles de Python pour régressions linéaires et logistiques, arbres de décision, arbres amplifiés et forêts aléatoires, tout parallélisme et capables d’en cours d’exécution dans des contextes de calcul à distance. Ce package prend en charge l’utilisation de plusieurs sources de données et des contextes de calcul distants. Le spécialiste des données ou le développeur peut exécuter du code Python sur un serveur SQL distant, pour Explorer les données ou de créer des modèles sans déplacement de données. <br/><br/>Le [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) package est l’équivalent de Python du package MicrosoftML R.<br/><br/>Intégration de T-SQL et Python via [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). Vous pouvez appeler n’importe quel code Python à l’aide de cette procédure stockée. Cette infrastructure sécurisée permet le déploiement d’entreprise des modèles de Python et des scripts qui peuvent être appelées à partir d’une application à l’aide d’une procédure stockée simple. Gains de performances supplémentaires sont réalisés par les données de diffusion en continu à partir de SQL aux processus de Python et de parallélisation des anneaux MPI. <br/><br/>Vous pouvez utiliser le code T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) (fonction) pour effectuer [notation native](sql-native-scoring.md) sur un modèle préentraîné qui a été précédemment enregistré dans le format binaire requis.|
| Version initiale | [**MicrosoftML (R)** ](using-the-microsoftml-package.md) contient la transformation de données et des algorithmes qui peut être des contextes de calcul à distance à l’échelle ou s’exécutent dans d’apprentissage de pointe. Les algorithmes sont personnalisables des réseaux neuronaux profonds, des arbres de décision et les forêts de décision, régression linéaire et régression logistique. |
| Version initiale | [**Modèles préentraînés** ](install/sql-pretrained-models-install.md) pour la reconnaissance d’images et analyse des sentiments de positif en négatif. Utilisez ces modèles pour générer des prédictions sur vos propres données. |
| Version initiale | [**Gestion des packages R**](r/install-additional-r-packages-on-sql-server.md), y compris les points importants suivants : la base de données pour aider à l’administrateur de gérer les packages et assigner des autorisations pour installer des packages, [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) instruction T-SQL pour aide DBA gérer les packages sans connaître R et un ensemble complet de R fonctionne dans [RevoScaleR](r/use-revoscaler-to-manage-r-packages.md) pour aider à installer, supprimer ou répertorier les packages détenus par des utilisateurs. |
| Version initiale | [**Opérationnalisation via mrsdeploy** ](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package) pour le déploiement et hébergement de script R comme un service web. S’applique à un script R uniquement (pas d’équivalent Python). Conçu pour l’option de serveur (autonome) éviter la concurrence de ressources avec d’autres opérations de SQL Server. |


## <a name="new-in-sql-server-2016"></a>Nouveautés de SQL Server 2016

Cette version introduite fonctionnalités machine learning dans SQL Server via **SQL Server 2016 R Services**, un moteur de base de données analytique pour le script de traitement R sur les données résidentes dans une instance du moteur de base de données.

En outre, **SQL Server 2016 R Server (autonome)** a été publié comme un moyen d’installer R Server sur un serveur Windows. Le programme d’installation de SQL Server fournies au départ, la seule façon d’installer R Server pour Windows. Dans les versions ultérieures, les développeurs et scientifiques des données qui souhaitaient R Server sur Windows peuvent utiliser un autre programme d’installation autonome pour atteindre le même objectif. Le serveur autonome dans SQL Server est fonctionnellement équivalent au produit serveur autonome, [Microsoft R Server pour Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

| Version |Mise à jour de fonctionnalité |
|---------|----------------|
| Ajouts CU | [**Calcul de score en temps réel** ](real-time-scoring.md) s’appuie sur les bibliothèques C++ natives pour lire un modèle stocké dans un format binaire optimisé, puis générer des prédictions sans avoir à appeler le runtime R. Cela rend les opérations de notation beaucoup plus rapides. Avec le calcul de scores en temps réel, vous pouvez exécuter une procédure stockée ou exécuter en temps réel à partir de code R de notation. Calcul de score en temps réel est également disponible pour SQL Server 2016, si l’instance est mis à niveau vers la dernière version de [!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]. |
| Version initiale | [**Intégration de R pour la base de données analytique**](r/sql-server-r-services.md). <br/><br/> Packages R pour R appelant les fonctions dans T-SQL et vice versa. Fonctions RevoScaleR fournissent analytique R à l’échelle en divisant les données en composants, la coordination et la gestion distribuée de traitement et l’agrégation des résultats. Dans SQL Server 2016 R Services (en base de données), le moteur de RevoScaleR est intégré à une instance du moteur de base de données, chambres data et analytique ensemble dans le même contexte de traitement. <br/><br/>Intégration de T-SQL et R via [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). Vous pouvez appeler n’importe quel code R à l’aide de cette procédure stockée. Cette infrastructure sécurisée permet le déploiement d’entreprise des modèles de Rn et des scripts qui peuvent être appelées à partir d’une application à l’aide d’une procédure stockée simple. Gains de performances supplémentaires sont réalisés par les données de diffusion en continu à partir de SQL pour les processus R et la parallélisation des anneaux MPI. <br/><br/>Vous pouvez utiliser le code T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) (fonction) pour effectuer [notation native](sql-native-scoring.md) sur un modèle préentraîné qui a été précédemment enregistré dans le format binaire requis.|

## <a name="linux-support-roadmap"></a>Feuille de route de prise en charge de Linux

Apprentissage à l’aide de R ou Python dans la base de données n’est pas pris en charge dans SQL Server sur Linux. Recherchez des annonces dans une version ultérieure.

Toutefois, sur Linux, vous pouvez effectuer [notation native](sql-native-scoring.md) à l’aide de la fonction PREDICT de T-SQL. Notation native vous permet de noter à partir d’un modèle préformé très rapide, sans appeler ou même nécessiter un runtime R. Cela signifie que vous pouvez utiliser SQL Server sur Linux pour générer des prédictions très rapides, pour traiter les applications clientes.

<a name="azure-sql-database-roadmap"></a>

## <a name="azure-sql-database-roadmap"></a>Feuille de route de base de données SQL Azure

Il existe une prise en charge limitée pour R dans Azure SQL Database : disponible uniquement dans l’ouest des États-Unis, dans les services créés au niveau Premium. Couverture de protection, y compris la prise en charge de Python, est susceptible de suivre dans une version ultérieure. Toutefois, il n’existe aucune date de mise en production prévue pour l’instant.  

## <a name="next-steps"></a>Étapes suivantes

+ [Installation de SQL Server 2017 Machine Learning Services (en base de données)](install/sql-machine-learning-services-windows-install.md)
+ [Exemples et didacticiels de machine learning](tutorials/machine-learning-services-tutorials.md)
