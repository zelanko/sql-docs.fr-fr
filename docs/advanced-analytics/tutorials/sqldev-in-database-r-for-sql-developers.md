---
title: 'Tutoriel R + T-SQL : développer un modèle'
description: Découvrez comment incorporer du code du langage de programmation R dans des procédures stockées SQL Server et des fonctions T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f0734203a5b5e49ad344b2c0440208c6b652c080
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73725467"
---
# <a name="tutorial-r-data-analytics-for-sql-developers"></a>Tutoriel : analytique de données R pour les développeurs SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce didacticiel pour les programmeurs SQL, vous apprendrez à intégrer R en créant et en déployant une solution de Machine Learning basée sur R à l’aide d’une base de données [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) sur SQL Server. Vous allez utiliser T-SQL, SQL Server Management Studio et une instance du moteur de base de données avec [Machine Learning Services] ([Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) et la prise en charge du langage R.

Ce didacticiel vous présente les fonctions R utilisées dans un workflow de modélisation des données. Les étapes incluent l’exploration des données, la création et l’apprentissage d’un modèle de classification binaire et le déploiement d’un modèle. Le modèle que vous allez créer prévoit si un trajet est susceptible de générer un pourboire en fonction de l’heure de la journée, de la distance parcourue et de l’emplacement de la prise en charge du passager. 

Tous les codes R utilisés dans ce didacticiel sont encapsulés dans les procédures stockées que vous créez et exécutez dans Management Studio.

## <a name="background-for-sql-developers"></a>Arrière-plan pour les développeurs SQL

Le processus de création d’une solution de Machine Learning est complexe. Il peut impliquer plusieurs outils et la coordination de plusieurs experts durant les différentes phases :

+ Extraction et nettoyage des données
+ Exploration des données et création de caractéristiques utiles pour la modélisation
+ Apprentissage et optimisation du modèle
+ Déploiement en production

Le développement et les tests du code réel fournissent de meilleurs résultats dans un environnement de développement dédié à R. Toutefois, une fois que le script est entièrement testé, vous pouvez facilement le déployer sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] dans l’environnement familier de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

L’objectif de ce didacticiel en plusieurs parties est de vous présenter un workflow classique pour la migration de « code R terminé » vers SQL Server. 

- [Leçon 1 : Explorez et visualisez la forme et la distribution des données en appelant des fonctions R dans des procédures stockées](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Leçon 2 : Créer des caractéristiques de données à l’aide d’un script R dans des fonctions T-SQL](sqldev-create-data-features-using-t-sql.md)
  
- [Leçon 3 : Entraîner et enregistrer un modèle R à l’aide de fonctions et de procédures stockées](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Leçon 4 : Prédire les résultats potentiels à l’aide d’un modèle R dans une procédure stockée](../tutorials/sqldev-operationalize-the-model.md)

Une fois que le modèle a été enregistré dans la base de données, appelez-le pour vos prédictions dans [!INCLUDE[tsql](../../includes/tsql-md.md)] à l’aide de procédures stockées.

## <a name="prerequisites"></a>Conditions préalables requises

Toutes les tâches peuvent être effectuées à l’aide de procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Vous devez être familiarisé avec les opérations de base de données, telles que la création de bases de données et de tables, l’importation de données et la rédaction de requêtes SQL. Vous n’avez pas besoin de connaître R, car tout le code R est fourni. 

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation) ou [SQL Server Machine Learning Services avec R activé](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Bibliothèques R](../package-management/r-package-information.md)

+ [Autorisations](../security/user-permission.md)

+ [Base de données de démonstration Taxis de New York](demo-data-nyctaxi-in-sql.md)


## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Explorer et visualiser les données à l’aide de fonctions R dans des procédures stockées](../tutorials/sqldev-explore-and-visualize-the-data.md)
