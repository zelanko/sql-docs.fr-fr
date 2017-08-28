---
title: "Récupération d’urgence pour SQL Server sur Linux | Documents Microsoft"
description: 
author: mihaelab
ms.author: mihaelab
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: c75717c8-c677-4033-8ca6-d0ac93aee04d
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 86f41971e06efb767dde336cf93f9224a204176d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="business-continuity-and-database-recovery-sql-server-on-linux"></a>Récupération entreprise la continuité des activités et de la base de données SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

SQL Server sur Linux permet aux organisations d’obtenir un vaste éventail d’objectifs du contrat de niveau de service pour prendre en compte les différents besoins de l’entreprise.

Solutions les plus simples tirer parti des technologies de virtualisation pour atteindre un niveau élevé de résilience contre les défaillances au niveau hôte, la tolérance de panne contre les défaillances matérielles, ainsi que l’élasticité et Maximisation des ressources. Ces systèmes peuvent exécuter localement, dans un cloud privé ou public, ou les environnements hybrides. La forme la plus simple de protection et de récupération d’urgence est la sauvegarde de base de données. Solutions simples disponibles dans SQL Server 2017 RC2 sont les suivantes :

- **Basculement de la machine virtuelle**
    - Résilience contre les échecs au niveau du système d’exploitation et de l’invité
    - Événements planifiées et non planifiées
    - Temps d’arrêt minimum pour les mises à niveau et de mise à jour corrective
    - RTO en minutes


- [**Sauvegarde et restauration**](sql-server-linux-backup-and-restore-database.md) 
    - Protection contre l’altération des données accidentelle ou malveillante
    - Récupération d’urgence
    - RTO en minutes, en heures

Les techniques de récupération d’urgence et haute disponibilité standard fournissent protection au niveau de l’instance associée à une infrastructure fiable de stockage partagé. Pour SQL Server 2017 RC2 standard haute disponibilité comprend :

- [**Cluster de basculement**](sql-server-linux-shared-disk-cluster-configure.md)
    - Protection au niveau instance
    - Basculement et détection de défaillance automatique
    - Résilience contre les défaillances du système d’exploitation et SQL Server
    - RTO en secondes à quelques minutes


## <a name="summary"></a>Résumé

SQL Server 2017 RC2 sur Linux comprend des clusters de virtualisation, de sauvegarde et de restauration et de basculement pour prendre en charge la haute disponibilité et récupération d’urgence. 
