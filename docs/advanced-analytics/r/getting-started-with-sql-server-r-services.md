---
title: Prise en main de SQL Server apprentissage | Documents Microsoft
ms.custom: SQL2016_New_Updated
ms.date: 12/07/2016
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 5b28a663-effe-41f6-9bda-eda95f0c6943
caps.latest.revision: "34"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c114d320e71a93ffc6614ae6cfb1b535af2510e1
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2017
---
# <a name="getting-started-with-sql-server-machine-learning"></a>Prise en main de SQL Server Machine Learning

Machine Learning Services dans SQL Server est conçu pour prendre en charge des tâches courantes relatives aux données sans exposer vos données à des risques de sécurité ou de déplacement unnecesarily de données.

+ Dans SQL Server 2016, vous pouvez travailler avec vos outils R favoris, mais l’échelle de votre analyse milliards d’enregistrements tout en renforçant les performances. Intégration d’apprentissage avec SQL Server signifie également que vous pouvez mettre du code R en production sans avoir à modifier le code.

+ SQL Server 2017 ajoute la prise en charge pour le code Python, à l’aide de la même infrastructure d’extensibilité.

Cette rubrique décrit les scénarios clés pour l’utilisation de R ou Python dans-base de données et fournit des ressources pour vous aider à démarrer avec vos propres solutions.

S’applique à : SQL Server 2016 R Services, SQL Server 2017 d’apprentissage Services (de-de base de données)

> [!NOTE]
> SQL Server 2016 prend en charge uniquement pour le langage R. Prise en charge pour le langage Python nécessite SQL Server 2017 CTP 2.0.

## <a name="step-1-set-up-sql-server-machine-learning-services"></a>Étape 1. Configurer les Services SQL Server Machine Learning

1. Exécutez le programme d’installation de SQL Server et installez au moins une instance du moteur de base de données SQL Server.
2. Ajouter la fonctionnalité qui prend en charge l’exécution des runtimes externes.
3. Dans SQL Server 2016, R est ajouté par défaut. Dans SQL Server 2017, vous devez sélectionner une langue à ajouter. Vous pouvez sélectionner R ou Python ou activer à la fois.
4. Lorsque le programme d’installation est terminé, effectuer quelques étapes supplémentaires pour permettre l’exécution du script externe et redémarrez le serveur.

**Ressources**

