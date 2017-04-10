---
title: "Didacticiels pour SQL Server R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/17/2017"
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
ms.assetid: 5ccc75f6-6703-47d9-b879-9a740569b45e
caps.latest.revision: 31
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 27
---
# Didacticiels pour SQL Server R Services
Utilisez ces didacticiels pour en savoir plus sur [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] et sur les scénarios de science des données pris en charge, notamment :

+ Le développement de modèles en code R et leur déploiement sur SQL Server
+ L’opérationnalisation du code R par le déploiement d’une solution développée par un spécialiste des données sur un serveur ou autre environnement de production.
+ Déplacement de données entre l’environnement R et SQL Server
+ Utilisation de contextes de calcul locaux et distants
  

## <a name="a-namebkmkend-to-endadeveloping-an-end-to-end-advanced-analytics-solution"></a><a name="bkmk_end-to-end"></a>Développement d’une solution analytique avancée de bout en bout  

[Procédure pas à pas pour une solution complète de science des données](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md) 

Découvrez la science des données, de l’acquisition de données à leur analyse, en passant par les scores. Découvrez comment utiliser les données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et comment rendre votre modèle opérationnel en l’enregistrant dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
Vous allez importer le jeu de données sur les taxis de New York dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec PowerShell et explorer les données à l’aide de R. 

Vous allez ensuite créer un modèle de prévision et déployer le modèle R sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour calculer les scores en mode de prédiction unique ou par lot. 

  
Ce didacticiel est destiné aux personnes qui possèdent des connaissances sur R, ainsi que sur les outils de développement tels que PowerShell et SQL Server Management Studio. Vous devez avoir accès à un environnement de développement R et connaître les commandes R. 
  
## <a name="a-namebkmkdatascienceadata-science-deep-dive"></a><a name="bkmk_dataScience"></a>Immersion dans la science des données  

