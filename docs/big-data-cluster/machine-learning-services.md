---
title: Machine Learning Services (Python, R)
titleSuffix: SQL Server Big Data Clusters
description: Découvrez comment exécuter des scripts Python et R sur l’instance maître de clusters Big Data SQL Server avec Machine Learning Services.
author: dphansen
ms.author: davidph
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
ms.openlocfilehash: dd8e1b948d259b4c233aebcb3614dea5b3e72129
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664133"
---
# <a name="run-python-and-r-scripts-with-machine-learning-services-on-sql-server-big-data-clusters"></a>Exécuter des scripts Python et R avec Machine Learning Services sur des clusters Big Data SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Vous pouvez exécuter des scripts Python et R sur l’instance maître de [clusters Big Data SQL Server](big-data-cluster-overview.md) avec [Machine Learning Services](../machine-learning/index.yml).

> [!NOTE]
> Vous pouvez également exécuter du code Java sur l’instance maître avec les [extensions de langage SQL Server](../language-extensions/language-extensions-overview.md). Suivez les étapes ci-dessous pour activer également les extensions de langage.

## <a name="enable-machine-learning-services"></a>Activer Machine Learning Services

Machine Learning Services est installé par défaut sur les clusters Big Data et nécessite une installation distincte.

Pour activer Machine Learning Services, exécutez l’instruction suivante sur l’instance maître :

```sql
EXEC sp_configure 'external scripts enabled', 1
RECONFIGURE WITH OVERRIDE
GO
```

## <a name="enable-always-on-availability-groups"></a>Activer des groupes de disponibilité Always On

Si vous utilisez des clusters Big Data SQL Server avec des [groupes de disponibilité Always On](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md), vous devez effectuer quelques étapes supplémentaires pour activer Machine Learning Services.

1. Connectez-vous à l’instance maître, puis exécutez l’instruction suivante :

    ```sql
    SELECT @@SERVERNAME
    ```

    Notez le nom du serveur. Dans cet exemple, le nom du serveur pour l’instance maître est **master-2**.

1. Exécutez les commandes `kubectl` suivantes sur chaque réplica du groupe de disponibilité Always On dans le cluster Big Data :

    ```
    kubectl -n bdc expose pod master-0 --port=1533 --name=mymaster-0 --type=LoadBalancer

    kubectl -n bdc expose pod master-1 --port=1533 --name=mymaster-1 --type=LoadBalancer

    kubectl -n bdc expose pod master-2 --port=1533 --name=mymaster-2 --type=LoadBalancer
    ```

    Vous devez voir une sortie similaire à ce qui suit :
    
    ```
    service/mymaster-0 exposed

    service/mymaster-1 exposed

    service/mymaster-2 exposed
    ```

1. Connectez-vous à chaque point de terminaison de réplica maître, et activez l’exécution du script.

    Exécutez l’instruction suivante :

    ```sql
    EXEC sp_configure 'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    GO
    ```

Vous êtes désormais prêt à exécuter les scripts Python et R sur l’instance maître de clusters Big Data. Consultez les guides de démarrage rapide ci-dessous pour exécuter votre premier script.

## <a name="next-steps"></a>Étapes suivantes

+ [Démarrage rapide : Créer et exécuter des scripts Python simples avec SQL Server Machine Learning Services](../machine-learning/tutorials/quickstart-python-create-script.md)
+ [Démarrage rapide : Créer un modèle prédictif doté d’un score en Python avec SQL Server Machine Learning Services](../machine-learning/tutorials/quickstart-python-train-score-model.md)
+ [Démarrage rapide : Créer et exécuter des scripts R simples avec SQL Server Machine Learning Services](../machine-learning/tutorials/quickstart-r-create-script.md)
+ [Démarrage rapide : Créer un modèle prédictif doté d’un score en R avec SQL Server Machine Learning Services](../machine-learning/tutorials/quickstart-r-train-score-model.md)
