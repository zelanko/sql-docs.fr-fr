---
title: Présentation du didacticiel Python de SQL Server 2017 - SQL Server Machine Learning
description: Introduction aux didacticiels Python pour l’analytique en base de données de SQL Server 2017.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: d5a434b6e089cd77a2bd685506e5552c4e1e7f6d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961946"
---
# <a name="sql-server-2017-python-tutorials"></a>Didacticiels de SQL Server 2017 Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit les didacticiels Python pour la base de données analytique sur [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md). 

+ Apprenez à encapsuler et exécuter le code Python dans les procédures stockées.
+ Sérialiser et enregistrer des modèles basés sur Python aux bases de données SQL Server.
+ En savoir plus sur les contextes de calcul locaux et distants et quand les utiliser.
+ Explorez les modules Python Microsoft pour la science des données et les tâches d’apprentissage.

<a name="bkmk_pythontutorials"></a>

## <a name="python-quickstarts-and-tutorials"></a>Didacticiels et guides de démarrage rapide Python

| Lien | Description |
|------|-------------|
| [Démarrage rapide : Script Python « Hello world » dans SQL Server](quickstart-python-run-using-t-sql.md) | Découvrez les principes fondamentaux de l’appel de Python dans T-SQL. |
| [Démarrage rapide : Créer, former et utiliser un modèle Python avec des procédures stockées dans SQL Server](quickstart-python-train-score-in-tsql.md) | Explique les mécanismes d’incorporation de code Python dans une procédure stockée, en fournissant des entrées et l’exécution de procédure stockée. |
| [Tutoriel : Créer un modèle à l’aide de revoscalepy](use-python-revoscalepy-to-create-model.md) | Montre comment exécuter du code à partir d’un terminal de Python à distance, à l’aide du contexte de calcul de SQL Server. Vous devez connaître un peu avec les environnements et outils de Python. Exemple de code est fourni qui crée un modèle à l’aide **rxLinMod**, à partir du nouveau **revoscalepy** bibliothèque. |
| [Tutoriel : Découvrez l’analytique de Python dans base de données pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md) | Cette procédure pas à pas de bout en bout montre le processus de génération d’une solution complète de Python à l’aide de procédures stockées T-SQL. Tout le code Python est inclus.|

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Exemples de code

Ces exemples et les démonstrations fournies par l’équipe de développement SQL Server mettez en surbrillance les façons dont vous pouvez utiliser analytique incorporée dans les applications réelles.

| Lien | Description |
|------|-------------|
| [Créer un modèle prédictif à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | Découvrez comment une entreprise de location de skis peut utiliser machine learning pour prédire les locations à venir, qui permet du plan d’activités et du personnel pour répondre à la demande future. |
| [Exécuter le client clustering à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | Découvrez comment utiliser l’algorithme de Kmeans pour effectuer la mise en cluster non supervisé des clients. |

## <a name="see-also"></a>Voir aussi

+ [Extension Python pour SQL Server](../concepts/extension-python.md)
+ [Didacticiels de SQL Server Machine Learning Services](machine-learning-services-tutorials.md)
