---
title: Tutoriels sur R
description: Présentation des didacticiels sur le langage R pour l’analyse dans la base de données SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 62264f728fec5b68c3034fb3c6260f04617353b5
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "81116112"
---
# <a name="sql-server-r-language-tutorials"></a>Didacticiels sur le langage R SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article décrit les didacticiels sur le langage R pour l’analyse dans la base de données sur [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) ou [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md).

+ Découvrez comment inclure dans un wrapper et exécuter le code R dans des procédures stockées.
+ Sérialisez et enregistrez les modèles basés sur R dans des bases de données SQL Server.
+ Apprenez-en plus sur les contextes de calcul distants et locaux et leur utilisation.
+ Explorez les bibliothèques Microsoft R pour les tâches de science des données et d’apprentissage automatique.

<a name="bkmk_sqltutorials"></a>

## <a name="r-quickstarts-and-tutorials"></a>Didacticiels et démarrages rapides sur R

| Lien | Description |
|------|-------------|
| [Démarrage rapide : Créer et exécuter des scripts R simples avec SQL Server Machine Learning Services](quickstart-r-create-script.md) | Le premier de nombreux démarrages rapides. Il illustre la syntaxe de base pour appeler une fonction R à l’aide d’un éditeur de requête T-SQL tel que SQL Server Management Studio. |
| [Tutoriel : Développement SQL pour les scientifiques de données R](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | Pour les développeurs R qui débutent avec SQL Server, ce didacticiel explique comment effectuer des tâches courantes de science des données dans SQL Server. Celles-ci comprennent le chargement et la visualisation des données, la formation et l’enregistrement d’un modèle dans SQL Server, et l’utilisation du modèle pour l’analyse prédictive. |
| [Tutoriel : Analyse des données R pour les développeurs SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md) | Créez et déployez une solution R complète à l’aide d’outils [!INCLUDE[tsql](../../includes/tsql-md.md)] uniquement. Se concentre sur le déplacement d’une solution en production. Vous découvrirez comment encapsuler du code R dans une procédure stockée, enregistrer un modèle R dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et effectuer des appels paramétrables au modèle R pour la prédiction. |
| [Tutoriel : Présentation approfondie de RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) | Découvrez comment utiliser les fonctions des packages RevoScaleR. Déplacez des données entre R et SQL Server, et basculez entre les contextes de calcul pour les adapter à une tâche particulière. Créez des tracés et des modèles, et déplacez-les entre votre environnement de développement et le serveur de base de données. |

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Exemples de code

| Lien | Description |
|------|-------------|
| [Build a predictive model using R and SQL Server ML Services](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) (Créer un modèle prédictif à l’aide de R et SQL Server ML Services) | Découvrez comment une entreprise de location de skis peut utiliser Machine Learning pour prédire les locations à venir, ce qui permet au plan d’entreprise et au personnel de répondre aux demandes futures. |
| [Perform customer clustering using R and SQL Server ML Services](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) (Effectuer un clustering de clients à l’aide de R et SQL Server ML Services) | Utilisez l’apprentissage non supervisé pour segmenter les clients en fonction des données de ventes. |

## <a name="see-also"></a>Voir aussi

+ [Extension du langage R dans SQL Server](../concepts/extension-r.md)