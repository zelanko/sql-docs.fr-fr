---
title: R Services dans SQL Server 2016 - Machine Learning Services SQL Server
description: R dans SQL Server pour les tâches R intégrés sur les données relationnelles, y compris la science des données et modélisation statistique, analytique prédictive, visualisation des données et bien plus encore.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/10/2018
ms.topic: overview
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 14be74e19219fee834a4ab82e74c004a4e426483
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642325"
---
# <a name="r-services-in-sql-server-2016"></a>R Services dans SQL Server 2016
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

R Services est un module complémentaire à une instance de moteur de base de données SQL Server 2016, utilisé pour l’exécution de code R et des fonctions sur SQL Server. Code s’exécute dans une infrastructure d’extensibilité, isolé des processus de moteur de base, mais totalement disponibles pour les données relationnelles comme des procédures stockées, en tant que script T-SQL qui contient des instructions de R ou en tant que code R contenant de T-SQL. 

R Services inclut une distribution de base de R, superposée aux packages R d’entreprise à partir de Microsoft afin que vous pouvez charger et traiter de grandes quantités de données sur plusieurs cœurs et agréger les résultats en une seule sortie consolidée. Algorithmes et des fonctions R de Microsoft sont conçues pour la mise à l’échelle et utilitaire : garantissant une analytique prédictive, modélisation statistique, des visualisations de données et pointe algorithmes machine learning dans un produit commercial server conçu et prise en charge par Microsoft. 

Incluent les bibliothèques R [ **RevoScaleR**](ref-r-revoscaler.md), [ **MicrosoftML (R)**](ref-r-microsoftml.md)et d’autres. Étant donné que R Services est intégré avec le moteur de base de données, vous pouvez conserver analytique proche des données et éliminer les coûts et les risques de sécurité associés au transfert de données.

> [!Note]
> R Services a été renommé dans SQL Server 2017 à [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md), qui reflète l’ajout de Python.

## <a name="components"></a>Composants

SQL Server 2016 est R uniquement. Le tableau suivant décrit les fonctionnalités de SQL Server 2016.

| Composant | Description |
|-----------|-------------|
| Service SQL Server Launchpad | Un service qui gère les communications entre les runtimes R externes et de l’instance de SQL Server. |
| Packages R | [**RevoScaleR** ](ref-r-revoscaler.md) est la bibliothèque principale pour évolutive fonctions R. dans cette bibliothèque sont parmi les plus couramment utilisées. Transformations de données et de manipulation, de synthèse statistique, de visualisation et de nombreuses formes de modélisation et les analyses sont trouvent dans ces bibliothèques. En outre, les fonctions dans ces bibliothèques distribuer automatiquement les charges de travail entre les cœurs disponibles pour le traitement parallèle, avec la possibilité de travailler sur des segments de données coordonnées et gérées par le moteur de calcul.  <br/>[**MicrosoftML (R)** ](ref-r-microsoftml.md) ajoute des algorithmes d’apprentissage automatique pour créer des modèles personnalisés pour l’analyse de texte, l’analyse de l’image et l’analyse des sentiments. <br/>[**sqlRUtils** ](ref-r-sqlrutils.md) fournit des fonctions d’assistance pour placer des scripts R dans une procédure stockée T-SQL, l’inscription d’une procédure stockée avec une base de données et l’exécution de la procédure stockée à partir d’un environnement de développement R.<br/>[**olapR** ](ref-r-olapr.md) permet de spécifier des requêtes MDX dans R.|
| Microsoft R Open (MRO) | [**MRO** ](https://mran.microsoft.com/open) est open source distribution Microsoft de R. Le package et un interpréteur sont inclus. Utilisez toujours la version de MRO installé par le programme d’installation. |
| Outils R | Invites de commandes et fenêtres de console R sont des outils standard dans une distribution de R.  |
| Exemples de R et scripts |  Les packages RevoScaleR et R Open source incluent les jeux de données intégrées afin que vous pouvez créer et exécuter le script à l’aide de données préalablement installées |
| Modèles préentraînés dans R | Modèles préentraînés sont créés pour les cas d’usage spécifiques et gérés par l’équipe d’ingénierie science des données chez Microsoft. Vous pouvez utiliser les modèles préformés comme-consiste à noter les sentiments négatifs positif dans le texte, ou à détecter les fonctionnalités dans des images, à l’aide de nouvelles entrées de données que vous fournissez. Les modèles s’exécutent dans les Services R, mais ne peut pas être installés via le programme d’installation de SQL Server. Pour plus d’informations, consultez [installation préentraîné modèles d’apprentissage sur SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="using-r-services"></a>À l’aide de R Services

Analystes et les développeurs ont souvent le code qui s’exécute sur une instance de SQL Server locale. En ajoutant des Services Machine Learning et l’activation de l’exécution du script externe, vous avez la possibilité d’exécuter du code de R dans les modalités de SQL Server : encapsulant le script dans les procédures stockées, stocker des modèles dans une table SQL Server ou combinaison des fonctions T-SQL et R dans les requêtes.

L’approche la plus courante pour la base de données analytique consiste à utiliser [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), en passant de script R comme un paramètre d’entrée.

Interactions client-serveur classique sont une autre approche. À partir de n’importe quel client station de travail avec un IDE, vous pouvez installer [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)et ensuite écrire du code qui exécute un push de l’exécution (appelé un *contexte de calcul distant*) aux données et aux opérations à SQL à distance Serveur. 

Enfin, si vous utilisez un [serveur autonome](r-server-standalone.md) et l’édition développeur, vous pouvez créer des solutions sur une station de travail cliente à l’aide de la même interpréteurs et des bibliothèques et déployer le code de production sur SQL Server Machine Learning Services (en base de données). 

## <a name="how-to-get-started"></a>La prise en main

Démarrer avec le programme d’installation, attacher les fichiers binaires à votre outil de développement favori et écrire votre premier script.

**Étape 1 :** Installez et configurez le logiciel. 

+ [Installer SQL Server 2016 R Services (en base de données)](../install/sql-r-services-windows-install.md)

**Étape 2 :** Acquérez une expérience pratique en utilisant l’un de ces didacticiels :

+ [Tutoriel : Découvrez l’analytique en base de données à l’aide de R](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Tutoriel : Procédure pas à pas de bout en bout avec R](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

**Étape 3 :** Ajouter vos packages R favoris et les utiliser avec des packages fournis par Microsoft

+ [Gestion des packages R pour SQL Server](install-additional-r-packages-on-sql-server.md)


## <a name="see-also"></a>Voir aussi

 [Installer SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
