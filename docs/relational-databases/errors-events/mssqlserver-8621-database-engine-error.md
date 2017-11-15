---
title: MSSQLSERVER_8621 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 8621 (Database Engine error)
ms.assetid: 67f59865-becd-4999-8bb0-90aedd7effbf
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 3894958f62fc19b76b65b710e2627ee0b2d5f621
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver8621"></a>MSSQLSERVER_8621
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|8621|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|OPTIMIZER_STACK_OVERFLOW_ERR|  
|Texte du message|Espace de pile du processeur de requêtes insuffisant lors de l'optimisation de la requête. Simplifiez la requête.|  
  
## <a name="explanation"></a>Explication  
La taille de la requête développée est la cause la plus probable de l'erreur. La requête développée substitue dans la requête d'origine les définitions de toutes les vues, colonnes calculées, fonctions [!INCLUDE[tsql](../../includes/tsql-md.md)] et expressions de table commune auxquelles elle fait référence, ainsi que les actions en cascade telles que la mise à jour des index secondaires, des vues et des déclencheurs.  
  
La requête possède probablement une dimension importante ; par exemple, le nombre de tables référencées par les définitions de vues ou une expression scalaire très importante.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Simplifiez la requête en la divisant en plusieurs requêtes le long de la dimension la plus importante. Commencez par supprimer tous les éléments de la requête qui ne sont pas réellement nécessaires, puis essayez d'ajouter une table temporaire et de diviser la requête en deux.  Le simple déplacement d'une partie de la requête vers une sous-requête, une fonction ou une expression de table commune ne suffit pas, car ces éléments sont réassociés par le compilateur [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
