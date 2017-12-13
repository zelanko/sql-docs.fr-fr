---
title: Quel &#39; est nouvelle dans Machine Learning Services | Documents Microsoft
ms.date: 11/16/2017
ms.prod: sql-non-specified
ms.prod_service: r-services
ms.service: 
ms.component: advanced-analytics
ms.reviewer: 
ms.suite: sql
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aff043a-8b37-4f3f-9827-10a671e1ad1c
caps.latest.revision: "36"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 41ff01d46e2ca0aa996d8f582733b24b7560e29b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="whats-new-in-machine-learning-services-in-sql-server"></a>Quelles sont les nouveautés dans Machine Learning Services dans SQL Server

Dans SQL Server 2016, Microsoft a introduit une fonctionnalité qui prend en charge la science des données de l’échelle de l’entreprise, en intégrant le langage R avec le moteur de base de données SQL Server de SQL Server R Services.

Dans SQL Server 2017, apprentissage intégré à la base de données est désormais encore plus performante, avec prise en charge de la langue de Python populaires. La prise en charge de nouvelles langues s’ajoute un nouveau nom : **Machine Learning Services (de-de base de données)**.

Intercepter la dernière annonce ici ! [Python dans SQL Server 2017 : amélioré dans base de données d’apprentissage](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="whats-new-in-sql-server-2017"></a>Nouveautés de SQL Server 2017

Machine Learning serveur dans SQL Server fournit une prise en charge complète pour créer et déployer des solutions d’apprentissage machine dans R ou Python. Voici les principales fonctionnalités de cette version :

### <a name="whats-new-in-cumulative-update-1-for-sql-server-2017"></a>Nouveautés à jour Cumulative 1 pour SQL Server 2017

Vous pouvez maintenant mettre à niveau vos composants de Python et R au serveur d’apprentissage Machine 9.2.1.24. Cette version propose de nombreuses améliorations **revoscalepy** et **RevoScaleR**, y compris les améliorations des performances.

### <a name="in-database-python-integration"></a>Intégration de Python dans base de données

Vous pouvez exécuter les Python dans les procédures stockées, ou exécutez Python à distance à l’aide de l’ordinateur SQL Server en tant que le contexte de calcul. Cette intégration ouvre de nouvelles voies pour la grande Communauté des développeurs de Python et des chercheurs de données à utiliser la puissance de SQL Server.

Les développeurs SQL Server pour accéder à des bibliothèques de Python complètes à partir de l’écosystème open source, y compris les infrastructures plébiscitées telles que scikit-en savoir plus, TensorFlow, Caffe et Theano/Keras. Et veillez à Explorer les innovations de Microsoft tels que **revoscalepy** et **microsoftml**!

Python en cours d’exécution dans la base de données n’est pas seulement une affaire d’apprentissage automatique, la façon dont. Il existe une multitude d’autres applications potentielles à l’intégration de Python avec SQL et à l’aide de la puissance de chaque langage pour offrir des solutions puissantes plus intelligentes.

+ **revoscalepy**

    Cette version inclut la version finale de **revoscalepy**, qui fournit des équivalents de Python des algorithmes dans RevoScaleR. Vous pouvez créer des modèles de Python pour des régressions linéaires et logistiques, les arbres de décision, les arbres augmentés et les forêts aléatoires, tout parallèles et capables de les exécuter dans des contextes de calcul à distance.

    Pour plus d’informations, consultez [What ' s revoscalepy](python/what-is-revoscalepy.md).

+ Contextes de calcul à distance pour Python

    Cette version prend en charge l’utilisation de plusieurs sources de données et les contextes de calcul à distance. Le chercheur de données ou le développeur peut exécuter du code Python sur un serveur SQL distant, pour Explorer les données ou de créer des modèles sans déplacement de données. L’utilisation de contextes de calcul à distance nécessite **revoscalepy**.

+ Prise en charge de Python dans Microsoft Machine Learning Server (autonome)

    [!INCLUDE[sscurrent-md](../includes/sscurrent-md.md)]inclut la possibilité d’installer une version autonome du serveur Microsoft Machine Learning. À l’aide de Machine Learning Server, vous pouvez distribuer et l’échelle de R ou Python code sans utiliser de SQL Server.

### <a name="linux-support"></a>Support Linux

Apprentissage à l’aide de R ou Python dans-base de données n’est pas pris en charge dans SQL Server sur Linux. Recherchez des annonces dans une version ultérieure.

Toutefois, sur Linux, vous pouvez effectuer [score native](sql-native-scoring.md) à l’aide de la fonction de prédiction de T-SQL. Calculer les scores native vous permet de score à partir d’un modèle préformé très rapide, sans appeler ou même nécessitant un runtime R. Cela signifie que vous pouvez utiliser SQL Server sur Linux pour générer des prédictions très rapides, à répondre à des applications clientes.

### <a name="new-algorithms"></a>Nouveaux algorithmes

Le **MicrosoftML** package pour R et Python contient des algorithmes d’apprentissage de pointe et la transformation des données qui peut être à distance à l’échelle ou s’exécuter dans des contextes de calcul. Les algorithmes sont des réseaux neuronaux profonds personnalisables, rapide de MDT et forêts décisionnelles, régression linéaire et la régression logistique. Le package MicrosoftML est fourni avec les interfaces R et Python.

Pour plus d’informations, consultez [présentation MicrosoftML](using-the-microsoftml-package.md) et [microsoftml pour Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package).

### <a name="operationalization"></a>À l’Opérationnalisation

Cette version contient plusieurs options et fonctionnalités pour vous aider à déployer et distribuer des tâches d’apprentissage automatique :

+ Déployer et intégrer des solutions de Python de machine, à l’aide de T-SQL

    L’intégration de Python avec T-SQL signifie que vous pouvez appeler n’importe quel code Python à l’aide `sp_execute_external_script`. Cette infrastructure de sécurité permet le déploiement d’entreprise de modèles de Python et des scripts qui peuvent être appelées à partir d’une application à l’aide d’une procédure stockée simple. Performances supplémentaires sont par diffusion en continu des données à partir de SQL pour les processus de Python et la parallélisation anneau MPI.

+ **mrsdeploy** pour Python

    Le **mrsdeploy** package pour [!INCLUDE[rsql-platform-md](../includes/rsql-platformnew-md.md)] et [!INCLUDE[rsql-platformnew-md](../includes/rsql-platformnew-md.md)] prend en charge le déploiement des modèles de Python et des scripts en tant que services web. Pour obtenir un exemple de son fonctionnement, consultez [publier et consommer le code Python](python/publish-consume-python-code.md).

+ Performance

    Microsoft a envoyé les limites des performances pour calculer les scores. Avec la base de données de calcul de score, nous avions traité un million de lignes par seconde à l’aide des modèles R. Dans cette version, les nouvelles fonctionnalités pour **en temps réel de calcul de score** et **score native** obtenir de meilleures performances dans une ligne et le calcul du score du lot.

### <a name="realtime-scoring-and-native-scoring"></a>Calculer les scores en temps réel et le score natif

Calculer les scores en temps réel s’appuie sur les bibliothèques natives C++ pour lire un modèle stocké dans un format binaire optimisé, puis générer des prédictions sans avoir à appeler le runtime R. Cela rend les opérations de calcul de score beaucoup plus rapides.

En outre, cette version de [!INCLUDE[sscurrent-md](../includes/sscurrent-md.md)] inclut une fonction native de T-SQL pour rapide calcul de score qui peut être exécuté sur n’importe quelle édition de SQL Server, y compris sur Linux. La fonction ne requiert aucune installation de R ou une configuration supplémentaire. Cela signifie que vous pouvez effectuer l’apprentissage d’un modèle à un autre emplacement, enregistrez-le dans SQL Server et puis effectuer le calcul de score sans jamais appeler R. Cette fonctionnalité est appelée _score natif_.

  - Calcul de score natif est disponible uniquement dans [!INCLUDE[sscurrent-md](../includes/sscurrent-md.md)]. Elle utilise une fonction de T-SQL qui peut s’exécuter dans n’importe quelle édition de SQL Server, notamment Linux.
 - Calculer les scores en temps réel sont prise en charge dans [!INCLUDE[sscurrent-md](../includes/sscurrent-md.md)]et Microsoft Machine Learning Server. Vous pouvez exécuter une procédure stockée ou effectuer en temps réel à partir du code R de calcul de score.
 - Calculer les scores en temps réel sont également disponible pour SQL Server 2016, si l’instance est mis à niveau vers la dernière version de [!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)].

Pour plus d’informations, consultez ces articles :

 + [Calculer les scores en temps réel](real-time-scoring.md)
 + [Calcul de score en natif](sql-native-scoring.md)
 + [Comment effectuer le calcul de score en temps réel ou évaluation natif](r/how-to-do-realtime-scoring.md)

### <a name="upgrade-your-machine-learning-experience-and-get-pre-trained-models"></a>Mise à niveau de votre expérience d’apprentissage et obtenir des modèles dont l’apprentissage

Si vous avez installé une version antérieure de SQL Server 2016 R Services, vous pouvez désormais mettre à niveau vers la dernière version en basculant de votre serveur pour utiliser la stratégie de cycle de vie des logiciels modernes. En procédant ainsi, vous pouvez tirer parti d’un cycle de mise en production plus rapide pour R et mise à niveau automatique de tous les composants R. Pour plus d’informations, consultez [quelles sont les nouveautés dans Machine Learning Server](https://docs.microsoft.com/machine-learning-server/whats-new-in-machine-learning-server).

Le programme d’installation offre également la possibilité d’installer une collection de modèles dont l’apprentissage au format binaire. Ces modèles prennent en charge l’apprentissage automatique dans les scénarios de reconnaissance d’image, où il peut être difficile pour les clients rechercher des jeux de données volumineux pour former un modèle. Après avoir installé un des modèles dont l’apprentissage, vous pouvez l’utiliser pour la prédiction de vos propres données sans le temps et les dépenses impliqués dans l’apprentissage de ce type de modèle volumineux et complexe.

Pour plus d’informations, consultez [installer dont l’apprentissage des modèles dans SQL Server](r/install-pretrained-models-sql-server.md)

### <a name="package-management"></a>Gestion des packages

Cette version inclut de nombreuses améliorations dans la gestion des packages pour SQL Server. notamment :

- Rôles de base de données pour aider à l’administrateur de gérer les packages et affecter des autorisations pour installer des packages
- L’instruction de créer une bibliothèque externe dans T-SQL, pour aider les administrateurs à gérer les packages sans avoir à connaître R
- Un ensemble complet de fonctions R pour aider à installer, supprimer ou répertorier les packages appartenant aux utilisateurs

Pour plus d’informations, consultez [gestion des packages](r/r-package-management-for-sql-server-r-services.md).

### <a name="get-started"></a>Prise en main

+ [Configurer les Python dans Machine Learning Services SQL Server](../advanced-analytics/python/setup-python-machine-learning-services.md)

+ [Configurer R dans Machine Learning Services SQL Server](r/set-up-sql-server-r-services-in-database.md)

+ [Exemples et didacticiels de machine learning](tutorials/machine-learning-services-tutorials.md)
