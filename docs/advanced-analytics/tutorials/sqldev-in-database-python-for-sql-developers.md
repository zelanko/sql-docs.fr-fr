---
title: En base de données analytique de Python pour les développeurs SQL | Microsoft Docs
description: Découvrez comment incorporer le code Python dans les procédures stockées SQL Server et des fonctions T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8c992cbda06d158bec0b76d6d46d71157a08cf3e
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51032986"
---
# <a name="tutorial-in-database-python-analytics-for-sql-developers"></a>Didacticiel : Analytique en base de données Python pour les développeurs SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans ce didacticiel pour les programmeurs SQL, en savoir plus sur l’intégration de Python en créant et déploiement d’un ordinateur basé sur Python learning à l’aide de la solution un [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) base de données sur SQL Server. 

Ce didacticiel vous présente les fonctions de Python utilisées dans un flux de travail de modélisation de données. Étapes comprennent l’exploration de données, création et l’apprentissage d’un modèle de classification binaire et un déploiement de modèle. Vous allez utiliser les exemples de données des taxis de New York City et Limosine Commission, et le modèle que vous générerez prédit si un voyage est susceptible d’entraîner une info-bulle en fonction de l’heure du jour, la distance parcourue et l’emplacement de la prise en charge. Tout le code Python utilisé dans ce didacticiel est encapsulé dans des procédures stockées que vous créez et exécutez dans Management Studio.

> [!NOTE]
> Ce didacticiel est disponible dans R et Python. Pour la version de R, consultez [en base de données analytique pour les développeurs R](sqldev-in-database-r-for-sql-developers.md).

## <a name="overview"></a>Vue d'ensemble

Le processus de création d’une solution d’apprentissage est complexe qui peut impliquer plusieurs outils et la coordination des experts du sujet dans plusieurs phases :

+ obtention et le nettoyage des données
+ Explorer des données et création de fonctionnalités utiles pour la modélisation
+ apprentissage et le modèle de paramétrage
+ déploiement en production

Développement et le test du code réel est préférable d’effectuer à l’aide d’un environnement de développement dédié. Toutefois, une fois que le script est entièrement testé, vous pouvez facilement déployer à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)] des procédures stockées dans l’environnement familier de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Habillage du code externe dans les procédures stockées est le mécanisme principal pour le code de mise en application dans SQL Server.

Si vous êtes un programmeur SQL vous débutez avec Python ou Python développeur SQL, ce didacticiel en plusieurs parties présente un flux de travail typique pour la conduite d’analytique en base de données avec Python et SQL Server. 

+ [Leçon 1 : Explorer et visualiser les données à l’aide de Python](sqldev-py3-explore-and-visualize-the-data.md)

+ [Leçon 2 : Créer des données de fonctionnalités à l’aide à l’aide de fonctions SQL personnalisées](sqldev-py4-create-data-features-using-t-sql.md)

+ [Leçon 3 : Former et enregistrer un modèle de Python à l’aide de T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

+ [Leçon 4 : Prédire les résultats potentiels à l’aide d’un modèle Python dans une procédure stockée](sqldev-py6-operationalize-the-model.md)

Une fois que le modèle a été enregistré dans la base de données, vous pouvez appeler le modèle pour les prédictions à partir de [!INCLUDE[tsql](../../includes/tsql-md.md)] à l’aide de procédures stockées.

## <a name="prerequisites"></a>Prérequis

+ [Services SQL Server 2017 Machine Learning avec Python](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Autorisations](../security/user-permission.md)

+ [Base de données de démonstration NYC Taxi](demo-data-nyctaxi-in-sql.md)

Toutes les tâches peuvent être effectuées à l’aide [!INCLUDE[tsql](../../includes/tsql-md.md)] procédures stockées dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Ce didacticiel suppose que vous êtes familiarisé avec les opérations de base de données telles que la création de tables et des bases de données, l’importation de données et l’écriture des requêtes SQL. Il ne suppose pas que vous Python. Par conséquent, tout le code Python est fourni. 

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Explorer et visualiser les données à l’aide de Python](sqldev-py3-explore-and-visualize-the-data.md)
