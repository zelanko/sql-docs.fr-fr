---
title: Tutoriels sur Python
description: Cet article décrit les didacticiels Python pour SQL Server Machine Learning Services. Découvrez comment exécuter des scripts Python. Générez, formez et déployez des modèles Python pour SQL Server. En savoir plus sur les contextes de calcul locaux et distants. Explorez les packages Microsoft Python pour la science des données et les Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/04/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: cd458727fad637414d7c71865b2633f3caf80175
ms.sourcegitcommit: 949e55b32eff6610087819a93160a35af0c5f1c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70383558"
---
# <a name="python-tutorials-for-sql-server-machine-learning-services"></a>Didacticiels Python pour SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article décrit les didacticiels et les guides de démarrage rapide Python pour [SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md).

+ Découvrez comment exécuter des scripts Python.
+ Générez, formez et déployez des modèles Python pour SQL Server.
+ En savoir plus sur les contextes de calcul locaux et distants.
+ Explorez les packages Microsoft Python pour la science des données et les Machine Learning.

<a name="bkmk_pythontutorials"></a>

## <a name="python-tutorials"></a>Tutoriels sur Python

| Didacticiel | Description |
|-|-|
| [Prédire la location de ski avec régression linéaire](python-ski-rental-linear-regression.md) | Utilisez Python et la régression linéaire pour prédire le nombre de locations de ski. Utilisez les blocs-notes dans Azure Data Studio pour la préparation des données et l’apprentissage du modèle, et T-SQL pour le déploiement de modèle. |
| [Catégorisation des clients à l’aide du clustering k-signifiant](python-clustering-model.md) | Utilisez Python pour développer et déployer un modèle de clustering K-signifiant afin de catégoriser les clients. Utilisez les blocs-notes dans Azure Data Studio pour la préparation des données et l’apprentissage du modèle, et T-SQL pour le déploiement de modèle. |
| [Créer un modèle à l’aide de revoscalepy](use-python-revoscalepy-to-create-model.md) | Montre comment exécuter du code à partir d’un client python distant à l’aide d’SQL Server en tant que contexte de calcul. Le didacticiel crée un modèle à l’aide de **rxLinMod** à partir de la bibliothèque **revoscalepy** . |
| [Analyse des données python pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md) | Cette procédure pas à pas de bout en bout illustre le processus de création d’une solution python complète à l’aide de T-SQL. |

## <a name="python-quickstarts"></a>Démarrages rapides de Python

Si vous débutez avec SQL Server Machine Learning Services, vous pouvez également essayer les Démarrages rapides de Python.

| Démarrage rapide | Description |
|-|-|
| [Hello World dans Python et SQL Server](quickstart-python-run-using-t-sql.md) | Découvrez les principes de base de l’appel de Python dans T-SQL. |
| [Gérer les entrées et les sorties à l’aide de Python dans SQL Server](quickstart-python-inputs-and-outputs.md) | Découvrez comment gérer les entrées et les sorties pour Python dans [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). |
| [Structures de données python dans SQL Server](quickstart-python-data-structures.md) | Montre comment SQL Server utilise le package Python pandas pour gérer les structures de données. |
| [Former et utiliser votre premier modèle](quickstart-python-train-score-in-tsql.md) | Explique comment créer, former et utiliser un modèle Python pour prédire de nouvelles données. |

## <a name="next-steps"></a>Étapes suivantes

+ [Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../what-is-sql-server-machine-learning.md)
+ [Extension Python à SQL Server](../concepts/extension-python.md)