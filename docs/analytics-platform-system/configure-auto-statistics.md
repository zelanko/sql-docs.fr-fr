---
title: Statistiques automatiques (Analytique Platform System)
description: Décrit la fonctionnalité de statistiques automatique introduite dans AU7 de système de plateforme Analytique.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
monikerRange: '>= aps-pdw-2016-au7 || = sqlallproducts-allversions'
ms.openlocfilehash: 000a31f76118a3f2acaf702ce5c74c1dd5703422
ms.sourcegitcommit: 3e5f1545e5c6c92fa32e116ee3bff1018ca946a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37107137"
---
# <a name="configure-auto-statistics"></a>Configurer automatiquement les statistiques

Découvrez comment configurer Parallel Data Warehouse pour utiliser automatique des statistiques pour la création et la mise à jour automatiquement les statistiques.  Utiliser cette fonctionnalité pour améliorer les plans de requête et donc améliorer les performances des requêtes.

**S’applique à :** APS (à partir de 2016-AU7)

## <a name="what-are-statistics"></a>Quelles sont les statistiques ?
Statistiques pour l’optimisation des requêtes sont des objets qui contiennent des informations statistiques sur la distribution des valeurs dans une ou plusieurs colonnes d’une table. L’optimiseur de requête utilise ces statistiques pour estimer la cardinalité, ou entraîne de nombre de lignes, dans la requête. Ces estimations de cardinalité permettent à l’optimiseur de requête créer un plan de requête de haute qualité. Par exemple, dans les points d’accès, les utilisations d’optimiseur de requête MPP estimations de cardinalité pour choisir de lecture aléatoire ou répliquer la plus petite des deux tables utilisées dans une clause join et ainsi améliorent les performances de requête.  Pour plus d’informations, consultez [statistiques](../relational-databases/statistics/statistics.md) et [DBCC SHOW_STATISTICS](../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)

## <a name="what-are-auto-statistics"></a>Quelles sont les statistiques automatique ?
Automatique des statistiques sont des statistiques de l’optimiseur de requête crée et met à jour automatiquement pour améliorer le plan de requête. Les statistiques deviennent obsolètes après les chargements, insère, met à jour et les opérations de suppression. Sans automatique des statistiques, vous devez réaliser votre propre analyse pour comprendre les colonnes ont besoin de statistiques et lorsque les statistiques doivent être mis à jour.

Automatique des statistiques inclut les trois paramètres suivants : 

### <a name="autocreatestatistics"></a>AUTO_CREATE_STATISTICS
Lorsque l’option de statistiques de création automatique AUTO_CREATE_STATISTICS est activée, l’optimiseur de requête crée des statistiques sur des colonnes individuelles du prédicat de requête, en fonction des besoins améliorer les estimations de cardinalité pour le plan de requête. Ces statistiques de colonne unique sont créées sur les colonnes où ne figure pas déjà un histogramme au niveau d'un objet de statistiques existant.

### <a name="autoupdatestatistics"></a>AUTO_UPDATE_STATISTICS 
Lorsque l'option de mise à jour automatique des statistiques AUTO_UPDATE_STATISTICS est activée, l'optimiseur de requête détermine si les statistiques sont obsolètes et les met éventuellement à jour lorsqu'elles sont utilisées par une requête. Les statistiques deviennent obsolètes si des opérations d’insertion, de mise à jour, de suppression ou de fusion changent la distribution des données dans la table ou la vue indexée. L'optimiseur de requête détermine si les statistiques sont obsolètes en comptant le nombre de modifications de données depuis la dernière mise à jour des statistiques et en comparant le nombre de modifications à un seuil. Ce seuil est basé sur le nombre de lignes contenues dans la table ou la vue indexée.

