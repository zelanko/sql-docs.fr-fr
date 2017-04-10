---
title: "Exploration de donn&#233;es et mod&#233;lisation pr&#233;dictive avec R | Microsoft Docs"
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
ms.assetid: bf6de7e2-f394-4b8a-a4b7-0b8dadf25426
caps.latest.revision: 20
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 19
---
# Exploration de donn&#233;es et mod&#233;lisation pr&#233;dictive avec R
  Les spécialistes de données adoptent le langage R pour explorer les données et créer des modèles prédictifs. C’est généralement un processus itératif d’essais et d’erreurs qui s’exécute jusqu’à obtenir un bon modèle prédictif. En tant que spécialiste des données, vous pouvez vous connecter à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et extraire les données vers votre poste de travail local à l’aide du package RODBC, explorer vos données et créer un modèle prédictif à l’aide des packages R standard.  
  
 Toutefois, cette approche a des inconvénients. Le déplacement des données peut être lent, inefficace ou non sécurisé et R lui-même présente des limitations en termes de performances et d’évolutivité. Ces inconvénients deviennent plus évidents lorsque vous avez besoin de déplacer et d’analyser de grandes quantités de données ou d’utiliser des jeux de données plus grands que la mémoire disponible de votre ordinateur.  
  
 Vous pouvez relever ces défis en utilisant les nouveaux packages évolutives et de fonctions R inclus avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Le package **RevoScaleR** contient des implémentations de certaines fonctions R plus populaires, qui ont été repensées pour fournir les fonctionnalités de parallélisme et mise à l’échelle. Le package RevoScaleR prend également en charge la modification du *contexte d’exécution*. Cela signifie que, pour une solution entière ou simplement une fonction, vous pouvez indiquer que les calculs doivent être effectués à l’aide des ressources de l’ordinateur qui héberge l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et non pas celles de votre poste de travail local. Cela présente plusieurs avantages : vous n’avez pas à déplacer des données inutiles et vous pouvez tirer parti des ressources de calcul supérieures sur l’ordinateur serveur.  
  
 Cette section fournit des conseils aux spécialistes des données sur l’utilisation de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] et sur les tâches liées au développement et au test des solutions R.  
  
##  <a name="bkmk_RDevTools"></a> Outils de développement R  
 Le Client Microsoft R donne les données scientifiques un environnement complet pour développer et tester des modèles prédictifs. R Client inclut :  
  
-  **[!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)]:** Une distribution du runtime R et un ensemble de packages, tels que la bibliothèque de noyaux mathématiques Intel, susceptibles d’améliorer les performances des opérations standard de R.  
  
-   **RevoScaleR :** un package R qui vous permet de distribuer des calculs à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[rsql_rre-noversion](../../includes/rsql-rre-noversion-md.md)]. Il inclut également un ensemble de fonctions R courantes qui ont été repensés pour fournir de meilleures performances et évolutivité. Le préfixe **rx** identifie ces fonctions améliorées. Il inclut également des fournisseurs de données améliorées pour diverses sources ; Ces fonctions sont précédées **Rx**.  
  
-   **Liberté de choix des outils de développement :** vous pouvez utiliser n’importe quel éditeur de code basé sur Windows qui prend en charge R, tel que [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] ou RStudio. Le téléchargement de [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)] inclut également des outils de ligne de commande courants pour R comme RGui.exe.  
  
##  <a name="bkmk_packages"></a> Packages et environnement R  
 L’environnement R pris en charge dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] se compose d’un runtime, du langage open source et d’un moteur graphique pris en charge et étendu par plusieurs packages. Le langage autorise l’utilisation d’extensions qui sont implémentées à l’aide de packages.  
  
 Il existe plusieurs sources de packages R supplémentaires que vous pouvez utiliser avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] :  
  
  
-   Packages R à usage général à partir des référentiels public. Vous pouvez obtenir les packages R open source les plus populaires auprès de référentiels publics, tels que le CRAN, lequel héberge plus de 6 000 packages utilisables par les spécialistes de données.  
  
     Les packages supplémentaires prennent en charge l’analyse prédictive dans des domaines spéciaux comme la finance, la génomique, entre autres.  
  
     Pour la plate-forme Windows, les packages R sont fournis en tant que fichiers zip et peuvent être téléchargés et installés sous licence GPL.  
  
     Pour plus d’informations sur l’installation des packages tiers pour une utilisation avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], consultez [installer des Packages R supplémentaires sur SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)  
  
