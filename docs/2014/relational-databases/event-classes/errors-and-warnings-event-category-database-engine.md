---
title: Catégorie d’événements Erreurs et avertissements (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Errors and Warnings event category [SQL Server]
- SQL Server event classes, Errors and Warnings event category
- event classes [SQL Server], Errors and Warnings event category
ms.assetid: 249c19b5-af68-4433-80f6-337395176641
author: stevestein
ms.author: sstein
ms.openlocfilehash: d55f37f5401f60ddfeec340af1ae6d532eb6ad01
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85029781"
---
# <a name="errors-and-warnings-event-category-database-engine"></a>Catégorie d'événements Erreurs et avertissements (moteur de base de données)
  La catégorie d’événements **Erreurs et avertissements** contient des événements généraux d’erreurs et d’avertissements.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Attention, classe d’événements](attention-event-class.md)|Indique qu’un événement **Attention** s’est produit.|  
|[Background Job Error, classe d’événements](background-job-error-event-class.md)|Indique qu'un travail en arrière-plan s'est terminé anormalement.|  
|[Bitmap Warning, classe d’événements](bitmap-warning-event-class.md)|Indique que le filtrage Bitmap a été désactivé dans une requête.|  
|[Blocked Process Report, classe d’événements](blocked-process-report-event-class.md)|Indique qu'une tâche a été bloquée plus longtemps qu'une période spécifiée.|  
|[CPU Threshold Exceeded, classe d’événements](cpu-threshold-exceeded-event-class.md)|Indique que Resource Governor détecte une requête qui dépasse le seuil de l'UC spécifié.|  
|[ErrorLog, classe d’événements](errorlog-event-class.md)|Indique que les événements d'erreurs ont été enregistrés dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Classe d'événements EventLog](eventlog-event-class.md)|Indique que les événements ont été consignés dans le journal des événements de Windows.|  
|[Classe d'événements Exception](exception-event-class.md)|Indique qu'une exception s'est produite dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Classe d'événements Exchange Spill](exchange-spill-event-class.md)|Indique que des tampons de communication dans un plan de requête parallèle ont été écrits dans la base de données tempdb.|  
|[Classe d'événements Execution Warnings](execution-warnings-event-class.md)|Indique que des avertissements d'allocation de mémoire se sont produits lors de l'exécution d'une instruction ou d'une procédure stockée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Classe d'événements Hash Warning](hash-warning-event-class.md)|Indique qu'une récurrence ou une interruption de hachage s'est produite pendant une opération de hachage.|  
|[Classe d'événements Missing Column Statistics](missing-column-statistics-event-class.md)|Indique que des statistiques de colonne qui auraient pu être utiles pour l'optimiseur ne sont pas disponibles.|  
|[Classe d'événements Missing Join Predicate](missing-join-predicate-event-class.md)|Indique qu'une requête en cours d'exécution est sans prédicat de jointure.|  
|[Classe d'événements Sort Warnings](sort-warnings-event-class.md)|Indique que des opérations de tri ne peuvent pas être effectuées en mémoire.|  
|[User Error Message, classe d’événements](user-error-message-event-class.md)|Affiche des messages d'erreur vus par l'utilisateur.|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