+ [Configurez SQL Server avec Machine Learning](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

> [!TIP]  
> Vous devez créer un serveur pour des travaux R, mais vous n’avez pas besoin de SQL Server ? Essayez [Microsoft R Server](https://msdn.microsoft.com/library/mt674874.aspx).  

## <a name="step-2-develop-your-r-or-python-solutions"></a>Étape 2. Développer votre R ou des Solutions de Python

Chercheurs de données utilisent généralement R ou Python sur leur propre station de travail d’un ordinateur portable ou de développement, pour Explorer les données et de créer et de paramétrer des modèles prédictifs jusqu'à ce qu’un bon modèle prédictif. 

Avec Machine Learning Services dans SQL Server, il est inutile de modifier ce processus. Une fois l’installation terminée, vous pouvez exécuter le code R ou Python sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] localement ou à distance :

![rsql_keyscenario2](media/rsql-keyscenario2.png) 

+ **Utiliser l’IDE vous préférez**. Les composants du client[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offrent aux spécialistes de la science des données tous les outils dont ils ont besoin pour tester et développer. Ces outils incluent le runtime R, la « Intel Math Kernel Library » pour améliorer les performances des opérations R standard, et un ensemble de packages R améliorés qui prennent en charge l’exécution du code R dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

+ **Travailler à distance ou localement**. Les chercheurs de données peuvent se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et apporter les données au client pour une analyse locale, comme d’habitude. Toutefois, une meilleure solution consiste à utiliser les API **ScaleR** pour envoyer des calculs à l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , évitant ainsi le déplacement coûteux et non sécurisé de données.

+ **Incorporer des scripts R ou Python dans [!INCLUDE[tsql](../../includes/tsql-md.md)] des procédures stockées**. Lorsque votre code est entièrement optimisé, placez-le dans une procédure stockée pour éviter le déplacement des données inutiles et optimiser les tâches de traitement des données.


**Ressources**

+ Installer [R Tools pour Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation) ou RStudio.  

## <a name="step-3-optimize"></a>Étape 3. Optimiser

Lorsque le modèle est prêt à l’échelle sur les données d’entreprise, le chercheur de données fonctionne souvent le développeur de base de données ou SQL pour optimiser les processus tels que :

+ Ingénierie des caractéristiques
+ Intégrer les données et la transformation des données
+ Calcul de score

En règle générale, les chercheurs de données à l’aide de R ont des problèmes de performances et d’évolutivité, surtout lorsque vous utilisez le jeu de données volumineux. C’est parce que l’implémentation common runtime est monothread et peut accepter uniquement les jeux de données qui entrent dans la mémoire disponible sur l’ordinateur local. L’intégration avec les Services de SQl Server Machine Learning offre plusieurs fonctionnalités pour de meilleures performances, davantage de données :

+ **RevoScaleR**. : package R ce contient des implémentations de certaines fonctions R plus populaires, repensées pour fournir un parallélisme et mise à l’échelle. Le package comprend également des fonctions qui améliorent encore davantage les performances et la mise à l’échelle en envoyant des calculs à l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , lequel dispose généralement de bien plus de mémoire et de puissance de calcul.

+ **revoscalepy**. Cette bibliothèque Python, nouvelle et disponible uniquement dans SQL Server 2017 CTP 2.0 implémente les fonctions les plus populaires dans RevoScaleR, telles que les contextes de calcul à distance et de nombreux algorithmes qui prennent en charge de traitement distribué.

+ Choisir le meilleur langage pour la tâche.  R est idéal pour effectuer des calculs statistiques qui sont difficiles à implémenter à l’aide de SQL. Pour les opérations basées sur les données, exploiter la puissance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour optimiser les performances. Utilisez le moteur de base de données en mémoire pour effectuer des calculs très rapides sur les colonnes.

**Ressources**

+ [Étude de cas sur les performances](../../advanced-analytics/r/performance-case-study-r-services.md)
+ [R et optimisation des données](../../advanced-analytics/r/r-and-data-optimization-r-services.md)


## <a name="step-4-deploy-and-consume"></a>Étape 4. Déployer et utiliser

Une fois le script ou modèle R est prêt pour la production, un développeur de base de données peut-être incorporer le code ou le modèle dans une procédure stockée, d’afin que le code R ou Python enregistré peut être appelé à partir d’une application. Le stockage et l’exécution de code R à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offrent de nombreux avantages : ils permettent d’utiliser l’interface [!INCLUDE[tsql](../../includes/tsql-md.md)] , et tous les calculs ont lieu dans la base de données, ce qui évite les déplacements inutiles des données.

![rsql_keyscenario1](media/rsql-keyscenario1.png)

+ **Sécurisé et extensible**. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] utilise une nouvelle architecture d’extensibilité qui protège votre moteur de base de données et isole les sessions R. Vous pouvez contrôler les utilisateurs autorisés à exécuter des scripts R, et spécifier les bases de données accessibles au code R. Vous pouvez contrôler la quantité de ressources allouées au runtime R afin d’éviter que des calculs massifs ne mettent en péril les performances globales du serveur.

+ **Planification et d’audit**. Lors de l’exécution des tâches de script externe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez contrôler et auditer les données utilisées par les chercheurs de données. Vous pouvez également planifier des travaux et créer des workflows contenant des scripts R ou Python externes, tout comme vous planifiez tout autre travail T-SQL ou procédure stockée.

Pour tirer parti de la gestion des ressources et les fonctionnalités de sécurité ne dans SQL Server, le processus de déploiement peut inclure ces tâches :

+ Convertir votre code R à une fonction qui peut exécuter de façon optimale dans une procédure stockée
+ Configuration de la sécurité et en verrouillant les packages utilisés par une tâche particulière
+ L’activation de la gouvernance de ressources

**Ressources**

+ [Gouvernance des ressources pour R](../../advanced-analytics/r/resource-governance-for-r-services.md)
+ [Gestion des packages R pour SQL Server](../../advanced-analytics/r/r-package-management-for-sql-server-r-services.md)

## <a name="quick-starts"></a>Démarrages rapides

Lisez cette procédure pas à pas pour comprendre le flux de travail complet, à partir de l’exploration de données pour la création d’un modèle, son déploiement sur SQL Server.

+ [Procédure pas à pas pour une solution complète de science des données](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

Découvrez comment utiliser le package RevoScaleR pour l’analyse des performances évolutives et haute.

+ [Immersion dans la science des données : utilisation des packages RevoScaleR](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)

En particulier pour les développeurs de données--tout le code R fournie ! Découvrez comment incorporer R dans les procédures stockées SQL pour créer ou de l’apprentissage des modèles et obtenir des prédictions à partir d’un modèle stocké.

+ [Analytique avancée en base de données pour les développeurs SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Découvrir la syntaxe pour appeler R à partir d’une procédure stockée.

+ [Utilisation de code R dans Transact-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)

## <a name="solutions"></a>Solutions

Pour plus d’exemples, y compris de l’industrie = des modèles de solution spécifiques, consultez [Machine Learning didacticiels de SQL Server](../tutorials/machine-learning-services-tutorials.md).
