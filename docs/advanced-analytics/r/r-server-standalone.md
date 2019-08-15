---
title: Que sont les Machine Learning Server autonomes ou les R Server dans SQL Server?
description: Présentation de la R Server et des Machine Learning Server autonomes dans SQL Server installation
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/13/2019
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: cb7aef4502f42bc91067cdcbd598b9b2ea7477cf
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028611"
---
# <a name="what-are-standalone-machine-learning-server-or-r-server-in-sql-server"></a>Que sont les Machine Learning Server autonomes ou les R Server dans SQL Server?
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server assure la prise en charge de l’installation d’un R Server autonome ou d’un Machine Learning Server qui s’exécute indépendamment de SQL Server. En fonction de votre version de SQL Server, un serveur autonome a une base de R Open source et éventuellement de Python, superposés avec des bibliothèques de haute performance de Microsoft qui ajoutent des analyses statistiques et prédictives à l’échelle. Les bibliothèques activent également des tâches Machine Learning scriptées dans R ou python. 

Dans SQL Server 2016, cette fonctionnalité est appelée **R Server (autonome)** et est R uniquement. Dans SQL Server 2017, elle est appelée **machine learning Server (autonome)** et comprend R et Python.  

> [!Note]
> Comme installé par SQL Server installation, un serveur autonome est fonctionnellement équivalent aux versions non-SQL de [Microsoft machine learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), prenant en charge les mêmes scénarios utilisateur, y compris l’exécution à distance, le fonctionnement et le Web et la collection complète des bibliothèques R et Python.

## <a name="components"></a>Composants

SQL Server 2016 est R uniquement. SQL Server 2017 prend en charge R et Python. Le tableau suivant décrit les fonctionnalités de chaque version.

