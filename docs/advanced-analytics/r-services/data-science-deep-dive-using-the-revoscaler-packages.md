---
title: "Immersion dans la science des donn&#233;es : utilisation des packages RevoScaleR | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
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
ms.assetid: c2efb3f2-cad5-4188-b889-15d68b742ef5
caps.latest.revision: 18
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 17
---
# Immersion dans la science des donn&#233;es : utilisation des packages RevoScaleR
Ce didacticiel présente les packages R améliorés inclus dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Vous allez apprendre à utiliser l’infrastructure d’entreprise évolutive pour l’exécution de packages R dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].   Grâce à ces fonctions R évolutives, un spécialiste des données peut créer des solutions R personnalisées qui s’exécutent dans des contextes locaux ou de serveur, afin de prendre en charge l’analyse haute performance de Big Data.  
  
Dans ce didacticiel, vous allez apprendre à déplacer des données entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et votre station de travail R, à analyser et à tracer des données, et à créer et déployer des modèles.  
    
## Vue d'ensemble 
 
Dans ce didacticiel, pour illustrer la puissance de traitement et la flexibilité des packages ScaleR, vous allez déplacer des données et changer de contexte de calcul fréquemment.

+ Les données obtenues initialement proviennent de fichiers CSV ou XDF. Vous allez apprendre à importer des données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide des fonctions du package RevoScaleR.    
+ L’apprentissage et le calcul des scores des modèles sont effectués dans le contexte de calcul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
    Vous allez apprendre à créer des tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à l’aide des fonctions **rx**, pour enregistrer les résultats de vos calculs de score.    
+ Vous allez créer des graphiques à la fois sur le serveur et en local, dans le contexte de calcul.  
+ Pour former le modèle, vous utilisez des données déjà stockées dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Tous les calculs sont effectués sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].    
+ Vous allez extraire un sous-ensemble de données et l’enregistrer dans un fichier XDF pour pouvoir le réutiliser dans les analyses sur votre station de travail locale.    
+ Les nouvelles données utilisées pendant le processus de calcul de score sont extraites de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide d’une connexion ODBC. Tous les calculs sont effectués sur la station de travail locale. 
+ Enfin, vous allez effectuer une simulation basée sur une fonction R personnalisée, en utilisant le contexte de calcul du serveur.

### Prise en main  

Ce didacticiel prend environ une heure, sans compter la configuration.  

-   [Leçon 1 : Utiliser les données SQL Server à l’aide de R](../../advanced-analytics/r-services/lesson-1-work-with-sql-server-data-using-r-data-science-deep-dive.md)  
  
-   [Leçon 2 : Créer et exécuter des scripts R](../../advanced-analytics/r-services/lesson-2-create-and-run-r-scripts-data-science-deep-dive.md)  
  
-   [Leçon 3 : Transformer des données à l’aide de R](../../advanced-analytics/r-services/lesson-3-transform-data-using-r-data-science-deep-dive.md)  
  
-   [Leçon 4 : Analyser les données dans un contexte de calcul local](../../advanced-analytics/r-services/lesson-4-analyze-data-in-local-compute-context-data-science-deep-dive.md)  
  
-   [Leçon 5 : Créer une simulation simple](../../advanced-analytics/r-services/lesson-5-create-a-simple-simulation-data-science-deep-dive.md)  

      
### Public visé  
  
Ce didacticiel est destiné aux spécialistes des données et aux personnes qui sont déjà familiarisées avec R et la science des données, notamment l’exploration, l’analyse statistique et le réglage de modèles.  Tout le code est fourni. Vous pouvez donc facilement exécuter le code et suivre la procédure, en supposant que vous disposez des environnements client et serveur nécessaires.  
  
Vous devez également être familiarisé avec la syntaxe [!INCLUDE[tsql](../../includes/tsql-md.md)] et savoir comment accéder à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou d’autres outils de base de données, tels que Visual Studio.  
  
> [!TIP]  
> Enregistrez votre espace de travail R entre les leçons pour pouvoir facilement reprendre là où vous en étiez.  
  
### Conditions préalables  
  
