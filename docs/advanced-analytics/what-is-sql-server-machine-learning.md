---
title: Vue d’ensemble de SQL Server Machine Learning Services (R, Python)
description: Vue d’ensemble de la fonctionnalité de Machine Learning Services dans SQL Server, dans laquelle vous pouvez intégrer Python et R avec des données relationnelles pour la modélisation statistique et de science des données, des modèles Machine Learning, des analyses prédictives, la visualisation des données et bien plus encore.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: ead0dd3d9ba69a4bf0079fe8065a2d5aa7a11d3e
ms.sourcegitcommit: 63c6f3758aaacb8b72462c2002282d3582460e0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68495400"
---
# <a name="sql-server-machine-learning-services-r-python"></a>SQL Server Machine Learning Services (R, Python)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Machine Learning Services est une fonctionnalité de SQL Server, utilisée pour l’exécution de scripts R et Python dans la base de données. Cette fonctionnalité comprend des [packages Microsoft R et Python](#components) pour l’analyse prédictive et l’machine learning à hautes performances. Les données relationnelles peuvent être utilisées dans des scripts R et Python via des procédures stockées, un script T-SQL contenant des instructions R et Python, ou du code R et Python contenant T-SQL.

Si vous avez déjà utilisé [SQL Server 2016 R services](r/sql-server-r-services.md), Machine Learning Services dans SQL Server 2017 et versions ultérieures est la nouvelle génération de prise en charge de r, avec les versions mises à jour de base r, RevoScaleR, MicrosoftML et d’autres bibliothèques introduites dans 2016.

Dans Azure SQL Database, [machine learning services (avec R)](https://docs.microsoft.com/azure/sql-database/sql-database-machine-learning-services-overview) est actuellement en préversion publique.

## <a name="bring-compute-power-to-the-data"></a>Mettre la puissance de calcul sur les données

La proposition de valeur clé de Machine Learning Services est la puissance de ses packages Enterprise R et Python pour fournir des analytiques avancées à l’échelle, ainsi que la possibilité d’apporter des calculs et des traitements à l’emplacement où résident les données, ce qui élimine le besoin d’extraire des données dans réseau. Cela offre plusieurs avantages:

+ Sécurité des données. L’exécution de R et de Python plus près de la source de données évite le gaspillage des données ou le déplacement des données.
+ Vitesse. Les bases de données sont optimisées pour les opérations basées sur un jeu. Les innovations récentes des bases de données telles que les tables en mémoire font des résumés et des agrégations, et constituent un complément parfait à la science des données.
+ Facilité de déploiement et d’intégration. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]est le point central des opérations pour de nombreuses autres tâches et applications de gestion des données. En utilisant des données qui résident dans la base de données ou dans l’entrepôt de création de rapports, vous vous assurez que les données utilisées par Machine Learning Solutions sont cohérentes et à jour. 
+ Efficacité dans le Cloud et localement. Au lieu de traiter les données dans des sessions R ou python, vous pouvez vous appuyer sur des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pipelines de données d’entreprise, y compris et Azure Data Factory. La création de rapports de résultats ou d’analyses est simple dans Power BI ou [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].

En utilisant le bonne combinaison entre SQL et R pour différentes tâches de traitement et d’analyse des données, tant les scientifiques des données que les développeurs peuvent gagner en productivité.

<a name="components"></a>

## <a name="components"></a>Composants

SQL Server 2017 prend en charge R et Python. Le tableau suivant décrit les composants de.

