---
title: "Prise en main de SQL Server R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "12/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: 5b28a663-effe-41f6-9bda-eda95f0c6943
caps.latest.revision: 34
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 32
---
# Prise en main de SQL Server R Services
 Pour créer une solution analytique avancée, généralement vous commencez par l’exploration des données et la modélisation prédictive. Le spécialiste de la science des données développe des scripts R et des modèles qui s’avèrent efficaces pour la tâche en cours. Une fois que les scripts et les modèles sont prêts, ils peuvent être déployés en production et intégrés aux applications nouvelles ou existantes.   
  
SQL Server R Services est conçu pour vous aider à effectuer ces tâches de science des données. Vous pouvez continuer à utiliser vos outils SQL ou R préférés, tout en appliquant l’analyse à des milliards d’enregistrements sans matériel supplémentaire, en améliorant les performances et en évitant les déplacements de données inutiles. Vous pouvez maintenant placer votre code R en production sans avoir à le réécrire dans un autre langage. Vous pouvez également utiliser R facilement pour des calculs statistiques qui pourraient être difficiles à implémenter avec SQL. En même temps, vous pouvez exploiter la puissance de SQL Server pour optimiser les performances, à l’aide de fonctionnalités comme les index columnstore et le moteur de base de données en mémoire.  
  
Les sections suivantes fournissent une vue d’ensemble globale de certains flux de travail analytiques standard et comment les activer avec SQL Server R Services.  

