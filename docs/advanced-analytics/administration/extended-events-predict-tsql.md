---
title: Surveiller T-SQL avec événements étendus
description: Découvrez comment utiliser des événements étendus pour surveiller et résoudre les problèmes des instructions T-SQL de prédiction dans SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 958ac3e24a9deec231e7fd4d5da14477d693f4de
ms.sourcegitcommit: fd3e81c55745da5497858abccf8e1f26e3a7ea7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71714303"
---
# <a name="monitor-predict-t-sql-statements-with-extended-events-in-sql-server-machine-learning-services"></a>Surveiller les instructions T-SQL de prédiction avec des événements étendus dans SQL Server Machine Learning Services

Découvrez comment utiliser des événements étendus pour surveiller et résoudre les problèmes des instructions T-SQL de [prédiction](../../t-sql/queries/predict-transact-sql.md) dans SQL Server machine learning services.

## <a name="table-of-extended-events"></a>Tableau des événements étendus

Les événements étendus suivants sont disponibles dans toutes les versions de SQL Server qui prennent en charge l’instruction T-SQL [Predict](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) . 

|name |object_type|description| 
|----|----|----|
|predict_function_completed |événement  |Répartition du temps d’exécution builtin|
|predict_model_cache_hit |événement|Se produit lorsqu’un modèle est récupéré à partir du cache de modèle de fonction PREDICT. Utilisez cet événement avec d’autres événements predict_model_cache_ * pour résoudre les problèmes provoqués par le cache du modèle de fonction PREDICT.|
|predict_model_cache_insert |événement  |   Se produit lorsqu’un modèle est inséré dans le cache du modèle de fonction PREDICT. Utilisez cet événement avec d’autres événements predict_model_cache_ * pour résoudre les problèmes provoqués par le cache du modèle de fonction PREDICT.    |
|predict_model_cache_miss   |événement|Se produit lorsqu’un modèle est introuvable dans le cache du modèle de fonction PREDICT. Des occurrences fréquentes de cet événement peuvent indiquer que SQL Server a besoin de davantage de mémoire. Utilisez cet événement avec d’autres événements predict_model_cache_ * pour résoudre les problèmes provoqués par le cache du modèle de fonction PREDICT.|
|predict_model_cache_remove |événement| Se produit lorsqu’un modèle est supprimé du cache de modèle pour la fonction PREDICT. Utilisez cet événement avec d’autres événements predict_model_cache_ * pour résoudre les problèmes provoqués par le cache du modèle de fonction PREDICT.|

## <a name="query-for-related-events"></a>Requête pour les événements connexes

Pour afficher la liste de toutes les colonnes retournées pour ces événements, exécutez la requête suivante dans SQL Server Management Studio:

```sql
SELECT * 
FROM sys.dm_xe_object_columns 
WHERE object_name LIKE `predict%'
```

## <a name="examples"></a>Exemples

Pour capturer des informations sur les performances d’une session de notation à l’aide de PREDICT:

1. Créez une nouvelle session d’événements étendus à l’aide d’Management Studio ou d’un autre [outil](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools)pris en charge.
2. Ajoutez les événements `predict_function_completed` et `predict_model_cache_hit` à la session.
3. Démarrez la session d’événements étendus.
4. Exécutez la requête qui utilise PREDICT.

Dans les résultats, passez en revue les colonnes suivantes:

+ La valeur pour `predict_function_completed` indique le temps passé par la requête lors du chargement du modèle et de la notation.
+ La valeur booléenne pour `predict_model_cache_hit` indique si la requête a utilisé ou non un modèle mis en cache. 

### <a name="native-scoring-model-cache"></a>Cache du modèle de notation natif

Outre les événements spécifiques à prédire, vous pouvez utiliser les requêtes suivantes pour obtenir plus d’informations sur le modèle mis en cache et l’utilisation du cache:

Afficher le cache du modèle de calcul de score natif:

```sql
SELECT *
FROM sys.dm_os_memory_clerks
WHERE type = 'CACHESTORE_NATIVESCORING';
```

Affichez les objets dans le cache du modèle:

```sql
SELECT *
FROM sys.dm_os_memory_objects
WHERE TYPE = 'MEMOBJ_NATIVESCORING';
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les événements étendus (parfois appelés XEvents) et sur le suivi des événements dans une session, consultez les articles suivants :

+ [Surveiller les scripts Python et R avec des événements étendus dans SQL Server Machine Learning Services](extended-events.md)
+ [Architecture et concepts des événements étendus](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)
+ [Configurer la capture d’événements dans SSMS](https://docs.microsoft.com/sql/relational-databases/extended-events/quick-start-extended-events-in-sql-server)
+ [Gérer les sessions d’événements dans l’Explorateur d’objets](https://docs.microsoft.com/sql/relational-databases/extended-events/manage-event-sessions-in-the-object-explorer)
