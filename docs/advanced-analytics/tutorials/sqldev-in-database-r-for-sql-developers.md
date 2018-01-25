---
title: "Dans base de données analytique de R pour les développeurs SQL (didacticiel) | Documents Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2016
dev_langs:
- R
- TSQL
ms.assetid: c18cb249-2146-41b7-8821-3a20c5d7a690
caps.latest.revision: "15"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: e1bb6f2e586bb2a4b8b2a92c8099dc33603e8475
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="in-database-r-analytics-for-sql-developers-tutorial"></a>Analytique de R dans base de données pour les développeurs SQL (didacticiel)

L’objectif de ce didacticiel est de fournir des programmeurs SQL avec une expérience pratique de créer une solution dans SQL Server d’apprentissage. Dans ce didacticiel, vous allez apprendre à intégrer R dans une application ou d’une solution Décisionnelle en insérant le code R dans les procédures stockées.

> [!NOTE]
> 
> La même solution est disponible dans Python. SQL Server 2017 est requis. Consultez [dans-base de données analytique pour les développeurs Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="overview"></a>Vue d'ensemble

Le processus de création d’une solution de bout en bout comprend généralement l’obtention et le nettoyage des données, l’exploration des données et l’ingénierie des caractéristiques, l’apprentissage et le réglage de modèles, et enfin le déploiement du modèle en production. Développement et test du code réel est préférable d’effectuer à l’aide d’un environnement de développement dédié. Pour R, cela peut signifier que RStudio ou [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)].

Toutefois, une fois que la solution est créée, vous pouvez facilement la déployer sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] dans l’environnement familier de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Dans ce didacticiel, nous supposons que vous avez reçu tout le code R requis pour la solution, puis de se concentrer sur la création et déploiement de la solution à l’aide de SQL Server.

- [Leçon 1 : Télécharger les exemples de données](../tutorials/sqldev-download-the-sample-data.md)

    Téléchargez l’exemple de dataset et les exemples de fichiers de script SQL sur un ordinateur local.

- [Leçon 2 : Importer des données vers SQL Server à l’aide de PowerShell](../r/sqldev-import-data-to-sql-server-using-powershell.md)

    Exécutez un script PowerShell qui crée une base de données et une table sur l’instance [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , et charge les exemples de données dans la table.

- [Leçon 3 : Explorer et visualiser les données](../tutorials/sqldev-explore-and-visualize-the-data.md)

    Effectuez une exploration et une visualisation de données de base en appelant des packages R et des fonctions de procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] .

- [Leçon 4 : Créer des fonctionnalités de données à l’aide de T-SQL](../tutorials/sqldev-create-data-features-using-t-sql.md)

    Créez des caractéristiques de données à l’aide de fonctions personnalisées.
  
-   [Leçon 5 : L’apprentissage et enregistrer un modèle R à l’aide de T-SQL](../r/sqldev-train-and-save-a-model-using-t-sql.md)

    Générer un modèle d’apprentissage à l’aide de R dans les procédures stockées. Enregistrez le modèle à une table SQL Server.
  
-   [Leçon 6 : Rendez le modèle opérationnel.](../tutorials/sqldev-operationalize-the-model.md)

    Une fois que le modèle a été enregistré dans la base de données, appelez-le pour la prédiction dans [!INCLUDE[tsql](../../includes/tsql-md.md)] à l’aide de procédures stockées.

### <a name="scenario"></a>Scénario

Ce didacticiel utilise un dataset publique connu, basé sur les boucles dans taxi de New York city. Pour exécuter l’exemple de code plus rapide, nous avons créé un échantillonnage représentatif de 1 % des données. Ces données vous permet de générer un modèle de classification binaire qui prévoit si un voyage particulier est susceptible d’obtenir un Conseil ou non, en fonction des colonnes, telles que l’heure du jour, distance et l’emplacement d’extraction.

### <a name="requirements"></a>Spécifications

Ce didacticiel est destiné aux utilisateurs qui sont déjà familiarisés avec les opérations fondamentales de la base de données, telles que la création de bases de données et tables, l’importation de données dans des tables et créer des requêtes SQL. Tout le code R est fourni, aucun environnement de développement R n’est donc nécessaire. Un programmeur expérimenté de SQL doit être en mesure d’effectuer cet exemple à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)] dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]et en exécutant les scripts PowerShell fournis.

Toutefois, avant de commencer le didacticiel, vous devez effectuer ces tâches de préparation :

- Se connecter à une instance de SQL Server 2016 avec R Services ou 2017 du serveur SQL avec les Services de Machine Learning et R activée.
- La connexion que vous utilisez pour ce didacticiel doit avoir les autorisations nécessaires pour créer des bases de données et autres objets, télécharger des données, sélectionnez les données et exécuter des procédures stockées.

> [!NOTE]
> Nous vous recommandons d’effectuer **pas** utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour écrire ou de tester le code R. Si le code que vous incorporez dans une procédure stockée a des problèmes, les informations retournées par la procédure stockée sont généralement insuffisant pour comprendre la cause de l’erreur.
> 
> Pour le débogage, nous vous recommandons d’utiliser un outil tel que [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)], ou RStudio. Les scripts R fournis dans ce didacticiel ont déjà été développés et débogués à l’aide des outils R traditionnels.

## <a name="next-lesson"></a>Leçon suivante

[Leçon 1 : Télécharger les exemples de données](../tutorials/sqldev-download-the-sample-data.md)