| Composant | Description |
|-----------|-------------|
| Packages R | [**RevoScaleR**](ref-r-revoscaler.md) est la bibliothèque principale de R évolutive avec des fonctions de manipulation, de transformation, de visualisation et d’analyse des données.  <br/>[**MicrosoftML**](ref-r-microsoftml.md) ajoute des algorithmes de machine learning pour créer des modèles personnalisés pour l’analyse de texte, l’analyse d’images et l’analyse des sentiments. <br/>[**sqlRUtils**](ref-r-sqlrutils.md) fournit des fonctions d’assistance pour placer des scripts R dans une procédure stockée T-SQL, inscrire une procédure stockée avec une base de données et exécuter la procédure stockée à partir d’un environnement de développement R.<br/>[**mrsdeploy**](operationalization-with-mrsdeploy.md) offre un déploiement de service Web (dans SQL Server 2017 uniquement). <br/>[**olapr**](ref-r-olapr.md) est destiné à la spécification de requêtes MDX dans R.|
| Microsoft R Open (MRO) | [**MRO**](https://mran.microsoft.com/open) est la distribution Open source de Microsoft de R. Le package et l’interpréteur sont inclus. Utilisez toujours la version de MRO regroupée dans le programme d’installation. |
| Outils R | Les fenêtres de console R et les invites de commande sont des outils standard dans une distribution R. Recherchez-les dans \Program files\Microsoft SQL Server\140\R_SERVER\bin\x64. |
| Exemples et scripts R |  Les packages R et RevoScaleR Open source incluent des jeux de données intégrés qui vous permettent de créer et d’exécuter un script à l’aide de données pré-installées. Recherchez-les dans \Program files\Microsoft SQL Server\140\R_SERVER\library\datasets et \library\RevoScaleR. |
| Packages Python | [**revoscalepy**](../python/ref-py-revoscalepy.md) est la bibliothèque principale de Python extensible avec fonctions de manipulation, de transformation, de visualisation et d’analyse des données. <br/>[**microsoftml**](../python/ref-py-microsoftml.md) ajoute des algorithmes de machine learning pour créer des modèles personnalisés pour l’analyse de texte, l’analyse d’images et l’analyse des sentiments.  |
| Outils python | L’outil de ligne de commande python intégré est utile pour les tâches et les tests ad hoc. Recherchez l’outil dans \Program files\Microsoft SQL Server\140\PYTHON_SERVER\python.exe. |
| Anaconda | Anaconda est une distribution Open source de packages Python et essentiels. |
| Exemples et scripts Python | Comme avec R, Python comprend des jeux de données et des scripts intégrés. Recherchez les données revoscalepy dans le dossier \Program files\Microsoft SQL Server\140\PYTHON_SERVER\lib\site-packages\revoscalepy\data\sample-data. |
| Modèles pré-formés dans R et Python | Des modèles préformés sont créés pour des cas d’usage spécifiques et gérés par l’équipe d’ingénierie de science des données chez Microsoft. Vous pouvez utiliser les modèles préformés tels quels pour noter des sentiments positifs et négatifs dans du texte, ou pour détecter des fonctionnalités dans des images, en utilisant de nouvelles entrées de données que vous fournissez. Les modèles préformés sont pris en charge et utilisables sur un serveur autonome, mais vous ne pouvez pas les installer via le programme d’installation de SQL Server. Pour plus d’informations, consultez [installer des modèles machine learning préformés sur SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="using-a-standalone-server"></a>Utilisation d’un serveur autonome

En général, les développeurs r et Python choisissent un serveur autonome pour aller au-delà de la mémoire et des contraintes de traitement des R et Python Open source. Les bibliothèques R et Python qui s’exécutent sur un serveur autonome peuvent charger et traiter de grandes quantités de données sur plusieurs cœurs et agréger les résultats dans une sortie consolidée unique. Les fonctions hautes performances sont conçues pour la mise à l’échelle et l’utilitaire: la diffusion d’analyses prédictives, de modélisations statistiques, de visualisations de données et d’algorithmes de Machine Learning de pointe dans un produit commercial conçu et pris en charge par Librairie.

En tant que serveur indépendant découplé de SQL Server, l’environnement R et Python est configuré, sécurisé et accessible à l’aide du système d’exploitation sous-jacent et des outils standard fournis sur le serveur autonome, et non SQL Server. Il n’existe aucune prise en charge intégrée pour SQL Server données relationnelles. Si vous souhaitez utiliser SQL Server données, vous pouvez créer des objets et des connexions de source de données comme vous le feriez avec n’importe quel client.

Comme complément à SQL Server, un serveur autonome est également utile en tant qu’environnement de développement puissant si vous avez besoin de l’informatique locale et à distance. Les packages R et Python sur un serveur autonome sont les mêmes que ceux fournis avec une installation du moteur de base de données, ce qui permet la portabilité du code et le basculement du [contexte de calcul](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).

## <a name="how-to-get-started"></a>Prise en main

Commencez par le programme d’installation, attachez les fichiers binaires à votre outil de développement favori et écrivez votre premier script.

### <a name="step-1-install-the-software"></a>Étape 1 : Installer le logiciel

Installez l’une des versions suivantes:

+ [SQL Server 2017 Machine Learning Server (autonome)](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Server (autonome)-R uniquement](../install/sql-r-standalone-windows-install.md)

### <a name="step-2-configure-a-development-tool"></a>Étape 2 : Configurer un outil de développement

Sur un serveur autonome, il est courant de travailler localement à l’aide d’un développement installé sur le même ordinateur.

+ [Configurer les outils R](set-up-a-data-science-client.md)
+ [Configurer les outils Python](../python/setup-python-client-tools-sql.md)

### <a name="step-3-write-your-first-script"></a>Étape 3 : Écrire votre premier script

Écrivez des scripts R ou python à l’aide de fonctions de RevoScaleR, revoscalepy et des algorithmes Machine Learning.
  
  + [Explorez R et RevoScaleR dans 25 fonctions](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): Commencez avec les commandes R de base, puis progressez vers les fonctions analytiques distribuable RevoScaleR qui offrent des performances et une mise à l’échelle élevées aux solutions R. Inclut des versions parallélisables des packages de modélisation R les plus populaires comme le clustering k-means, les arbres de décision, les forêts de décision et les outils de manipulation des données.

  + [Démarrage rapide : Exemple de classification binaire avec le package](https://docs.microsoft.com/machine-learning-server/python/quickstart-binary-classification-with-microsoftml)python microsoftml: Créez un modèle de classification binaire à l’aide des fonctions de microsoftml et du jeu de données du cancer du sein connu.

Choisissez la meilleure langue pour la tâche. R est idéal pour les calculs statistiques qui sont difficiles à implémenter à l’aide de SQL. Pour les opérations basées sur des ensembles sur des données, tirez parti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la puissance de pour atteindre des performances maximales. Utilisez le moteur de base de données en mémoire pour les calculs très rapides sur les colonnes.

### <a name="step-4-operationalize-your-solution"></a>Étape 4 : Rendre votre solution opérationnelle

Les serveurs autonomes peuvent utiliser la fonctionnalité de [fonctionnement](https://docs.microsoft.com//machine-learning-server/what-is-operationalization) du [Microsoft machine learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)non-SQL. Vous pouvez configurer un serveur autonome pour la configuration, ce qui offre les avantages suivants: déployer et héberger votre code en tant que services Web, exécuter des diagnostics, tester la capacité du service Web.

### <a name="step-5-maintain-your-server"></a>Étape 5 : Gérer votre serveur

SQL Server publie des mises à jour cumulatives régulièrement. L’application des mises à jour cumulatives ajoute une sécurité et des améliorations fonctionnelles à une installation existante. 

Pour obtenir une description des fonctionnalités nouvelles ou modifiées, consultez l’article [téléchargements CAB](../install/sql-ml-cab-downloads.md) et les pages web pour [SQL Server mises à jour cumulatives 2016](https://support.microsoft.com/help/3177312/sql-server-2016-build-versions) et [SQL Server mises à jour cumulatives 2017](https://support.microsoft.com/help/4047329). 

Pour plus d’informations sur la façon d’appliquer des mises à jour à une instance existante, consultez [appliquer des mises à jour](../install/sql-machine-learning-standalone-windows-install.md#apply-cu) dans les instructions d’installation.

## <a name="see-also"></a>Voir aussi

 [Installer R Server (autonome) ou Machine Learning Server (autonome)](../install/sql-machine-learning-standalone-windows-install.md)

