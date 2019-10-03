---
title: Gérer les charges de travail Python et R avec Resource Governor
description: Découvrez comment utiliser Resource Governor pour gérer l’allocation de ressources de processeur, d’e/s physique et de mémoire pour les charges de travail Python et R dans SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/02/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 9000ab8bb15e8f9910b8b780aa38d134fa984032
ms.sourcegitcommit: af5e1f74a8c1171afe759a4a8ff2fccb5295270a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71823543"
---
# <a name="manage-python-and-r-workloads-with-resource-governor-in-sql-server-machine-learning-services"></a>Gérer les charges de travail Python et R avec Resource Governor dans SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Découvrez comment utiliser [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) pour gérer l’allocation de ressources de processeur, d’e/s physique et de mémoire pour les charges de travail Python et R dans SQL Server machine learning services.

Les algorithmes d’apprentissage automatique dans Python et R sont généralement gourmands en ressources de calcul. En fonction des priorités de votre charge de travail, vous devrez peut-être augmenter ou diminuer les ressources disponibles pour Machine Learning Services.

Pour plus d’informations générales, consultez [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).

> [!NOTE] 
> Resource Governor est une fonctionnalité Enterprise Edition.

## <a name="default-allocations"></a>Allocations par défaut

Par défaut, les runtimes de script externes pour Machine Learning sont limités à 20% de la mémoire totale de l’ordinateur. Cela dépend de votre système, mais en général, cette limite peut s’avérer inadaptée pour des tâches de Machine Learning importantes telles que l’apprentissage d’un modèle ou la prédiction de nombreuses lignes de données. 

## <a name="manage-resources-with-resource-governor"></a>Gérer les ressources avec Resource Governor
 
Par défaut, les processus externes utilisent jusqu’à 20% de la mémoire totale de l’ordinateur hôte sur le serveur local. Vous pouvez modifier le pool de ressources par défaut pour apporter des modifications à l’ensemble du serveur, avec des processus R et Python qui utilisent la capacité que vous mettez à disposition des processus externes.

Vous pouvez également créer des **pools de ressources externes**personnalisés, avec des classifieurs et des groupes de charges de travail associés, pour déterminer l’allocation des ressources pour les demandes provenant de programmes spécifiques, d’hôtes ou d’autres critères que vous fournissez. Un pool de ressources externe est un type de pool de ressources [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] introduit dans pour aider à gérer les processus R et Python externes au moteur de base de données.

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
  
## <a name="next-steps"></a>Étapes suivantes

+ [Créer un pool de ressources pour Machine Learning](create-external-resource-pool.md)
+ [Pools de ressources de Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
