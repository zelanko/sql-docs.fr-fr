---
title: SQL Server Machine Learning Server (autonome) et R Server (autonome) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a8cdceabc26c55b6eade57712fa610d3e84808f5
ms.sourcegitcommit: c37da15581fb34250d426a8d661f6d0d64f9b54c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39174786"
---
# <a name="sql-server-machine-learning-server-standalone-and-r-server-standalone"></a>SQL Server Machine Learning Server (autonome) et R Server (autonome)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Un serveur autonome est une installation de composants d’apprentissage automatique, exprimées en tant que fonctionnalités R et Python, qui s’exécutent indépendamment des instances de moteur de base de données SQL Server. Vous pouvez installer un serveur autonome en lui-même, sans dépendances sur SQL Server. Car un serveur autonome est indépendant de SQL Server, configuration et administration des tâches et outils sont plus similaires à une version non-SQL de Machine Learning Server, vous pouvez découvrir dans [cet article](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server).

L’objectif d’une machine de formation autonome server consiste à fournir un environnement de développement riche en fonctionnalités, avec le traitement des charges de travail R et Python sur des jeux de données petites et grandes, à l’aide des packages propriétaires et les moteurs de calcul parallèle et distribué installé avec le serveur. Les packages R et Python sur un serveur autonome sont les mêmes que celles fournies dans une installation de SQL Server (en base de données), facilitant ainsi la portabilité du code et [changement de contexte de calcul](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).

Les développeurs de la raison principale pour laquelle choisissent qu'une autonome machine learning server consiste à déplacer au-delà les contraintes de mémoire et le traitement de l’open source R et Python. Serveurs autonomes peuvent charger et traiter de grandes quantités de données sur plusieurs cœurs et agréger les résultats en une seule sortie consolidée. Les algorithmes et les fonctions sont conçues pour la mise à l’échelle et utilitaire : garantissant une analytique prédictive, modélisation statistique, des visualisations de données et pointe algorithmes machine learning dans un produit commercial serveur conçu et pris en charge par Microsoft.

En règle générale, nous vous recommandons de traiter (autonome) et (en base de données) installations mutuellement exclusif afin d’éviter les conflits de ressources, mais si vous disposez de suffisamment de ressources, il n’existe aucune interdiction par rapport à les installer à la fois sur le même ordinateur physique.

Vous ne pouvez avoir qu’un serveur autonome sur l’ordinateur : soit [SQL Server 2017 Machine Learning Server (autonome)](../install/sql-machine-learning-standalone-windows-install.md) ou [SQL Server 2016 R Server (autonome)](../install/sql-r-standalone-windows-install.md). Vous devez désinstaller manuellement une version avant d’installer une version différente.

## <a name="components-of-a-standalone-server"></a>Composants d’un serveur autonome

SQL Server 2016 est R uniquement. SQL Server 2017 prend en charge R et Python. Le tableau suivant décrit les fonctionnalités de chaque version.

