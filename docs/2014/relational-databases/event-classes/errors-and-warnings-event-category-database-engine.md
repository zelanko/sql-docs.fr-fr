---
title: Catégorie d’événements Erreurs et avertissements (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Errors and Warnings event category [SQL Server]
- SQL Server event classes, Errors and Warnings event category
- event classes [SQL Server], Errors and Warnings event category
ms.assetid: 249c19b5-af68-4433-80f6-337395176641
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 18dfc3fd77742a1c09b23b800fa6b8136168c83b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37302439"
---
# <a name="errors-and-warnings-event-category-database-engine"></a>Catégorie d'événements Erreurs et avertissements (moteur de base de données)
  La catégorie d’événements **Erreurs et avertissements** contient des événements généraux d’erreurs et d’avertissements.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Attention, classe d’événements](attention-event-class.md)|Indique qu’un événement **Attention** s’est produit.|  
|[Background Job Error, classe d’événements](background-job-error-event-class.md)|Indique qu'un travail en arrière-plan s'est terminé anormalement.|  
|[Classe d'événements Bitmap Warning](bitmap-warning-event-class.md)|Indique que le filtrage Bitmap a été désactivé dans une requête.|  
|[Classe d'événements Blocked Process Report](blocked-process-report-event-class.md)|Indique qu'une tâche a été bloquée plus longtemps qu'une période spécifiée.|  
|[CPU Threshold Exceeded, classe d’événements](cpu-threshold-exceeded-event-class.md)|Indique que Resource Governor détecte une requête qui dépasse le seuil de l'UC spécifié.|  
|[Classe d'événements ErrorLog](errorlog-event-class.md)|Indique que les événements d'erreurs ont été enregistrés dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Classe d'événements EventLog](eventlog-event-class.md)|Indique que les événements ont été consignés dans le journal des événements de Windows.|  
|[Classe d'événements Exception](exception-event-class.md)|Indique qu'une exception s'est produite dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Classe d'événements Exchange Spill](exchange-spill-event-class.md)|Indique que des tampons de communication dans un plan de requête parallèle ont été écrits dans la base de données tempdb.|  
|[Classe d'événements Execution Warnings](execution-warnings-event-class.md)|Indique que des avertissements d'allocation de mémoire se sont produits lors de l'exécution d'une instruction ou d'une procédure stockée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Classe d'événements Hash Warning](hash-warning-event-class.md)|Indique qu'une récurrence ou une interruption de hachage s'est produite pendant une opération de hachage.|  
|[Classe d'événements Missing Column Statistics](missing-column-statistics-event-class.md)|Indique que des statistiques de colonne qui auraient pu être utiles pour l'optimiseur ne sont pas disponibles.|  
|[Classe d'événements Missing Join Predicate](missing-join-predicate-event-class.md)|Indique qu'une requête en cours d'exécution est sans prédicat de jointure.|  
|[Classe d'événements Sort Warnings](sort-warnings-event-class.md)|Indique que des opérations de tri ne peuvent pas être effectuées en mémoire.|  
|[Classe d'événements User Error Message](user-error-message-event-class.md)|Affiche des messages d'erreur vus par l'utilisateur.|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
