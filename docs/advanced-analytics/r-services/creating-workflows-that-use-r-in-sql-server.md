---
title: "Cr&#233;ation de workflows qui utilisent R dans SQL Server | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34c3b1c2-97db-4cea-b287-c7f4fe4ecc1b
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Cr&#233;ation de workflows qui utilisent R dans SQL Server
  Une base de données relationnelle est une technologie hautement optimisée pour fournir des solutions évolutives de traitement, de stockage et l’interrogation des données de transaction. Toutefois, généralement solutions R généralement reposent sur l’importation de données à partir de diverses sources, souvent dans un format CSV, pour effectuer une modélisation et exploration de données supplémentaire. Ces pratiques sont non seulement inefficaces, mais aussi non sécurisées.  
  
 À l’aide de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offre plusieurs avantages :  
  
-   Sécurité des données. La puissance R est placée dans la base de données proche de la source de données. Permet d’éviter le déplacement des données inutiles ou non sécurisé.  
  
-   Vitesse. Bases de données sont optimisés pour les opérations de jeu. En outre, innovations récentes dans les bases de données telles que les tables en mémoire et stockage des données en colonnes plus améliorent votre connaissance des données en utilisant agrégations éclair rapide.  
  
-   Intégration. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est le point central des opérations de nombreuses autres tâches de gestion de données et les applications qui utilisent l’entreprise. Utilisation des données déjà dans la base de données garantit que les données sont cohérentes et à jour. Au lieu de traiter les données dans R, vous pouvez compter sur les pipelines de données d’entreprise, y compris [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et Azure Data Factory. Rapport des résultats ou des analyses est facile via Power BI ou [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 En utilisant le bonne combinaison entre SQL et R pour différentes tâches de traitement et d’analyse des données, tant les scientifiques des données que les développeurs peuvent gagner en productivité. Cette section décrit une façon d’intégrer R avec d'autres solutions d'entreprise pour la transformation des données, l’analyse et les comptes rendus.  
  
##  <a name="bkmk_ssis"></a> Créer des flux de travail efficaces qui couvrent R et la base de données  
 Les workflows de science des données sont hautement itératifs et impliquent beaucoup de transformations de données, notamment la mise à l'échelle, les agrégations, le calcul des probabilités, le renommage et la fusion des attributs. Scientifiques sont habitués à faire beaucoup de ces tâches dans R, Python ou une autre langue. Toutefois, l’exécution de ces flux de travail sur les données d’entreprise nécessite une intégration transparente avec les outils ETL et les processus.  
  
 Étant donné que [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] vous permet d’exécuter des opérations complexes de R via Transact-SQL et des procédures stockées, vous pouvez intégrer des tâches spécifiques à R avec les processus ETL existants sans le travail de développement nouvelle minimal. Plutôt que de procéder à une chaîne de mémoire-ntensive tâches dans R, les préparation des données peut être optimisée à l’aide des outils les plus efficaces, notamment [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Par exemple, vous pouvez combiner R avec [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans les scénarios suivants :  
  
-   Utilisez [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] tâches pour créer les objets nécessaires dans la base de données SQL  
  
-   Utiliser le branchement conditionnel afin de changer de contexte de calcul pour les travaux R  
  
-   Exécuter des travaux R qui génèrent leurs propres données  
  
-   Utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour appeler un script R enregistré dans une variable de texte  
  
### Exemples et ressources  
 [Faire fonctionner votre projet d’apprentissage machine à l’aide de SQL Server 2016 SSIS et Services de R](https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/)  
  
 Dans ce billet de blog, vous allez apprendre comment :  
  
-   Utiliser R dans la tâche d’exécution SQL pour générer des données et l’enregistrer dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Utiliser une procédure stockée pour former un modèle R et le stocker dans la base de données  
  
-   Effectuer le calcul de score à l’aide de la tâche de Script et la tâche d’exécution SQL  
  
##  <a name="bkmk_ssrs"></a> Créer des visualisations qui couvrent R et les outils de rapports d’entreprise  
 Si R permet de créer des graphiques et offre une visualisation intéressante, il n'est pas bien intégré avec des sources de données externes, ce qui signifie que chaque diagramme ou graphique doit être produit individuellement. Le partage peut également être difficile.  
  
 À l’aide de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], vous pouvez exécuter des opérations complexes de R via [!INCLUDE[tsql](../../includes/tsql-md.md)] procédures stockées qui peuvent facilement être consommées par une variété d’outils, y compris les rapports d’entreprise [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et Power BI.  
  
-   Visualiser les objets graphiques retournés à partir d’un script R   
    utilisation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   Utilisez le tableau dans Power BI  
  
## Exemples et ressources  
 [R Graphics Device de Microsoft Reporting Services (SSRS)](https://rgraphicsdevice.codeplex.com/)  
  
 Ce projet CodePlex fournit le code pour vous aider à créer un élément de rapport personnalisé qui restitue la sortie graphique r sous la forme d’une image qui peut être utilisée dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] rapports.  À l’aide de l’élément de rapport personnalisé, vous pouvez :  
  
-   Publier des graphiques et des graphiques créés à l’aide du périphérique graphique R à [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] tableaux de bord  
  
-   Transmettez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] paramètres graphiques de R  
  
> [!NOTE]  
>  Notez que le code qui prend en charge le périphérique graphique R pour Reporting Services doit être installé sur le serveur Reporting Services, ainsi que dans Visual Studio. Configuration et la compilation manuelle est également requis.  
  
  