---
title: Apprentissage automatique du cycle de vie et le processus d’équipe - SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 4d19c103f2e90220bc7d80a1da65eb0352252ad6
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511286"
---
# <a name="machine-learning-lifecycle-and-personas"></a>Les personnages et cycle de vie machine learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Projets machine learning peuvent être complexes, car ils nécessitent les compétences et la collaboration d’un ensemble disparate de professionnels. Cet article décrit les principales tâches dans la machine learning du cycle de vie, le type de professionnels des données qui sont engagés dans l’apprentissage automatique, et comment SQL Server prend en charge les besoins.

> [!TIP]
> 
> Avant de démarrer sur un projet machine learning, nous vous recommandons de consulter les outils et les meilleures pratiques fournies par le [Microsoft Team Data Science Process](https://blogs.technet.microsoft.com/machinelearning/2017/10/09/the-microsoft-team-data-science-process-tdsp-recent-updates/), ou TDSP. Ce processus a été créé par apprentissage des consultants Microsoft permettant de consolider les meilleures pratiques concernant la planification et l’itération sur les projets d’apprentissage. Le processus TDSP a ses racines dans les normes industrielles telles que CRISP-DM, mais intègre des pratiques récentes telles que les opérations de développement et de visualisation.

## <a name="machine-learning-life-cycle"></a>Cycle de vie machine learning

Machine learning est un processus complexe qui touche tous les aspects des données de l’entreprise, et de nombreux projets machine learning se retrouvent prend plus de temps et qui est plus complexe que prévu. Voici quelques-unes des méthodes qu’apprentissage nécessite la prise en charge de professionnels des données dans l’entreprise :

+ Apprentissage commence avec l’identification des objectifs et des règles d’entreprise.
+ Les professionnels de l’apprentissage machine doivent être conscient des stratégies de stockage, d’extraction et de données d’audit.
+ Collecte de données potentiellement applicables est la suivante.  Sources de données doivent être identifiés et les données appropriées extraites à partir des capteurs et applications d’entreprise. 
+ La qualité des efforts de machine learning est hautement dépend non seulement le type de données qui est disponibles, mais les processus très utilisés pour extraire, traiter et stocker des données. 
+ Aucun projet machine learning ne serait complet sans une stratégie pour le rapport d’analyse et éventuellement engagement des clients et des commentaires.

SQL Server vous aide à combler la plupart des écarts entre les professionnels de l’entreprise données et d’experts en formation :

+ Les données peuvent être stockées en local ou dans le cloud
+ SQL Server est intégré à chaque étape du traitement des données entreprise, y compris reporting et ETL
+ SQL Server prend en charge la sécurité des données, de redondance des données et de l’audit
+ Fournit la gouvernance des ressources

## <a name="data-scientists"></a>Les scientifiques des données

Les scientifiques de données utilisent un large éventail d’outils analyse de données et apprentissage automatique, allant d’Excel ou des plateformes open source gratuits, aux coûteuses suites statistiques qui nécessitent des connaissances techniques approfondies. Toutefois, à l’aide de R ou Python avec SQL Server offre certains avantages uniques par rapport à ces outils traditionnels :

+ Vous pouvez développer et tester une solution à l’aide de l’environnement de développement de votre choix, puis déployer votre code R ou Python en tant que partie du code T-SQL.
+ Déplacer des calculs complexes hors tension de l’ordinateur portable du chercheur de données et sur le serveur, évitant ainsi le déplacement de données pour se conformer aux stratégies de sécurité d’entreprise.
+ Performances et évolutivité sont améliorées par le biais des packages R spéciaux et des API. Vous n’êtes plus limité par l’architecture monothread, liée à la mémoire de R et pourrez travailler avec les jeux de données volumineux et des calculs multithreads, multicœurs et multiprocessus.
+ Portabilité du code : Solutions peuvent être exécutées dans SQL Server ou dans Hadoop ou Linux, à l’aide de [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server). Code une seule fois, puis déployez partout.

## <a name="application-and-database-developers"></a>Développeurs d’application et de la base de données

Les développeurs de base de données sont chargés d’intégrer plusieurs technologies et de les faire fonctionner ensemble afin que toute l’entreprise puisse en bénéficier. Le développeur de base de données fonctionne avec les développeurs d’applications, les développeurs SQL et aux chercheurs de données pour concevoir des solutions, recommandons des méthodes de gestion des données et l’architecture ou déployer des solutions.

Intégration avec SQL Server offre de nombreux avantages aux développeurs de données :

+ Les spécialistes des données peuvent travailler dans RStudio, tandis que le développeur de données déploie la solution à l’aide de SQL Server Management Studio. Ne plus recoder des solutions R ou Python.
+ Optimisez vos solutions à l’aide de la meilleure de T-SQL, R et Python. Des opérations complexes sur les jeux de données volumineux pouvant être exécutées beaucoup plus efficacement à l’aide de SQL Server que dans R. Tirez parti de vos professionnels de la base de données, la base de connaissances pour améliorer les performances des solutions machine learning, à l’aide des index columnstore en mémoire, et agrégations à l’aide des opérations de jeu SQL. 
+ Facilement automatiser les tâches qui doivent s’exécuter à plusieurs reprises sur de grandes quantités de données, comme la génération de scores de prédiction sur les données de production. 
+ Accès paramétrables script R ou Python à partir de n’importe quelle application qui utilise [!INCLUDE[tsql](../../includes/tsql-md.md)]. Suffit d’appeler une procédure stockée pour former un modèle, générer un graphique ou des prédictions de sortie.
+ API peuvent diffuser les jeux de données volumineux et tirer parti des calculs dans base de données multithreads, multicœurs et multiprocessus.

Pour plus d’informations sur les tâches associées, consultez :
+ [Opérationnalisation de votre code R](../../advanced-analytics/r/operationalizing-your-r-code.md)

### <a name="database-administrators"></a>Administrateurs de base de données

Les administrateurs de base de données doivent intégrer des projets et priorités concurrents dans un point de contact unique : le serveur de base de données. Il doivent accorder l’accès aux données, non seulement aux chercheurs de données mais aussi aux développeurs de rapports, analystes d’entreprise et autres utilisateurs de données d’entreprise, tout en préservant l’intégrité des magasins de données opérationnelles et de rapport. En entreprise, l’administrateur de base de données est un intervenant essentiel dans la conception et le déploiement d’une infrastructure efficace pour la recherche de données. 

SQL Server fournit des fonctionnalités uniques pour l’administrateur de base de données qui doit de prendre en charge le rôle de science des données :

+ Sécurité par SQL Server : L’architecture de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] protège vos bases de données et isole l’exécution des sessions de script externe à partir de l’opération de l’instance de base de données. Vous pouvez spécifier qui est autorisé à exécuter des scripts d’apprentissage automatique et utiliser des rôles de base de données pour gérer les packages.

