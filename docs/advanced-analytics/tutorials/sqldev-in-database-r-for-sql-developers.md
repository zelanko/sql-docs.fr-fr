---
title: Didacticiel pour l’analytique en base de données à l’aide de R - SQL Server Machine Learning
description: Découvrez comment incorporer le code de langue dans les procédures stockées SQL Server et des fonctions T-SQL de programmation R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8e5b0bc8633e956817e778a1d5a2d75a86df8588
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53596340"
---
# <a name="tutorial-in-database-analytics-for-sql-developers-using-r"></a>Didacticiel : Analytique en base de données pour les développeurs SQL à l’aide de R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans ce didacticiel pour les programmeurs SQL, en savoir plus sur l’intégration de R en création et en déployant une basée sur R d’apprentissage à l’aide de la solution un [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) base de données sur SQL Server. 

Ce didacticiel vous présente les fonctions R utilisées dans un flux de travail de modélisation de données. Étapes comprennent l’exploration de données, création et l’apprentissage d’un modèle de classification binaire et un déploiement de modèle. Le modèle que vous générerez prédit si un voyage est susceptible d’entraîner une info-bulle en fonction de l’heure du jour, la distance parcourue et l’emplacement de la prise en charge. Tout le code R utilisé dans ce didacticiel est encapsulé dans des procédures stockées que vous créez et exécutez dans Management Studio.

## <a name="background-for-sql-developers"></a>En arrière-plan pour les développeurs SQL

Le processus de création d’une solution d’apprentissage est complexe qui peut impliquer plusieurs outils et la coordination des experts du sujet dans plusieurs phases :

+ obtention et le nettoyage des données
+ Explorer des données et création de fonctionnalités utiles pour la modélisation
+ apprentissage et le modèle de paramétrage
+ déploiement en production

Développement et le test du code réel est préférable d’effectuer à l’aide d’un environnement de développement R dédié. Toutefois, une fois que le script est entièrement testé, vous pouvez facilement déployer à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)] des procédures stockées dans l’environnement familier de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

L’objectif de ce didacticiel en plusieurs parties est une introduction à un flux de travail typique pour migration » terminé le code R » pour SQL Server. 

- [Leçon 1 : Explorer et visualiser la forme de données et la distribution en appelant des fonctions R dans les procédures stockées](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Leçon 2 : Créer des caractéristiques de données à l’aide de R dans les fonctions T-SQL](sqldev-create-data-features-using-t-sql.md)
  
- [Leçon 3 : Former et enregistrer un modèle R à l’aide des fonctions et procédures stockées](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Leçon 4 : Prédire les résultats potentiels à l’aide d’un modèle R dans une procédure stockée](../tutorials/sqldev-operationalize-the-model.md)

Une fois que le modèle a été enregistré dans la base de données, appelez le modèle pour les prédictions à partir de [!INCLUDE[tsql](../../includes/tsql-md.md)] à l’aide de procédures stockées.

## <a name="prerequisites"></a>Prérequis

Toutes les tâches peuvent être effectuées à l’aide [!INCLUDE[tsql](../../includes/tsql-md.md)] procédures stockées dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Ce didacticiel suppose que vous êtes familiarisé avec les opérations de base de données telles que la création de tables et des bases de données, l’importation de données et l’écriture des requêtes SQL. Il ne suppose pas que vous R. Par conséquent, tout le code R est fourni. 

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation) ou [SQL Server 2017 Machine Learning Services avec R est activé](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Bibliothèques R](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location)

+ [Autorisations](../security/user-permission.md)

+ [Base de données de démonstration NYC Taxi](demo-data-nyctaxi-in-sql.md)


## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Configurer la base de données NYC Taxi](demo-data-nyctaxi-in-sql.md)