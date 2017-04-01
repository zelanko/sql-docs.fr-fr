---
title: "Prise en main de Microsoft R Server (autonome) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "r-server"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52347d0d-ce60-4bb8-98d2-6163e87716b0
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 16
---
# Prise en main de Microsoft R Server (autonome)
  Microsoft R Server (autonome) vous permet de mettre en œuvre le langage R Open Source populaire dans votre entreprise pour permettre l’utilisation de solutions d’analyse hautes performances et l’intégration avec d’autres applications de gestion des informations professionnelles.  
  
## Qu’est-ce que Microsoft R Server ?  
 Microsoft R Server (autonome) inclut les packages R améliorés développés par Revolution Analytics et prend en charge les connexions à diverses sources de données, telles que Hadoop, Teradata et plus encore. En installant le serveur autonome, vous pouvez créer un environnement serveur pour l’exécution de travaux R complexes et évolutifs.  
  
## Avantages de l’utilisation du serveur Microsoft R (autonome)  
 R est le langage de programmation le plus puissant au monde pour le calcul de statistiques, l’apprentissage automatique et la création de graphiques. Il est soutenu par une communauté mondiale d’utilisateurs, de développeurs et de contributeurs toujours plus nombreuse. En règle générale, l’utilisation du langage R dans un environnement d’entreprise présente certains défis, en particulier quand le volume de données augmente, ou lorsque vous avez besoin de déployer des solutions dans des environnements de production. Microsoft R Server résout le problème lié au déploiement et à l’opérationnalisation du code R.  
  
 Microsoft R Server peut être installé sur n’importe quel ordinateur Windows et inclut tous les packages R et les outils de connectivité pour activer le contexte de calcul à distance et prendre en charge des solutions évolutives et parallèles.  
  
 Microsoft R serveur (autonome) prend en charge ces scénarios :  
  
-   **Utilisation d’un serveur central pour opérationnaliser les solutions R**  
  
     Le serveur autonome vous offre des performances R améliorées sans avoir recours à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Calculs complexes ou gourmandes en ressources peuvent être exécutées sur le serveur sur un ordinateur portable ou de développement qui peut avoir des ressources limitées.  
  
     Vous pouvez également centraliser les tâches, par exemple, si vous souhaitez évaluer par rapport à un modèle prédictif en production, ou utiliser le serveur R comme un point de contact unique pour R et les prévisions utilisée dans le rapport. 
     
     Nous recommandons également d’installer le serveur de R (autonome) sur votre ordinateur SQL Server si vous devez fréquemment exécuter R en dehors du contexte de SQL Server.
  
-   **Mise en œuvre d’une exploration de données et d’une modélisation prédictive plus puissantes**  
  
     Le spécialiste des données peut utiliser n’importe quelle station de travail cliente et n’importe quel outil de développement R pour créer des solutions R. Si la solution s’appuie sur les API du package RevoScaleR, les calculs peuvent être effectués sur le serveur, ce qui offre généralement une mémoire et une puissance de traitement considérablement accrues. Vos solutions peuvent ainsi prendre en charge des jeux de données beaucoup plus volumineux et tirer parti des calculs multithreads, multicœurs et multiprocessus.  
  
## Comment l’obtenir ?  
 Pour connaître les instructions d’installation, consultez [Create a Standalone R Server](../../advanced-analytics/r-services/create-a-standalone-r-server.md). Tous les composants peuvent être installés à l’aide de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation.  
  
## Installer les outils R supplémentaires  
 Si vous n’avez pas un environnement de développement préféré R, il existe de nombreuses options. Pour plus d’informations, consultez [le programme d’installation ou de configurer les outils R](../../advanced-analytics/r-services/setup-or-configure-r-tools.md). 
 
 Pour la connexion à Microsoft R Server ou aux Services de R SQL Server à partir d’une station de travail de science des données, nous vous recommandons la version gratuite [Microsoft R Client](http://aka.ms/rclient/download) (télécharger).  
  
## Le Script R en cours d’exécution sur le serveur Microsoft R (autonome)  
 Après avoir configuré les composants du serveur et installé votre IDE favori de R, vous pouvez commencer à développer votre solution à l’aide du package RevoScaleR. Ces API vous permettent d’envoyer des commandes R sur un serveur distant à des fins d’exécution.  
  
-   [DETARTREUR](https://msdn.microsoft.com/microsoft-r/scaler-getting-started): démarrer en explorant cette collection de fonctions analytiques distribuables qui offrent des performances élevées et de mise à l’échelle des solutions de R. Inclut des versions parallèles de nombreux packages, tels que le clustering k-means, arbres de décision, les forêts de décision et des outils pour la manipulation des données de modélisation R plus populaires. Vous pouvez également utiliser HPC pour construire votre propre algorithme parallèle.  
    
-   [DeployR](https://msdn.microsoft.com/microsoft-r/deployr-about): cette option framework fournit les outils R programmeurs Java, JavaScript ou .net pour intégrer l’analyse R de sortie avec un package tiers.  

Vous pouvez travailler avec des données dans divers formats, y compris les fichiers SAS, SPSS, Hadoop et texte. Vous pouvez analyser les données en place ou déplacer vos données de manière efficace dans votre environnement de développement local R en utilisant le format de fichier .xdf.  
  
Pour commencer avec un serveur de R, consultez ce guide dans la bibliothèque MSDN : [R Server - mise en route](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started)  
  
 Pour plus d’informations sur l’utilisation de packages ScaleR, consultez [un didacticiel de R dans les 25 fonctions](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started#an-r-tutorial-in-25-functions-or-so)  
  
## Voir aussi  
 [Prise en main de SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
  
  