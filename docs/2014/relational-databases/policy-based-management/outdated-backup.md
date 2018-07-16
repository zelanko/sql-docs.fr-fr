---
title: Sauvegarde obsolète | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 307a4ad0-675a-4f97-9a3c-cedd61bdfae5
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 045400c76e2926660a55906ec8a417f0633ef1d3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37225229"
---
# <a name="outdated-backup"></a>Sauvegarde obsolète
  Cette règle vérifie qu'une base de données dispose de sauvegardes récentes. La planification de sauvegardes régulières est importante pour éviter les pertes de données pouvant résulter de défaillances diverses. La fréquence appropriée de sauvegarde des données dépend du mode de récupération de la base de données, des spécifications métier concernant les pertes de données éventuelles et de la fréquence de mise à jour de la base de données. Dans une base de données fréquemment mise à jour, les risques de perte de travail augmentent relativement vite entre les sauvegardes.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Nous vous recommandons d'effectuer des sauvegardes suffisamment fréquentes pour protéger les bases de données contre les pertes de données.  
  
 Le mode de récupération simple et le mode de récupération complète requièrent tous deux des sauvegardes de données. Dans ces deux modes, vous pouvez compléter vos sauvegardes complètes avec des sauvegardes différentielles de manière à réduire efficacement le risque de perte de données.  
  
 Pour une base de données qui utilise le mode de récupération simple, nous vous recommandons d'effectuer des sauvegardes fréquentes des journaux. Pour une base de données de production qui contient des données très importantes, les sauvegardes de journaux doivent généralement être effectuées toutes les une à quinze minutes.  
  
> [!NOTE]  
>  La méthode recommandée pour planifier les sauvegardes est un plan de maintenance de base de données.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Sauvegarde et restauration des bases de données système &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [Modes de récupération &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md)  
  
 [Créer une sauvegarde différentielle de base de données &#40;SQL Server&#41;](../backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 [Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
 [Plans de maintenance](../maintenance-plans/maintenance-plans.md)  
  
 [Sauvegardes des journaux de transactions &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
