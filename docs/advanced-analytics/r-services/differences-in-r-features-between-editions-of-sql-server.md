---
title: "Diff&#233;rences de fonctionnalit&#233;s de R entre les &#233;ditions de SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "01/19/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b33a3e2-04d3-4bad-9335-9568ae09db0b
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Diff&#233;rences de fonctionnalit&#233;s de R entre les &#233;ditions de SQL Server
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] est disponible dans les éditions suivantes de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
-   **Enterprise Edition**  
    
     Inclut les deux Services R pour l’analytique dans base de données dans SQL Server 2016, ainsi que le serveur R (autonome) sur Windows, qui peut être utilisé pour se connecter à une variété de bases de données et extraire les données pour l’analyse à l’échelle, mais qui ne s’exécute pas dans base de données. Inclut également **DeployR**, qui peut être utilisé pour déployer des modèles et des scripts R comme un Service Web.  

     Aucune restriction. Optimisation des performances et l’évolutivité grâce à la parallélisation et diffusion en continu. Analyse de Suopprts de jeux de données volumineux qui ne tiennent pas dans la mémoire disponible, à l’aide de la **ScaleR** fonctions.  
  
     Analytique base de données dans SQL Server prend en charge la gestion des ressources de scripts externes pour personnaliser l’utilisation des ressources serveur.  
  
-   **Developer Edition**  

    Mêmes fonctionnalités que l’édition entreprise. Toutefois, Developer Edition ne peut pas être utilisée dans les environnements de production.  

  
  
-   **Édition standard**  
  
     Toutes les capacités de dans base de données analytique sont inclus avec l’édition entreprise, à l’exception de la gouvernance de ressources flexible. Performances et évolutivité est également limité : les données qui peuvent être traitées doit tenir dans la mémoire du serveur et le traitement est limité à un thread de calcul unique, même si vous utilisez la **ScaleR** fonctions.
  
-   **Éditions Express**  
  
     Uniquement Express Edition with Advanced Services fournit des Services de R. Les limitations de performances sont similaires à Standard Edition.  
  
 Pour plus d’informations sur les autres fonctionnalités du produit, consultez la page [fonctionnalités prises en charge par les éditions de SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  

> [!NOTE]
>
> + Microsoft R Open est inclus dans toutes les éditions.
> + Le Client Microsoft R peut fonctionner avec toutes les éditions.
  
## Enterprise Edition  
 Performances des solutions de R [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit généralement être mieux que toute implémentation R conventionnelle, étant donné le même matériel, étant donné que R peut être exécuté à l’aide des ressources du serveur, parfois distribuées sur plusieurs processus à l’aide de la **ScaleR** fonctions.  
  
 Les utilisateurs pourront également voir des différences considérables dans les performances et l’évolutivité pour les fonctions R mêmes si vous exécutez dans Visual Studio Enterprise Edition. Édition standard. Prise en charge de traitement parallèle, la diffusion et accrue de threads disponibles pour les processus de travail R de traitement des raisons.  
  
 Toutefois, les performances même sur du matériel identique peuvent être affectées par de nombreux facteurs en dehors du code R, y compris des demandes simultanées sur les ressources serveur, le type du plan de requête qui est créée, les modifications de schéma, la nécessité de mettre à jour les statistiques ou en créer un nouveau plan de requête, la fragmentation et bien plus encore. Il est possible qu’une procédure stockée contenant du code R peut s’exécuter dans les secondes sous une charge de travail, mais prennent minutes lorsque d’autres services en cours d’exécution.  Par conséquent, nous vous recommandons de surveiller plusieurs aspects des performances du serveur, y compris la mise en réseau pour les contextes de calcul à distance, lors de la quantification des performances R.  

Nous vous recommandons également de configurer [du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md) (disponible dans Enterprise Edition) pour personnaliser la manière que les travaux R sont hiérarchisées ou gérés sous des charges de travail trop importante du serveur. Vous pouvez définir des fonctions classifieur pour spécifier la source de la tâche de R et de hiérarchiser certaines charges de travail, de limiter la quantité de mémoire utilisée par les requêtes SQL et contrôler le nombre de traitements parallèles chaque charge de travail.  
  
## Developer Edition  
 L’édition développeur fournit des performances équivalentes à celles de l’édition entreprise. Toutefois, l’utilisation de l’édition développeur n’est pas pris en charge pour les environnements de production.  
  
  
## Édition standard  
 Même Standard Edition doit offrir des gains de performance par rapport aux packages R standard, étant donné la même configuration matérielle.  
  
 Toutefois, Standard Edition ne prend pas en charge le gouverneur de ressources. À l’aide de la gestion des ressources est la meilleure façon de personnaliser les ressources du serveur pour prendre en charge diverses charges de travail R comme modèle d’apprentissage et de notation.  
  
 Standard Edition fournit également des performances limitées et l’évolutivité par rapport aux éditions Enterprise et Developer. Plus précisément, tous les **ScaleR** les fonctions et les packages sont inclus avec l’Édition Standard, mais le service qui lance et gère les scripts R est limité dans le nombre de processus, il peut utiliser. En outre, les données traitées par le script doivent tenir dans la mémoire.  
  
  
## Express Edition with Advanced Services  
 Express Edition est soumis aux mêmes limitations que Standard Edition.  
  
## Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
  
  