| Composant | Description |
|-----------|-------------|
| Service SQL Server Launchpad | Service qui gère les communications entre les runtimes externes R et Python et l’instance du moteur de base de données. |
| Packages R | [**RevoScaleR**](r/ref-r-revoscaler.md) est la bibliothèque principale de R. les fonctions évolutives dans cette bibliothèque sont parmi les plus couramment utilisées. La transformation et la manipulation des données, le résumé statistique, la visualisation et de nombreuses formes de modélisation et d’analyse sont rendues possibles avec ces bibliothèques. De plus, les fonctions de ces bibliothèques répartissent automatiquement les charges de travail entre les cœurs disponibles pour un traitement parallèle, avec la possibilité de travailler sur des blocs de données qui sont coordonnés et gérés par le moteur de calcul.  <br/>[**MicrosoftML (R)** ](r/ref-r-microsoftml.md) ajoute des algorithmes machine learning pour créer des modèles personnalisés pour l’analyse de texte, l’analyse d’images et l’analyse des sentiments. <br/>[**sqlRUtils**](r/ref-r-sqlrutils.md) fournit des fonctions d’assistance pour placer des scripts R dans une procédure stockée T-SQL, inscrire une procédure stockée avec une base de données et exécuter la procédure stockée à partir d’un environnement de développement R.<br/>[**olapr**](r/ref-r-olapr.md) est destiné à la génération ou à l’exécution d’une requête MDX dans un script R.|
| Microsoft R Open (MRO) | [**MRO**](https://mran.microsoft.com/open) est la distribution Open source de Microsoft de R. Le package et l’interpréteur sont inclus. Utilisez toujours la version de MRO installée par le programme d’installation de. |
| Outils R | Les fenêtres de console R et les invites de commande sont des outils standard dans une distribution R.  |
| Exemples et scripts R |  Les packages R et RevoScaleR Open source incluent des jeux de données intégrés qui vous permettent de créer et d’exécuter un script à l’aide de données pré-installées. |
| Packages Python | [**revoscalepy**](python/ref-py-revoscalepy.md) est la bibliothèque principale de Python extensible avec fonctions de manipulation, de transformation, de visualisation et d’analyse des données. <br/>[**microsoftml (Python)** ](python/ref-py-microsoftml.md) ajoute des algorithmes de machine learning pour créer des modèles personnalisés pour l’analyse de texte, l’analyse d’images et l’analyse des sentiments.  |
| Outils python | L’outil de ligne de commande python intégré est utile pour les tâches et les tests ad hoc.  |
| Anaconda | Anaconda est une distribution Open source de packages Python et essentiels. |
| Exemples et scripts Python | Comme avec R, Python comprend des jeux de données et des scripts intégrés.  |
| Modèles pré-formés dans R et Python | Des modèles préformés sont créés pour des cas d’usage spécifiques et gérés par l’équipe d’ingénierie de science des données chez Microsoft. Vous pouvez utiliser les modèles préformés tels quels pour noter des sentiments positifs et négatifs dans du texte, ou pour détecter des fonctionnalités dans des images, en utilisant de nouvelles entrées de données que vous fournissez. Les modèles s’exécutent dans Machine Learning Services, mais ne peuvent pas être installés par le biais du programme d’installation de SQL Server. Pour plus d’informations, consultez [installer des modèles de machine learning pré-formés sur SQL Server](install/sql-pretrained-models-install.md). |

## <a name="using-sql-mls"></a>Utilisation de SQL MLS

Les développeurs et les analystes ont souvent du code s’exécutant sur une instance de SQL Server locale. En ajoutant Machine Learning Services et en activant l’exécution de scripts externes, vous avez la possibilité d’exécuter du code R et Python dans SQL Server modales: l’encapsulation de script dans des procédures stockées, le stockage de modèles dans une table SQL Server ou la combinaison de fonctions T-SQL et R ou python. dans les requêtes.

L’exécution du script se trouve dans les limites du modèle de sécurité des données: les autorisations sur la base de données relationnelle constituent la base de l’accès aux données dans votre script. Un utilisateur exécutant le script R ou python ne doit pas être en mesure d’utiliser des données qui n’ont pas pu être accessibles par cet utilisateur dans une requête SQL. Vous avez besoin des autorisations de lecture et d’écriture de la base de données standard, ainsi que d’une autorisation supplémentaire pour exécuter un script externe. Les modèles et le code que vous écrivez pour les données relationnelles sont encapsulés dans des procédures stockées, ou sérialisés dans un format binaire et stockés dans une table, ou chargés à partir du disque si vous avez sérialisé le flux d’octets bruts dans un fichier.

L’approche la plus courante pour l’analyse dans la base de données consiste à utiliser [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), en passant le script R ou python en tant que paramètre d’entrée.

Les interactions client-serveur classiques sont une autre approche. À partir de n’importe quelle station de travail cliente dotée d’un IDE, vous pouvez installer [Microsoft R client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) ou les [bibliothèques python](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter), puis écrire du code qui pousse l’exécution (appelée *contexte de calcul distant*) vers des données et des opérations vers un SQL Server distant. 

Enfin, si vous utilisez un [serveur autonome](r/r-server-standalone.md) et l’édition développeur, vous pouvez créer des solutions sur une station de travail cliente à l’aide des mêmes bibliothèques et interpréteurs, puis déployer le code de production sur SQL Server machine learning services (dans la base de données). 

## <a name="how-to-get-started"></a>Prise en main

### <a name="step-1-install-the-software"></a>Étape 1 : Installer le logiciel

+ [SQL Server Machine Learning Services (dans la base de données)](install/sql-machine-learning-services-windows-install.md)
 
### <a name="step-2-configure-a-development-tool"></a>Étape 2 : Configurer un outil de développement

Les scientifiques des données utilisent généralement R ou python sur leur propre ordinateur portable ou station de travail de développement, pour explorer les données et pour créer et paramétrer des modèles prédictifs jusqu’à ce qu’un bon modèle prédictif soit atteint. Avec l’analytique dans la base de données dans SQL Server, il n’est pas nécessaire de modifier ce processus. Une fois l’installation terminée, vous pouvez exécuter du code R ou python sur SQL Server localement et à distance.

![rsql_keyscenario2](r/media/rsql-keyscenario2.png) 

+ **Utilisez l’IDE de votre choix**. Vous pouvez lier les bibliothèques R et Python à votre outil de développement de votre choix. Pour plus d’informations, consultez [configurer les outils R](r/set-up-a-data-science-client.md) et [configurer les outils python](python/setup-python-client-tools-sql.md).  

+ **Travaillez à distance ou localement**. Les scientifiques des données peuvent se connecter à SQL Server et transférer les données au client pour une analyse locale, comme d’habitude. Toutefois, une meilleure solution consiste à utiliser les API **RevoScaleR** ou **revoscalepy** pour envoyer des calculs à l’ordinateur SQL Server, évitant ainsi un déplacement de données coûteux et non sécurisé.

+ **Incorporez des scripts R ou python dans SQL Server procédures stockées**. Lorsque votre code est entièrement optimisé, encapsulez-le dans une procédure stockée pour éviter le déplacement inutile des données et optimiser les tâches de traitement des données.

### <a name="step-3-write-your-first-script"></a>Étape 3 : Écrire votre premier script

Appelez les fonctions R ou python à partir de script T-SQL:

+ [R En savoir plus sur l’analytique de base de données à l’aide de R](tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [R Procédure pas à pas de bout en bout avec R](tutorials/walkthrough-data-science-end-to-end-walkthrough.md)
+ [Software Exécuter Python à l’aide de T-SQL](tutorials/run-python-using-t-sql.md)
+ [Software Apprendre les analyses dans la base de données à l’aide de Python](tutorials/sqldev-in-database-python-for-sql-developers.md)

Choisissez la meilleure langue pour la tâche. R est idéal pour les calculs statistiques qui sont difficiles à implémenter à l’aide de SQL. Pour les opérations basées sur des ensembles de données, tirez parti de la puissance de SQL Server pour atteindre des performances maximales. Utilisez le moteur de base de données en mémoire pour les calculs très rapides sur les colonnes.

### <a name="step-4-optimize-your-solution"></a>Étape 4 : Optimiser votre solution

Lorsque le modèle est prêt à être mis à l’échelle sur des données d’entreprise, le chercheur de données travaille souvent avec l’administrateur de bases de données ou le développeur SQL pour optimiser les processus tels que:

+ Ingénierie des caractéristiques
+ Ingestion de données et transformation des données
+ Soulign

Traditionnellement, les scientifiques des données qui utilisent R ont rencontré des problèmes de performances et de mise à l’échelle, en particulier lors de l’utilisation d’un jeu de données volumineux. Cela est dû au fait que l’implémentation d’exécution courante est monothread et ne peut prendre en charge que les jeux de données qui tiennent dans la mémoire disponible sur l’ordinateur local. L’intégration avec SQL Server Machine Learning Services fournit plusieurs fonctionnalités pour de meilleures performances, avec davantage de données:

+ **RevoScaleR**: Ce package R contient des implémentations de certaines fonctions R les plus populaires, repensées pour fournir un parallélisme et une mise à l’échelle. Le package inclut également des fonctions qui améliorent les performances et la mise à l’échelle en envoyant des calculs à l’ordinateur SQL Server, qui a généralement beaucoup plus de mémoire et de puissance de calcul.

+ **revoscalepy**. Cette bibliothèque python implémente les fonctions les plus populaires dans RevoScaleR, telles que les contextes de calcul distants, et de nombreux algorithmes qui prennent en charge le traitement distribué.

Pour plus d’informations sur les performances, consultez cette [étude de cas](r/performance-case-study-r-services.md) sur les performances et l' [optimisation de R et de données](r/r-and-data-optimization-r-services.md).

### <a name="step-5-deploy-and-consume"></a>Étape 5 : Déployer et utiliser

Une fois que le script ou le modèle est prêt pour une utilisation en production, un développeur de base de données peut incorporer le code ou le modèle dans une procédure stockée afin que le code R ou python enregistré puisse être appelé à partir d’une application. Le stockage et l’exécution de code R à partir de SQL Server présentent de nombreux avantages: vous pouvez utiliser l’interface SQL Server pratique, et tous les calculs ont lieu dans la base de données, ce qui évite les déplacements de données inutiles.

![rsql_keyscenario1](r/media/rsql-keyscenario1.png)

+ **Sécurisé et extensible**. SQL Server utilise une nouvelle architecture d’extensibilité qui protège votre moteur de base de données et isole les sessions R et Python. Vous pouvez également contrôler les utilisateurs qui peuvent exécuter des scripts et spécifier les bases de données accessibles par le code. Vous pouvez contrôler la quantité de ressources allouées au runtime, afin d’éviter que des calculs massifs ne mettent en péril les performances globales du serveur.

+ **Planification et audit**. Lorsque des tâches de script externe sont exécutées dans SQL Server, vous pouvez contrôler et auditer les données utilisées par les scientifiques des données. Vous pouvez également planifier des travaux et créer des flux de travail contenant des scripts R ou python externes, comme vous le feriez pour tout autre travail ou procédure stockée T-SQL.

Pour tirer parti des fonctionnalités de sécurité et de gestion des ressources de SQL Server, le processus de déploiement peut inclure les tâches suivantes:

+ Conversion de votre code en fonction qui peut s’exécuter de façon optimale dans une procédure stockée
+ Configuration de la sécurité et verrouillage des packages utilisés par une tâche particulière
+ Activation de la gouvernance des ressources (nécessite l’édition Enterprise)

Pour plus d’informations, consultez [gouvernance des ressources pour r](r/resource-governance-for-r-services.md) et [r Package Management pour SQL Server](r/install-additional-r-packages-on-sql-server.md).

## <a name="version-history"></a>Historique des versions

SQL Server 2017 Machine Learning Services est la nouvelle génération de SQL Server 2016 R services, améliorée pour inclure Python. Le tableau suivant est une liste complète de toutes les versions de produit, de la création à la version actuelle. 

| Nom de produit | Version du moteur | Date de publication |
|--------------|---------|--------------|
| SQL Server 2017 Machine Learning Services (en base de données) | R Server 9.2.1 <br/> Python Server 9,2 | Octobre 2017 |
| SQL Server 2017 Machine Learning Server (autonome) | R Server 9.2.1 <br/> Python Server 9,2 | Octobre 2017 |
| SQL Server 2016 R services (en base de données) | R Server 9,1  | Juillet 2017  |
| SQL Server 2016 R Server (autonome)  |  R Server 9,1 | Juillet 2017 |

Pour les versions de package par version, consultez mappage de version dans les [composants Upgrade R et Python](install/upgrade-r-and-python.md#version-map).

## <a name="portability-and-related-products"></a>Portabilité et produits associés

La portabilité de votre code R et Python personnalisé est traitée via la distribution de packages et les interpréteurs intégrés à plusieurs produits. Les packages fournis dans SQL Server sont également disponibles dans plusieurs autres produits et services Microsoft, y compris une version non-SQL appelée [Microsoft machine learning Server](https://docs.microsoft.com/machine-learning-server/). 

Les clients gratuits qui incluent nos interpréteurs R et Python sont [Microsoft R client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) et les [bibliothèques python](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter).

Sur Azure, les packages et interpréteurs R et Python de Microsoft sont également disponibles sur Azure Machine Learning, ainsi que sur les services Azure tels que [HDInsight](https://docs.microsoft.com/azure/hdinsight/r-server/r-server-overview)et les [machines virtuelles Azure](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-azure-vm-on-linux). Le [Data science Virtual Machine](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) comprend une station de travail de développement entièrement équipée avec des outils de plusieurs fournisseurs, ainsi que les bibliothèques et les interpréteurs de Microsoft.

## <a name="see-also"></a>Voir aussi

[Installer SQL Server Machine Learning Services](install/sql-machine-learning-services-windows-install.md)
