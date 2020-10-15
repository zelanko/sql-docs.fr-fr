---
title: Qu’est-ce qu’une instance Machine Learning Server ou R Server autonome ?
description: Découvrez les différences entre R Server et Machine Learning Server dans la configuration de SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 08/13/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 342c9bd2f83fed2b74cbce1f5ea7b7d942e9fd63
ms.sourcegitcommit: afb02c275b7c79fbd90fac4bfcfd92b00a399019
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91956910"
---
# <a name="what-are-standalone-machine-learning-server-or-r-server-in-sql-server"></a>Qu’est-ce qu’une instance Machine Learning Server ou R Server autonome dans SQL Server ?
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

SQL Server prend en charge l’installation d’une instance R Server ou Machine Learning Server autonome qui s’exécute indépendamment de SQL Server. En fonction de votre version de SQL Server, un serveur autonome a une base R open source et possiblement Python, superposé de bibliothèques hautes performances de Microsoft qui ajoutent des analyses prédictives et statistiques à l’échelle. Les bibliothèques permettent également d’effectuer des tâches d’apprentissage automatique dans R ou Python. 

Dans SQL Server 2016, cette fonctionnalité est appelée **R Server (autonome)** et prend uniquement en charge R. Dans SQL Server 2017, elle s’appelle **Machine Learning Server (autonome)** inclut R et Python.  

> [!Note]
> Comme il est installé par le programme d’installation SQL Server, un serveur autonome est fonctionnellement équivalent aux versions non-SQL de [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server), prenant en charge les mêmes scénarios utilisateur, y compris l’exécution à distance, l’opérationnalisation et les services Web, et la collection complète de bibliothèques R et Python.

## <a name="components"></a>Components

SQL Server 2016 prend uniquement en charge R. SQL Server 2017 prend en charge R et Python. Le tableau ci-dessous décrit les fonctionnalités de chaque version.