> [!TIP] Consultez ce didacticiel pour démarrer rapidement. Vous allez apprendre comment une entreprise de location de skis peut utiliser l’apprentissage automatique pour prédire les locations à venir et organiser le personnel pour répondre à la demande.
> 
> [Créer une application intelligente avec SQL Server et R](https://www.microsoft.com/sql-server/developer-get-started/r)


  
-   **Développer**  
  
     Les chercheurs de données utilisent généralement R pour explorer des données et créer des modèles prédictifs à partir de leur station de travail en utilisant un environnement de développement intégré (IDE) R de leur choix. Le chercheur de données effectue une itération de test et de réglage jusqu’à obtenir un modèle prédictif approprié. 
     
     Les composants du client [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offrent aux spécialistes de la science des données tous les outils dont ils ont besoin pour tester et développer. Ces outils incluent le runtime R, la « Intel Math Kernel Library » pour améliorer les performances des opérations R standard, et un ensemble de packages R améliorés qui prennent en charge l’exécution du code R dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Les chercheurs de données peuvent se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et apporter les données au client pour une analyse locale, comme d’habitude. Toutefois, une meilleure solution consiste à utiliser les API **ScaleR** pour envoyer des calculs à l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], évitant ainsi le déplacement coûteux et non sécurisé de données.  
  
     Pour développer des solutions R, les spécialistes de la science des données peuvent utiliser tout IDE Windows qui prend en charge R, y compris [R Tools pour Visual Studio](https://www.visualstudio.com/features/rtvs-vs.aspx) ou RStudio.  
 
    ![rsql_keyscenario2](../../advanced-analytics/r-services/media/rsql-keyscenario2.PNG) 
 
     Pour plus d’informations, voir [Data Exploration and Predictive Modeling with R](../../advanced-analytics/r-services/data-exploration-and-predictive-modeling-with-r.md).  

  
-   **Optimiser**  
  
     Lors de l’analyse de jeux de données volumineux avec R, les chercheurs de données rencontrent souvent des problèmes de performances et de mise à l’échelle, car l’implémentation de l’exécution courante est monothread et ne peut prendre en charge que les jeux de données qui tiennent dans la mémoire disponible sur l’ordinateur local. Pour obtenir de meilleures performances et traiter davantage de données, le spécialiste de la science des données peut utiliser les API **ScaleR** fournies dans le cadre de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Le package **RevoScaleR** contient des implémentations de certaines fonctions R les plus populaires, qui ont été repensées pour fournir un parallélisme et une mise à l’échelle. Le package comprend également des fonctions qui améliorent encore davantage les performances et la mise à l’échelle en envoyant des calculs à l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], lequel dispose généralement de bien plus de mémoire et de puissance de calcul.  
  
     Pour plus d’informations, voir [Data Exploration and Predictive Modeling with R](../../advanced-analytics/r-services/data-exploration-and-predictive-modeling-with-r.md).  
  
-   **Déployer**  
  
     Une fois le script ou le modèle R prêt pour l’utilisation en production, un développeur de base de données peut incorporer le code ou le modèle dans des procédures stockées, et appeler le code enregistré à partir d’une application. Le stockage et l’exécution de code R à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offrent de nombreux avantages : ils permettent d’utiliser l’interface [!INCLUDE[tsql](../../includes/tsql-md.md)], et tous les calculs ont lieu dans la base de données, ce qui évite les déplacements inutiles des données. Vous pouvez utiliser [!INCLUDE[tsql](../../includes/tsql-md.md)] pour générer des scores à partir d’un modèle prédictif en production, ou de renvoyer des graphiques générés par R et les présenter dans une application telle que [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
     Pour optimiser davantage le code R incorporé dans des procédures stockées système, nous vous recommandons d’utiliser les API du package [ScaleR](https://msdn.microsoft.com/microsoft-r/rserver/rserver-scaler-getting-started) qui peuvent opérer sur des jeux de données plus volumineux. Ces packages prennent en charge l’exécution dans la base de données de calculs multicœur, multithread et multiprocessus.  
  
     Lorsque vous avez besoin déployer du code R en production, [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offre le meilleur des deux mondes R et SQL. Vous pouvez utiliser R pour effectuer des calculs statistiques qui sont difficiles à implémenter à l’aide de SQL, mais qui tirent parti de la puissance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour optimiser les performances, à l’aide de fonctionnalités telles que les index columnstore et le moteur de base de données en mémoire.  
  
    ![rsql_keyscenario1](../../advanced-analytics/r-services/media/rsql-keyscenario1.PNG)  
  
     Pour plus d’informations, consultez [Opérationnalisation de votre code R](../../advanced-analytics/r-services/operationalizing-your-r-code.md).  
 
 > [!TIP] Découvrez comment intégrer SQL Server à la science des données dans ce guide, disponible en téléchargement gratuit à partir de Microsoft Virtual Academy : [Data Science with Microsoft SQL Server 2016](https://mva.microsoft.com/ebooks/) (Science des données avec Microsoft SQL Server 2016)

-   **Gérer et surveiller**  
  
     [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] utilise une nouvelle architecture d’extensibilité qui protège votre moteur de base de données et isole les sessions R. Vous pouvez contrôler les utilisateurs autorisés à exécuter des scripts R, et spécifier les bases de données accessibles au code R. Vous pouvez contrôler la quantité de ressources allouées au runtime R afin d’éviter que des calculs massifs ne mettent en péril les performances globales du serveur.  
  
     Quand vous exécutez des travaux R dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez également contrôler et auditer les données utilisées par les analystes, ou planifier des tâches et créer des flux de travail contenant des scripts R, comme vous le feriez avec d’autres procédures stockées système.  
  
     Pour plus d'informations, voir [Managing and Monitoring R Solutions](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  
  
  
-   **Intégrer**  
  
     Vous ne devez plus dilapider votre budget informatique pour faire en sorte que vos outils d’entreprise fonctionnent avec un environnement d’exécution R externe. Vous pouvez en effet travailler dans l’environnement familier de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], et développer des flux de travail et solutions de création de rapports intégrés utilisant [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
     Pour plus d’informations, consultez [Création de workflows qui utilisent R dans SQL Server](../../advanced-analytics/r-services/creating-workflows-that-use-r-in-sql-server.md).  
  
  
## <a name="how-do-i-get-it"></a>Comment l’obtenir ?  
   
  
+   **Installer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou version supérieure et activer R Services (en base de données)**  
  
    [Configurer SQL Server R Services &#40;en base de données&#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).  
  
  
-   **Configurer la station de travail cliente**  
  
     [Configurer un client de science des données](../../advanced-analytics/r-services/set-up-a-data-science-client.md)  
   
> [!TIP]   
>   
> Vous devez créer un serveur pour des travaux R, mais vous n’avez pas besoin de SQL Server ? Essayez [Microsoft R Server](https://msdn.microsoft.com/library/mt674874.aspx).  
  
## <a name="how-to-run-r-code-using-sql-server-r-services"></a>Exécution du code R à l’aide de SQL Server R Services  
 Une fois l’installation terminée, vous pouvez exécuter le code R sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en incorporant R dans des procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] ou en écrivant des scripts R ad hoc qui fonctionnent avec les données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Découvrez comment appeler le code R à partir d’une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] et renvoyer les résultats dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
     [Utilisation de code R dans Transact-SQL](../../advanced-analytics/r-services/using-r-code-in-transact-sql-sql-server-r-services.md)  
  
-   Présentation du flux complet de création d’une solution analytique avancée et de son déploiement à l’aide de SQL Server R Services  
  
     [Procédure pas à pas pour une solution complète de science des données](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md)  
  
-   En savoir plus sur l’utilisation du package RevoScaleR pour une analyse scalable et hautement performante, et sur l’envoi de calculs R sur l’ordinateur SQL Server  
  
     [Immersion dans la science des données : utilisation des packages RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
-   Incorporer un script de travail R dans des procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] afin d’appeler des modèles pour la prédiction, de former à nouveau des modèles ou d’obtenir des prédictions à partir d’applications  
  
     [Analytique avancée en base de données pour les développeurs SQL](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
  
-   Utilisez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et les outils décisionnels dans la pile [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour automatiser les processus d’apprentissage automatique. La préparation des données et la création de rapports peuvent être automatisées à l’aide de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Affichez les tracés R ainsi que d’autres rapports à l’aide de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ou de Power View.  
  
+ Plus d’exemples, notamment des modèles de solution et des exemples de code R  
   [SQL Server R Services Tutorials](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [Bien démarrer avec Microsoft R Server &#40;autonome&#41;](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
  
  