| Composant | Description |
|-----------|-------------|
| Packages R | [RevoScaleR](revoscaler-overview.md) est la bibliothèque principale pour R évolutive avec des fonctions de manipulation de données, transformation, visualzation et l’analyse.  <br/>[MicrosoftML (R)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) ajoute des algorithmes d’apprentissage automatique pour créer des modèles personnalisés pour l’analyse de texte, l’analyse de l’image et l’analyse des sentiments. <br/>[mrsdeploy](operationalization-with-mrsdeploy.md) offres web déploiement de service (dans SQL Server 2017 uniquement). <br/>[olapR](how-to-create-mdx-queries-using-olapr.md) permet de spécifier des requêtes MDX dans R.|
| Microsoft R Open (MRO) | [MRO](https://mran.microsoft.com/open) est open source distribution Microsoft de R. Le package et un interpréteur sont inclus. Utilisez toujours la version de MRO fournie dans le programme d’installation. |
| Outils R | Invites de commandes et fenêtres de console R sont des outils standard dans une distribution de R. Les trouver à \Program files\Microsoft SQL Server\140\R_SERVER\bin\x64. |
| Exemples de R et scripts |  Les packages RevoScaleR et R Open source incluent les jeux de données intégrées afin que vous pouvez créer et exécuter le script à l’aide de données préinstallées. Examinez les \Program files\Microsoft SQL Server\140\R_SERVER\library\datasets et \library\RevoScaleR. |
| Packages Python | [revoscalepy](../python/what-is-revoscalepy.md) est la bibliothèque principale pour Python et évolutive avec des fonctions de manipulation de données, transformation, visualzation et l’analyse. <br/>[microsoftml (Python)](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) ajoute des algorithmes d’apprentissage automatique pour créer des modèles personnalisés pour l’analyse de texte, l’analyse de l’image et l’analyse des sentiments.  |
| Outils Python | L’outil de ligne de commande Python intégré est utile pour les tests ad hoc et tâches. Recherchez l’outil à \Program files\Microsoft SQL Server\140\PYTHON_SERVER\python.exe. |
| Anaconda | Anaconda est une distribution open source de Python et les packages essentiels. |
| Scripts et des exemples Python | Comme avec R, Python inclut des jeux de données intégrés et des scripts. Rechercher les données de revoscalepy à Files\Microsoft SQL Server\140\PYTHON_SERVER\lib\site-packages\revoscalepy\data\sample-data. |
| Modèles préentraînés dans R et Python | Modèles préentraînés sont pris en charge et utilisable sur un serveur autonome, mais vous ne pouvez pas les installer via le programme d’installation de SQL Server. Le programme d’installation de Microsoft Machine Learning Server fournit les modèles, vous pouvez installer gratuitement. Pour plus d’informations, consultez [installation préformé modèles d’apprentissage automatique sur SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="get-started-step-by-step"></a>Prise en main de pas à pas

Démarrer avec le programme d’installation, attacher les fichiers binaires à votre outil de développement favori et écrire votre premier script.

### <a name="step-1-install-the-software"></a>Étape 1 : Installer le logiciel

Installer l’une de ces versions :

+ [SQL Server 2017 Machine Learning Server (autonome)](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Server (autonome) - R uniquement](../install/sql-r-standalone-windows-install.md)

### <a name="step-2-configure-a-development-tool"></a>Étape 2 : Configurer un outil de développement

Configurer vos outils de développement pour utiliser les fichiers binaires de Machine Learning Server. Pour plus d’informations sur Python, consultez [les binaires Python de lien](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools). Pour obtenir des instructions sur la façon de se connecter dans R Studio, consultez [à l’aide de différentes Versions de R](https://support.rstudio.com/hc/en-us/articles/200486138-Using-Different-Versions-of-R) et pointez l’outil sur C:\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64. Vous pouvez également essayer [outils R pour Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation). 

### <a name="step-3-write-your-first-script"></a>Étape 3 : Écrire votre premier script

Écrire un script R ou Python à l’aide de fonctions à partir de RevoScaleR et revoscalepy algorithmes d’apprentissage.
  
  + [Découvrir R and RevoScaleR in 25 Functions](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): démarrer avec les commandes de base R, puis de progression pour les fonctions analytiques distribuables RevoScaleR qui offrent des performances élevées et de mise à l’échelle vers des solutions R. Inclut des versions parallélisables des packages de modélisation R les plus populaires comme le clustering k-means, les arbres de décision, les forêts de décision et les outils de manipulation des données.

  + [Démarrage rapide : Un exemple de classification binaire avec le package de Python microsoftml](https://docs.microsoft.com/machine-learning-server/python/quickstart-binary-classification-with-microsoftml): créer un modèle de classification binaire en utilisant les fonctions de microsoftml et le jeu de données du cancer du sein bien connu.

Choisir le meilleur langage pour la tâche. R est idéal pour les calculs statistiques qui sont difficiles à implémenter à l’aide de SQL. Pour les opérations de jeu basé sur les données, tirez parti des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour optimiser les performances. Utiliser le moteur de base de données en mémoire pour effectuer des calculs très rapides sur les colonnes.

### <a name="step-4-operationalize-your-solution"></a>Étape 4 : Rendre opérationnel votre solution

Serveurs autonomes peuvent utiliser le [Opérationnalisation](https://docs.microsoft.com//machine-learning-server/what-is-operationalization) fonctionnalités de la non SQL-personnalisée [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server). Vous pouvez configurer un serveur autonome pour l’Opérationnalisation, ce qui vous offre ces avantages : déployer et héberger votre code, comme les services web, exécutez les diagnostics, tester la capacité du service web.

## <a name="see-also"></a>Voir aussi

 [SQL Server Machine Learning Services (en base de données)](sql-server-r-services.md)