-   **Serveur de base de données avec prise en charge de R**  
  
    Installez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et activez SQL Server R Services (dans la base de données). Ce processus est expliqué dans la [Documentation en ligne de SQL Server 2016](http://msdn.microsoft.com/library/mt696069(SQL.130).aspx).  
  
-   **Autorisations de base de données**  
  
    Pour exécuter les requêtes utilisées pour former le modèle, vous devez disposer des privilèges de **db_datareader** sur la base de données où sont stockées les données.  
  
  
-   **Station de travail de science des données**  
  
    Vous devez installer les packages RevoScaleR. Le moyen le plus simple de le faire consiste à installer Microsoft R Server (version autonome) ou le client Microsoft R. Pour plus d’informations, consultez [Configurer un client de science des données](http://msdn.microsoft.co/library/mt696067(SQL.130).aspx).
      
    > [!NOTE] 
    > Les autres versions de Revolution R Enterprise ou Revolution R Open ne sont pas prises en charge. 
    > 
    > Une distribution open source de R, telle que R 3.2.2, ne fonctionnera pas dans ce didacticiel, car seule la fonction ScaleR peut utiliser des contextes de calcul distants. 
  
-   **Packages R supplémentaires**  
  
    Pour ce didacticiel, vous devez installer les packages suivants : **dplyr**, **ggplot2**, **ggthemes**, **reshape2** et **e1071**. Des instructions sont fournies dans le didacticiel.  
  
    Tous les packages doivent également être installés sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur laquelle s’effectue l’apprentissage. Il est important que les packages soient installés dans la bibliothèque de packages R utilisée par SQL Server. **N’installez pas les packages dans une bibliothèque d’utilisateur.** Si vous n’êtes pas autorisé à installer des packages dans ce dossier, demandez à un administrateur de base de données d’ajouter les packages.   
  
Pour plus d’informations, consultez les [Conditions préalables pour les procédures pas à pas de science de données &#40;SQL Server R Services&#41;](../../advanced-analytics/r-services/prerequisites-for-data-science-walkthroughs-sql-server-r-services.md).  
  
## Stratégies de données pour les solutions R distribuées
    
En général, avant de commencer à écrire et exécuter des scripts R dans votre environnement de développement local, vous devez toujours prendre le temps de planifier votre utilisation des données et de déterminer l’emplacement d’exécution de chaque partie de la solution pour de meilleures performances.  

Dans ce didacticiel, vous utiliserez les fonctionnalités haute performance d’analyse de données, et apprendrez à créer des modèles et à créer les traçages inclus dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Nous parlerons de ces fonctions comme de fonctions ScaleR ou Microsoft R, pour les différencier des fonctions dérivées d’autres packages open source R. Pour plus d’informations sur les différences entre Microsoft R et R open source, consultez ce [guide de prise en main](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started#microsoft-r-products). 

L’un des principaux avantages des fonctions ScaleR, c’est qu’elles prennent en charge l’utilisation des *sources de données* locales et de serveur, ainsi que des *contextes de calcul* locaux et distants.  Par conséquent, pour ce didacticiel, réfléchissez aux stratégies de données que vous devrez adopter pour vos propres solutions.
  
-   **Quel type d’analyse voulez-vous effectuer ?** S’agit-il d’une analyse pour votre usage personnel ou allez-vous partager les modèles, les résultats ou les graphiques avec d’autres utilisateurs ?
 
    Dans ce didacticiel, vous allez apprendre à déplacer les résultats entre votre environnement de développement et le serveur (et inversement) pour faciliter le partage et l’analyse des données. 
  
-   **Le package R dont vous avez besoin prend-il en charge l’exécution à distance ?** Toutes les fonctions des packages ScaleR fournis par [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] peuvent être exécutées dans des contextes de calcul distants et éventuellement en parallèle. En revanche, les fonctions des packages tiers peuvent nécessiter des ressources supplémentaires pour une exécution monothread. 
    
    Dans ce didacticiel, vous allez apprendre à basculer entre les contextes de calcul locaux et distants pour tirer parti des ressources du serveur quand vous en avez besoin. Vous apprendrez également à encapsuler les fonctions R standard dans *rxExec* pour prendre en charge l’exécution à distance des fonctions R arbitraires.
    
  
-   **Où se trouvent vos données et quelles sont leurs caractéristiques ?**  Si vos données résident en local, vous devez décider si vous allez charger les nouvelles données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou effectuer l’apprentissage localement et enregistrer uniquement le modèle dans la base de données. Toutefois, lorsque vous déploierez les données sur le serveur de production, vous devrez peut-être effectuer l’apprentissage à partir des données d’entreprise et utiliser les processus ETL pour nettoyer et charger les données.  
  
-   Des questions similaires s’appliquent aux données de calcul de score. Allez-vous créer le pipeline des données de calcul de score sur votre station de travail ou allez-vous utiliser des sources de données d’entreprise ? Le nettoyage et la préparation des données seront-ils effectués dans le cadre des processus ETL ou s’agit-il d’une expérience unique ?  

    Dans ce didacticiel, vous allez apprendre à déplacer vos données efficacement et en toute sécurité entre votre environnement R local et SQL Server. 
  
-   **Quel contexte de calcul devez-vous utiliser ?** Vous pouvez effectuer l’apprentissage de votre modèle localement à partir de données échantillonnées, puis utiliser les données de serveur pour le serveur de test et de production.

    Dans ce didacticiel, vous allez apprendre à déplacer des données entre SQL Server et R à l’aide de R. Vous apprendrez également à utiliser des données à l’aide de fichiers XDF et à traiter des données de segments à l’aide de fonctions ScaleR.  
  
 
  
## Étape suivante  
[Leçon 1 : Utiliser les données SQL Server à l’aide de R &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/lesson-1-work-with-sql-server-data-using-r-data-science-deep-dive.md)  
  
  
  
