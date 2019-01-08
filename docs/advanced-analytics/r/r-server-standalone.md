---
title: Installation Standalone R Server ou Machine Learning Server - SQL Server Machine Learning Services
description: Présentation de vue d’ensemble de R Server autonome et Machine Learning Server dans le programme d’installation de SQL Server
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: overview
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f1cbc4a7c02597c6c8bece8c47976fabdb4959e7
ms.sourcegitcommit: 0bb306da5374d726b1e681cd4b5459cb50d4a87a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53731976"
---
# <a name="r-server-standalone-and-machine-learning-server-standalone-in-sql-server"></a>R Server (autonome) et Machine Learning Server (autonome) dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server fournit la prise en charge de l’installation pour un travail autonome R Server ou Machine Learning Server s’exécute indépendamment de SQL Server. Selon votre version de SQL Server, un serveur autonome possède une base de R open source et, éventuellement, Python, superposées aux bibliothèques de hautes performances à partir de Microsoft qui ajoutent l’analytique prédictive et de statistiques à l’échelle. Bibliothèques permettent également des tâches d’apprentissage écrites en R ou Python. 

Dans SQL Server 2016, cette fonctionnalité est appelée **R Server (autonome)** et est R uniquement. Dans SQL Server 2017, elle est appelée **Machine Learning Server (autonome)** et inclut R et Python.  

> [!Note]
> Installé par le programme d’installation de SQL Server, un serveur autonome est fonctionnellement équivalent pour les versions non SQL personnalisée de [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), prenant en charge les mêmes scénarios utilisateur, y compris l’exécution à distance, Opérationnalisation et les services web et la collection complète des bibliothèques R et Python.

## <a name="components"></a>Composants

SQL Server 2016 est R uniquement. SQL Server 2017 prend en charge R et Python. Le tableau suivant décrit les fonctionnalités de chaque version.

