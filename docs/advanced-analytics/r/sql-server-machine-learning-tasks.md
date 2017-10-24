---
title: "Apprentissage des tâches de l’ordinateur SQL Server | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 04/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52ad3f10-6d24-477a-aeb6-110456b2ed1c
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 60272ce672c0a32738b0084ea86f8907ec7fc0a5
ms.openlocfilehash: c0e7a0929d5caa84df1a1fb02894db08313a36bd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="sql-server-machine-learning-tasks"></a>Tâches d’apprentissage automatique SQL Server

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] associe la puissance et la flexibilité du langage R open source avec les outils de niveau entreprise pour le stockage et l’administration des données, le développement de flux de travail, ainsi que la création et la visualisation de rapports. Cette rubrique décrit l’apprentissage de cycle de vie et la manière dont SQL Server prend en charge les besoins de quatre professionnels différentes données enagged dans l’apprentissage.

## <a name="machine-learning-life-cycle"></a>Cycle de vie d’apprentissage

Apprentissage automatique n’est pas une tâche à court terme, mais plutôt un processus à long terme qui touche tous les aspects des données de l’entreprise. Apprentissage commence avec l’identification des objectifs et des règles et la collection de données à partir de capteurs et applications d’entreprise. Apprentissage automatique dépend largement du processus d’extraction, de traitement et le stockage des données et est plus en plus important lorsque vous envisagez de stratégies pour le stockage, l’extraction et l’audit des données. Enfin, apprentissage est maintenant une homologation importante des stratégies pour le rapport d’analyse, ainsi que l’engagement client et des commentaires.



SQL Server est idéale pour l’apprentissage, car elle établit un pont entre la plupart des trous dans le processus d’apprentissage :

+ Fonctionne localement ou dans le cloud
+ Intégré à chaque étape du traitement des données entreprise, y compris le décisionnel
+ Prend en charge améliorée de la sécurité des données
+ Fournit la gouvernance des ressources et audit

## <a name="data-professionals-and-how-they-use-machine-learning"></a>Données professionnels et comment ils utiliser Machine Learning

### <a name="data-scientists"></a>Chercheurs de données

Chercheurs de données ont accès à une variété d’outils d’analyse de données et l’apprentissage automatique, allant d’Excel ou les plateformes open source gratuits, aux coûteuses suites statistiques qui requièrent des connaissances techniques approfondies. Toutefois, l’intégration avec SQL Server offre des avantages uniques :

+ Développez et testez vos solutions à l’aide de l’environnement de développement R de votre choix.
+ Transmettre des calculs à la base de données, ce qui évite le déplacement des données tout en respectant les stratégies de sécurité d’entreprise.
+ Performances et évolutivité sont améliorées via les API et les packages R spéciale. Vous n’êtes plus limité par l’architecture monothread, liée à la mémoire de R et pouvez utiliser les jeux de données volumineux et de calculs multicœurs, multithreads et multiprocessus.
+ Code R peut être déployé en production et appelé par les tableaux de bord, des applications, d’autres bases de données et des outils d’entreprise.
+ Les chercheurs de données peuvent déployer et mettre à jour d’une solution d’analyse tout en respectant les spécifications standard pour la gestion de données d’entreprise, notamment la sécurité et l’audit d’accès
+ Portabilité du code : réutiliser facilement votre code R sur d’autres sources de données, telles que Hadoop

### <a name="application-and-database-developers"></a>Application et développeurs de base de données

Les développeurs de base de données sont chargés d’intégrer plusieurs technologies et de les faire fonctionner ensemble afin que toute l’entreprise puisse en bénéficier. Les développeurs de base de données travaillent en collaboration avec des développeurs d’applications, des développeurs SQL et des spécialistes des données pour concevoir des solutions, recommander des méthodes de gestion des données, mais aussi créer et déployer des solutions. 

Intégration avec SQL Server offre les avantages aux développeurs de données qui travaillent avec machine learning :

