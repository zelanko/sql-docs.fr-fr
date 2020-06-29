---
title: Configurer un conteneur de boucles for | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: b9cd7ea7-b198-4a35-8b16-6acf09611ca5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3b162c6d93e00900cc8393cdec0539d3cd495a32
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85434946"
---
# <a name="configure-a-for-loop-container"></a>Configurer un conteneur de boucles For
  Cette procédure décrit comment configurer un conteneur de boucles For à l’aide de la boîte de dialogue **Éditeur de boucle For** .  
  
### <a name="to-configure-the-for-loop-container"></a>Pour configurer le conteneur de boucles For  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], double-cliquez sur le conteneur de boucles For pour ouvrir l’ **Éditeur de boucle For**.  
  
2.  Si vous le souhaitez, modifiez le nom et la description du conteneur de boucles For.  
  
3.  Si vous le souhaitez, tapez une expression d’initialisation dans la zone de texte **InitExpression** .  
  
4.  Tapez une expression d’évaluation dans la zone de texte **EvalExpression** .  
  
    > [!NOTE]  
    >  L'expression doit prendre une valeur de type Boolean. Lorsque l'expression correspond à `false`, la boucle cesse de s'exécuter.  
  
5.  Si vous le souhaitez, tapez une expression d’assignation dans la zone de texte **AssignExpression** .  
  
6.  Si vous le souhaitez, cliquez sur **Expressions** et, dans la page **Expressions** , créez des expressions de propriété pour les propriétés du conteneur de boucles For. Pour plus d’informations, consultez [Ajouter ou modifier une Expression de propriété](expressions/add-or-change-a-property-expression.md).  
  
7.  Cliquez sur **OK** pour fermer la boîte de dialogue **Éditeur de boucle For**.  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneur de boucles for](control-flow/for-loop-container.md)   
 [Integration Services &#40;des expressions de&#41; SSIS](expressions/integration-services-ssis-expressions.md)   
 [Expressions de propriété dans des packages](expressions/use-property-expressions-in-packages.md)  
  
  