[Prise en main de RevoScaleR et SQL Server](http://go.microsoft.com/fwlink/?LinkID=691640&clcid=0x809)  

Cette procédure pas à pas est un bon point de départ pour les développeurs ou les spécialistes des données qui connaissent déjà le langage R et qui souhaitent en savoir plus sur les packages et les fonctions Microsoft R améliorés, fournis par Revolution Analytics. 

Vous allez apprendre à utiliser les fonctions dans les packages ScaleR pour déplacer des données entre R et SQL et basculer entre les contextes de calcul pour vous adapter à une tâche particulière. Vous allez créer des tracés et des modèles, et les déplacer entre votre environnement de développement et SQL Server.  
  
Ce didacticiel est conçu pour les personnes qui utilisent R et qui souhaitent en savoir plus sur la façon dont RevoScaleR et SQL Server peuvent améliorer leur utilisation de R.

## <a name="in-database-advanced-analytics-for-the-sql-developer"></a>Analytique avancée en base de données pour les développeurs SQL  
  
[Analytique avancée en base de données pour les développeurs SQL &#40;Didacticiel&#41;](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)

Créez et déployez une solution d’analyse avancée complète à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Cet exemple est axé sur l’intégration du langage R open source au moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous découvrirez comment encapsuler du code R dans une procédure stockée, enregistrer un modèle R dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et effectuer des appels paramétrables au modèle R pour la prédiction. 
  
Ce didacticiel est destiné aux développeurs SQL, aux développeurs d’applications et aux administrateurs de bases de données SQL qui utilisent des solutions R et souhaitent savoir comment déployer des modèles R dans SQL Server.  Aucun environnement R n’est nécessaire. Tout le code R est fourni et vous pouvez générer la solution complète en utilisant uniquement [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et les outils d’analyse décisionnelle et de développement SQL que vous connaissez déjà.   

## <a name="use-r-services-in-an-application"></a>Utiliser R Services dans une application

[Créer une application intelligente avec SQL Server et R](https://www.microsoft.com/sql-server/developer-get-started/r)

Dans ce didacticiel, vous allez apprendre comment une entreprise de location de skis peut utiliser Machine Learning pour prédire les locations à venir, ce qui permet au plan d’entreprise et au personnel de répondre aux demandes futures.


## <a name="using-r-code-in-t-sql"></a>Utilisation de code R dans T-SQL  

[Utilisation de code R dans Transact-SQL &#40;SQL Server R Services&#41;](../../advanced-analytics/r-services/using-r-code-in-transact-sql-sql-server-r-services.md)  

Il s’agit d’une série d’exemples autonomes courts qui illustrent la syntaxe de base pour l’utilisation de R dans [!INCLUDE[tsql](../../includes/tsql-md.md)]. 

Vous allez apprendre à appeler le runtime R à partir de SQL, à faire la différence entre les types de données SQL et R, à encapsuler les fonctions R dans le code SQL et à exécuter une procédure stockée qui enregistre la sortie R dans une table SQL.
  
Ce didacticiel s’adresse aux personnes qui découvrent R Services et qui souhaitent apprendre les bases de l’appel de code R à l’aide de T-SQL. Aucune expérience en langage R n’est requise. Cependant, vous devez savoir comment utiliser SQL Server Management Studio ou tout autre outil qui peut se connecter à une base de données et exécuter des requêtes T-SQL simples.

  
## <a name="a-namebkmkprerequisitesaprerequisites"></a><a name="bkmk_Prerequisites"></a>Conditions préalables
  
Pour effectuer l’un de ces didacticiels, vous devez télécharger et installer **R Services (dans la base de données)** comme indiqué ici : [Configurer SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)

Après avoir configuré SQL Server, n’oubliez pas ces étapes supplémentaires :
+ Activer R Services en exécutant *sp_configure*
+ Redémarrer le serveur
+ Vérifier que le service qui appelle le runtime R dispose des autorisations nécessaires
+ Vérifier que la connexion SQL ou le compte d’utilisateur Windows que vous allez utiliser pour votre code R dispose des autorisations nécessaires pour se connecter au serveur et à ses bases de données

Si vous rencontrez des problèmes, consultez cet article qui aborde certains problèmes courants : [Upgrade and Installation of SQL Server R Services](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md) (Mise à niveau et installation de SQL Server R Services).

Si vous n’avez pas encore défini un environnement de développement R préféré, vous pouvez installer l’un de ces outils pour commencer :

+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started)
+ [Outils R pour Visual Studio](https://www.visualstudio.com/vs/rtvs/)

Notez que les bibliothèques R standard sont insuffisantes pour ces didacticiels. Votre environnement de développement R et l’ordinateur SQL Server qui exécute R doivent disposer des packages ScaleR Microsoft. Pour plus d’informations sur les nouveautés de Microsoft R, consultez cet article : [Produits Microsoft R](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started#compare-prods).

## <a name="additional-resources"></a>Ressources supplémentaires

Lorsque vous avez terminé ces didacticiels, utilisez les liens suivants pour voir des exemples et des scénarios plus avancés.
  
### <a name="end-to-end-solution-templates-for-key-machine-learning-tasks"></a>Modèles de solutions de bout en bout pour les principales tâches d’apprentissage automatique  

[Machine Learning Templates with SQL Server 2016 R Services](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/) (Modèles d’apprentissage automatique avec SQL Server 2016 R Services).  

L’équipe Microsoft Machine Learning fournit un ensemble de modèles personnalisables pour vous aider à mettre rapidement en œuvre une solution d’apprentissage automatique pour les tâches clés d’apprentissage automatique suivantes :  
* Détection des fraudes  
* Prédiction d’évolution personnalisée  
* Maintenance prédictive  
  
Tout le code T-SQL et R est fourni, ainsi que des instructions sur l’apprentissage et le déploiement d’un modèle de calcul de scores à l’aide de procédures stockées SQL Server. 

### <a name="sample-data-and-sample-scripts"></a>Exemples de scripts et exemples de données  
Des exemples de produits pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sont disponibles à partir du Centre de téléchargement Microsoft. Pour obtenir uniquement les exemples pour [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], sélectionnez le fichier .zip et ouvrez le dossier **Advanced Analytics**.  Certaines des instructions s’appliquent aux versions antérieures. Elles contiennent toutefois une démonstration de la détection des fraudes à l’assurance basée sur la loi de Benford, ainsi qu’une procédure pas à pas simple pour un modèle de prévision basé sur un très petit dataset (le dataset Iris) qui peut être utile pour les démonstrations.
  
[Exemples de produits SQL Server 2016](https://www.microsoft.com/en-us/download/details.aspx?id=49502)  
### <a name="learn-more-about-r"></a>En savoir plus sur R  
Pour en savoir plus sur R en général, consultez l’une des nombreuses excellentes ressources répertoriées ici : [Ressources sur le langage R](http://revolutionanalytics.com/r-language-resources).  
  
Pour plus d’informations sur les packages R fournis dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], consultez le  [site de Revolution Analytics](http://go.microsoft.com/fwlink/?LinkId=691541).  
  
Ce billet de blog décrit le processus d’utilisation des fonctions et packages R fournis par [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et comprend des exemples de code : [Using R inside SQL Server](http://blog.revolutionanalytics.com/2015/10/previewing-using-revolution-r-enterprise-inside-sql-server.html)(Utilisation de R dans SQL Server).  
  
## <a name="see-also"></a>Voir aussi  
[Prise en main de SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
[Fonctionnalités et tâches de SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)  
  
