---
title: 'Python + T-SQL : développer un modèle'
description: Découvrez comment incorporer du code Python dans des procédures stockées SQL Server et des fonctions T-SQL.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 10/29/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d5cdec0ad291fecf0606650d116f0c7979831c19
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785637"
---
# <a name="tutorial-python-data-analytics-for-sql-developers"></a>Tutoriel : Analytique des données Python pour développeurs SQL
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Dans ce tutoriel pour les programmeurs SQL, vous apprendrez à intégrer Python en créant et en déployant une solution de machine learning basée sur Python à l’aide d’une base de données [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) sur SQL Server. Vous allez utiliser T-SQL, SQL Server Management Studio et une instance du moteur de base de données avec [Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) et la prise en charge du langage Python.

Ce tutoriel vous présente les fonctions Python utilisées dans un workflow de modélisation des données. Les étapes incluent l’exploration des données, la création et l’apprentissage d’un modèle de classification binaire et le déploiement d’un modèle. Vous allez utiliser des exemples de données provenant de New York City Taxi and Limosine Commission. Le modèle que vous allez créer prédit si un voyage est susceptible de générer un pourboire en fonction de l’heure de la journée, de la distance parcourue et de l’emplacement de départ. 

Tous les codes Python utilisés dans ce tutoriel sont encapsulés dans les procédures stockées que vous créez et exécutez dans Management Studio.

> [!NOTE]
> Ce tutoriel est disponible au format R et Python. Pour la version R, consultez [Analytique dans la base de données pour les développeurs R](sqldev-in-database-r-for-sql-developers.md).

## <a name="overview"></a>Vue d’ensemble

Le processus de création d’une solution de Machine Learning est complexe. Il peut impliquer plusieurs outils et la coordination de plusieurs experts durant les différentes phases :

+ Extraction et nettoyage des données
+ Exploration des données et création de caractéristiques utiles pour la modélisation
+ Apprentissage et optimisation du modèle
+ Déploiement en production

Le développement et les tests du code réel fournissent de meilleurs résultats dans un environnement de développement dédié. Toutefois, une fois que le script est entièrement testé, vous pouvez facilement le déployer sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] dans l’environnement familier de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. L’encapsulation de code externe dans les procédures stockées est le mécanisme principal permettant de rendre le code opérationnel dans SQL Server.

Que vous soyez un programmeur SQL ne connaissant pas Python ou un développeur Python ne connaissant pas SQL, ce tutoriel en plusieurs parties présente un workflow standard pour effectuer des analyses dans des bases de données avec Python et SQL Server. 

+ [Leçon 1 : Explorer et visualiser les données à l’aide de Python](sqldev-py3-explore-and-visualize-the-data.md)

+ [Leçon 2 : Créer des caractéristiques de données à l’aide de fonctions SQL](sqldev-py4-create-data-features-using-t-sql.md)

+ [Leçon 3 : Entraîner et enregistrer un modèle Python à l’aide de T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

+ [Leçon 4 : Prédire les résultats potentiels à l’aide d’un modèle Python dans une procédure stockée](sqldev-py6-operationalize-the-model.md)

Une fois que le modèle a été enregistré dans la base de données, vous pouvez l’appeler pour vos prédictions dans [!INCLUDE[tsql](../../includes/tsql-md.md)] à l’aide de procédures stockées.

## <a name="prerequisites"></a>Prérequis

+ [SQL Server Machine Learning Services avec Python](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [autorisations](../security/user-permission.md)

+ [Base de données de démonstration Taxis de New York](demo-data-nyctaxi-in-sql.md)

Toutes les tâches peuvent être effectuées à l’aide de procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Vous devez être familiarisé avec les opérations de base de données, telles que la création de bases de données et de tables, l’importation de données et la rédaction de requêtes SQL. Cela ne suppose pas que vous connaissiez Python. L’ensemble du code Python est fourni. 

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Explorer et visualiser les données à l’aide de Python](sqldev-py3-explore-and-visualize-the-data.md)
