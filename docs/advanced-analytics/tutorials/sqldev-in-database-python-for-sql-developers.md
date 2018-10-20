---
title: En base de données analytique de Python pour les développeurs SQL | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 250d2efd6d212348083f5dc3bbc355c466f4811b
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461855"
---
# <a name="in-database-python-analytics-for-sql-developers"></a>Analytique en base de données Python pour les développeurs SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L’objectif de cette procédure pas à pas consiste à fournir aux programmeurs SQL expérience pratique pour créer une solution machine learning à l’aide de Python qui s’exécute dans SQL Server. Dans cette procédure pas à pas, vous allez apprendre à ajouter le code Python à des procédures stockées et exécuter des procédures stockées pour générer et de prédire à partir de modèles.

> [!NOTE]
> Vous préférez R ? Consultez [ce didacticiel](sqldev-in-database-r-for-sql-developers.md), qui fournit une solution similaire, mais utilise R et peut être exécuté dans SQL Server 2016 ou SQL Server 2017.

## <a name="overview"></a>Vue d'ensemble

Le processus de création d’une solution d’apprentissage est complexe qui peut impliquer plusieurs outils et la coordination des experts du sujet dans plusieurs phases :

+ obtention et le nettoyage des données
+ Explorer des données et création de fonctionnalités utiles pour la modélisation
+ apprentissage et le modèle de paramétrage
+ déploiement en production

**Cette procédure pas à pas porte sur la conception et déploiement d’une solution à l’aide de SQL Server.**

Les données sont dans le jeu de données NYC Taxi bien connu. Pour effectuer cette procédure pas à pas simple et rapide, les données sont échantillonnées. Vous allez créer un modèle de classification binaire qui prédit si un voyage en particulier est susceptible d’obtienne un pourboire ou non, selon les colonnes telles que l’heure de la journée, distance et l’emplacement de la prise en charge.

Toutes les tâches peuvent être effectuées à l’aide [!INCLUDE[tsql](../../includes/tsql-md.md)] des procédures stockées dans l’environnement familier de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]

- [Étape 1 : Télécharger les exemples de données](demo-data-nyctaxi-in-sql.md)

    Téléchargez l’exemple de dataset et tous les fichiers de script sur un ordinateur local.

- [Étape 2 : Importer des données dans SQL Server à l’aide de PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

    Exécuter un script PowerShell qui crée une base de données et une table sur l’instance spécifiée et charge les exemples de données à la table.

- [Étape 3 : Explorer et visualiser les données à l’aide de Python](sqldev-py3-explore-and-visualize-the-data.md)

    Effectuer l’exploration de données de base et la visualisation, en appelant Python à partir de [!INCLUDE[tsql](../../includes/tsql-md.md)] des procédures stockées.

- [Étape 4 : Créer des fonctionnalités de données à l’aide de Python dans T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

    Créez des caractéristiques de données à l’aide de fonctions personnalisées.
  
- [Étape 5 : Former et enregistrer un modèle de Python à l’aide de T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

    Créer et enregistrer le modèle d’apprentissage automatique, à l’aide de Python dans les procédures stockées.
  
    Cette procédure pas à pas montre comment effectuer une tâche de classification binaire ; Vous pouvez également utiliser les données pour générer des modèles de régression ou la classification multiclasse.

  
-  [Étape 6 : Rendre opérationnel du modèle Python](sqldev-py6-operationalize-the-model.md)

    Une fois que le modèle a été enregistré dans la base de données, appelez le modèle pour la prédiction à l’aide [!INCLUDE[tsql](../../includes/tsql-md.md)].

## <a name="requirements"></a>Spécifications

### <a name="prerequisites"></a>Prérequis

+ Installez une instance de SQL Server 2017 avec les Services Machine Learning et Python est activée. Pour plus d’informations, consultez [installer SQL Server 2017 Machine Learning Services (en base de données)](../install/sql-machine-learning-services-windows-install.md).
+ La connexion que vous utilisez pour cette procédure pas à pas doit avoir les autorisations pour créer des bases de données et autres objets, pour charger des données, sélectionner des données et exécuter des procédures stockées.

### <a name="experience-level"></a>Niveau d’expérience

Vous devez connaître avec les opérations fondamentales de la base de données, telles que la création de tables et des bases de données, l’importation de données dans des tables et créer des requêtes SQL.

Un programmeur SQL expérimenté doit être en mesure d’effectuer cette procédure pas à pas à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)] dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou en exécutant les scripts PowerShell fournis.

Python : Une connaissance élémentaire est utile mais pas obligatoire. Tout le code Python est fourni.

Une connaissance de PowerShell est utile.

### <a name="tools"></a>Outils

Pour ce didacticiel, nous partons du principe que vous avez atteint la phase de déploiement. Vous disposent de nettoyer les données, le code T-SQL pour la fonctionnalité d’ingénierie et l’utilisation de code Python complet. Par conséquent, vous pouvez suivre ce didacticiel à l’aide de SQL Server Management Studio, ou tout autre outil qui prend en charge les instructions SQL en cours d’exécution.

+ [Vue d’ensemble des outils SQL Server](https://docs.microsoft.com/sql/tools/overview-sql-tools) 

Si vous souhaitez développer et tester votre propre code Python ou que vous déboguez une solution de Python, nous recommandons d’utiliser un environnement de développement dédié :

+ **Visual Studio 2017** prend en charge les deux R et [Python](https://blogs.msdn.microsoft.com/visualstudio/2017/05/12/a-lap-around-python-in-visual-studio-2017/). Nous vous recommandons du [charge de travail de science des données](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/data-science-workloads-in-visual-studio-2017-rc/), qui prend également en charge R et F #.
+ Si vous avez une version antérieure de Visual Studio, [Extensions Python pour Visual Studio](https://docs.microsoft.com/visualstudio/python/python-in-visual-studio) rend facile à gérer plusieurs environnements Python.
+ PyCharm est un IDE populaires parmi les développeurs Python.

    > [!NOTE]
    > En règle générale, évitez écrire ou tester le nouveau code Python dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Si le code que vous incorporez dans une procédure stockée a des problèmes, les informations retournées par la procédure stockée ne permettent généralement pas d’identifier la cause de l’erreur.

Utilisez les ressources suivantes pour vous aider à planifier et exécuter un projet d’apprentissage réussie :

+ [Team Data Science Process](https://docs.microsoft.com/azure/machine-learning/team-data-science-process/overview)

### <a name="estimated-time-required"></a>Durée estimée nécessaire

|Étape| Temps (h)|
|----|----|
|Télécharger les exemples de données| 0:15|
|Importer des données dans SQL Server à l’aide de PowerShell|0:15|
|Explorer et visualiser les données|0:20|
|Créer des caractéristiques de données à l’aide de T-SQL|0:30|
|Former et enregistrer un modèle à l’aide de T-SQL|0:15|
|Rendre le modèle opérationnel|0:40|

## <a name="get-started"></a>Bien démarrer

  [Étape 1 : Télécharger les exemples de données](demo-data-nyctaxi-in-sql.md)
