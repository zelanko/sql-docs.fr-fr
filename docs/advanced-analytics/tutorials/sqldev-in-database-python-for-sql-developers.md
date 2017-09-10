---
title: "Dans base de données Analytique de Python pour les développeurs SQL | Documents Microsoft"
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 984ff8097b1f28cf11e28cc464c88dc3b9580a12
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="in-database-python-analytics-for-sql-developers"></a>Dans base de données Analytique de Python pour les développeurs SQL

L’objectif de cette procédure pas à pas est de fournir des programmeurs SQL avec une expérience pratique de créer une solution dans SQL Server d’apprentissage. Dans cette procédure pas à pas, vous allez apprendre à intégrer les Python dans une application en ajoutant le code Python à des procédures stockées.

> [!NOTE]
> Préférez R ? Consultez [ce didacticiel](sqldev-in-database-r-for-sql-developers.md), qui fournit une solution similaire, mais utilise R, et peut s’exécuter eb dans SQL Server 2016 ou SQL Server 2017.

## <a name="overview"></a>Vue d'ensemble

Le processus de création d’une solution de bout en bout comprend généralement l’obtention et le nettoyage des données, l’exploration des données et l’ingénierie des caractéristiques, l’apprentissage et le réglage de modèles, et enfin le déploiement du modèle en production. Développement et test du code réel est préférable d’effectuer à l’aide d’un environnement de développement dédié, telles que ces outils Python :

+ PyCharm, un IDE populaires
+ Spyder, qui est inclus avec [Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2017/05/12/a-lap-around-python-in-visual-studio-2017/) si vous installez le [charge de travail de science des données](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/data-science-workloads-in-visual-studio-2017-rc/)
+ [Extensions de Python pour Visual Studio](https://docs.microsoft.com/visualstudio/python/python-in-visual-studio).

Une fois que vous avez créé et testé la solution dans l’IDE, vous pouvez déployer le code Python à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)] des procédures stockées dans l’environnement familier de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Dans cette procédure pas à pas, nous supposerons que vous avez reçu de tout le code Python que nécessaire pour la solution, et vous devez vous concentrer sur la génération et déploiement de la solution à l’aide de SQL Server.

- [Étape 1 : Télécharger les exemples de données](sqldev-py1-download-the-sample-data.md)

  Téléchargez l’exemple de dataset et tous les fichiers de script sur un ordinateur local.

- [Étape 2 : Importer des données dans SQL Server à l’aide de PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

  Exécuter un script PowerShell qui crée une base de données et une table sur l’instance spécifiée et charge les données d’exemple à la table.

- [Étape 3 : Explorer et visualiser les données](sqldev-py3-explore-and-visualize-the-data.md)

  En appelant Python à partir de la visualisation et l’exploration de données de base [!INCLUDE[tsql](../../includes/tsql-md.md)] des procédures stockées.

- [Étape 4 : Créer des fonctionnalités de données à l’aide de T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

  Créez des caractéristiques de données à l’aide de fonctions personnalisées.
  
- [Step 5 : Former et enregistrer un modèle à l’aide de T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

   Générez et enregistrez le modèle d’apprentissage automatique, à l’aide de Python dans les procédures stockées.
  
-  [Étape 6 : Rendre le modèle opérationnel](sqldev-py6-operationalize-the-model.md)

  Une fois que le modèle a été enregistré dans la base de données, appelez le modèle pour la prédiction à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)].

> [!NOTE]
> Nous vous recommandons de ne pas utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour écrire ou de tester le code Python. Si le code que vous incorporez dans une procédure stockée a des problèmes, les informations retournées par la procédure stockée sont généralement insuffisant pour comprendre la cause de l’erreur.


### <a name="scenario"></a>Scénario

Cette procédure pas à pas utilise le jeu de données NYC Taxi bien connu. Pour effectuer cette procédure pas à pas simple et rapide, les données sont échantillonnées. À l’aide de ces données, vous allez créer un modèle de classification binaire qui prédit si un voyage particulier est susceptible d’obtenir un Conseil ou non, en fonction des colonnes, telles que l’heure du jour, distance et l’emplacement d’extraction.

### <a name="requirements"></a>Spécifications

Cette procédure pas à pas est destinée aux utilisateurs qui sont déjà familiarisés avec les opérations fondamentales de base de données, telles que la création de tables et de bases de données, l’importation de données dans des tables et la création de requêtes SQL.

Tout le code Python est fourni. Un programmeur SQL expérimenté doit être en mesure d’effectuer cette procédure pas à pas à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)] dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou en exécutant les scripts PowerShell fournis.

Avant de commencer la procédure pas à pas, vous devez effectuer ces tâches de préparation :

- Installer une instance de SQL Server 2017 avec Machine Learning Services et Python activé (requiert la version CTP 2.0 ou version ultérieure).
- La connexion que vous utilisez pour cette procédure pas à pas doit avoir les autorisations pour créer des bases de données et autres objets, pour charger des données, sélectionner des données et exécuter des procédures stockées.

## <a name="next-step"></a>Étape suivante

  [Étape 1 : Télécharger les exemples de données](sqldev-py1-download-the-sample-data.md)

## <a name="see-also"></a>Voir aussi

[Machine Learning Services avec Python](../python/sql-server-python-services.md)



