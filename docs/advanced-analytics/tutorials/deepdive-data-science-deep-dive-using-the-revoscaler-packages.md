---
title: "Immersion dans la science des données : utilisation des packages RevoScaleR | Microsoft Docs"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: c2efb3f2-cad5-4188-b889-15d68b742ef5
caps.latest.revision: 18
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 51f4a782ad941d8b9a66ba00cbf2b3540478361c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="data-science-deep-dive-using-the-revoscaler-packages"></a>Immersion dans la science des données : utilisation des packages RevoScaleR

Ce didacticiel montre comment utiliser les packages R améliorés fournis dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] pour travailler avec des données SQL Server et créer des solutions R évolutives, en utilisant le serveur en tant qu’un contexte de calcul pour l’analytique des données hautes performances.

Vous allez apprendre à créer un contexte de calcul à distance, de déplacer des données entre les contextes de calcul locaux et distants et exécuter le code R sur un serveur SQL distant. Vous allez également apprendre comment analyser et tracer des données à la fois localement et sur le serveur distant et comment créer et déployer des modèles.

> [!NOTE]
> 
> Ce didacticiel fonctionne plus précisément les données SQL Server sur Windows et utilise des contextes de calcul de la base de données. Si vous souhaitez utiliser R dans d’autres contextes, tels que Teradata, Linux ou Hadoop, consultez les didacticiels de Microsoft R Server : 
> + [Utiliser un serveur R avec sparklyr](https://msdn.microsoft.com/microsoft-r/microsoft-r-get-started-spark-interop)
> + [Explore R and ScaleR in 25 functions](https://msdn.microsoft.com/microsoft-r/microsoft-r-tutorial-r2revoscaler) (Découvrir 25 fonctions de R et ScaleR)
> + [Prise en main ScaleR sur Hadoop MapReduce](https://msdn.microsoft.com/microsoft-r/scaler-hadoop-getting-started)
> + [Guide de démarrage RevoScaleR Teradata mise en route](https://msdn.microsoft.com/microsoft-r/scaler-teradata-getting-started)

## <a name="overview"></a>Vue d'ensemble

Dans ce didacticiel, pour illustrer la puissance de traitement et la flexibilité des packages ScaleR, vous allez déplacer des données et changer de contexte de calcul fréquemment.

+ Les données obtenues initialement proviennent de fichiers CSV ou XDF. Vous allez apprendre à importer des données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide des fonctions du package RevoScaleR.
+ L’apprentissage et le calcul des scores des modèles sont effectués dans le contexte de calcul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
    Vous allez apprendre à créer des tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , à l’aide des fonctions **rx** , pour enregistrer les résultats de vos calculs de score.
+ Vous allez créer des graphiques à la fois sur le serveur et en local, dans le contexte de calcul.
+ Pour former le modèle, vous utilisez des données déjà stockées dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Tous les calculs sont effectués sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
+ Vous allez extraire un sous-ensemble de données et l’enregistrer dans un fichier XDF pour pouvoir le réutiliser dans les analyses sur votre station de travail locale.
+ Les nouvelles données utilisées pendant le processus de calcul de score sont extraites de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide d’une connexion ODBC. Tous les calculs sont effectués sur la station de travail locale.
+ Enfin, vous allez effectuer une simulation basée sur une fonction R personnalisée, en utilisant le contexte de calcul du serveur.

### <a name="get-started-now"></a>Prise en main

Ce didacticiel prend environ 75 minutes, ne pas les paramètres de configuration.

1. [Travailler avec des données SQL Server à l’aide de R](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)
2. [Créer des objets de données SQL Server à l’aide de RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
3. [Interroger et modifier les données du serveur SQL](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)
4. [Définir et utiliser les contextes de calcul](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)
5. [Créer et exécuter des Scripts R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
6. [Visualiser les données de SQL Server à l’aide de R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)
7. [Créez des modèles R](../../advanced-analytics/tutorials/deepdive-create-models.md)
8. [Score de nouvelles données](../../advanced-analytics/tutorials/deepdive-score-new-data.md)
9. [Transformer des données à l’aide de R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)
10. [Charger des données dans la mémoire à l’aide de rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)
11. [Créer la nouvelle Table SQL Server à l’aide de rxDataStep](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
12. [Effectuer une analyse de segmentation à l’aide de rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
13. [Analyser les données dans le contexte de calcul Local ;](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)
14. [Déplacement des données entre SQL Server et le fichier XDF](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
15. [Créez une Simulation Simple](../../advanced-analytics/tutorials/deepdive-create-a-simple-simulation.md)

### <a name="target-audience"></a>Public visé

Ce didacticiel est destiné aux spécialistes des données et aux personnes qui sont déjà familiarisées avec R et la science des données, notamment l’exploration, l’analyse statistique et le réglage de modèles.  Toutefois, tout le code est fourni, même si vous ne connaissez pas R, vous pouvez donc facilement exécuter le code et suivre la procédure, en supposant que vous avez les environnements de client et le serveur requis.

Vous devez également être familiarisé avec la syntaxe [!INCLUDE[tsql](../../includes/tsql-md.md)] et savoir comment accéder à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou d’autres outils de base de données, tels que Visual Studio.
  
> [!TIP]
> Enregistrez votre espace de travail R entre les leçons pour pouvoir facilement reprendre là où vous en étiez.

### <a name="prerequisites"></a>Conditions préalables

- **SQL Server avec prise en charge pour R**
  
    Installer SQL Server 2016 et activer R Services (de-de base de données). Ou, installez SQL Server 2017 et activer les Services de Machine Learning et choisissez le langage R. Le processus d’installation est décrit dans [la documentation en ligne de SQL Server 2016](http://msdn.microsoft.com/library/mt696069(SQL.130).aspx).
  
-  **Autorisations de base de données**
  
    Pour exécuter les requêtes utilisées pour former le modèle, vous devez disposer des privilèges de **db_datareader** sur la base de données où sont stockées les données. Pour exécuter R, l’utilisateur doit disposer de l’autorisation EXECUTE ANY EXTERNAL SCRIPT.

-   **Ordinateur de développement de science des données**
  
    Vous devez également installer les packages de RevoScaleR et les fournisseurs associés dans votre environnement de développement R. Pour ce faire, le plus simple consiste à installer Microsoft R Client ou Microsoft R Server (autonome). Pour plus d’informations, consultez [Configurer un client de science des données](http://msdn.microsoft.co/library/mt696067(SQL.130).aspx).
      
    > [!NOTE] 
    > Les autres versions de Revolution R Enterprise ou Revolution R Open ne sont pas prises en charge.
    > 
    > Une distribution open source de R, tel que R 3.2.2, ne fonctionnera pas dans ce didacticiel, car seules les fonctions RevoScaleR peuvent utiliser les contextes de calcul à distance.
  
-   **Packages R supplémentaires**
  
    Pour ce didacticiel, vous devez installer les packages suivants : **dplyr**, **ggplot2**, **ggthemes**, **reshape2**et **e1071**. Des instructions sont fournies dans le didacticiel.
  
    Tous les packages doivent être installés dans deux emplacements : sur l’ordinateur que vous utilisez pour le développement de solutions de R et sur l’ordinateur SQL Server où des scripts R seront exécutées. Si vous n’avez pas l’autorisation d’installer des packages sur l’ordinateur serveur, demandez à un administrateur. **N’installez pas les packages dans une bibliothèque d’utilisateur.** Il est important que les packages installés dans la bibliothèque de package de R est utilisée par l’instance de SQL Server.

Pour plus d’informations, consultez [conditions préalables pour les procédures pas à pas de données scientifiques](../../advanced-analytics/tutorials/walkthrough-prerequisites-for-data-science-walkthroughs.md).



## <a name="next-step"></a>Étape suivante

[Travailler avec des données SQL Server à l’aide de R](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)


