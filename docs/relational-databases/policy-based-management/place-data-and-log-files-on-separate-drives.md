---
title: "Placer les fichiers de données et les fichiers journaux sur des lecteurs distincts | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
caps.latest.revision: "9"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 511c28ed59846bb5c9d82c2a490bf4c5021a80e7
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="place-data-and-log-files-on-separate-drives"></a>Placer les fichiers de données et les fichiers journaux sur des lecteurs distincts
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Cette règle vérifie si les fichiers de données et les fichiers journaux sont placés sur des lecteurs logiques distincts. Si les fichiers de données et les fichiers journaux sont placés sur le même appareil, des problèmes de contention peuvent se produire sur celui-ci et les performances risquent de se dégrader. Lorsque ces fichiers sont placés sur des lecteurs distincts, l'activité E/S peut avoir lieu simultanément pour les fichiers de données et les fichiers journaux.  
  
## <a name="recommendations"></a>Recommandations  
 Lorsque vous créez une base de données, spécifiez des lecteurs distincts pour les fichiers de données et les fichiers journaux. Pour déplacer ces fichiers une fois la base de données créée, cette dernière doit être placée hors connexion. Déplacez les fichiers à l’aide d’une des méthodes suivantes :  
  
> [!NOTE]  
>  Cette stratégie ne permet pas de détecter des périphériques physiques distincts par le biais de points de montage.  
  
-   Restaurez la base de données à partir d'une sauvegarde à l'aide de l'instruction RESTORE DATABASE avec l'option WITH MOVE.  
  
-   Détachez puis attachez la base de données en spécifiant des emplacements distincts pour les unités de données et les unités de journaux.  
  
-   Spécifiez un nouvel emplacement en exécutant l'instruction ALTER DATABASE avec l'option MODIFY FILE, puis en redémarrant l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Déplacer des fichiers de bases de données](../../relational-databases/databases/move-database-files.md)  
  
 [Déplacer des bases de données utilisateur](../../relational-databases/databases/move-user-databases.md)  
  
 [Attacher et détacher une base de données &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
