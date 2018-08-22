---
title: Gestion de la mémoire pour OLTP en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d82f21fa-6be1-4723-a72e-f2526fafd1b6
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1ba49bf6834800a4da450952e94a8474d40f2b5f
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392785"
---
# <a name="managing-memory-for-in-memory-oltp"></a>Gestion de la mémoire pour l'OLTP en mémoire
  Les tables mémoire optimisées nécessitent suffisamment de mémoire pour conserver tous les index et les lignes en mémoire. Dans la mesure où la mémoire est une ressource limitée, il est important de comprendre et de gérer l'utilisation de la mémoire sur votre système. Les rubriques de cette section traitent de scénarios courants d'utilisation et de gestion de la mémoire.  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
|Section|Description|  
|-------------|-----------------|  
|[Estimer les besoins en mémoire des tables mémoire optimisées](../relational-databases/in-memory-oltp/memory-optimized-tables.md)|Estimer les besoins en mémoire d'une table.|  
|[Lier une base de données avec des tables à mémoire optimisée à un pool de ressources](../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)|Procédure pas à pas pour lier une base de données à un pool de ressources.|  
|[Surveiller l’utilisation de la mémoire et résoudre les problèmes connexes](../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)|Outils que vous pouvez utiliser pour surveiller l'utilisation de la mémoire. Couvre également le dépannage si l'utilisation de la mémoire est trop intensive.|  
|[Résoudre les problèmes de mémoire insuffisante](../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md)|Étapes pour récupérer d'une situation d'insuffisance de mémoire.|  
|[Restaurer une base de données et la lier à un pool de ressources](../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md)|Étapes pour restaurer une base de données [!INCLUDE[hek_2](../includes/hek-2-md.md)] et la lier à un pool de ressources nommé.|  
|[Nettoyage de la mémoire dans l’OLTP en mémoire](../relational-databases/in-memory-oltp/in-memory-oltp-garbage-collection.md)|Comprendre comment le garbage collection fonctionne sur les lignes supprimées.|  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
