---
title: Gouvernance des ressources pour l’exécution de scripts R et Python
description: Allouez de la mémoire RAM, du processeur et des e/s pour les charges de travail R et Python sur SQL Server instance du moteur de base de données.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 55a83e7e63a4e43afe1168aab3307f2806a55fca
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715263"
---
# <a name="resource-governance-for-machine-learning-in-sql-server"></a>Gouvernance des ressources pour Machine Learning dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

La science des données et les algorithmes de Machine Learning sont gourmands en calculs. En fonction des priorités de la charge de travail, vous devrez peut-être augmenter les ressources disponibles pour la science des données ou réduire la réapprovisionnement si l’exécution des scripts R et Python diminue les performances des autres services exécutés simultanément. 

Lorsque vous devez rééquilibrer la distribution des ressources système sur plusieurs charges de travail, vous pouvez utiliser [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) pour allouer le processeur, les e/s physiques et les ressources mémoire consommées par les runtimes externes pour R et Python. Si vous décalez des allocations de ressources, n’oubliez pas que vous devrez peut-être également réduire la quantité de mémoire réservée pour les autres charges de travail et services. 

> [!NOTE] 
> Resource Governor est une fonctionnalité Enterprise Edition.

## <a name="default-allocations"></a>Allocations par défaut

Par défaut, les runtimes de script externes pour Machine Learning sont limités à 20% de la mémoire totale de l’ordinateur. Cela dépend de votre système, mais en général, cette limite peut s’avérer inadaptée pour des tâches de Machine Learning importantes telles que l’apprentissage d’un modèle ou la prédiction de nombreuses lignes de données. 

## <a name="use-resource-governor-to-control-resourcing"></a>Utiliser Resource Governor pour contrôler la réapprovisionnement
 
Par défaut, les processus externes utilisent jusqu’à 20% de la mémoire totale de l’ordinateur hôte sur le serveur local. Vous pouvez modifier le pool de ressources par défaut pour apporter des modifications à l’ensemble du serveur, avec des processus R et Python qui utilisent la capacité que vous mettez à disposition des processus externes.

Vous pouvez également créer des pools de *ressources externes*personnalisés, avec des classifieurs et des groupes de charges de travail associés, pour déterminer l’allocation des ressources pour les demandes provenant de programmes spécifiques, d’hôtes ou d’autres critères que vous fournissez. Un pool de ressources externe est un type de pool de ressources [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] introduit dans pour aider à gérer les processus R et Python externes au moteur de base de données.

1. [Activer la gouvernance des ressources](https://docs.microsoft.com/sql/relational-databases/resource-governor/enable-resource-governor) (désactivé par défaut).

2. Exécutez [créer un pool de ressources externes](https://docs.microsoft.com/sql/t-sql/statements/create-external-resource-pool-transact-sql) pour créer et configurer le pool de ressources, suivi de [ALTER RESOURCE GOVERNOR](https://docs.microsoft.com/sql/t-sql/statements/alter-resource-governor-transact-sql) pour l’implémenter.

3. Créez un groupe de charge de travail pour les allocations granulaires, par exemple entre la formation et le score.

4. Créez un classifieur pour intercepter les appels pour le traitement externe.

5. Exécuter des requêtes et des procédures à l’aide des objets que vous avez créés.

Pour obtenir une procédure pas à pas, consultez [comment créer un pool de ressources pour les scripts R et Python externes](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md) pour obtenir des instructions pas à pas.

Pour obtenir une présentation de la terminologie et des concepts généraux, consultez [Resource Governor pool de ressources](../../relational-databases/resource-governor/resource-governor-resource-pool.md).

## <a name="processes-under-resource-governance"></a>Processus sous gouvernance des ressources
  
 Vous pouvez utiliser un *pool de ressources externes* pour gérer les ressources utilisées par les exécutables suivants sur une instance du moteur de base de données:

+ Rterm. exe lorsqu’il est appelé localement à partir de SQL Server ou appelé à distance avec SQL Server comme contexte de calcul distant
+ Python. exe lorsqu’il est appelé localement à partir d’SQL Server ou appelé à distance avec SQL Server comme contexte de calcul distant
+ BxlServer.exe et les processus satellites
+ Processus satellites lancés par Launchpad, tels que PythonLauncher. dll
  
> [!NOTE]
> La gestion directe du service Launchpad à l’aide de Resource Governor n’est pas prise en charge. Launchpad est un service approuvé qui peut héberger uniquement les lanceurs fournis par Microsoft. Les lanceurs approuvés sont explicitement configurés pour éviter de consommer trop de ressources.
  
## <a name="see-also"></a>Voir aussi

+ [Gérer l’intégration des Machine Learning](../r/managing-and-monitoring-r-solutions.md)
+ [Créer un pool de ressources pour Machine Learning](../r/how-to-create-a-resource-pool-for-r.md)
+ [Pools de ressources de Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
