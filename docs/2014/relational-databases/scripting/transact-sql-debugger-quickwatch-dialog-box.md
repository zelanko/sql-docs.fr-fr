---
title: Espion express, boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.quickwatch
helpviewer_keywords:
- QuickWatch Dialog [Transact-SQL]
ms.assetid: d6bbb373-1452-41f2-bdc5-86ae689c3dc0
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b9809cd60703058c994af441145d0668cd7f76b1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043824"
---
# <a name="quickwatch-dialog-box"></a>Boîte de dialogue Espion express
  Utilisez la boîte de dialogue **Espion express** pour consulter rapidement le type de données et la valeur d’une expression [!INCLUDE[tsql](../../includes/tsql-md.md)] (par exemple, une variable ou un paramètre) pendant que vous déboguez le code [!INCLUDE[tsql](../../includes/tsql-md.md)] . Pour surveiller plusieurs expressions, vous pouvez également ajouter l’expression à une fenêtre **Espion** .  
  
## <a name="task-list"></a>Liste des tâches  
 **Pour accéder à la boîte de dialogue Espion express**  
  
-   Dans le menu **Déboguer** , cliquez sur **Espion express**.  
  
 **Pour afficher les informations relatives à une expression**  
  
1.  Dans la zone de liste **Expression** , tapez ou sélectionnez l’expression souhaitée. Les expressions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes sont prises en charge :  
  
    -   variables ;  
  
    -   Paramètres.  
  
    -   Fonctions système dont le nom commence par @@.  
  
    -   Expressions générées par l’application d’opérateurs à une ou plusieurs variables, un ou plusieurs paramètres ou une ou plusieurs fonctions système, comme @IntegerCounter + 1 ou FirstName + LastName.  
  
    -   Instructions Transact-SQL qui retournent une seule valeur, par exemple : SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1.  
  
2.  Cliquez sur **Réévaluer**.  
  
 **Pour ajouter l'expression Espion express à la fenêtre Espion**  
  
-   Cliquez sur **Ajouter un espion**.  
  
 **Pour modifier la valeur de l'expression Espion express**  
  
-   Cliquez avec le bouton droit sur l’expression, puis sélectionnez **Modifier la valeur**.  
  
## <a name="options"></a>Options  
 **Liste d'expressions**  
 Affiche l'expression sélectionnée. La liste déroulante contient un ensemble d'expressions que vous pouvez choisir d'afficher. Les expressions présentes dans la liste sont celles qui sont disponibles dans l’étendue du frame de pile sélectionné dans la fenêtre **Pile des appels** . Pour afficher une autre expression, entrez-la ou sélectionnez-la dans la liste. Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] prend en charge les expressions suivantes : variables, paramètres et fonctions système dont les noms commencent par @@.  
  
 **Grille Valeur**  
 Affiche les propriétés de l'expression actuellement surveillée.  
  
 **Nom**  
 Expression [!INCLUDE[tsql](../../includes/tsql-md.md)] actuellement surveillée.  
  
 **Value**  
 Affiche la valeur actuellement assignée à l'expression. Si l'expression n'a pas de valeur, un espace est affiché.  
  
 Si la longueur d'une expression dépasse la largeur de la colonne **Valeur** , une info-bulle affiche la valeur complète lorsque vous placez le pointeur sur la cellule **Valeur** de cette expression.  
  
 La présence d'une icône de loupe dans une cellule **Valeur** indique que le visualiseur du débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] est disponible. Dans la liste, vous pouvez spécifier **Visualiseur de texte**, **Visualiseur XML**ou **Visualiseur HTML**. Pour démarrer un visualiseur du débogueur, cliquez sur l'icône de loupe. Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] ouvre une boîte de dialogue qui affiche les données dans un format adapté au type de données.  
  
 **Type**  
 Affiche le type de données de l'expression.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogueur Transact-SQL](transact-sql-debugger.md)   
 [Informations du débogueur Transact-SQL](transact-sql-debugger-information.md)   
 [Espion (fenêtre)](transact-sql-debugger-watch-window.md)   
 [Variables locales (fenêtre)](transact-sql-debugger-locals-window.md)   
 [Fenêtre Pile des appels](transact-sql-debugger-call-stack-window.md)   
 [Expressions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql)  
  
  
