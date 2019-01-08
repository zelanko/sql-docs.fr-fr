---
title: Interroger des serveurs | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- target servers [SQL Server], polling interval
- polling master servers [SQL Server]
- server polling [SQL Server]
- master servers [SQL Server], polling
- polling interval [SQL Server]
ms.assetid: 96f5fd43-3edd-4418-9dd0-4d34e618890e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ae75dc8af9364a619113d2c38071a441e15351be
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52774931"
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
  
-   Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour contrôler les travaux multiserveur ;  
  
-   des procédures stockées de travail qui ne modifient pas les planifications ou les étapes de travail.  
  
 **Pour forcer l'interrogation d'un serveur maître par un serveur cible**  
  
-   [SQL Server Management Studio](force-a-target-server-to-poll-the-master-server.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les événements](manage-events.md)  
  
  
