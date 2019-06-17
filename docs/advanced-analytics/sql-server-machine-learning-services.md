---
title: R et Python documentation machine learning - SQL Server Machine Learning Services
description: R et Python dans SQL Server, avec intégration de la modélisation pour la science des données et d’algorithmes de Machine Learning pour l’analyse des données d’entreprise à grande échelle.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: overview
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: cbe617ea7732468732555bf6f0bba8ebaec2c17a
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141378"
---
# <a name="sql-server-machine-learning-services"></a>SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

## <a name="sql-server-machine-learning-services-r-and-python-documentation"></a>SQL Server Documentation Machine Learning Services (R et Python)

Découvrez comment utiliser des bibliothèques externes et les langages R et Python sur des données relationnelles résidentes avec nos guides de démarrage rapide, nos tutoriels et nos articles pratiques. Les bibliothèques R et Python dans [SQL Server Machine Learning Services](what-is-sql-server-machine-learning.md) incluent des distributions de base, les modèles de science des données, les algorithmes d’apprentissage automatique et les fonctions pour la conduite d’analytique hautes performances à grande échelle, sans avoir à transférer des données sur le réseau.

::: moniker range="=sql-server-ver15||=sqlallproducts-allversions"
> [!NOTE]
> Pour obtenir la documentation sur Java, consultez le [documentation sur les Extensions de langage SQL Server](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview).
::: moniker-end

|   |   |
|---|:--|
| ![Logo R](media/index/logo_r.png) | R open source, étendu avec [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) et algorithmes Microsoft AI dans [MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package). Ces bibliothèques mettent à votre disposition des modèles de prévision et de prédiction, des analyses statistiques, des visualisations et des manipulations de données à grande échelle.<br/>L’intégration de R commence avec [SQL Server 2016](install/sql-r-services-windows-install.md) et se trouve également dans [SQL Server 2017](install/sql-machine-learning-services-windows-install.md). |
| ![Logo Python](media/index/logo_python.png) | Les développeurs Python peuvent utiliser les bibliothèques [revoscalepy](/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) et [microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package) de Microsoft pour l’analytique prédictive et le Machine Learning à grande échelle. Les bibliothèques compatibles avec Anaconda et Python 3.5 sont la distribution de référence.<br/>L’intégration de Python commence avec [SQL Server 2017](install/sql-machine-learning-services-windows-install.md). |
| &nbsp; | &nbsp; |

## <a name="5-minute-quickstarts"></a>Démarrages rapides en 5 minutes

- [Créer un modèle prédictif dans R](tutorials/rtsql-create-a-predictive-model-r.md)

- [Prédire et tracer à partir d’un modèle avec R](tutorials/rtsql-predict-and-plot-from-model.md)

## <a name="step-by-step-tutorials"></a>Tutoriels pas à pas

- [Comment installer les Services Machine Learning dans SQL Server](install/sql-machine-learning-services-windows-install.md)

- [Guide pratique pour exécuter R à partir de T-SQL et de procédures stockées](tutorials/sqldev-in-database-r-for-sql-developers.md)

- [Guide pratique pour utiliser l’analytique incorporée dans Python](tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="video-introduction"></a>Vidéo de présentation

> [!VIDEO https://www.youtube.com/embed/ACejZ9optCQ]

## <a name="reference"></a>Référence

| Package | Langue | Description |
|:--------|:---------|:------------|
| [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) | R | Traitement distribué et parallèle pour les tâches R : transformation des données, exploration, visualisation, analytique statistique et prédictive. |
| [MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package) | R | Fonctions basées sur les algorithmes d’intelligence artificielle de Microsoft, adaptées pour R. |
| [olapR](/machine-learning-server/r-reference/olapr/olapr) | R | Importation de données depuis des cubes OLAP |
| [sqlRUtils](/machine-learning-server/r-reference/sqlrutils/sqlrutils) | R | Fonctions helper pour l’encapsulation de R et de T-SQL. |
[revoscalepy](/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | Python | Traitement distribué et parallèle pour les tâches Python : transformation des données, exploration, visualisation, analytique statistique et prédictive. |
| [microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Python | Fonctions basées sur les algorithmes d’intelligence artificielle de Microsoft, adaptées pour Python. |
| &nbsp; | &nbsp; | &nbsp; |
