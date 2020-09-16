---
title: Spécifier une condition de point d'arrêt
description: Découvrez comment établir une condition de point d’arrêt pour contrôler si le débogueur exécute une action de point d’arrêt lorsque le point d’arrêt et le nombre d’accès sont atteints.
titleSuffix: T-SQL debugger
ms.prod: sql
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint conditions
ms.assetid: b43d8a2b-99a3-4fb7-8848-99c042ea7ef7
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.reviewer: ''
ms.date: 12/04/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 451776ba842c38ca306c17291404355908cb5202
ms.sourcegitcommit: 6d53ecfdc463914f045c20eda96da39dec22acca
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88901600"
---
# <a name="specify-a-breakpoint-condition"></a>Spécifier une condition de point d'arrêt

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Une condition de point d'arrêt est une expression [!INCLUDE[tsql](../../includes/tsql-md.md)] évaluée par le débogueur lorsque le point d'arrêt est atteint. Si la condition est satisfaite et si le nombre d'accès spécifié est atteint, le débogueur arrête ou effectue l'action spécifiée pour le point d'arrêt.  

[!INCLUDE[ssms-old-versions](../../includes/ssms-old-versions.md)]

## <a name="specifying-conditions"></a>Spécification des conditions

L'expression spécifiée doit être une expression Transact-SQL valide qui correspond à une valeur booléenne. Pour plus d’informations, consultez [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 Si vous spécifiez une condition de point d'arrêt avec une syntaxe incorrecte, un message d'avertissement apparaît immédiatement. Si vous spécifiez une condition avec une syntaxe correcte mais une sémantique incorrecte, un message d'avertissement s'affiche lorsque le point d'arrêt est atteint pour la première fois. Dans les deux cas, le débogueur arrête l'exécution lorsque le point d'arrêt non valide est atteint.  
  
#### <a name="to-specify-a-condition"></a>Pour spécifier une condition
  
1. Dans la fenêtre de l’éditeur, cliquez avec le bouton droit sur le glyphe du point d’arrêt, puis cliquez sur **Condition** dans le menu contextuel.  
  
     -ou-  
  
     Dans la fenêtre **Points d’arrêt** , cliquez avec le bouton droit sur le glyphe du point d’arrêt, puis cliquez sur **Condition** dans le menu contextuel.  
  
2. Dans la boîte de dialogue **Condition de point d’arrêt** , entrez une expression booléenne valide dans la zone **Condition** .  
  
3. Choisissez **Est vrai** si vous souhaitez arrêter quand l’expression correspond à la valeur **true**, ou choisissez **a changé** si vous souhaitez arrêter quand la valeur de l’expression a changé.  
  
    > [!NOTE]  
    >  Le débogueur n'évalue l'expression booléenne que lorsque le point d'arrêt est atteint pour la première fois. Si vous choisissez **a changé**, le débogueur ne considère pas la première évaluation comme une modification, donc il ne s’y arrête pas.  
  
## <a name="see-also"></a>Voir aussi

- [Spécifier un nombre d’accès](../../relational-databases/scripting/specify-a-hit-count.md)
- [Spécifier une action de point d’arrêt](../../relational-databases/scripting/specify-a-breakpoint-action.md)
