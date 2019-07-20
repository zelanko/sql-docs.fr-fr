---
title: Didacticiel sur la base de données python Analytics pour les développeurs SQL
description: Découvrez comment incorporer du code python dans SQL Server procédures stockées et les fonctions T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: ed8008bbda76bfc8a194897e9389c9d5dc6bb031
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345937"
---
# <a name="tutorial-python-data-analytics-for-sql-developers"></a>Tutoriel : Analyse des données python pour les développeurs SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans ce didacticiel pour les programmeurs SQL, découvrez l’intégration de Python en générant et en déployant une solution de Machine Learning basée sur Python à l’aide d’une base de données [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) sur SQL Server. Vous allez utiliser T-SQL, SQL Server Management Studio et une instance du moteur de base de données avec la prise en charge du langage [machine learning services](../install/sql-machine-learning-services-windows-install.md) et Python.

Ce didacticiel présente les fonctions python utilisées dans un flux de travail de modélisation des données. Les étapes incluent l’exploration de données, la création et l’apprentissage d’un modèle de classification binaire et le déploiement de modèle. Vous allez utiliser des exemples de données provenant de la Limosine de New York City et des commissions de la région, et le modèle que vous allez créer prévoit si un voyage est susceptible de générer un pourboire en fonction de l’heure de la journée, de la distance parcourue et de l’emplacement de départ. 

Tout le code python utilisé dans ce didacticiel est encapsulé dans les procédures stockées que vous créez et exécutez dans Management Studio.

> [!NOTE]
> Ce didacticiel est disponible à la fois dans R et dans Python. Pour obtenir la version R, consultez [analyse en base de données pour les développeurs r](sqldev-in-database-r-for-sql-developers.md).

## <a name="overview"></a>Vue d'ensemble

Le processus de création d’une solution de Machine Learning est un processus complexe qui peut impliquer plusieurs outils et la coordination des experts de l’objet entre plusieurs phases:

+ obtention et nettoyage des données
+ exploration des données et création de fonctionnalités utiles pour la modélisation
+ apprentissage et paramétrage du modèle
+ déploiement en production

Le développement et le test du code réel sont le meilleur moyen d’utiliser un environnement de développement dédié. Toutefois, une fois le script entièrement testé, vous pouvez le déployer facilement à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l' [!INCLUDE[tsql](../../includes/tsql-md.md)] aide de procédures stockées dans l’environnement [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]familier de. L’encapsulation de code externe dans les procédures stockées est le mécanisme principal permettant de configurer du code dans SQL Server.

Que vous soyez un programmeur SQL qui n’est pas une nouveauté de Python ou un développeur python nouveau dans SQL, ce didacticiel en plusieurs parties introduit un flux de travail standard pour effectuer des analyses en base de données avec Python et SQL Server. 

+ [Leçon 1 : Explorez et Visualisez les données à l’aide de Python](sqldev-py3-explore-and-visualize-the-data.md)

+ [Leçon 2 : Créer des fonctionnalités de données à l’aide de fonctions SQL personnalisées](sqldev-py4-create-data-features-using-t-sql.md)

+ [Leçon 3 : Former et enregistrer un modèle Python à l’aide de T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

+ [Leçon 4 : Prédire les résultats potentiels à l’aide d’un modèle python dans une procédure stockée](sqldev-py6-operationalize-the-model.md)

Une fois que le modèle a été enregistré dans la base de données, vous pouvez appeler le modèle [!INCLUDE[tsql](../../includes/tsql-md.md)] pour les prédictions à partir de à l’aide de procédures stockées.

## <a name="prerequisites"></a>Prérequis

+ [SQL Server 2017 Machine Learning Services avec Python](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [autorisations](../security/user-permission.md)

+ [Base de données de démonstration du taxi de New York](demo-data-nyctaxi-in-sql.md)

Toutes les tâches peuvent être effectuées [!INCLUDE[tsql](../../includes/tsql-md.md)] à l’aide [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]de procédures stockées dans.

Ce didacticiel part du principe que vous êtes familiarisé avec les opérations de base de données de base, telles que la création de bases de données et de tables, l’importation de données et l’écriture de requêtes SQL. Cela ne suppose pas que vous connaissiez Python. En tant que tel, tout le code Python est fourni. 

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Explorez et Visualisez les données à l’aide de Python](sqldev-py3-explore-and-visualize-the-data.md)
