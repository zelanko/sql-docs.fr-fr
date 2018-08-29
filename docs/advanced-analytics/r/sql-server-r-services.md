---
title: R Services dans SQL Server 2016 | Microsoft Docs
description: Présentation de vue d’ensemble pour les Services SQL Server, R prend en charge pour la base de données analytique
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/27/2018
ms.topic: overview
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 9be6cf7b38482673db0308b4680500dede313e09
ms.sourcegitcommit: e4e9f02b5c14f3bb66e19dec98f38c012275b92c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43118337"
---
# <a name="r-services-in-sql-server-2016"></a>R Services dans SQL Server 2016
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2016 R Services est un module complémentaire à une instance du moteur de base de données, utilisé pour l’exécution de code R sur SQL Server. Code s’exécute dans une infrastructure d’extensibilité, isolé des processus de moteur de base, mais totalement disponibles pour les données relationnelles comme des procédures stockées, en tant que script T-SQL qui contient des instructions de R ou en tant que code R contenant de T-SQL. 

R Services inclut une distribution de base de R, superposée aux packages R d’entreprise à partir de Microsoft afin que vous pouvez charger et traiter de grandes quantités de données sur plusieurs cœurs et agréger les résultats en une seule sortie consolidée. Algorithmes et des fonctions R de Microsoft sont conçues pour la mise à l’échelle et utilitaire : garantissant une analytique prédictive, modélisation statistique, des visualisations de données et pointe algorithmes machine learning dans un produit commercial server conçu et prise en charge par Microsoft. 

Les bibliothèques R incluent RevoScaleR, MicrosoftML et autres. Étant donné que R Services est intégré avec le moteur de base de données, vous pouvez conserver analytique proche des données et éliminer les coûts et les risques de sécurité associés au transfert de données.

## <a name="components"></a>Components

SQL Server 2016 est R uniquement. Le tableau suivant décrit les fonctionnalités de SQL Server 2016.

| Composant | Description |
|-----------|-------------|
| Service SQL Server Launchpad | Un service qui gère les communications entre les runtimes R externes et de l’instance de SQL Server. |
| Packages R | [**RevoScaleR** ](revoscaler-overview.md) est la bibliothèque principale pour Scalable fonctions R. dans cette bibliothèque sont parmi les plus couramment utilisées. Transformations de données et de manipulation, de synthèse statistique, de visualisation et de nombreuses formes de modélisation et les analyses sont trouvent dans ces bibliothèques. En outre, les fonctions dans ces bibliothèques distribuer automatiquement les charges de travail entre les cœurs disponibles pour le traitement parallèle, avec la possibilité de travailler sur des segments de données coordonnées et gérées par le moteur de calcul.  <br/>[**MicrosoftML (R)** ](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) ajoute des algorithmes d’apprentissage automatique pour créer des modèles personnalisés pour l’analyse de texte, l’analyse de l’image et l’analyse des sentiments. <br/>[**sqlRUtils** ](generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md) fournit des fonctions d’assistance pour placer des scripts R dans une procédure stockée T-SQL, l’inscription d’une procédure stockée avec une base de données et l’exécution de la procédure stockée à partir d’un environnement de développement R.<br/>[**olapR** ](how-to-create-mdx-queries-using-olapr.md) permet de spécifier des requêtes MDX dans R.|
| Microsoft R Open (MRO) | [**MRO** ](https://mran.microsoft.com/open) est open source distribution Microsoft de R. Le package et un interpréteur sont inclus. Utilisez toujours la version de MRO installé par le programme d’installation. |
| Outils R | Invites de commandes et fenêtres de console R sont des outils standard dans une distribution de R.  |
| Exemples de R et scripts |  Les packages RevoScaleR et R Open source incluent les jeux de données intégrées afin que vous pouvez créer et exécuter le script à l’aide de données préalablement installées |
| Modèles préentraînés dans R | Modèles préentraînés sont créés pour les cas d’usage spécifiques et gérés par l’équipe d’ingénierie science des données chez Microsoft. Vous pouvez utiliser les modèles préformés comme-consiste à noter les sentiments négatifs positif dans le texte, ou à détecter les fonctionnalités dans des images, à l’aide de nouvelles entrées de données que vous fournissez. Les modèles s’exécutent dans les Services R, mais ne peut pas être installés via le programme d’installation de SQL Server. Pour plus d’informations, consultez [installation préentraîné modèles d’apprentissage sur SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="how-to-get-started"></a>La prise en main

Démarrer avec le programme d’installation, attacher les fichiers binaires à votre outil de développement favori et écrire votre premier script.

**Étape 1 :** installer et configurer le logiciel. 

+ [Installer SQL Server 2016 R Services (en base de données)](../install/sql-r-services-windows-install.md)

**Étape 2 :** acquérir une expérience pratique en utilisant l’un de ces didacticiels :

+ [: Didacticiel analytique en base de données à l’aide de R](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Didacticiel : Procédure pas à pas End-to-end avec R](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

**Étape 3 :** ajouter vos packages R favoris et les utiliser avec des packages fournis par Microsoft

+ [Gestion des packages R pour SQL Server](install-additional-r-packages-on-sql-server.md)


## <a name="see-also"></a>Voir aussi

 [Installer SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
