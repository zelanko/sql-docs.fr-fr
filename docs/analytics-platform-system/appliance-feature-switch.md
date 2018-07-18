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
ms.openlocfilehash: b06c715549cd1c9cf464a13b03790764ebf40b97
ms.sourcegitcommit: 3e5f1545e5c6c92fa32e116ee3bff1018ca946a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37107177"
---
#<a name="appliance-feature-switch"></a>Commutateur de fonctionnalité d’appliance
Le **commutateur de fonctionnalité** page affiche des informations sur les commutateurs de deux fonctionnalité qui sont introduites dans le système 2016 AU7 Analytique Platform. Utilisez cette page pour mettre à jour ou activer/désactiver les fonctionnalités et les paramètres d’Analytique Platform System. Modification des valeurs de commutateur de fonctionnalité nécessite un redémarrage du service.

![Commutateur de fonctionnalité Appliance DWConig](media/feature-switch/SQL_Server_PDW_DWConfig_feature_switch.png "DWConig Appliance fonctionnalité commutateur") 

##<a name="autostatsenabled-switch"></a>Commutateur de AutoStatsEnabled
Contrôle la fonctionnalité de statistiques automatique. Cette fonctionnalité de commutateur est définie sur true par défaut après la mise à niveau vers AU7. Toute base de données créée après que la mise à niveau hérite de la création automatique et mise à jour asynchrone des statistiques. Pour les bases de données existantes, les administrateurs de base de données peuvent activer des automatique des statistiques avec [Modifier la base de données] (/ sql/t-sql/statements/alter-database-parallel-data-warehouse). Pour plus d’informations sur les statistiques, consultez [statistiques](../relational-databases/statistics/statistics.md).

##<a name="dmsprocessstopmessagetimeoutinseconds-switch"></a>Commutateur de DmsProcessStopMessageTimeoutInSeconds
Contrôle le délai d’attente de Service de déplacement des données (DMS) pour synchroniser sur un système occupé lors de l’annulation d’une requête impliquant le déplacement des données. Mise à jour vers AU7 définit cette valeur à 900 secondes (15 minutes) par défaut. La plage valide est 0 et 3 600 secondes.
