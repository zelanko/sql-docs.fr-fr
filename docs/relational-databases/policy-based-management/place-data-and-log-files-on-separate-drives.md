---
title: Placer les fichiers de données et les fichiers journaux sur des lecteurs distincts | Microsoft Docs
description: Placez les fichiers de données et les fichiers journaux sur des lecteurs logiques distincts. Les emplacements distincts permettent à chaque activité de se produire en même temps, ce qui améliore les performances SQL.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 7c0ed515a8fe166d4b53fec5750fa3b09a48a06a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716858"
---
# <a name="place-data-and-log-files-on-separate-drives"></a>Placer les fichiers de données et les fichiers journaux sur des lecteurs distincts
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette règle vérifie si les fichiers de données et les fichiers journaux sont placés sur des lecteurs logiques distincts. Si les fichiers de données et les fichiers journaux sont placés sur le même appareil, des problèmes de contention peuvent se produire sur celui-ci et les performances risquent de se dégrader. Lorsque ces fichiers sont placés sur des lecteurs distincts, l'activité E/S peut avoir lieu simultanément pour les fichiers de données et les fichiers journaux.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les bonnes pratiques à l’aide de la gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
