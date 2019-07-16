---
title: Présentation du didacticiel SQL Server R - SQL Server Machine Learning
description: Introduction aux didacticiels de langage R pour l’analytique en base de données de SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 467c9320880f1b113cecd36101345f6ee99f7b75
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961932"
---
# <a name="sql-server-r-language-tutorials"></a>Didacticiels sur le langage SQL Server R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit les didacticiels de langage R pour la base de données analytique sur [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) ou [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md).

+ Apprenez à encapsuler et exécuter le code R dans les procédures stockées.
+ Sérialiser et enregistrer des modèles basés sur r aux bases de données SQL Server.
+ En savoir plus sur les contextes de calcul locaux et distants et quand les utiliser.
+ Explorez les bibliothèques Microsoft R pour la science des données et les tâches d’apprentissage.

<a name="bkmk_sqltutorials"></a>

## <a name="r-quickstarts-and-tutorials"></a>Didacticiels et guides de démarrage rapide R

| Lien | Description |
|------|-------------|
| [Démarrage rapide : À l’aide de R dans T-SQL](rtsql-using-r-code-in-transact-sql-quickstart.md) | Première de plusieurs guides de démarrage rapide, avec celle-ci illustrant la syntaxe de base pour appeler une fonction R à l’aide d’un éditeur de requête T-SQL comme SQL Server Management Studio. |
| [Tutoriel : Découvrez l’analytique de R en base de données pour les scientifiques de données](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | Pour les développeurs R familiarisés avec SQL Server, ce didacticiel explique comment effectuer les tâches de science des données courantes dans SQL Server. Charger et visualiser les données, former et enregistrer un modèle dans SQL Server et utiliser le modèle pour l’analytique prédictive. |
| [Tutoriel : Découvrez l’analytique de R en base de données pour les développeurs SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md) | Générer et déployer une solution complète de R, à l’aide uniquement [!INCLUDE[tsql](../../includes/tsql-md.md)] outils. Se concentre sur le déplacement d’une solution en production. Vous découvrirez comment encapsuler du code R dans une procédure stockée, enregistrer un modèle R dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et effectuer des appels paramétrables au modèle R pour la prédiction. |
| [Tutoriel : Présentation approfondie RevoScalepR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) | Découvrez comment utiliser les fonctions dans les packages RevoScaleR. Déplacer des données entre R et SQL Server et commutateur contextes de calcul pour répondre à une tâche particulière. Créer des modèles et des tracés et déplacez-les entre votre environnement de développement et le serveur de base de données. |

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Exemples de code

| Lien | Description |
|------|-------------|
| [Créer un modèle prédictif à l’aide de R et SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Découvrez comment une entreprise de location de skis peut utiliser machine learning pour prédire les locations à venir, qui permet du plan d’activités et du personnel pour répondre à la demande future. |
| [Exécuter le client clustering à l’aide de R et SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Utiliser l’apprentissage non supervisé pour segmenter les clients basés sur les données de ventes. |

## <a name="see-also"></a>Voir aussi

+ [Extension de R vers SQL Server](../concepts/extension-r.md)
+ [Didacticiels de SQL Server Machine Learning Services](machine-learning-services-tutorials.md)

