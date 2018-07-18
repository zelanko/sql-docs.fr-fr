---
title: Spécifier une condition de point d’arrêt | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpt.condition
helpviewer_keywords:
- Transact-SQL debugger, breakpoint conditions
ms.assetid: b43d8a2b-99a3-4fb7-8848-99c042ea7ef7
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ecee19e4846d2ccf49c21d90b8ab9815ed63a5b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282775"
---
# <a name="specify-a-breakpoint-condition"></a>Spécifier une condition de point d'arrêt
  Une condition de point d'arrêt est une expression [!INCLUDE[tsql](../../includes/tsql-md.md)] évaluée par le débogueur lorsque le point d'arrêt est atteint. Si la condition est satisfaite et si le nombre d'accès spécifié est atteint, le débogueur arrête ou effectue l'action spécifiée pour le point d'arrêt.  
  
## <a name="specifying-conditions"></a>Spécification des conditions  
 L'expression spécifiée doit être une expression Transact-SQL valide qui correspond à une valeur booléenne. Pour plus d’informations, consultez [Expressions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql).  
  
 Si vous spécifiez une condition de point d'arrêt avec une syntaxe incorrecte, un message d'avertissement apparaît immédiatement. Si vous spécifiez une condition avec une syntaxe correcte mais une sémantique incorrecte, un message d'avertissement s'affiche lorsque le point d'arrêt est atteint pour la première fois. Dans les deux cas, le débogueur arrête l'exécution lorsque le point d'arrêt non valide est atteint.  
  
#### <a name="to-specify-a-condition"></a>Pour spécifier une condition  
  
1.  Dans la fenêtre de l’éditeur, cliquez avec le bouton droit sur le glyphe du point d’arrêt, puis cliquez sur **Condition** dans le menu contextuel.  
  
     -ou-  
  
     Dans la fenêtre **Points d’arrêt** , cliquez avec le bouton droit sur le glyphe du point d’arrêt, puis cliquez sur **Condition** dans le menu contextuel.  
  
2.  Dans la boîte de dialogue **Condition de point d’arrêt** , entrez une expression booléenne valide dans la zone **Condition** .  
  
3.  Choisissez **vaut** si vous souhaitez arrêter lorsque l’expression prend la valeur `true`, ou choisissez **a changé** si vous souhaitez arrêter quand la valeur de l’expression a changé.  
  
    > [!NOTE]  
    >  Le débogueur n'évalue l'expression booléenne que lorsque le point d'arrêt est atteint pour la première fois. Si vous choisissez **a changé**, le débogueur ne considère pas la première évaluation comme une modification, donc il ne s’y arrête pas.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier un nombre d'accès](specify-a-hit-count.md)   
 [Spécifier une action de point d’arrêt](specify-a-breakpoint-action.md)  
  
  
