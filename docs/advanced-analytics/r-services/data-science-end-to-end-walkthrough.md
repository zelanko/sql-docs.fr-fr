---
title: "Proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es | Microsoft Docs"
ms.custom: ""
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
ms.assetid: edd76ae9-4125-45a8-bf42-47a85b9d9a32
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# Proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es
Dans cette procédure pas à pas, vous allez développer une solution complète de modélisation prédictive en utilisant [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
Cette procédure pas à pas est basée sur un jeu de données public bien connu, en l’occurrence le jeu de données des taxis de New York. Vous allez utiliser une combinaison de code R, de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et de fonctions SQL personnalisées pour générer un modèle de classification qui indique la probabilité que le chauffeur obtienne un pourboire sur un trajet en taxi particulier. Vous allez également déployer votre modèle R sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et utiliser des données de serveur pour générer des scores basés sur le modèle.  
  
Cet exemple peut facilement être étendu à tous les types de problèmes réels, tels que la prédiction des réponses des clients aux campagnes de vente ou la prédiction des dépenses par les visiteurs d’un événement. En outre, le modèle pouvant être appelé à partir d’une procédure stockée, vous pouvez facilement l’incorporer dans une application.  
  
**Public visé**  
  
Cette procédure pas à pas est destinée aux développeurs R. Vous devez être familiarisé avec les opérations fondamentales de base de données, telles que la création de bases de données, la création de tables, l’importation de données dans des tables et l’interrogation des tables à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)].  Nous vous fournirons les scripts SQL et R à exécuter.  
  
Si vous ne connaissez pas R, mais que vous connaissez bien les bases de données, ce didacticiel indique comment intégrer R aux workflows d’entreprise à l’aide de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Aucun codage R n’est requis ; tous les scripts sont fournis. Vous n’avez pas besoin d’installer un IDE R particulier pour exécuter les commandes.  
  
**Conditions préalables**  
  
Pour effectuer ce didacticiel, vous devez avoir accès à une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] installé. Pour votre environnement local, préparez une station de travail de science des données qui peut se connecter à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis installez les bibliothèques R requises.  
  
Pour plus d’informations, consultez [Prerequisites for Data Science Walkthroughs &#40;SQL Server R Services&#41;](../../advanced-analytics/r-services/prerequisites-for-data-science-walkthroughs-sql-server-r-services.md) (Conditions préalables pour les procédures pas à pas pour une solution de science des données &#40;SQL Server R Services&#41;).  
  
## <a name="overview"></a>Vue d'ensemble  
Cette procédure pas à pas illustre une solution de bout en bout classique dans le cadre d’une analytique avancée. Vous devez effectuer les leçons dans l’ordre.  
  
||Durée estimée|  
|-|------------------------------|  
|[Leçon 1 : Préparer les données &#40;Procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)<br /><br />Le processus analytique commence par l’obtention des données utilisées pour la création d’un modèle. Vous téléchargerez un jeu de données public et l’enregistrerez dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|30 minutes|  
|[Leçon 2 : Afficher et explorer les données &#40;Procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-2-view-and-explore-the-data-data-science-end-to-end-walkthrough.md)<br /><br />Un expert en traitement de données consacre souvent beaucoup de temps à explorer des données et à les préparer à des fins de modélisation, de création de caractéristiques ou de transformations des données en fonction des besoins.  Vous utiliserez SQL et R pour explorer les données et générer des résumés.|20 minutes|  
|[Leçon 3 : Créer des caractéristiques de données &#40;procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-3-create-data-features-data-science-end-to-end-walkthrough.md)<br /><br />Vous créerez des caractéristiques de données à l’aide de fonctions personnalisées dans R et [!INCLUDE[tsql](../../includes/tsql-md.md)].|10 minutes|  
|[Leçon 4 : Créer et enregistrer le modèle &#40;Procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-4-build-and-save-the-model-data-science-end-to-end-walkthrough.md)<br /><br />Une fois les données prêtes, l’expert en traitement de données forme et ajuste le modèle, en évaluant ses performances et en essayant différents paramètres. Dans cette procédure pas à pas, vous créerez un modèle de classification et utiliserez des données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour générer des prédictions. Vous tracerez également la précision du modèle à l’aide de R.|15 minutes|  
|[Leçon 5 : Déployer et utiliser le modèle &#40;procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-5-deploy-and-use-the-model-data-science-end-to-end-walkthrough.md)<br /><br />Enfin, vous déploierez le modèle en production en l’enregistrant dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et appellerez le modèle à partir d’une procédure stockée pour générer des prédictions.|10 minutes|  
  
## <a name="notes"></a>Remarques  
La procédure pas à pas étant conçue pour présenter [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]aux développeurs R, les actions sont effectuées à l’aide de R, dans la mesure du possible. Cela ne signifie pas que R est nécessairement le meilleur outil pour chaque tâche. Dans de nombreux cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut offrir de meilleures performances, en particulier pour des tâches telles que l’agrégation de données et l’ingénierie de caractéristiques. Ces tâches peuvent notamment profiter de nouvelles fonctionnalités dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], telles que les index columnstore optimisés en mémoire.  
  
## <a name="next-step"></a>Étape suivante  
[Leçon 1 : Préparer les données &#40;Procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)  
  
  
  
