---
title: Intégration - SQL Server Machine Learning Services des fonctionnalités de langage R et Python
description: Langage R et les fonctionnalités de Python dans SQL Server, l’intégration avec des données relationnelles pour la science des données et modélisation statistique, modèles d’apprentissage automatique, analytique prédictive, visualisation des données et bien plus encore.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2018
ms.topic: overview
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 59ec5bbacf23d0f86f88a17a68faaf27162ebdcb
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53596790"
---
# <a name="machine-learning-services-r-python-in-sql-server-2017"></a>Machine Learning Services (R, Python) dans SQL Server 2017
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2017 Machine Learning Services est un module complémentaire à une instance du moteur de base de données, utilisé pour l’exécution de code R et Python sur SQL Server. La fonctionnalité inclut [packages Microsoft R et Python](#components) pour l’analytique prédictive hautes performances et l’apprentissage. Code s’exécute dans une infrastructure d’extensibilité, isolé des processus de moteur de base, mais totalement disponibles pour les données relationnelles comme des procédures stockées, en tant que script T-SQL qui contient des instructions de R ou Python ou en tant que code R ou Python contenant T-SQL. 

Si vous avez utilisé précédemment [SQL Server 2016 R Services](r/sql-server-r-services.md), Machine Learning Services dans SQL Server 2017 est la nouvelle génération de prise en charge de R, avec les versions mises à jour de base R, RevoScaleR, MicrosoftML, et autres bibliothèques introduites en 2016. 

Dans la base de données SQL Azure, [Machine Learning Services (avec R)](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-r) est actuellement en version préliminaire publique.

La proposition de valeur de clé de Machine Learning Services est la puissance de son entreprise R et les packages Python pour fournir une analytique avancée à l’échelle et la possibilité de définir des calculs et traitement à l’emplacement des données, éliminant la nécessité pour extraire les données entre le réseau.

<a name="components"></a>

## <a name="components"></a>Composants

SQL Server 2017 prend en charge R et Python. Le tableau suivant décrit les composants.

| Composant | Description |
|-----------|-------------|
| Service SQL Server Launchpad | Un service qui gère les communications entre les runtimes R et Python externes et l’instance du moteur de base de données. |
| Packages R | [**RevoScaleR** ](r/ref-r-revoscaler.md) est la bibliothèque principale pour évolutive fonctions R. dans cette bibliothèque sont parmi les plus couramment utilisées. Transformations de données et de manipulation, de synthèse statistique, de visualisation et de nombreuses formes de modélisation et les analyses sont trouvent dans ces bibliothèques. En outre, les fonctions dans ces bibliothèques distribuer automatiquement les charges de travail entre les cœurs disponibles pour le traitement parallèle, avec la possibilité de travailler sur des segments de données coordonnées et gérées par le moteur de calcul.  <br/>[**MicrosoftML (R)** ](r/ref-r-microsoftml.md) ajoute des algorithmes d’apprentissage automatique pour créer des modèles personnalisés pour l’analyse de texte, l’analyse de l’image et l’analyse des sentiments. <br/>[**sqlRUtils** ](r/ref-r-sqlrutils.md) fournit des fonctions d’assistance pour placer des scripts R dans une procédure stockée T-SQL, l’inscription d’une procédure stockée avec une base de données et l’exécution de la procédure stockée à partir d’un environnement de développement R.<br/>[**olapR** ](r/ref-r-olapr.md) est de construction ou de l’exécution d’une requête MDX dans un script R.|
| Microsoft R Open (MRO) | [**MRO** ](https://mran.microsoft.com/open) est open source distribution Microsoft de R. Le package et un interpréteur sont inclus. Utilisez toujours la version de MRO installé par le programme d’installation. |
| Outils R | Invites de commandes et fenêtres de console R sont des outils standard dans une distribution de R.  |
| Exemples de R et scripts |  Les packages RevoScaleR et R Open source incluent les jeux de données intégrées afin que vous pouvez créer et exécuter le script à l’aide de données préinstallées. |
| Packages Python | [**revoscalepy** ](python/ref-py-revoscalepy.md) est la bibliothèque principale pour Python évolutive avec des fonctions de manipulation de données, de transformation, de visualisation et d’analyse. <br/>[**microsoftml (Python)** ](python/ref-py-microsoftml.md) ajoute des algorithmes d’apprentissage automatique pour créer des modèles personnalisés pour l’analyse de texte, l’analyse de l’image et l’analyse des sentiments.  |
| Outils Python | L’outil de ligne de commande Python intégré est utile pour les tests ad hoc et tâches.  |
| Anaconda | Anaconda est une distribution open source de Python et les packages essentiels. |
| Scripts et des exemples Python | Comme avec R, Python inclut des jeux de données intégrés et des scripts.  |
| Modèles préentraînés dans R et Python | Modèles préentraînés sont créés pour les cas d’usage spécifiques et gérés par l’équipe d’ingénierie science des données chez Microsoft. Vous pouvez utiliser les modèles préformés comme-consiste à noter les sentiments négatifs positif dans le texte, ou à détecter les fonctionnalités dans des images, à l’aide de nouvelles entrées de données que vous fournissez. Les modèles s’exécutent dans Machine Learning Services, mais ne peut pas être installés via le programme d’installation de SQL Server. Pour plus d’informations, consultez [installation préentraîné modèles d’apprentissage sur SQL Server](install/sql-pretrained-models-install.md). |

## <a name="using-sql-mls"></a>À l’aide de SQL MLS

Analystes et les développeurs ont souvent le code qui s’exécute sur une instance de SQL Server locale. En ajoutant des Services Machine Learning et l’activation de l’exécution du script externe, vous avez la possibilité d’exécuter du code R et Python dans les modalités de SQL Server : encapsulant le script dans les procédures stockées, stocker des modèles dans une table SQL Server ou combinaison de T-SQL et des fonctions R ou Python dans les requêtes.

L’exécution du script se trouve dans les limites du modèle de sécurité des données : les autorisations sur la base de données relationnel constituent la base d’accès aux données dans votre script. Un utilisateur exécute le script R ou Python ne doit pas être en mesure d’utiliser toutes les données qui ne sont pas accessible par l’utilisateur dans une requête SQL. Vous avez besoin de la lecture de la base de données standard et autorisations d’écriture, ainsi qu’une autorisation supplémentaire pour exécuter le script externe. Modèles et le code que vous écrivez pour les données relationnelles sont encapsulées dans des procédures stockées, sérialisés dans un format binaire et stockés dans une table ou chargés à partir du disque, si vous sérialisiez le flux d’octets bruts dans un fichier.

L’approche la plus courante pour la base de données analytique consiste à utiliser [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), en passant de script R ou Python comme paramètre d’entrée.

Interactions client-serveur classique sont une autre approche. À partir de n’importe quel client station de travail avec un IDE, vous pouvez installer [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) ou [bibliothèques Python](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)et ensuite écrire du code qui exécute un push de l’exécution (appelé un *calcul à distance contexte*) aux données et aux opérations à un serveur SQL distant. 

Enfin, si vous utilisez un [serveur autonome](r/r-server-standalone.md) et l’édition développeur, vous pouvez créer des solutions sur une station de travail cliente à l’aide de la même interpréteurs et des bibliothèques et déployer le code de production sur SQL Server Machine Learning Services (en base de données). 

## <a name="how-to-get-started"></a>La prise en main

### <a name="step-1-install-the-software"></a>Étape 1 : Installer le logiciel

+ [SQL Server Machine Learning Services (en base de données)](install/sql-machine-learning-services-windows-install.md)
 
### <a name="step-2-configure-a-development-tool"></a>Étape 2 : Configurer un outil de développement

Les scientifiques des données utilisent généralement R ou Python sur leur propre station de travail d’ordinateur portable ou de développement, pour Explorer les données et de créer et de régler des modèles prédictifs jusqu'à ce qu’un bon modèle prédictif est établie. Avec l’analytique en base de données dans SQL Server, il est inutile de modifier ce processus. Une fois l’installation terminée, vous pouvez exécuter le code R ou Python sur SQL Server localement et à distance.

![rsql_keyscenario2](r/media/rsql-keyscenario2.png) 

+ **Utiliser l’IDE que vous préférez**. Vous pouvez lier les bibliothèques R et Python à votre outil de développement favori. Pour plus d’informations, consultez [configurer les outils R](r/set-up-a-data-science-client.md) et [configurer Python tools](python/setup-python-client-tools-sql.md).  

+ **Travailler à distance ou localement**. Les scientifiques des données peuvent se connecter à SQL Server et importer les données au client pour une analyse locale, comme d’habitude. Toutefois, une meilleure solution consiste à utiliser le **RevoScaleR** ou **revoscalepy** API pour envoyer des calculs à l’ordinateur SQL Server, évitant ainsi le déplacement de données coûteux et non sécurisé.

+ **Incorporer des scripts R ou Python dans les procédures stockées SQL Server**. Lorsque votre code est entièrement optimisé l’encapsuler dans une procédure stockée pour éviter le déplacement des données inutiles et optimiser les tâches de traitement des données.

### <a name="step-3-write-your-first-script"></a>Étape 3 : Écrire votre premier script

Appeler des fonctions R ou Python à partir de dans le script T-SQL :

+ [R : Découvrez l’analytique en base de données à l’aide de R](tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [R : Procédure pas à pas de bout en bout avec R](tutorials/walkthrough-data-science-end-to-end-walkthrough.md)
+ [Python : Exécutez le code Python à l’aide de T-SQL](tutorials/run-python-using-t-sql.md)
+ [Python : Découvrez l’analytique en base de données à l’aide de Python](tutorials/sqldev-in-database-python-for-sql-developers.md)

Choisir le meilleur langage pour la tâche. R est idéal pour les calculs statistiques qui sont difficiles à implémenter à l’aide de SQL. Pour les opérations de jeu basé sur les données, exploiter la puissance de SQL Server pour optimiser les performances. Utiliser le moteur de base de données en mémoire pour effectuer des calculs très rapides sur les colonnes.

### <a name="step-4-optimize-your-solution"></a>Étape 4 : Optimiser votre solution

Lorsque le modèle est prêt à l’échelle sur les données d’entreprise, les spécialistes des données est souvent fonctionnement avec le développeur de base de données ou SQL pour optimiser les processus tels que :

+ Ingénierie des caractéristiques
+ Ingestion des données et la transformation des données
+ Calcul de score

En règle générale, les scientifiques des données à l’aide de R ont eu des problèmes de performances et de mise à l’échelle, surtout lorsque vous utilisez le jeu de données volumineux. C’est parce que l’implémentation common runtime est monothread et qu’il peut accepter uniquement les jeux de données qui entrent dans la mémoire disponible sur l’ordinateur local. Intégration avec SQL Server Machine Learning Services fournit plusieurs fonctionnalités pour de meilleures performances, avec plus de données :

+ **RevoScaleR**: Ce package R contient des implémentations de certaines fonctions R plus populaires, ont été repensées pour fournir un parallélisme et mise à l’échelle. Le package comprend également des fonctions qui améliorent encore davantage les performances et mise à l’échelle en envoyant des calculs à l’ordinateur SQL Server, lequel dispose généralement bien plus de mémoire et de puissance de calcul.

+ **revoscalepy**. Cette bibliothèque Python implémente les fonctions plus populaires dans RevoScaleR, telles que les contextes de calcul distants et de nombreux algorithmes qui prennent en charge de traitement distribué.

Pour plus d’informations sur les performances, consultez ce [étude de cas de performances](r/performance-case-study-r-services.md) et [R et les données d’optimisation](r/r-and-data-optimization-r-services.md).

### <a name="step-5-deploy-and-consume"></a>Étape 5 : Déployer et utiliser

Une fois le script ou le modèle est prêt pour la production, un développeur de base de données peut incorporer le code ou le modèle dans une procédure stockée d’afin que le code R ou Python enregistré peut être appelé à partir d’une application. Stockage et l’exécution du code R à partir de SQL Server présente de nombreux avantages : vous pouvez utiliser l’interface pratique de SQL Server, et tous les calculs ont lieu dans la base de données, évitant ainsi le déplacement de données inutiles.

![rsql_keyscenario1](r/media/rsql-keyscenario1.png)

+ **Sécurisé et extensible**. SQL Server utilise une nouvelle architecture d’extensibilité qui protège votre moteur de base de données et isole les sessions R et Python. Vous pouvez contrôler les utilisateurs qui peuvent exécuter des scripts, et vous pouvez spécifier les bases de données sont accessibles par le code. Vous pouvez contrôler la quantité de ressources allouées au runtime, pour éviter que des calculs massifs mettent en péril les performances globales du serveur.

+ **Planification et d’audit**. Lorsque les tâches de script externe sont exécutées dans SQL Server, vous pouvez contrôler et auditer les données utilisées par les scientifiques de données. Vous pouvez également planifier des travaux et créer des workflows contenant des scripts R ou Python externes, comme vous planifiez tout autre travail T-SQL ou procédure stockée.

Pour tirer parti de la gestion des ressources et les fonctionnalités de sécurité dans SQL Server, le processus de déploiement peut inclure ces tâches :

+ Conversion de votre code à une fonction qui peut exécuter de façon optimale dans une procédure stockée
+ Configuration de la sécurité et de verrouillage de packages utilisés par une tâche spécifique
+ L’activation de la gouvernance des ressources (nécessite l’édition Enterprise)

Pour plus d’informations, consultez [gouvernance des ressources pour R](r/resource-governance-for-r-services.md) et [gestion des packages R pour SQL Server](r/install-additional-r-packages-on-sql-server.md).

## <a name="version-history"></a>Historique des versions

SQL Server 2017 Machine Learning Services est la nouvelle génération de SQL Server 2016 R Services, améliorées pour inclure les Python. Le tableau suivant est une liste complète de toutes les versions de produit, de la création à la version actuelle. 

| Nom de produit | Version du moteur | Date de publication |
|--------------|---------|--------------|
| SQL Server 2017 Machine Learning Services (en base de données) | R Server 9.2.1 <br/> Python Server 9.2 | Octobre 2017 |
| SQL Server 2017 Machine Learning Server (autonome) | R Server 9.2.1 <br/> Python Server 9.2 | Octobre 2017 |
| SQL Server 2016 R Services (en base de données) | R Server 9.1  | Juillet 2017  |
| SQL Server 2016 R Server (autonome)  |  R Server 9.1 | Juillet 2017 |

Pour les versions de package par version, voir la version de la carte dans [les composants de mise à niveau de R et Python](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md#version-map).

## <a name="portability-and-related-products"></a>Portabilité et des produits associés

Portabilité de votre code personnalisé R et Python est résolue via les interpréteurs qui sont intégrées dans plusieurs produits et de la distribution de package. Les packages qui sont fournis dans SQL Server sont également disponibles dans plusieurs autres produits et services Microsoft, y compris une version non SQL appelée [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/). 

Les clients gratuits comprenant notre interpréteurs R et Python sont [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) et [bibliothèques Python](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter).

Sur Azure, interpréteurs et des packages R et Python de Microsoft sont également disponibles sur Azure Machine Learning, et les services Azure comme [HDInsight](https://docs.microsoft.com/azure/hdinsight/r-server/r-server-overview), et [machines virtuelles](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-azure-vm-on-linux). Le [Data Science Virtual Machine](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) inclut une station de travail de développement entièrement équipé des outils à partir de plusieurs fournisseurs, ainsi que les bibliothèques et des interpréteurs de Microsoft.

## <a name="see-also"></a>Voir aussi

[Installer SQL Server Machine Learning Services](install/sql-machine-learning-services-windows-install.md)
