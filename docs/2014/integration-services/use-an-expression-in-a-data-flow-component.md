---
title: Utiliser une expression dans un composant de Data Flow | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], data flow
- expressions [Integration Services], data flow components
ms.assetid: 9181b998-d24a-41fb-bb3c-14eee34f910d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0c996889b6127bb8ea16bab077bfd9d757921b11
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85420346"
---
# <a name="use-an-expression-in-a-data-flow-component"></a>Utiliser une expression dans un composant de flux de données
  Cette procédure permet d'ajouter une expression à la transformation de fractionnement conditionnel ou à la transformation de colonne dérivée. La transformation de fractionnement conditionnel utilise des expressions pour définir les conditions qui dirigent les lignes de données vers une sortie de transformation et la transformation de colonne dérivée utilise des expressions pour définir les valeurs affectées aux colonnes.  
  
 Pour implémenter une expression dans une transformation, le package doit déjà inclure au moins une tâche de flux de données et une source. Pour plus d'informations sur l'ajout d'éléments aux packages, consultez les rubriques suivantes :  
  
-   [Ajouter ou supprimer une tâche ou un conteneur dans un flux de contrôle](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
    
  
-   [Ajouter ou supprimer un composant dans un flux de données](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
-   [Connecter des composants dans un flux de données](data-flow/connect-components-in-a-data-flow.md)  
  
### <a name="to-create-an-expression"></a>Pour créer une expression  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , cliquez sur l’onglet **Flux de contrôle** , puis cliquez sur la tâche de flux de données contenant le flux de données dans lequel vous voulez implémenter une expression.  
  
4.  Cliquez sur l’onglet **Flux de données** , et faites glisser une transformation de fractionnement conditionnel ou de colonne dérivée de la **Boîte à outils** jusqu’à l’aire de conception.  
  
5.  Faites glisser le connecteur vert de la source ou d'une transformation vers la transformation de fractionnement conditionnel ou de colonne dérivée.  
  
6.  Double-cliquez sur la transformation pour ouvrir sa boîte de dialogue.  
  
7.  Dans le volet gauche, développez **Variables** pour afficher les variables système et définies par l’utilisateur, et développez **Colonnes** pour afficher les colonnes d’entrée de transformation.  
  
8.  Dans le volet droit, développez **Fonctions mathématiques**, **Fonctions de chaîne**, **Fonctions de date et d’heure**, **Fonctions NULL**, **Casts de type**et **Opérateurs** pour accéder aux fonctions, conversions et opérateurs fournis par la grammaire d’expression.  
  
9. Selon la transformation, effectuez l'une des opérations suivantes pour générer une expression :  
  
    -   Dans la boîte de dialogue **Éditeur de transformation de fractionnement conditionnel** , faites glisser les variables, colonnes, fonctions, conversions et opérateurs vers la colonne **Condition** . Vous pouvez également aussi taper une expression directement dans la colonne **Condition** .  
  
    -   Dans la boîte de dialogue **Éditeur de transformation de colonne dérivée** , faites glisser les variables, colonnes, fonctions, conversions et opérateurs vers la colonne **Expression** . Vous pouvez également taper une expression directement dans la colonne **Expression** .  
  
        > [!NOTE]  
        >  Quand la colonne **Condition** ou **Expression** n’est plus active, le texte de l’expression peut être mis en surbrillance, ce qui indique que la syntaxe de l’expression est incorrecte.  
  
10. Cliquez sur **OK** pour quitter la boîte de dialogue.  
  
    > [!NOTE]  
    >  Si l'expression n'est pas valide, une alerte apparaît et décrit les erreurs de syntaxe de l'expression.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services &#40;des expressions de&#41; SSIS](expressions/integration-services-ssis-expressions.md)   
 [Transformation de fractionnement conditionnel](data-flow/transformations/conditional-split-transformation.md)   
 [Transformation de colonne dérivée](data-flow/transformations/derived-column-transformation.md)   
 [Tâche de workflow](control-flow/data-flow-task.md)   
 [Flux de données](data-flow/data-flow.md)  
  
  
