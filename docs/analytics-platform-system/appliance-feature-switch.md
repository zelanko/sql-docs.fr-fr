---
title: Commutateur de fonctionnalité (Analytique Platform System)
description: Affiche des informations sur les commutateurs de deux fonctionnalité qui sont introduites dans AU7 de système de plateforme Analytique.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
monikerRange: '>= aps-pdw-2016-au7 || = sqlallproducts-allversions'
ms.openlocfilehash: b4fa05bcc33c9a305253563e40bf071338f19461
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63276148"
---
# <a name="appliance-feature-switches"></a>Commutateurs de fonctionnalité d’appliance

Le **commutateur de fonctionnalité** page affiche des informations sur les commutateurs de fonctionnalité ont été introduits dans Analytique Platform System AU7 et versions ultérieures. Utilisez cette page de configuration pour mettre à jour ou activer/désactiver les fonctionnalités et les paramètres d’Analytique Platform System.

> [!NOTE]
> Modifications apportées aux valeurs de commutateur de fonctionnalité requièrent un redémarrage du service.

![Commutateur de fonctionnalité Appliance DWConfig](media/feature-switch/SQL_Server_PDW_DWConfig_feature_switch.png "commutateur de fonctionnalité des appliances DWConfig")

## <a name="autostatsenabled"></a>AutoStatsEnabled

Contrôle la fonctionnalité de statistiques automatique. Cette fonctionnalité de commutateur est définie sur true par défaut après la mise à niveau vers AU7. Toute base de données créée après que la mise à niveau hérite de la création automatique et mise à jour asynchrone des statistiques. Pour les bases de données existantes, les administrateurs de base de données peuvent activer des automatique des statistiques avec [ALTER DATABASE (Parallel Data Warehouse)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw). Pour plus d’informations sur les statistiques, consultez [statistiques](../relational-databases/statistics/statistics.md).

## <a name="maxdopforinsertqueries"></a>MaxDOPForInsertQueries

Vous permet de choisir les paramètres maxdop supérieures à 1 pour les opérations insert/select. Options pour ce paramètre sont 0, 1, 2 et 4, valeur par défaut est 1.

## <a name="optimizecommonsubexpressions"></a>OptimizeCommonSubExpressions

Améliore les performances des requêtes en éliminant le déplacement des données pour une sous-expression commune dans l’optimiseur de requête SQL. Vous pouvez trouver une explication détaillée de cette fonctionnalité [ici](common-sub-expression-elimination.md).

## <a name="usecatalogqueries"></a>UseCatalogQueries

À l’aide des objets de catalogue pour certains appels de métadonnées au lieu d’utiliser SMO a montré l’amélioration des performances. La valeur true par défaut dans CU7.1, ce commutateur contrôle ce comportement.

## <a name="dmsprocessstopmessagetimeoutinseconds"></a>DmsProcessStopMessageTimeoutInSeconds

Contrôle le délai d’attente de Service de déplacement des données (DMS) pour synchroniser sur un système occupé lors de l’annulation d’une requête impliquant le déplacement des données. Mise à jour vers AU7 définit cette valeur à 900 secondes (15 minutes) par défaut. La plage valide est 0 - 3 600 secondes.