| Composant | Description |
|-----------|-------------|
| Packages R | [**RevoScaleR**](ref-r-revoscaler.md) est la bibliothèque principale pour l’évolution de R avec des fonctions pour la manipulation, la transformation, la visualisation et l’analyse des données.  <br/>[**MicrosoftML**](ref-r-microsoftml.md) ajoute des algorithmes d’apprentissage automatique pour créer des modèles personnalisés pour l’analyse des textes, l’analyse des images et l’analyse des sentiments. <br/>[**sqlRUtils**](ref-r-sqlrutils.md) fournit des fonctions d’assistance permettant de placer leurs scripts R dans une procédure stockée T-SQL, d’inscrire cette procédure auprès d’une base de données, et d’exécuter la procédure stockée à partir d’un environnement de développement R.<br/>[**olapR**](ref-r-olapr.md) permet de spécifier des requêtes MDX dans R.|
| Microsoft R Open (MRO) | [**MRO**](https://mran.microsoft.com/open) est la distribution Open source Microsoft de R. Le package et l’interpréteur sont inclus. Utilisez toujours la version de MRO groupée dans le programme d’installation. |
| Outils R | Les invites de commandes et les fenêtres de console R sont des outils standard dans une distribution R. Retrouvez-les dans \Program files\Microsoft SQL Server\140\R_SERVER\bin\x64. |
| Scripts et exemples R |  Les packages R et RevoScaleR Open source incluent des jeux de données intégrés qui vous permettent de créer et d’exécuter un script à l’aide de données pré-installées. Retrouvez-les dans \Program files\Microsoft SQL Server\140\R_SERVER\library\datasets et \library\RevoScaleR. |
| Packages Python | [**revoscalepy**](../python/ref-py-revoscalepy.md) est la bibliothèque principale pour l’évolution de Python avec des fonctions pour la manipulation, la transformation, la visualisation et l’analyse des données. <br/>[**microsoftml**](../python/ref-py-microsoftml.md) ajoute des algorithmes d’apprentissage automatique pour créer des modèles personnalisés pour l’analyse des textes, l’analyse des images et l’analyse des sentiments.  |
| Outils Python | L’outil en ligne de commande Python intégré est utile pour les tâches et les tests ad hoc. Retrouvez l’outil dans \Program files\Microsoft SQL Server\140\PYTHON_SERVER\python.exe. |
| Anaconda | Anaconda est une distribution open source de packages essentiels et Python. |
| Scripts et exemples Python | Comme avec R, Python comprend des jeux de données et des scripts intégrés. Retrouvez les données revoscalepy dans Program files\Microsoft SQL Server\140\PYTHON_SERVER\lib\site-packages\revoscalepy\data\sample-data. |
| Modèles préformés dans R et Python | Les modèles préformés sont créés pour des cas d’usage spécifiques et gérés par l’équipe d’ingénierie de science des données chez Microsoft. Vous pouvez utiliser les modèles préformés tels quels pour procéder au scoring des sentiments positifs-négatifs dans le texte ou détecter des caractéristiques dans des images, à l’aide des nouvelles entrées de données que vous fournissez. Les modèles préformés sont pris en charge et utilisables sur un serveur autonome, mais vous ne pouvez pas les installer via le programme d’installation SQL Server. Pour plus d’informations, consultez [Installer des modèles de Machine Learning préformés sur SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="using-a-standalone-server"></a>Utilisation d’un serveur autonome

En général, les développeurs R et Python choisissent un serveur autonome pour dépasser les limites de Python et R open source en termes de traitement et de mémoire. Les bibliothèques R et Python qui s’exécutent sur un serveur autonome peuvent charger et traiter de grandes quantités de données sur plusieurs cœurs et agréger les résultats dans une sortie consolidée unique. Les fonctions hautes performances sont conçues pour la mise à l’échelle et l’utilitaire : elles permettent de fournir des analyses prédictives, des modélisations statistiques, des visualisations de données et des algorithmes d’apprentissage automatique de pointe dans un produit serveur commercial conçu et pris en charge par Microsoft.

En tant que serveur indépendant découplé de SQL Server, l’environnement R et Python est configuré, sécurisé et accessible à l’aide du système d’exploitation sous-jacent et des outils standard fournis dans le serveur autonome et non SQL Server. Il n’existe aucune prise en charge intégrée pour les données relationnelles SQL Server. Si vous souhaitez utiliser les données SQL Server, vous pouvez créer des connexions et des objets de source de données comme vous le feriez avec n’importe quel client.

En tant que complément de SQL Server, un serveur autonome est également utile en tant qu’environnement de développement puissant si vous avez besoin d’effectuer des calculs en local et à distance. Les packages R et Python sur un serveur autonome sont les mêmes que ceux fournis avec une installation de moteur de base de données, ce qui permet la portabilité du code et le [basculement entre les contextes de calcul](/machine-learning-server/r/concept-what-is-compute-context).

## <a name="how-to-get-started"></a>Bien démarrer

Commencez avec l’installation, attachez les fichiers binaires à votre outil de développement favori et écrivez votre premier script.

### <a name="step-1-install-the-software"></a>Étape 1 : Installer le logiciel

Installez l’une des versions suivantes :

+ [SQL Server 2017 Machine Learning Server (autonome)](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Server (autonome) - prise en charge de R uniquement](../install/sql-machine-learning-standalone-windows-install.md?view=sql-server-2016)

### <a name="step-2-configure-a-development-tool"></a>Étape 2 : Configurer un outil de développement

Sur un serveur autonome, il est courant de travailler localement à l’aide d’un développement installé sur le même ordinateur.

+ [Configurer les outils R](set-up-a-data-science-client.md)
+ [Configurer les outils Python](../python/setup-python-client-tools-sql.md)

### <a name="step-3-write-your-first-script"></a>Étape 3 : Écrire votre premier script R

Écrivez un script R ou Python à l’aide des fonctions de RevoScaleR, revoscalepy, et des algorithmes d’apprentissage automatique.
  
  + [Basic R commands and RevoScaleR functions: 25 common examples](/machine-learning-server/r/tutorial-r-to-revoscaler) (Fonctions RevoScaleR et commandes R de base : 25 exemples courants) : commencez avec des commandes R de base pour ensuite découvrir les fonctions analytiques distribuables RevoScaleR qui offrent des performances élevées et la mise à l’échelle vers des solutions R. Inclut des versions parallélisables des packages de modélisation R les plus populaires comme le clustering k-means, les arbres de décision, les forêts de décision et les outils de manipulation des données.

  + [Démarrage rapide : An example of binary classification with the microsoftml Python package](/machine-learning-server/python/quickstart-binary-classification-with-microsoftml) (Un exemple de classification binaire avec le package microsoftml Python) : créez un modèle de classification binaire à l’aide des fonctions de microsoftml et du jeu de données sur le cancer du sein connu.

Choisissez le meilleur langage pour la tâche. R est plus adapté pour effectuer des calculs statistiques difficiles à implémenter avec SQL. Pour les opérations de données basées sur des ensembles de données, tirez parti de la puissance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour un maximum de performances. Utilisez le moteur de base de données en mémoire pour effectuer des calculs très rapides sur des colonnes.

### <a name="step-4-operationalize-your-solution"></a>Étape 4 : Opérationnaliser votre solution

Les serveurs autonomes peuvent utiliser la fonctionnalité [d’opérationnalisation](//machine-learning-server/what-is-operationalization) de la version non SQL de [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server). Vous pouvez configurer un serveur autonome pour l’opérationnalisation, qui offre les avantages suivants : le déploiement et l’hébergement de votre code en tant que services web, l’exécution de diagnostics et le test de la capacité du service web.

### <a name="step-5-maintain-your-server"></a>Étape 5 : Maintenir vos serveurs

SQL Server publie régulièrement des mises à jour cumulatives. L’application des mises à jour cumulatives ajoute des améliorations fonctionnelles et de sécurité à une installation existante. 

Pour obtenir une description des fonctionnalités nouvelles ou modifiées, consultez l’article [Téléchargements CAB pour les mises à jour cumulatives des instances d’analyse en base de données SQL Server](../install/sql-ml-cab-downloads.md) et les pages web sur les [mises à jour cumulatives de SQL Server 2016](https://support.microsoft.com/help/3177312/sql-server-2016-build-versions) et les [mises à jour cumulatives de SQL Server 2017](https://support.microsoft.com/help/4047329). 

Pour plus d’informations sur l’application des mises à jour sur une instance existante, consultez la section [Appliquer des mises à jour](../install/sql-machine-learning-standalone-windows-install.md#apply-cu) dans les instructions d’installation.

## <a name="see-also"></a>Voir aussi

 [Installer Machine Learning Server (autonome) ou R Server (autonome) en utilisant le programme d’installation de SQL Server](../install/sql-machine-learning-standalone-windows-install.md)