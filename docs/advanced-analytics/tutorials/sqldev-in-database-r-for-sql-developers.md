---
title: Didacticiel sur l’analytique en base de données à l’aide de R
description: Découvrez comment incorporer du code du langage de programmation R dans SQL Server procédures stockées et des fonctions T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 5b2629a50a73208181cc14fd843cd9ab9c0b05df
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69633607"
---
# <a name="tutorial-r-data-analytics-for-sql-developers"></a>Tutoriel : Analyse des données R pour les développeurs SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce didacticiel pour les programmeurs SQL, découvrez l’intégration de R en créant et en déployant une solution de Machine Learning basée sur R à l’aide d’une base de données [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) sur SQL Server. Vous allez utiliser T-SQL, SQL Server Management Studio et une instance du moteur de base de données avec [Machine Learning Services] ([machine learning services](../install/sql-machine-learning-services-windows-install.md) et la prise en charge du langage R

Ce didacticiel présente les fonctions R utilisées dans un flux de travail de modélisation des données. Les étapes incluent l’exploration de données, la création et l’apprentissage d’un modèle de classification binaire et le déploiement de modèle. Le modèle que vous allez créer prévoit si un voyage est susceptible d’entraîner un pourboire en fonction de l’heure de la journée, de la distance parcourue et de l’emplacement de récupération. 

Tout le code R utilisé dans ce didacticiel est encapsulé dans les procédures stockées que vous créez et exécutez dans Management Studio.

## <a name="background-for-sql-developers"></a>Arrière-plan pour les développeurs SQL

Le processus de création d’une solution de Machine Learning est un processus complexe qui peut impliquer plusieurs outils et la coordination des experts de l’objet entre plusieurs phases:

+ obtention et nettoyage des données
+ exploration des données et création de fonctionnalités utiles pour la modélisation
+ apprentissage et paramétrage du modèle
+ déploiement en production

Le développement et le test du code réel s’effectuent mieux à l’aide d’un environnement de développement R dédié. Toutefois, une fois le script entièrement testé, vous pouvez le déployer facilement à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l' [!INCLUDE[tsql](../../includes/tsql-md.md)] aide de procédures stockées dans l’environnement [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]familier de.

L’objectif de ce didacticiel en plusieurs parties est une introduction à un flux de travail classique pour la migration de «code R terminé» vers SQL Server. 

- [Leçon 1 : Explorez et visualisez la forme et la distribution des données en appelant des fonctions R dans des procédures stockées](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Leçon 2 : Créer des fonctionnalités de données à l’aide de R dans les fonctions T-SQL](sqldev-create-data-features-using-t-sql.md)
  
- [Leçon 3 : Former et enregistrer un modèle R à l’aide de fonctions et de procédures stockées](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Leçon 4 : Prédire les résultats potentiels à l’aide d’un modèle R dans une procédure stockée](../tutorials/sqldev-operationalize-the-model.md)

Une fois que le modèle a été enregistré dans la base de données, appelez le modèle [!INCLUDE[tsql](../../includes/tsql-md.md)] pour les prédictions à partir de à l’aide de procédures stockées.

## <a name="prerequisites"></a>Prérequis

Toutes les tâches peuvent être effectuées [!INCLUDE[tsql](../../includes/tsql-md.md)] à l’aide [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]de procédures stockées dans.

Ce didacticiel part du principe que vous êtes familiarisé avec les opérations de base de données de base, telles que la création de bases de données et de tables, l’importation de données et l’écriture de requêtes SQL. Il ne suppose pas que vous connaissiez R. Ainsi, tout le code R est fourni. 

+ [SQL Server 2016 r services](../install/sql-r-services-windows-install.md#verify-installation) ou [SQL Server machine learning services avec l’option r activée](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Bibliothèques R](../package-management/r-package-information.md)

+ [autorisations](../security/user-permission.md)

+ [Base de données de démonstration du taxi de New York](demo-data-nyctaxi-in-sql.md)


## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Explorer et visualiser les données à l’aide des fonctions R dans les procédures stockées](../tutorials/sqldev-explore-and-visualize-the-data.md)