| Composant | Description |
|-----------|-------------|
| Packages R | [**RevoScaleR** ](ref-r-revoscaler.md) est la bibliothèque principale pour R évolutive avec des fonctions de manipulation de données, de transformation, de visualisation et d’analyse.  <br/>[**MicrosoftML** ](ref-r-microsoftml.md) ajoute des algorithmes d’apprentissage automatique pour créer des modèles personnalisés pour l’analyse de texte, l’analyse de l’image et l’analyse des sentiments. <br/>[**sqlRUtils** ](ref-r-sqlrutils.md) fournit des fonctions d’assistance pour placer des scripts R dans une procédure stockée T-SQL, l’inscription d’une procédure stockée avec une base de données et l’exécution de la procédure stockée à partir d’un environnement de développement R.<br/>[**mrsdeploy** ](operationalization-with-mrsdeploy.md) offres web déploiement de service (dans SQL Server 2017 uniquement). <br/>[**olapR** ](ref-r-olapr.md) permet de spécifier des requêtes MDX dans R.|
| Microsoft R Open (MRO) | [**MRO** ](https://mran.microsoft.com/open) est open source distribution Microsoft de R. Le package et un interpréteur sont inclus. Utilisez toujours la version de MRO fournie dans le programme d’installation. |
| Outils R | Invites de commandes et fenêtres de console R sont des outils standard dans une distribution de R. Les trouver à \Program files\Microsoft SQL Server\140\R_SERVER\bin\x64. |
| Exemples de R et scripts |  Les packages RevoScaleR et R Open source incluent les jeux de données intégrées afin que vous pouvez créer et exécuter le script à l’aide de données préinstallées. Examinez les \Program files\Microsoft SQL Server\140\R_SERVER\library\datasets et \library\RevoScaleR. |
| Packages Python | [**revoscalepy** ](../python/ref-py-revoscalepy.md) est la bibliothèque principale pour Python évolutive avec des fonctions de manipulation de données, de transformation, de visualisation et d’analyse. <br/>[**microsoftml** ](../python/ref-py-microsoftml.md) ajoute des algorithmes d’apprentissage automatique pour créer des modèles personnalisés pour l’analyse de texte, l’analyse de l’image et l’analyse des sentiments.  |
| Outils Python | L’outil de ligne de commande Python intégré est utile pour les tests ad hoc et tâches. Recherchez l’outil à \Program files\Microsoft SQL Server\140\PYTHON_SERVER\python.exe. |
| Anaconda | Anaconda est une distribution open source de Python et les packages essentiels. |
| Scripts et des exemples Python | Comme avec R, Python inclut des jeux de données intégrés et des scripts. Rechercher les données de revoscalepy à Files\Microsoft SQL Server\140\PYTHON_SERVER\lib\site-packages\revoscalepy\data\sample-data. |
| Modèles préentraînés dans R et Python | Modèles préentraînés sont créés pour les cas d’usage spécifiques et gérés par l’équipe d’ingénierie science des données chez Microsoft. Vous pouvez utiliser les modèles préformés comme-consiste à noter les sentiments négatifs positif dans le texte, ou à détecter les fonctionnalités dans des images, à l’aide de nouvelles entrées de données que vous fournissez. Modèles préentraînés sont pris en charge et utilisable sur un serveur autonome, mais vous ne pouvez pas les installer via le programme d’installation de SQL Server. Pour plus d’informations, consultez [installation préformé modèles d’apprentissage automatique sur SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="using-a-standalone-server"></a>À l’aide d’un serveur autonome

Les développeurs R et Python choisissez généralement un serveur autonome de dépasser les contraintes de mémoire et le traitement de l’open source R et Python. Bibliothèques R et Python, l’exécution sur un serveur autonome peuvent charger et traiter de grandes quantités de données sur plusieurs cœurs et agréger les résultats en une seule sortie consolidée. Fonctions de hautes performances sont conçues pour la mise à l’échelle et utilitaire : garantissant une analytique prédictive, modélisation statistique, des visualisations de données et pointe algorithmes machine learning dans un produit commercial serveur conçu et pris en charge par Microsoft.

Comme un serveur indépendant découplé à partir de SQL Server, l’environnement R et Python est configuré, sécurisées et accessibles en utilisant le système d’exploitation sous-jacent et les outils standards fournis dans le serveur autonome, pas de SQL Server. Il n’existe aucune prise en charge intégrée pour les données relationnelles SQL Server. Si vous souhaitez utiliser les données de SQL Server, vous pouvez créer des connexions et les objets source de données comme vous le feriez à partir de n’importe quel client.

En outre à SQL Server, un serveur autonome est également utile comme un puissant environnement de développement si vous avez besoin de l’informatique local et distant. Les packages R et Python sur un serveur autonome sont les mêmes que ceux fournis avec une installation du moteur de base de données, ce qui permet la portabilité du code et [changement de contexte de calcul](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).

## <a name="how-to-get-started"></a>La prise en main

Démarrer avec le programme d’installation, attacher les fichiers binaires à votre outil de développement favori et écrire votre premier script.

### <a name="step-1-install-the-software"></a>Étape 1 : Installer le logiciel

Installer l’une de ces versions :

+ [SQL Server 2017 Machine Learning Server (autonome)](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Server (autonome) - R uniquement](../install/sql-r-standalone-windows-install.md)

### <a name="step-2-configure-a-development-tool"></a>Étape 2 : Configurer un outil de développement

Sur un serveur autonome, il est courant de travailler localement à l’aide d’un environnement de développement installé sur le même ordinateur.

+ [Configurer les outils R](set-up-a-data-science-client.md)
+ [Configurer les outils Python](../python/setup-python-client-tools-sql.md)

### <a name="step-3-write-your-first-script"></a>Étape 3 : Écrire votre premier script

Écrire un script R ou Python à l’aide de fonctions à partir de RevoScaleR et revoscalepy algorithmes d’apprentissage.
  
  + [Découvrir R and RevoScaleR in 25 Functions](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): Démarrer avec les commandes de base R et ensuite de progression pour les fonctions analytiques distribuables RevoScaleR qui fournissent des performances élevées et la mise à l’échelle vers des solutions R. Inclut des versions parallélisables des packages de modélisation R les plus populaires comme le clustering k-means, les arbres de décision, les forêts de décision et les outils de manipulation des données.

  + [Démarrage rapide : Un exemple de classification binaire avec le package de Python microsoftml](https://docs.microsoft.com/machine-learning-server/python/quickstart-binary-classification-with-microsoftml): Créer un modèle de classification binaire en utilisant les fonctions de microsoftml et le jeu de données du cancer du sein bien connu.

Choisir le meilleur langage pour la tâche. R est idéal pour les calculs statistiques qui sont difficiles à implémenter à l’aide de SQL. Pour les opérations de jeu basé sur les données, tirez parti des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour optimiser les performances. Utiliser le moteur de base de données en mémoire pour effectuer des calculs très rapides sur les colonnes.

### <a name="step-4-operationalize-your-solution"></a>Étape 4 : Faire fonctionner votre solution

Serveurs autonomes peuvent utiliser le [Opérationnalisation](https://docs.microsoft.com//machine-learning-server/what-is-operationalization) fonctionnalités de la non SQL-personnalisée [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server). Vous pouvez configurer un serveur autonome pour l’Opérationnalisation, ce qui vous offre ces avantages : déployer et héberger votre code, comme les services web, exécutez les diagnostics, tester la capacité du service web.

### <a name="step-5-maintain-your-server"></a>Étape 5 : Gérer votre serveur

SQL Server libère des mises à jour cumulatives de manière régulière. Appliquer les mises à jour cumulatives ajoute des améliorations fonctionnelles et sécurité à une installation existante. 

Vous trouverez des descriptions des fonctionnalités nouvelles ou modifiées dans le [CAB télécharge](../install/sql-ml-cab-downloads.md) article et sur les pages web pour [mises à jour cumulatives de SQL Server 2016](https://support.microsoft.com/help/3177312/sql-server-2016-build-versions) et [mises à jour cumulatives de SQL Server 2017 ](https://support.microsoft.com/help/4047329). 

Pour plus d’informations sur la façon d’appliquer des mises à jour à une instance existante, consultez [appliquer les mises à jour](../install/sql-machine-learning-standalone-windows-install.md#apply-cu) dans les instructions d’installation.

## <a name="see-also"></a>Voir aussi

 [Installer R Server (autonome) ou Machine Learning Server (autonome)](../install/sql-machine-learning-standalone-windows-install.md)

