---
title: "Analytique avanc&#233;e en base de donn&#233;es pour les d&#233;veloppeurs SQL (Didacticiel) | Microsoft Docs"
ms.custom: ""
ms.date: "04/19/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
  - "TSQL"
ms.assetid: c18cb249-2146-41b7-8821-3a20c5d7a690
caps.latest.revision: 15
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# Analytique avanc&#233;e en base de donn&#233;es pour les d&#233;veloppeurs SQL (Didacticiel)
L’objectif de cette procédure pas à pas consiste à fournir aux programmeurs SQL une expérience pratique pour créer une solution analytique avancée à l’aide de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Dans cette procédure pas à pas, vous allez apprendre à intégrer R dans une application ou une solution BI en encapsulant le code R dans des procédures stockées.  
  
## Vue d'ensemble  
Le processus de création d’une solution de bout en bout comprend généralement l’obtention et le nettoyage des données, l’exploration des données et l’ingénierie des caractéristiques, l’apprentissage et le réglage de modèles, et enfin le déploiement du modèle en production. Le développement et les tests du code R réel fournissent de meilleurs résultats dans un environnement de développement conçu pour R, tel que RStudio ou [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)]. Toutefois, une fois que la solution est créée, vous pouvez facilement la déployer sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] dans l’environnement familier de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
Par conséquent, dans cette procédure pas à pas nous supposons que vous avez reçu tout le code R nécessaire pour la solution et que vous vous concentrez sur la conception et le déploiement d’une solution analytique avancée qui a déjà été codée en R.  
  
-   [Étape 1 : Télécharger les exemples de données](../../advanced-analytics/r-services/step-1-download-the-sample-data-in-database-advanced-analytics-tutorial.md).    Téléchargez l’exemple de dataset et les exemples de fichiers de script SQL sur un ordinateur local.  
  
-   [Étape 2 : Importer des données dans SQL Server à l’aide de PowerShell](../../advanced-analytics/r-services/step-2-import-data-to-sql-server-using-powershell.md).  Exécutez un script PowerShell qui crée une base de données et une table sur l’instance [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], et charge les exemples de données dans la table.  
  
-   [Étape 3 : Explorer et visualiser les données](../../advanced-analytics/r-services/step-3-explore-and-visualize-the-data-in-database-advanced-analytics-tutorial.md).   Effectuez une exploration et une visualisation de données de base en appelant des packages R et des fonctions de procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   [Étape 4 : Créer des caractéristiques de données à l’aide de T-SQL](../../advanced-analytics/r-services/step-4-create-data-features-using-t-sql-in-database-advanced-analytics-tutorial.md).  Créez des caractéristiques de données à l’aide de fonctions personnalisées.  
  
-   [Étape 5 : Former et enregistrer un modèle à l’aide de T-SQL](../../advanced-analytics/r-services/step-5-train-and-save-a-model-using-t-sql.md).  Créez et enregistrez le modèle d’apprentissage automatique à l’aide de procédures stockées.  
  
-   [Étape 6 : Rendre le modèle opérationnel](../../advanced-analytics/r-services/step-6-operationalize-the-model-in-database-advanced-analytics-tutorial.md).  Une fois que le modèle a été enregistré dans la base de données, appelez-le pour la prédiction dans [!INCLUDE[tsql](../../includes/tsql-md.md)] à l’aide de procédures stockées.  
  
> [!NOTE]  
> Nous vous recommandons de ne pas utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour écrire ou tester le code R. Si le code R que vous incorporez dans une procédure stockée a des problèmes, les informations retournées par la procédure stockée ne permettent généralement pas d’identifier la cause de l’erreur.   
>   
> Pour le débogage, nous vous recommandons d’utiliser un outil tel que RStudio ou [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)]. Les scripts R fournis dans ce didacticiel ont déjà été développés et débogués à l’aide des outils R traditionnels.  
>   
> Si vous souhaitez savoir comment développer des scripts R qui peuvent s’exécuter dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], consultez ce didacticiel : [Procédure pas à pas pour une solution complète de science des données](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md))  
  
### Scénario  
Cette procédure pas à pas utilise le jeu de données NYC Taxi bien connu. Ce jeu de données public contient 20 Go de fichiers CSV compressés (environ 48 Go décompressés), qui décrivent les détails de plus de 173 millions de courses de taxi individuelles en 2013, ainsi que les tarifs de chaque course. Pour rendre cette procédure pas à pas facile et rapide, nous avons créé un échantillon représentatif des données : 1 % des données, soit 1 703 957 lignes et 23 colonnes. Pour cette procédure pas à pas, vous utilisez ces données pour créer un modèle de classification binaire qui prédit si une course en particulier est susceptible d’obtenir un pourboire ou non, en fonction de colonnes telles que l’heure du jour, la distance et le lieu de prise en charge.  
  
  
### Spécifications  
Cette procédure pas à pas est destinée aux utilisateurs qui sont déjà familiarisés avec les opérations fondamentales de base de données, telles que la création de tables et de bases de données, l’importation de données dans des tables et la création de requêtes SQL. Tout le code R est fourni, aucun environnement de développement R n’est donc nécessaire. Un programmeur SQL expérimenté doit être en mesure d’effectuer cette procédure pas à pas à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)] dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou en exécutant les scripts PowerShell fournis.  
  
Toutefois, avant de commencer la procédure pas à pas, vous devez effectuer ces tâches de préparation :  
  
-   Connectez-vous à une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] avec SQL Server R Services activé (nécessite CTP 3 ou version ultérieure). Pour plus d’informations, consultez les instructions d’installation : [Configurer SQL Server R Services (dans la base de données)](https://msdn.microsoft.com/library/mt696069.aspx)  
  
 -   La connexion que vous utilisez pour cette procédure pas à pas doit avoir les autorisations pour créer des bases de données et autres objets, pour charger des données, sélectionner des données et exécuter des procédures stockées.  
  
## Étape suivante  
[Étape 1 : Télécharger les exemples de données](../../advanced-analytics/r-services/step-1-download-the-sample-data-in-database-advanced-analytics-tutorial.md)  
  
## Voir aussi  
[Didacticiels pour SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
[SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)  
  
  
  
