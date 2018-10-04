---
title: Database Suspect Data Page, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event notifications [SQL Server], database mirroring
- suspect_pages system table
- database mirroring [SQL Server], event notifications
- Database Suspect Data Page event class
ms.assetid: 098e1443-a8a0-425c-9311-0a479b1370ed
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 50ee8a83c87ec6f2b14ac07caa77774b7a7c2d15
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137901"
---
# <a name="database-suspect-data-page-event-class"></a>classe d'événements Database Suspect Data Page
  La classe d’événements **Database Suspect Data Page** indique qu’une page a été ajoutée à la table [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) dans la base de données [msdb](../databases/msdb-database.md). Incluez cette classe d'événements dans les traces qui surveillent l'occurrence de pages suspectes.  
  
> [!NOTE]  
>  Cet événement est émis de façon asynchrone à partir de l’insertion d’une ligne correspondante dans la table **suspect_pages** . Par conséquent, un travail à l’écoute de cet événement peut ne pas trouver immédiatement l’entrée **suspect_pages** correspondante.  
  
 Lorsque la classe d'événements **Database Suspect Data Page** est incluse au sein d’une trace, la surcharge relative est peu élevée. La surcharge peut être plus élevée si le nombre de pages suspectes augmente, par exemple, si un lecteur de disque rencontre des problèmes.  
  
## <a name="database-suspect-data-page-event-class-data-columns"></a>Colonnes de données de la classe d'événements Database Suspect Data Page  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**Int**|ID de la base de données pour laquelle l'événement de page suspecte a été déclenché. Il correspond à la valeur de la colonne **database_id** de la table **suspect_pages** .|3|Oui|  
|**EventClass**|**Int**|Le type de l'événement est 213.|27|non|  
|**EventSequence**|**Int**|Séquence de la classe d'événements dans le lot.|51|non|  
|**SPID**|**Int**|ID de la tâche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui a rencontré la page suspecte.|12|Oui|  
|**StartTime**|**datetime**|Heure à laquelle l'événement s'est produit.|14|Oui|  
|**ObjectID**|**Int**|ID du fichier de base de données qui contient la page suspecte. Il correspond à la valeur de la colonne **file_id** de la table **suspect_pages** .|22|Oui|  
|**ObjectID2**|**Int**|ID de la page suspecte dans le fichier. Il correspond à la valeur de la colonne **page_id** de la table **suspect_pages** .|56|Oui|  
|**Erreur**|**Int**|Type de l’erreur rencontrée. Il s’agit de la même valeur que celle de l’élément **event_type** de la page dans la table **suspect_pages** .|31|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Gérer la table suspect_pages &#40;SQL Server&#41;](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
