---
title: Points d’arrêt Transact-SQL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoints
ms.assetid: c234430f-bd94-4d0d-9e74-2bf11681fa50
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e170a2177ceefb0329e85f8fbf252cc62de76469
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66063556"
---
# <a name="transact-sql-breakpoints"></a>Points d'arrêt Transact-SQL
  Les points d'arrêt spécifient que le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] suspend l'exécution à une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] spécifique ; vous pouvez ensuite consulter l'état des éléments de code à ce point.  
  
## <a name="breakpoints"></a>Points d’arrêt  
 En exécutant le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] , vous pouvez basculer un point d'arrêt sur des instructions spécifiques. Lorsque l'exécution atteint une instruction avec un point d'arrêt, le débogueur suspend l'exécution afin que vous puissiez afficher des informations de débogage telles que les valeurs présentes dans les variables et les paramètres.  
  
 Vous pouvez gérer les points d’arrêt individuellement dans la fenêtre de l’éditeur ou collectivement via la fenêtre **Points d’arrêt** . Vous pouvez modifier des points d'arrêt afin de spécifier des éléments tels que les conditions spécifiques sous lesquelles l'exécution doit être suspendue ou les actions à prendre si le point d'arrêt est exécuté.  
  
## <a name="breakpoint-tasks"></a>Tâches de point d'arrêt  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Explique comment spécifier l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suite à laquelle vous souhaitez que le débogueur soit suspendu.|[Basculer un point d'arrêt](../spatial/point.md)|  
|Explique comment désactiver temporairement un point d'arrêt et le réactiver ultérieurement. Explique également comment supprimer un point d'arrêt.|[Activer, désactiver et supprimer des points d'arrêt](enable-disable-and-delete-breakpoints.md)|  
|Explique comment spécifier une condition qui définit si le point d'arrêt entraîne un arrêt d'après l'évaluation d'une expression Transact-SQL spécifiée.|[Spécifier une condition de point d'arrêt](specify-a-breakpoint-condition.md)|  
|Explique comment spécifier un nombre d'accès qui provoque uniquement l'arrêt d'un point d'arrêt lorsque l'instruction contenant le point d'arrêt a été exécutée un nombre spécifié de fois.|[Spécifier un nombre d'accès](specify-a-hit-count.md)|  
|Explique comment spécifier un filtre qui provoque uniquement l'arrêt d'un point d'arrêt pour les processus ou les threads spécifiés.|[Spécifier un filtre de point d'arrêt](specify-a-breakpoint-filter.md)|  
|Explique comment spécifier une action **Lorsqu’il est atteint** , c’est-à-dire une opération personnalisée qui est effectuée lors de l’exécution de l’instruction de point d’arrêt. Citons en exemple l'impression d'un message.|[Spécifier une action de point d'arrêt](specify-a-breakpoint-action.md)|  
|Explique comment modifier l'emplacement d'un point d'arrêt.|[Modifier un emplacement de point d'arrêt](edit-a-breakpoint-location.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations du débogueur Transact-SQL](transact-sql-debugger-information.md)  
  
  
