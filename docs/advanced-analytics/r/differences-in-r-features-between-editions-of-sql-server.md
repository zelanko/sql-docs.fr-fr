---
title: "Disponibilité des fonctionnalités entre différentes éditions de SQL Server Machine - Learning Services | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 16ca6c44b15c9fb7c1983d5a04175ebbade57895
ms.sourcegitcommit: 6b1618aa3b24bf6759b00a820e09c52c4996ca10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2018
---
# <a name="feature-availability-across-editions-of-sql-server-machine-learning-services"></a>Disponibilité des fonctionnalités entre différentes éditions de SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
 Fonctionnalités de machine learning sont disponibles dans SQL Server 2016 et SQL Server 2017. Cet article répertorie les éditions qui fournit la fonctionnalité, décrit les limitations qui s’appliquent dans les éditions spécifiques et répertorie les fonctionnalités disponibles uniquement dans certaines éditions.

 > [!NOTE]
 > En règle générale, l’apprentissage de SQL Server (de-de base de données) n’inclut pas le [à l’Opérationnalisation](https://docs.microsoft.com/machine-learning-server/what-is-operationalization) des fonctionnalités qui sont incluses dans une installation R Server ou une Machine Learning serveur autonome. À l’Opérationnalisation inclut le déploiement du service web et l’hébergement et donc en concurrence pour les mêmes ressources que les autres opérations de SQL Server.
 > 
 > Pour cette raison, nous vous recommandons de l’installation de SQL Server 2016 R Server (autonome) ou SQL Server 2017 Machine Learning Server (autonome) sur un autre serveur physique pour prendre en charge le déploiement de modèles prédictifs comme un service web. 

## <a name="sql-server-2017-machine-learning-services-in-database-and-standalone"></a>SQL Server 2017 Machine Learning Services (de-de base de données) et (autonome)

L’Édition Developer offre des performances équivalentes à celles de l’édition Enterprise. Utilisation de Developer Edition n’est pas prise en charge pour les environnements de production.

|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------|----------|--------|---|------------------------------|-------|
| Interpréteur R & packages propriétaires | Oui | Oui | Non | Non | non | 
| Bibliothèques d’interpréteur & client Python | Oui | Oui | Non | Non | non | 
| Segmentation de données <br/>(grandes quantités de données, dépassant ce qui tient dans la mémoire de processus) | Oui | Non | Non | Non | non |
| Traitement de la montée en puissance parallèle <br/>(plus de 2 processeurs) | Oui | Non | Non | Non | non |
| À l’Opérationnalisation | Oui | Non | Non | Non | non |
| [PRÉDIRE](../../t-sql/queries/predict-transact-sql.md) (fonction) <br/>(effectue [score native](../sql-native-scoring.md) sur un modèle dont l’apprentissage, précédemment enregistré dans le format binaire requis) | Oui | Oui | Oui | Oui | Oui |
| Compatibilité du Client de R | Oui | Oui | Non | Non | non | 
| Microsoft R Open | Oui | Oui | Non | Non | non | 
| Anaconda Python 3.5 | Oui | Oui | Non | Non | non | 

## <a name="sql-server-2016-r-services-in-database-and-r-server-standalone"></a>SQL Server 2016 R Services (de-de base de données) et R Server (autonome)

Disponibilité des fonctionnalités est le même que 2017, moins la prise en charge de Python qui ne fait pas partie de la version 2016 tout d’abord.

## <a name="r-feature-availability-in-azure-sql-database"></a>Disponibilité des fonctionnalités de R dans la base de données SQL Azure
  
Après une version test initial, les Services de R est actuellement **pas** disponibles dans la base de données SQL Azure, en attente d’un développement ultérieur. 

## <a name="performance-expectations-for-enterprise-edition"></a>Attentes en matière de performances de Enterprise Edition

Performances des solutions de machine learning [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est censé dépassent généralement des implémentations à l’aide de R classique, étant donné le même matériel. Car, dans SQL Server, des solutions R peuvent être exécutées à l’aide des ressources du serveur et parfois distribuées à plusieurs processus à l’aide de la **RevoScaleR** fonctions. 

Performances n’a pas été évalué pour les solutions de Python, comme la fonction est toujours en cours de développement, mais certains avantages de la mêmes application sont attendus.

Les utilisateurs pourront également voir des différences considérables des performances et une extensibilité accrues pour la même solution d’apprentissage s’exécuter dans Visual Studio d’Enterprise Edition. Standard Edition. Raisons prennent en charge parallèle traitement, l’augmentation de threads disponibles pour l’apprentissage et de diffusion en continu (ou de segmentation), ce qui permet les fonctions RevoScaleR gérer plus de données que vous pouvez tenir dans la mémoire. 

Toutefois, les performances même sur du matériel identiques peuvent être affectées par de nombreux facteurs en dehors du code R ou Python. Ces facteurs incluent les demandes concurrentes sur les ressources de serveur, le type de plan de requête qui est créé, les modifications de schéma, la nécessité de mettre à jour les statistiques ou en créer un nouveau plan de requête, la fragmentation et bien plus encore. Il est possible qu’une procédure stockée contenant du code R ou Python peut s’exécuter dans les secondes sous une charge de travail, mais prennent en minutes lorsque d’autres services en cours d’exécution.  Par conséquent, nous vous recommandons de surveiller plusieurs aspects des performances du serveur, y compris la mise en réseau pour les contextes de calcul à distance, lors de la mesure des performances d’une machine learning.

Nous recommandons également de configurer [du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md) (disponible dans l’édition Enterprise) pour personnaliser la manière que les travaux de script externe sont classés par priorité ou gérées sous des charges de travail lourd du serveur. Vous pouvez définir des fonctions classifieur pour spécifier la source de la tâche de script externe et de hiérarchiser certaines charges de travail, de limiter la quantité de mémoire utilisée par les requêtes SQL et contrôler le nombre de traitements parallèles utilisées dans une charge de travail.

## <a name="see-also"></a>Voir aussi

+ [Éditions et composants de SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md)
+ [Éditions et composants de SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md)
+ [Obtenir des conseils sur le calcul des données volumineuses dans R (serveur d’apprentissage Machine)](https://docs.microsoft.com/machine-learning-server/r/tutorial-large-data-tips)