### <a name="autoupdatestatisticsasync"></a>AUTO_UPDATE_STATISTICS_ASYNC
L'option de mise à jour asynchrone des statistiques AUTO_UPDATE_STATISTICS_ASYNC détermine si l'optimiseur de requête utilise des mises à jour de statistiques synchrones ou asynchrones. Pour les points d’accès, l’option de mise à jour asynchrone des statistiques est activé par défaut, et l’optimiseur de requête met à jour les statistiques de façon asynchrone. L’option AUTO_UPDATE_STATISTICS_ASYNC s’applique aux objets de statistiques créés pour les index, aux colonnes uniques contenues dans les prédicats de requête et aux statistiques créées à l’aide de l’instruction CREATE STATISTICS.

## <a name="configuration-settings-for-system-administrators"></a>Paramètres de configuration pour les administrateurs système
Après la mise à niveau vers les points d’accès AU7, automatique des statistiques sont activée par défaut. L’administrateur système peut activer ou désactiver automatiquement les statistiques avec le [commutateur de fonctionnalité](appliance-feature-switch.md) option dans le Gestionnaire de Configuration Appliance.  Une fois activé, les utilisateurs peuvent modifier les paramètres de statistiques par base de données.
Changer des valeurs de commutateur de fonctionnalité nécessite un redémarrage du service sur les points d’accès.

## <a name="change-auto-statistics-settings-on-a-database"></a>Modifier les paramètres de statistiques automatique sur une base de données
Lorsque automatique des statistiques sont activée par l’administrateur système, vous pouvez utiliser [ALTER DATABASE (Parallel Data Warehouse)](/sql/t-sql/statements/alter-database-parallel-data-warehouse) pour modifier les paramètres de statistiques sur une base de données. Si le commutateur de fonctionnalité de statistiques automatique est activée par l’administrateur système, les nouvelles bases de données créées après la mise à niveau vers AU7 aura automatique des statistiques est activées. Toutes les bases de données qui existaient avant la mise à niveau vers AU7 possèdent des statistiques automatique désactivés. L’exemple suivant active automatiquement les statistiques sur le myPDW de base de données existante.

```sql
ALTER DATABASE myPDW SET AUTO_CREATE_STATISTICS ON
ALTER DATABASE myPDW SET AUTO_UPDATE_STATISTICS ON 
ALTER DATABASE myPDW SET AUTO_UPDATE_STATISTICS_ASYNC ON
```
 
Option de AUTO_UPDATE STATISTICS_ASYNC fonctionne uniquement si l’option AUTO_UPDATE_STATISTICS est activée.  Par conséquent, les statistiques ne sont pas mis à jour lorsque l’option AUTO_UPDATE_STATISTICS est désactivée (OFF) et AUTO_UPDATE_STATISTICS_ASYNC a la valeur ON. 

### <a name="error-messages"></a>Messages d’erreur
Vous pouvez recevoir le message d’erreur « cette option n’est pas prise en charge dans PDW ».  Cette erreur se produit lorsque l’administrateur système n’a pas activé automatiquement les statistiques, et que vous essayez de définir automatiquement les options de statistiques dans ALTER DATABASE. 

### <a name="limitations-and-restrictions"></a>Limitations et restrictions
Automatique des statistiques ne fonctionnent pas sur les tables externes. 

### <a name="check-the-current-values"></a>Vérifiez les valeurs en cours
La requête suivante retourne les valeurs actuelles des paramètres de statistiques automatique pour toutes les bases de données.

```sql
SELECT NAME
    , IS_AUTO_CREATE_STATS_ON 
    , IS_AUTO_UPDATE_STATS_ON
    , IS_AUTO_UPDATE_STATS_ASYNC_ON
FROM
    sys.databases;
```

Une valeur de retour de 1 signifie que le paramètre se trouve sur, et 0 signifie que le paramètre est désactivé. 

## <a name="next-steps"></a>Étapes suivantes
Pour voir le fonctionnement de vos requêtes, consultez [surveillance des requêtes actives](monitoring-active-queries.md)
