---
title: Vue d’ensemble du didacticiel SQL Server R
description: Présentation des didacticiels de langage R pour SQL Server l’analytique dans la base de données.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ff1027a3a791ef0151e61982445cafff7be40329
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715424"
---
# <a name="sql-server-r-language-tutorials"></a>Didacticiels sur le langage R SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article décrit les didacticiels de langage R pour l’analytique en base de données sur [SQL Server 2016 R services](../install/sql-r-services-windows-install.md) ou [SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md).

+ Découvrez comment encapsuler et exécuter du code R dans des procédures stockées.
+ Sérialisez et enregistrez les modèles basés sur r pour SQL Server bases de données.
+ En savoir plus sur les contextes de calcul locaux et distants et leur utilisation.
+ Explorez les bibliothèques Microsoft R pour la science des données et les tâches de Machine Learning.

<a name="bkmk_sqltutorials"></a>

## <a name="r-quickstarts-and-tutorials"></a>Guides de démarrage rapide et didacticiels R

| Lien | Description |
|------|-------------|
| [Démarrage rapide : Utilisation de R dans T-SQL](rtsql-using-r-code-in-transact-sql-quickstart.md) | Tout d’abord, ce qui illustre la syntaxe de base pour appeler une fonction R à l’aide d’un éditeur de requête T-SQL comme SQL Server Management Studio. |
| [Tutoriel : En savoir plus sur la base de données analytique R pour les scientifiques des données](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | Pour les développeurs R qui débutent dans SQL Server, ce didacticiel explique comment effectuer des tâches courantes de science des données dans SQL Server. Charger et visualiser des données, former et enregistrer un modèle dans SQL Server, et utiliser le modèle pour l’analyse prédictive. |
| [Tutoriel : Découvrez les analyses en base de données R pour les développeurs SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md) | Créez et déployez une solution R complète, en [!INCLUDE[tsql](../../includes/tsql-md.md)] utilisant uniquement des outils. Se concentre sur le déplacement d’une solution en production. Vous découvrirez comment encapsuler du code R dans une procédure stockée, enregistrer un modèle R dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et effectuer des appels paramétrables au modèle R pour la prédiction. |
| [Tutoriel : Présentation approfondie de RevoScalepR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) | Découvrez comment utiliser les fonctions des packages RevoScaleR. Déplacer des données entre R et SQL Server, et basculer les contextes de calcul pour les adapter à une tâche particulière. Créez des modèles et des tracés, puis déplacez-les entre votre environnement de développement et le serveur de base de données. |

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Exemples de code

| Lien | Description |
|------|-------------|
| [Créer un modèle prédictif à l’aide de R et SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Découvrez comment une entreprise de location de ski peut utiliser Machine Learning pour prédire les futurs loyers, ce qui aide le plan et le personnel de l’entreprise à répondre à la demande future. |
| [Effectuer un clustering des clients à l’aide de R et SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Utilisez l’apprentissage non supervisé pour segmenter les clients en fonction des données de ventes. |

## <a name="see-also"></a>Voir aussi

+ [Extension R pour SQL Server](../concepts/extension-r.md)
+ [Didacticiels de Machine Learning Services SQL Server](machine-learning-services-tutorials.md)

