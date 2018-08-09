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
ms.openlocfilehash: d9657b1433b0647d7165cb427da6333c0a325583
ms.sourcegitcommit: 0cda14b1151d9bce1253d96dea038c038484f07a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39400922"
---
#<a name="appliance-feature-switch"></a>Commutateur de fonctionnalité d’appliance
Le **commutateur de fonctionnalité** page affiche des informations sur les commutateurs de deux fonctionnalité qui sont introduites dans le système 2016 AU7 Analytique Platform. Utilisez cette page pour mettre à jour ou activer/désactiver les fonctionnalités et les paramètres d’Analytique Platform System. Modification des valeurs de commutateur de fonctionnalité nécessite un redémarrage du service.

![Commutateur de fonctionnalité Appliance DWConig](media/feature-switch/SQL_Server_PDW_DWConfig_feature_switch.png "DWConig Appliance fonctionnalité commutateur") 

##<a name="autostatsenabled-switch"></a>Commutateur de AutoStatsEnabled
Contrôle la fonctionnalité de statistiques automatique. Cette fonctionnalité de commutateur est définie sur true par défaut après la mise à niveau vers AU7. Toute base de données créée après que la mise à niveau hérite de la création automatique et mise à jour asynchrone des statistiques. Pour les bases de données existantes, les administrateurs de base de données peuvent activer des automatique des statistiques avec [ALTER DATABASE (Parallel Data Warehouse)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw). Pour plus d’informations sur les statistiques, consultez [statistiques](../relational-databases/statistics/statistics.md).

##<a name="dmsprocessstopmessagetimeoutinseconds-switch"></a>Commutateur de DmsProcessStopMessageTimeoutInSeconds
Contrôle le délai d’attente de Service de déplacement des données (DMS) pour synchroniser sur un système occupé lors de l’annulation d’une requête impliquant le déplacement des données. Mise à jour vers AU7 définit cette valeur à 900 secondes (15 minutes) par défaut. La plage valide est 0 et 3 600 secondes.