+ Les sessions R et Python sont exécutées dans un processus séparé pour garantir que votre serveur continue à exécuter comme d’habitude, même si le script externe rencontre des problèmes.

+ Gouvernance des ressources à l’aide de SQL Server vous permet de contrôler la mémoire et les processus alloués aux runtimes externes, pour éviter que des calculs massifs mettent en péril les performances globales du serveur.

Pour plus d’informations sur les tâches associées, consultez :
+ [Gestion et surveillance des solutions Machine Learning](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)

## <a name="architects-and-data-engineers"></a>Ingénieurs de données et les architectes

Architectes de concevoir des flux de travail intégrés qui couvrent tous les aspects du cycle de vie machine learning. Les ingénieurs de données concevoir et créer des solutions ETL, puis déterminent comment optimiser les tâches ingénierie de fonctionnalité pour l’apprentissage. La plate-forme de données globale doit être conçue pour équilibrer les besoins métier concurrents.

Étant donné que [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] est profondément intégré à d’autres outils Microsoft, tels que l’aide à la décision et la pile de l’entrepôt de données, les outils d’entreprise cloud et de mobilité, et Hadoop, il offre divers avantages à l’ingénieur chargé du traitement des données ou à l’architecte système désireux de promouvoir des analyses avancées.

+ Appeler n’importe quel script Python ou R à l’aide de procédures stockées système, pour remplir des jeux de données, générer des graphiques ou obtenir des prédictions. Aucun plus conception flux de travail parallèles dans la science des données et les outils ETL. Prise en charge pour Azure Data Factory et Azure SQL Database rend plus facile à utiliser des sources de données cloud dans des flux de travail d’apprentissage.

+ Pour la planification et la gestion des tâches d’apprentissage, utiliser des flux de travail automation standard dans SQL Server, selon les Services d’intégration, l’Agent SQL ou Azure Data Factory. Ou, utilisez la [fonctionnalités d’Opérationnalisation](https://docs.microsoft.com/machine-learning-server/operationalize/how-to-deploy-web-service-publish-manage-in-r) dans Machine Learning Server.

Pour plus d’informations sur les tâches associées, consultez :

+ [Création de flux de travail machine learning dans SQL Server](../../advanced-analytics/r/creating-workflows-that-use-r-in-sql-server.md)