-   Autres packages et bibliothèques fournis par [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].   
  
     Le **RevoScaleR** package inclut l’analytique des données volumineuses hautes performances, des versions améliorées des fonctions qui prennent en charge les tâches de science des données courantes, apprenants optimisés pour Naive Bayes, régression linéaire, modèles de série chronologique et réseaux neuronaux et les bibliothèques de mathématiques avancées.  
  
     Le package **RevoPemaR** vous permet de développer vos propres algorithmes de mémoire externe parallèle dans R.  
  
     Pour plus d’informations sur ces packages et leur utilisation, consultez la page [Exploration des données et modélisation prédictive & #40 ; Didacticiel : Services de SQL Server R & #41 ;](../../advanced-analytics/r-services/sql-server-r-services.md).  
  
## Utilisation de sources de données et de contextes de calcul  
 Lorsque vous utilisez le package RevoScaleR pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il existe certaines nouvelles fonctions importantes à utiliser dans votre code R :  
  
-   [RxSqlServerData](RxSqlServerData.md) est fourni dans le package RevoScaleR pour prendre en charge la connectivité de données améliorées à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Utilisez cette fonction dans votre code R pour définir la *source de données*. L’objet de source de données spécifie le serveur et les tables où les données résident et gère la tâche de lecture et d’écriture de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Le [RxInSqlServer](rxInSqlServer.md) fonction peut être utilisée pour spécifier le *contexte de calcul*.  En d’autres termes, vous pouvez indiquer où le code R doit être exécuté : sur votre poste de travail local ou sur l’ordinateur qui héberge le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.  
  
     Lorsque vous définissez le contexte de calcul, elle affecte uniquement les calculs qui prennent en charge le contexte de l’exécution à distance, ce qui signifie que les opérations de R fournis par le package RevoScaleR et des fonctions associées. En règle générale, les solutions R basées sur les packages CRAN standard ne peut pas exécuter dans un contexte de calcul à distance, s’ils peuvent être exécutés le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ordinateur si démarrée à T-SQL. Toutefois, vous pouvez utiliser la `rxExec` fonction à appeler des fonctions R individuelles et de les exécuter à distance dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].  
  
 Pour obtenir des exemples montrant comment créer et utiliser des sources de données et les contextes d’exécution, consultez trois didacticiels :
 
 + [Présentation approfondie de science des données](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
 +  [RevoScaleR SQL Server mise en route](https://msdn.microsoft.com/microsoft-r/rserver/rserver-scaler-sql-server-getting-started).  
  
## Déploiement de votre code R en production  
 La science des données consiste principalement à échanger des analyses entre spécialistes ou à utiliser des modèles prédictifs pour les résultats ou les processus métier. Dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], il est facile de passer en production lorsque votre script ou modèle R est prêt.  
  
 Pour plus d’informations sur la façon dont vous pouvez déplacer votre code s’exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez la page [à mettre en application de votre Code R](../../advanced-analytics/r-services/operationalizing-your-r-code.md).  
  
 En général, le processus de déploiement commence par nettoyer votre script afin d’éliminer le code qui n’est pas nécessaire en production. Lorsque vous déplacez des calculs de plus près aux données, vous constaterez des manières de déplacer plus efficacement, résumer ou présenter des données plutôt que d’effectuer tout en R.  
  
 Nous recommandons qu’avec un développeur de base de données sur les façons d’améliorer les performances, consultez les données scientifiques, surtout si cette solution ne nettoyage des données ou une fonctionnalité d’ingénierie qui peut être plus efficace dans SQL. Modifications apportées aux processus ETL peuvent être nécessaire pour s’assurer que les flux de travail de construction ou d’un modèle de score n’échouent pas, et que les données d’entrée sont disponibles dans le bon format.  
  
##  <a name="bkmk_SQLInR"></a> Dans cette section  

[Comparaison des fonctions de DETARTREUR et CRAN R](Summary%20of%20rx%20Functions.md)

[Fonctions scaleR pour une utilisation avec SQL Server](../../advanced-analytics/r-services/scaler-functions-for-working-with-sql-server-data.md)
   
## Voir aussi  

 
 [Fonctionnalités et tâches de SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)   
 
 [Opérationnalisation de votre code R](../../advanced-analytics/r-services/operationalizing-your-r-code.md)  
  
  