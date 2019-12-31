---
title: Variables locales (fenêtre)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Locals Window [Transact-SQL]
ms.assetid: 59bea640-7823-4b4d-832c-f384d83cca2f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44aedf7d53b2a9ad91b37f5023c13d8e20097da1
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75243050"
---
# <a name="locals-window"></a>Variables locales (fenêtre)
  La fenêtre **variables locales** affiche des informations sur les expressions locales dans l’étendue actuelle du [!INCLUDE[tsql](../../includes/tsql-md.md)] débogueur. L'étendue est définie selon le frame de pile des appels actuellement sélectionné dans la fenêtre **Pile des appels** . Vous devez être en mode débogage pour afficher les expressions locales.  
  
## <a name="task-list"></a>Liste des tâches  
 **Pour accéder à la fenêtre variables locales**  
  
-   Dans le menu **Déboguer** , cliquez sur **Fenêtres**, puis sur **Variables locales**.  
  
 **Pour modifier la valeur d’une expression**  
  
-   Cliquez avec le bouton droit sur l’expression, puis sélectionnez **Modifier la valeur**.  
  
## <a name="columns"></a>Colonnes  
 **Nomme**  
 Nom de l'expression locale. Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] répertorie les variables, les paramètres et les fonctions système dont les noms commencent par @@.  
  
 **Valeur**  
 Affiche la valeur actuellement assignée à l'expression locale. Cette colonne est vide si aucune valeur n'a été assignée à l'expression.  
  
 Si la longueur d'une expression dépasse la largeur de la colonne **Valeur** , une info-bulle affiche la valeur complète lorsque vous placez le pointeur sur la cellule **Valeur** de cette expression.  
  
 La présence d'une icône de loupe dans une cellule **Valeur** indique que le visualiseur du débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] est disponible. Dans la liste, vous pouvez spécifier **Visualiseur de texte**, **Visualiseur XML**ou **Visualiseur HTML**. Pour démarrer un visualiseur du débogueur, cliquez sur l'icône de loupe. Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] ouvre une boîte de dialogue qui affiche les données dans un format adapté au type de données.  
  
 **Entrer**  
 Affiche le type de données de l'expression.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogueur Transact-SQL](transact-sql-debugger.md)   
 [Informations sur le débogueur Transact-SQL](transact-sql-debugger-information.md)   
 [Fenêtre Espion](transact-sql-debugger-watch-window.md)   
 [Fenêtre pile des appels](transact-sql-debugger-call-stack-window.md)   
 [Espion express (boîte de dialogue)](transact-sql-debugger-quickwatch-dialog-box.md)   
 [Expressions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql)  
