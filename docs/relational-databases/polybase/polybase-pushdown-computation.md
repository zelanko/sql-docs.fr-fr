---
title: Calculs pushdown dans PolyBase | Microsoft Docs
ms.date: 04/23/2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: aboke
manager: craigg
monikerRange: '>= sql-server-2016 || =sqlallproducts-allversions'
ms.openlocfilehash: 4cfaa18c314358c290fb06cfad23527a42e0369b
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67731137"
---
# <a name="pushdown-computations-in-polybase"></a>Calculs pushdown dans PolyBase

## <a name="dmv"></a>Vue de gestion dynamique

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Le calcul pushdown améliore les performances des requêtes sur votre cluster Hadoop.

## <a name="enable-pushdown"></a>Activer le calcul pushdown

Les étapes d’activation du calcul pushdown sont décrites dans l’article suivant :

[Activer le calcul pushdown dans Hadoop](polybase-configure-hadoop.md#pushdown)

## <a name="select-a-subset-of-rows"></a>Sélectionner un sous-ensemble de lignes

Utilisez une poussée vers le bas de prédicat pour améliorer les performances d’une requête qui sélectionne un sous-ensemble de lignes d’une table externe.

Dans cet exemple, SQL Server 2016 lance un travail MapReduce pour récupérer les lignes qui correspondent au prédicat `customer.account_balance < 200000` sur Hadoop. Comme la requête peut s’effectuer correctement sans analyser toutes les lignes de la table, seules les celles qui répondent aux critères du prédicat sont copiées sur SQL Server. Cette opération permet de gagner un temps considérable et nécessite moins d’espace de stockage temporaire quand le nombre de soldes clients inférieur à < 200000 est faible par rapport au nombre de clients ayant des soldes de compte supérieurs à 200000.

```sql
SELECT * FROM customer WHERE customer.account_balance < 200000
SELECT * FROM SensorData WHERE Speed > 65;  
```

### <a name="select-a-subset-of-columns"></a>Sélectionner un sous-ensemble de colonnes

Utilisez une poussée vers le bas de prédicat pour améliorer les performances d’une requête qui sélectionne un sous-ensemble de colonnes d’une table externe.

Dans cette requête, SQL Server lance une tâche Map/Reduce pour prétraiter le fichier texte délimité Hadoop afin que seules les données pour les deux colonnes, customer.name et customer.zip_code, soient copiées dans SQL Server PDW.

```sql
SELECT customer.name, customer.zip_code FROM customer WHERE customer.account_balance < 200000
```

### <a name="pushdown-for-basic-expressions-and-operators"></a>Poussée vers le bas pour les opérateurs et expressions de base

SQL Server autorise les opérateurs et expressions de base suivants pour une poussée vers le bas de prédicat.

+ Opérateurs de comparaison binaire (\<, >, =, !=, <>, >=, <=) pour les valeurs numériques, d’heure et de date.

+ Opérateurs arithmétiques (+, -, *, /, %).

+ Opérateurs logiques (AND, OR).

+ Opérateurs unaires (NOT, IS NULL, IS NOT NULL).

Les opérateurs BETWEEN, NOT, IN et LIKE peuvent être poussés vers le bas. Le comportement réel dépend de la façon dont l’optimiseur de requête réécrit les expressions des opérateurs sous la forme d’une série d’instructions qui utilisent des opérateurs relationnels de base.

La requête de cet exemple comporte plusieurs prédicats pouvant être refoulés vers Hadoop. SQL Server peut placer des travaux MapReduce dans Hadoop pour exécuter le prédicat `customer.account_balance <= 200000`. L’expression `BETWEEN 92656 and 92677` est également constituée d’opérations binaires et logiques qui peuvent être empilées vers Hadoop. Le **AND** logique dans `customer.account_balance and customer.zipcode` est une expression finale.

Étant donnée cette combinaison de prédicats, les travaux MapReduce peuvent exécuter l’ensemble de la clause WHERE. Seules les données qui répondent aux critères SELECT seront recopiées dans SQL Server PDW.

```sql
SELECT * FROM customer WHERE customer.account_balance <= 200000 AND customer.zipcode BETWEEN 92656 AND 92677
```

## <a name="force-pushdown"></a>Forcer la poussée vers le bas

```sql
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65
OPTION (FORCE EXTERNALPUSHDOWN);
```

## <a name="disable-pushdown"></a>Désactiver la poussée vers le bas

```sql
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65
OPTION (DISABLE EXTERNALPUSHDOWN);
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur PolyBase, consultez [Qu’est-ce que PolyBase ?](polybase-guide.md).
