---
title: Tutoriels sur Python
description: Cet article décrit les tutoriels Python pour SQL Server Machine Learning Services. Découvrez comment exécuter des scripts et générer des modèles de Machine Learning dans SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/04/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b8caa58c178f68ebcf773fcef8f18509b85ad24a
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "81116122"
---
# <a name="python-tutorials-for-sql-server-machine-learning-services"></a>Tutoriels Python pour SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article décrit les tutoriels et les démarrages rapides Python pour [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md).

+ Découvrez comment exécuter des scripts Python.
+ Créez et entraînez des modèles Python, puis déployez-les sur SQL Server.
+ Découvrez ce que sont les contextes de calcul distants et locaux.
+ Explorez les packages Microsoft Python pour la science des données et le Machine Learning.

<a name="bkmk_pythontutorials"></a>

## <a name="python-tutorials"></a>Tutoriels sur Python

| Didacticiel | Description |
|-|-|
| [Prédire les locations de skis avec la régression linéaire](python-ski-rental-linear-regression.md) | Utilisez Python et la régression linéaire pour prédire le nombre de skis qui seront loués. Utilisez des notebooks dans Azure Data Studio pour préparer les données et entraîner le modèle, et T-SQL pour le déploiement du modèle. |
| [Classement des clients par catégorie à l’aide du clustering k-moyennes](python-clustering-model.md) | Utilisez Python pour développer et déployer un modèle de clustering K-moyennes en vue de classer les clients par catégorie. Utilisez des notebooks dans Azure Data Studio pour préparer les données et entraîner le modèle, et T-SQL pour le déploiement du modèle. |
| [Créer un modèle à l’aide de revoscalepy](use-python-revoscalepy-to-create-model.md) | Montre comment exécuter du code à partir d’un client Python distant avec SQL Server comme contexte de calcul. Le tutoriel crée un modèle en utilisant **rxLinMod** de la bibliothèque **revoscalepy**. |
| [Analytique données Python pour développeurs SQL](sqldev-in-database-python-for-sql-developers.md) | Cette procédure pas à pas détaille l’ensemble du processus de création d’une solution Python complète en utilisant T-SQL. |

## <a name="python-quickstarts"></a>Démarrages rapides Python

Si vous débutez avec SQL Server Machine Learning Services, vous pouvez aussi essayer les démarrages rapides Python.

| Démarrage rapide | Description |
|-|-|
| [Hello World dans Python et SQL Server](quickstart-python-create-script.md) | Découvrez les principes de base de l’appel de Python dans T-SQL à l’aide de [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). |
| [Gérer les types de données et les objets en utilisant Python dans SQL Server](quickstart-python-data-structures.md) | Montre comment SQL Server utilise le package Pandas Python pour gérer les structures de données. |
| [Créer et scorer un modèle prédictif dans Python](quickstart-python-train-score-model.md) | Explique comment créer, entraîner et utiliser un modèle Python pour effectuer des prédictions à partir de nouvelles données. |

## <a name="next-steps"></a>Étapes suivantes

+ [Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../what-is-sql-server-machine-learning.md)
+ [Extension Python dans SQL Server](../concepts/extension-python.md)