+ Utiliser des outils familiers pour interagir avec des scripts R. Laisser le chercheur de données fonctionnent dans RStudio pendant que le développeur de données déploie la solution à l’aide de SQL Server Management Studio. Réécriture du code n’y a plus de solutions de R ou Python.
+ Optimiser en mélangeant et en SQL et R, ou SQL et Python. De nombreux cas, les opérations complexes sur les jeux de données volumineux peuvent être exécutées beaucoup plus efficacement à l’aide des fonctionnalités de SQL Server, tels que mémoire columnstoreindexes ou agrégats très rapides dans T-SQL. Utilisez un langage d’apprentissage où il est judicieux, utilisation de SQL pour déplacer et traiter des données.
+ Facilement automatiser les tâches qui doivent s’exécuter à plusieurs reprises sur de grandes quantités de données, comme la génération de scores de prédiction sur les données de production.
+ Exécutez le script R ou Python à partir de toute application qui utilise [!INCLUDE[tsql](../../includes/tsql-md.md)]. Simplement appeler une procédure stockée pour créer un modèle paramétrable, générer un graphique complex ou de sortie des prédictions.
+ Le **RevoScaleR** et **revoscalepy** API permettre opérer sur les jeux de données volumineux et tirer parti des calculs dans la base de données multicœurs, multithreads et multiprocessus.

Pour plus d’informations sur les tâches associées, consultez :
+ [Opérationnalisation de votre code R](../../advanced-analytics/r-services/operationalizing-your-r-code.md)

### <a name="database-administrators"></a>Administrateurs de base de données

Les administrateurs de base de données doivent intégrer des projets et priorités concurrents dans un point de contact unique : le serveur de base de données. Il doivent accorder l’accès aux données, non seulement aux chercheurs de données mais aussi aux développeurs de rapports, analystes d’entreprise et autres utilisateurs de données d’entreprise, tout en préservant l’intégrité des magasins de données opérationnelles et de rapport. En entreprise, l’administrateur de base de données est un intervenant essentiel dans la conception et le déploiement d’une infrastructure efficace pour la recherche de données. 

SQL Server fournit des fonctionnalités uniques pour l’administrateur de base de données qui doit prendre en charge les données chargé de :

+ Sécurité par SQL Server : l’architecture de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] protège vos bases de données et isole l’exécution des sessions de script externe à partir de l’opération de l’instance de base de données. Vous pouvez spécifier qui est autorisé à exécuter des scripts de machine learning, et qui peut installer des nouveaux packages R, à l’aide de rôles de base de données.

+ Les sessions R et Python sont exécutées dans un processus séparé pour garantir que votre serveur continue à exécuter comme d’habitude, même si le script externe rencontre des problèmes.

+ La gouvernance de ressources à l’aide de SQL Server vous permet de contrôler la mémoire allouées aux runtimes externes, pour empêcher que des calculs massifs mettent en péril les performances globales du serveur de processus.

Pour plus d’informations sur les tâches associées, consultez :
+ [Managing and Monitoring R Solutions](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)

### <a name="architects-and-etl-designers"></a>Architectes et concepteurs d’ETL

Des architectes conçoivent des flux de travail intégrés qui s’étendent sur tous les aspects du cycle de vie machine learning. Les ingénieurs de données concevoir et créer des solutions ETL et déterminer comment optimiser l’ingénierie de fonctionnalité qui ont des tâches font partie du processus d’apprentissage. Souvent, la plate-forme de données globale doit être conçue pour équilibrer les besoins métier concurrents et complémentaires.

Étant donné que [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] est profondément intégré à d’autres outils Microsoft, tels que l’aide à la décision et la pile de l’entrepôt de données, les outils d’entreprise cloud et de mobilité, et Hadoop, il offre divers avantages à l’ingénieur chargé du traitement des données ou à l’architecte système désireux de promouvoir des analyses avancées.

+ Outils de développement familiers pour développer des solutions R et Python. Vous pouvez appeler n’importe quel script Python ou R à l’aide de procédures stockées système, pour remplir les jeux de données, de générer des graphiques ou d’obtenir des prédictions. Aucun plus conception flux de travail parallèles dans la science des données et des outils ETL. Prise en charge d’Azure Data Factory et de la base de données SQL Azure facilite transformer et gérer les données et utiliser des sources de données de cloud dans le flux de travail d’apprentissage.

+ La planification et la gestion à l’aide des fonctionnalités d’à l’Opérationnalisation dans Microsoft R Server.

Pour plus d’informations sur les tâches associées, consultez :

+ [Création de flux de travail qui utilisent R dans SQL Server](../../advanced-analytics/r-services/creating-workflows-that-use-r-in-sql-server.md)


