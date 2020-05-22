---
title: Tutoriels sur R
titleSuffix: SQL machine learning
description: Cet article décrit les tutoriels R pour le Machine Learning SQL. Découvrez comment exécuter des scripts et générer des modèles Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.topic: tutorial
author: cawrites
ms.author: chadam
ms.reviewer: garye, davidph
ms.date: 05/04/2020
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 63c271c4e1d59c9446495607b42b0b5ad13ea246
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606919"
---
# <a name="r-tutorials-for-sql-machine-learning"></a>Tutoriels R pour le Machine Learning SQL

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Cet article décrit les tutoriels et les démarrages rapides R pour [Machine Learning Services sur SQL Serveur](../sql-server-machine-learning-services.md) et les [clusters Big Data](../../big-data-cluster/machine-learning-services.md).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Cet article décrit les tutoriels et les démarrages rapides R pour [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md).
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Cet article décrit les tutoriels et les démarrages rapides R pour [SQL Server 2016 R Services](../r/sql-server-r-services.md).
::: moniker-end

<a name="bkmk_sqltutorials"></a>

## <a name="r-tutorials"></a>Tutoriels sur R

| Didacticiel | Description |
|------|-------------|
| [Prédire la location de skis avec l’arbre de décision](r-predictive-model-introduction.md) | Utilisez R et un modèle d’arbre de décision pour prédire le nombre de futures locations de skis. Utilisez des notebooks dans Azure Data Studio pour préparer les données et entraîner le modèle, et T-SQL pour le déploiement du modèle. |
| [Classement des clients par catégorie à l’aide du clustering k-moyennes](r-clustering-model-introduction.md) | Utilisez R pour développer et déployer un modèle de clustering k-moyennes en vue de classer les clients par catégorie. Utilisez des notebooks dans Azure Data Studio pour préparer les données et entraîner le modèle, et T-SQL pour le déploiement du modèle. |
| [Analytique R en base de données pour les scientifiques de données](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | Pour les développeurs R qui débutent avec SQL Server, ce didacticiel explique comment effectuer des tâches courantes de science des données dans SQL Server. Celles-ci comprennent le chargement et la visualisation des données, la formation et l’enregistrement d’un modèle dans SQL Server, et l’utilisation du modèle pour l’analyse prédictive. |
| [Analytique R en base de données pour les développeurs SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md) | Créez et déployez une solution R complète à l’aide d’outils [!INCLUDE[tsql](../../includes/tsql-md.md)] uniquement. Se concentre sur le déplacement d’une solution en production. Vous découvrirez comment encapsuler du code R dans une procédure stockée, enregistrer un modèle R dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et effectuer des appels paramétrables au modèle R pour la prédiction. |

## <a name="r-quickstarts"></a>Démarrages rapides R

Si vous débutez avec le Machine Learning SQL, vous pouvez aussi essayer les démarrages rapides R.

| Démarrage rapide | Description |
|-|-|
| [Exécuter des scripts R simples](quickstart-r-create-script.md) | Découvrez les principes de base de l’appel de R dans T-SQL à l’aide de [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). |
| [Objets et structures de données avec R](quickstart-r-data-types-and-objects.md) | Montre comment SQL utilise R pour gérer les structures de données. |
| [Créer et scorer un modèle prédictif dans R](quickstart-r-data-types-and-objects.md) | Explique comment créer, entraîner et utiliser un modèle R pour effectuer des prédictions à partir de nouvelles données. |

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations techniques sur R dans SQL Server, consultez [Extension de langage R dans SQL Server](../concepts/extension-r.md).
