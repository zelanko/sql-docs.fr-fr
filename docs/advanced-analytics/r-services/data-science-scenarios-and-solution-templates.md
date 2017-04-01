---
title: "Sc&#233;narios de science des donn&#233;es et mod&#232;les de solutions | Microsoft Docs"
ms.custom: ""
ms.date: "04/18/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 49e54fa9-9b28-44ba-b256-06dad4e8dece
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 17
---
# Sc&#233;narios de science des donn&#233;es et mod&#232;les de solutions
Les modèles sont des exemples de solutions qui illustrent les bonnes pratiques et fournissent les bases qui vous aideront à implémenter une solution rapidement. Chaque modèle est conçu pour résoudre un problème spécifique et inclut des exemples de données, du code R (Microsoft R Server) et des procédures stockées SQL. Les tâches dans chaque modèle vont de la préparation des données à la formation du modèle et au calcul des scores, en passant par l’ingénierie des caractéristiques. Vous pouvez exécuter le code dans un environnement de développement intégré R, les calculs étant effectués dans SQL Server ou à l’aide d’un outil client SQL tel que SQL Server Management Studio.  
  
Vous pouvez utiliser ces modèles pour découvrir comment fonctionne [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], et générer et déployer votre propre solution en personnalisant le modèle selon votre propre scénario.  
  
Pour obtenir des instructions de téléchargement et d’installation, consultez [Comment utiliser les modèles](#bkmk_HowTo) à la fin de cette rubrique.  
  
## Détection des fraudes  
[Modèle de détection de fraude en ligne (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/FraudDetection/Introduction.md)  
  
Pour une entreprise effectuant des transactions en ligne, l’une des tâches importantes consiste à détecter les transactions frauduleuses et à identifier celles effectuées à l’aide de moyens de paiement ou d’informations d’identification dérobés, afin de réduire les pertes financières. Quand des transactions frauduleuses sont découvertes, les entreprises prennent généralement des mesures pour bloquer certains comptes dès que possible, afin d’empêcher toute perte supplémentaire. Dans ce scénario, vous allez découvrir comment utiliser des données de transactions d’achat en ligne pour identifier les fraudes probables. Vous pouvez facilement appliquer cette méthodologie à la détection des fraudes dans d’autres domaines.  
  
Dans ce modèle, vous allez découvrir comment utiliser des données de transactions d’achat en ligne pour identifier les fraudes probables. La détection des fraudes est résolue en tant que problème de classification binaire. Vous pouvez facilement appliquer la méthodologie utilisée dans ce modèle à la détection des fraudes dans d’autres domaines.    
  
## Taux d’attrition  
[Modèle de prédiction de taux d’attrition (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/Churn/Introduction.md)  
  
L’analyse et la prédiction du taux d’attrition sont importantes dans tout secteur où la perte de clients à la concurrence doit être gérée et prévenue : secteur bancaire, télécommunications et vente au détail, pour n’en citer que quelques-uns. L’objectif de l’analyse de l’attrition consiste à identifier les clients susceptibles de passer à la concurrence, puis d’effectuer les actions appropriées pour conserver ces clients.  
  
Ce modèle aborde la prévention de l’attrition en formulant le problème de l’attrition en tant que problème de **classification binaire**. Il utilise des exemples de données de deux sources, données démographiques et transactions de clients, pour classer les clients comme susceptibles ou non de passer à la concurrence.   
  
## Maintenance prédictive  
[Modèle de maintenance prédictive (SQL Server 2016)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/PredictiveMaintenance/Introduction.md)  
  
L’objectif de la maintenance prédictive « pilotée par les données » consiste à augmenter l’efficacité des tâches de maintenance en capturant les défaillances passées et en utilisant ces informations pour prédire quand et où un appareil est susceptible de tomber en panne. La capacité à prédire l’obsolescence d’appareils est particulièrement importante pour les applications qui reposent sur des capteurs ou des données distribués, comme dans le cas de l’Internet des objets (IoT).  
  
Ce modèle s’attache à répondre à la question « Quand un ordinateur en service va-t-il tomber en panne ? » Les données d’entrée représentent des mesures de capteurs simulées pour des moteurs d’avion. Les données obtenues à partir de la surveillance des conditions d’exploitation actuelles du moteur, telles que le cycle de travail, les paramètres, les mesures de capteurs et ainsi de suite, sont utilisées pour créer trois types de modèles prédictifs :  
  
-   **Modèles de régression**, pour prédire dans combien de temps un moteur tombera en panne. L’exemple de modèle prédit la métrique Durée de vie restante (RUL), également appelée Time to Failure (TTF).  
  
-   **Modèles de classification**, pour prédire si un moteur est susceptible de tomber en panne.  
  
    Le **modèle de classification binaire** prédit si un moteur tombera en panne dans un délai donné (nombre de jours).  
  
    Le **modèle de classification multiclasse** prédit si un moteur particulier tombera en panne et, si oui, fournit une fenêtre de temps de défaillance probable. Par exemple, pour un jour donné, vous pouvez prédire si un appareil est susceptible de tomber en panne ce jour-là ou dans un laps de temps suivant ce jour.  
      
      
## Prévision de demande d’énergie  
[Modèle de prévision de demande d’énergie avec SQL Server R Services](https://gallery.cortanaintelligence.com/Tutorial/Energy-Demand-Forecast_Template_with_SQL-Server-R-Services-1)  
  
Ce modèle montre comment utiliser SQL Server R Services pour prédire la demande en électricité. La solution comprend un simulateur de demande, tout le code R et T-SQL nécessaire pour former un modèle, ainsi que les procédures stockées que vous pouvez utiliser pour générer des prédictions et créer des rapports.   
  
## <a name="bkmk_HowTo"></a>Utilisation des modèles  
Pour télécharger les fichiers fournis avec chaque modèle, vous pouvez utiliser des commandes GitHub ou ouvrir le lien et cliquer sur **Download Zip** pour enregistrer tous les fichiers sur votre ordinateur.  Une fois téléchargée, la solution contient généralement ces dossiers :  
  
-   **Data** : contient les exemples de données pour chaque application.  
  
-   **R** : contient tout le code de développement R dont vous avez besoin pour la solution. La solution nécessite les bibliothèques fournies par Microsoft R Server, mais peut être ouverte et modifiée dans n’importe quel IDE R. Le code R a été optimisé pour que les calculs soient effectués « dans la base de données », en affectant une instance de SQL Server comme contexte de calcul.  
  
-   **SQLR** : contient plusieurs fichiers .sql que vous pouvez exécuter dans un environnement SQL comme [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour créer les procédures stockées qui effectuent des tâches associées, telles que le traitement des données, l’ingénierie des caractéristiques et le déploiement de modèle.  
  
    Ce dossier contient également un script PowerShell que vous pouvez exécuter pour appeler tous les scripts et créer l’environnement de bout en bout.  
  
    N’oubliez pas de modifier le script pour l’adapter à votre environnement.  
  
  
## Voir aussi  
[Didacticiels pour SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
[Annonce relative aux modèles dans Azure ML](https://blogs.technet.microsoft.com/machinelearning/2015/04/09/exciting-new-templates-in-azure-ml/)  
[Nouveau modèle de maintenance prédictive](https://blogs.technet.microsoft.com/machinelearning/2015/04/09/exciting-new-templates-in-azure-ml/)  
  
  
  
