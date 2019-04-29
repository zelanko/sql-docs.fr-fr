---
title: Performance, catégorie d’événement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Performance event category
- Performance event category [SQL Server]
- event classes [SQL Server], Performance event category
ms.assetid: 708f3585-d8be-4980-bbff-672d7c59397e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b7f387145077e5a562279b6c72bc0f7eefadde36
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63023306"
---
# <a name="performance-event-category"></a>Performance, catégorie d'événements
  Utilisez les classes d’événements **Performance** pour surveiller les classes d’événements **Showplan** et celles produites par l’exécution des opérateurs du langage de manipulation des données SQL (DML, Data Manipulation Language).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Classe d'événements Auto Stats](auto-stats-event-class.md)|Indique qu'une mise à jour automatique des statistiques d'index et de colonne a eu lieu.|  
|[Degree of Parallelism &#40;7.0 Insert&#41;, classe d’événements](degree-of-parallelism-7-0-insert-event-class.md)|Indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a exécuté une instruction SELECT, INSERT, UPDATE ou DELETE en utilisant un plan série ou parallèle. Le nombre d'unités centrales utilisées pour effectuer l'opération est également indiqué.|  
|[Classe d'événements Performance Statistics](performance-statistics-event-class.md)|Contrôle les performances des requêtes exécutées.|  
|[Classe d'événements Showplan All](showplan-all-event-class.md)|Identifie des opérateurs **Showplan** dans une instruction SQL.|  
|[Classe d'événements Showplan All for Query Compile](showplan-all-for-query-compile-event-class.md)|Affiche des données temporelles de compilation pour des opérateurs **Showplan** .|  
|[Classe d'événements Showplan Statistics Profile](showplan-statistics-profile-event-class.md)|Affiche le coût estimé d'une requête.|  
|[Classe d'événements Showplan XML](showplan-xml-event-class.md)|Identifie les opérateurs **Showplan** dans une instruction SQL. La classe d'événements stocke chaque événement sous la forme d'un document XML bien défini.|  
|[Classe d'événements Showplan XML for Query Compile](showplan-xml-for-query-compile-event-class.md)|Affiche des données temporelles de compilation pour des opérateurs **Showplan** au format XML.|  
|[Classe d'événements Showplan XML Statistics Profile](showplan-xml-statistics-profile-event-class.md)|Identifie les opérateurs **Showplan** associés à une instruction SQL. La sortie est un document XML.|  
|[Classe d'événements SQL:FullTextQuery](sql-fulltextquery-event-class.md)|Indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a exécuté une requête de texte intégral.|  
|[Classe d'événements Plan Guide Successful](plan-guide-successful-event-class.md)|Indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a pu produire un plan d'exécution pour une requête ou un lot qui contenait un repère de plan.|  
|[Classe d'événements Plan Guide Unsuccessful](plan-guide-unsuccessful-event-class.md)|Indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas pu produire un plan d'exécution pour une requête ou un lot qui contenait un repère de plan.|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../extended-events/extended-events.md)  
  
  
