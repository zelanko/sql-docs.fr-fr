---
title: "Points d’arrêt Transact-SQL | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Transact-SQL debugger, breakpoints
ms.assetid: c234430f-bd94-4d0d-9e74-2bf11681fa50
caps.latest.revision: "10"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 76e95825cbe59d6a901234a85306092a810bd982
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="transact-sql-breakpoints"></a>Points d'arrêt Transact-SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Les points d’arrêt spécifient que le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] suspend l’exécution à une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] spécifique. Vous pouvez ensuite consulter l’état des éléments de code à ce point.  
  
## <a name="breakpoints"></a>Points d’arrêt  
 En exécutant le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] , vous pouvez basculer un point d'arrêt sur des instructions spécifiques. Lorsque l'exécution atteint une instruction avec un point d'arrêt, le débogueur suspend l'exécution afin que vous puissiez afficher des informations de débogage telles que les valeurs présentes dans les variables et les paramètres.  
  
 Vous pouvez gérer les points d’arrêt individuellement dans la fenêtre de l’éditeur ou collectivement via la fenêtre **Points d’arrêt** . Vous pouvez modifier des points d'arrêt afin de spécifier des éléments tels que les conditions spécifiques sous lesquelles l'exécution doit être suspendue ou les actions à prendre si le point d'arrêt est exécuté.  
  
## <a name="breakpoint-tasks"></a>Tâches de point d'arrêt  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Explique comment spécifier l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suite à laquelle vous souhaitez que le débogueur soit suspendu.|[Basculer un point d'arrêt](../../relational-databases/scripting/toggle-a-breakpoint.md)|  
|Explique comment désactiver temporairement un point d'arrêt et le réactiver ultérieurement. Explique également comment supprimer un point d'arrêt.|[Activer, désactiver et supprimer des points d'arrêt](../../relational-databases/scripting/enable-disable-and-delete-breakpoints.md)|  
|Explique comment spécifier une condition qui définit si le point d'arrêt entraîne un arrêt d'après l'évaluation d'une expression Transact-SQL spécifiée.|[Spécifier une condition de point d'arrêt](../../relational-databases/scripting/specify-a-breakpoint-condition.md)|  
|Explique comment spécifier un nombre d'accès qui provoque uniquement l'arrêt d'un point d'arrêt lorsque l'instruction contenant le point d'arrêt a été exécutée un nombre spécifié de fois.|[Spécifier un nombre d'accès](../../relational-databases/scripting/specify-a-hit-count.md)|  
|Explique comment spécifier un filtre qui provoque uniquement l'arrêt d'un point d'arrêt pour les processus ou les threads spécifiés.|[Spécifier un filtre de point d'arrêt](../../relational-databases/scripting/specify-a-breakpoint-filter.md)|  
|Explique comment spécifier une action **Lorsqu’il est atteint** , c’est-à-dire une opération personnalisée qui est effectuée lors de l’exécution de l’instruction de point d’arrêt. Citons en exemple l'impression d'un message.|[Spécifier une action de point d'arrêt](../../relational-databases/scripting/specify-a-breakpoint-action.md)|  
|Explique comment modifier l'emplacement d'un point d'arrêt.|[Modifier un emplacement de point d'arrêt](../../relational-databases/scripting/edit-a-breakpoint-location.md)|  
  
## <a name="see-also"></a> Voir aussi  
 [Informations du débogueur Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)  
  
  
