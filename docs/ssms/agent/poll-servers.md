---
title: Interroger des serveurs | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- target servers [SQL Server], polling interval
- polling master servers [SQL Server]
- server polling [SQL Server]
- master servers [SQL Server], polling
- polling interval [SQL Server]
ms.assetid: 96f5fd43-3edd-4418-9dd0-4d34e618890e
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d45f50c0ac7a211f00fbdb1b0b08245c474bebf1
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="poll-servers"></a>Interroger des serveurs
Lorsqu'une administration multiserveur est mise en œuvre, les serveurs cibles contactent périodiquement le serveur maître pour transférer des informations sur les travaux ayant été exécutés et pour télécharger de nouveaux travaux. Le processus de contact du serveur maître se nomme *interrogation de serveur* et intervient selon *une fréquence d’interrogation*spécifique.  
  
## <a name="polling-intervals"></a>Fréquences d'interrogation  
La fréquence d'interrogation (une minute par défaut) contrôle à quelle fréquence le serveur cible se connecte au serveur maître pour télécharger des instructions et transférer les résultats d'exécution d'un travail.  
  
Quand un serveur cible interroge le serveur maître, il lit les opérations attribuées au serveur cible à partir de la table **sysdownloadlist** de la base de données **msdb** . Ces opérations contrôlent les travaux multiserveur et différents aspects du comportement du serveur cible. La suppression, l'insertion, le démarrage d'un travail et la mise à jour de la fréquence d'interrogation du serveur cible sont des exemples d'opérations.  
  
Les opérations sont publiées dans la table **sysdownloadlist** de l’une des manières suivantes :  
  
-   Explicitement au moyen de la procédure stockée **sp_post_msx_operation**  
  
-   Implicitement au moyen d'autres procédures stockées de travail  
  
Si vous utilisez des procédures stockées de travail pour modifier les planifications ou les étapes d'un travail multiserveur, ou bien des objets SQL-DMO pour contrôler des travaux multiserveur, vous devez soumettre la commande suivante après la modification des planifications ou des étapes d'un travail multiserveur :  
  
```  
EXECUTE msdb.dbo.sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
La soumission de cette commande maintient les serveurs cibles synchronisés avec la définition du travail en cours.  
  
Il n'est pas nécessaire de publier les opérations de manière explicite si vous utilisez :  
  
-   Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] pour contrôler les travaux multiserveur ;  
  
-   des procédures stockées de travail qui ne modifient pas les planifications ou les étapes de travail.  
  
**Pour forcer l'interrogation d'un serveur maître par un serveur cible**  
  
-   [SQL Server Management Studio](../../ssms/agent/force-a-target-server-to-poll-the-master-server.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/085deef8-2709-4da9-bb97-9ab32effdacf)  
  
## <a name="see-also"></a>Voir aussi  
[Gérer les événements](../../ssms/agent/manage-events.md)  
  
