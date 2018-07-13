---
title: Ajouter des Expressions aux contraintes de précédence | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- precedence executables [Integration Services]
- precedence constraints [Integration Services], adding expressions
- adding expressions
- constrained executables [Integration Services]
- combining constraints
- expressions [Integration Services], constraints
ms.assetid: 5574d89a-a68e-4b84-80ea-da93305e5ca1
caps.latest.revision: 43
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bc4a614af4bd20a4209d323902c17db1c0a61ece
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161040"
---
# <a name="add-expressions-to-precedence-constraints"></a>Ajouter des expressions aux contraintes de précédence
  Une contrainte de précédence peut utiliser une expression pour définir la contrainte entre deux exécutables : l'exécutable de précédence et l'exécutable contraint. Les exécutables peuvent être des tâches ou des conteneurs. L'expression peut être utilisée seule ou en combinaison avec le résultat d'exécution de l'exécutable de précédence. Le résultat d'exécution d'un exécutable est soit succès, soit échec. Lorsque vous configurez le résultat d'exécution d'une contrainte de précédence, vous pouvez lui affecter la valeur `Success`, `Failure` ou `Completion`. `Success` exige que l'exécutable de précédence réussisse, `Failure` exige que l'exécutable de précédence échoue et `Completion` indique que l'exécutable contraint doit s'exécuter, que la tâche de précédence réussisse ou échoue. Pour plus d’informations, consultez [Contraintes de précédence](control-flow/precedence-constraints.md).  
  
 Le résultat d'évaluation de l'expression doit être `True` ou `False` et l'expression doit être une expression [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] valide. L'expression peut utiliser des littéraux, des variables système et personnalisées, ainsi que les fonctions et opérateurs fournis par la grammaire des expressions [!INCLUDE[ssIS](../includes/ssis-md.md)]. Par exemple, l'expression `@Count == SQRT(144) + 10` utilise la variable `Count`, la fonction SQRT, ainsi que les opérateurs égal à (==) et ajouter (+). Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).  
  
 Dans l'illustration qui suit, la tâche A et la tâche B sont liées par une contrainte de précédence qui utilise un résultat d'exécution et une expression. La valeur de la contrainte est définie sur `Success` et l'expression est `@X >== @Z`. La tâche B, la tâche contrainte, s'exécute uniquement si la tâche A se termine avec succès et si la valeur de la variable `X` est supérieure ou égale à la valeur de la variable `Z`.  
  
 ![Contrainte de précédence entre deux tâches](media/mw-dts-03.gif "Contrainte de précédence entre deux tâches")  
  
 Les exécutables peuvent également être liés par plusieurs contraintes de précédence contenant des expressions différentes. Par exemple, dans l'illustration qui suit, les tâches B et C sont liées à la tâche A par des contraintes de précédence qui utilisent des résultats d'exécution et des expressions. Les deux valeurs de contrainte sont définies `Success.` une contrainte de précédence inclut l’expression `@X >== @Z`, et l’autre contrainte de précédence inclut l’expression `@X < @Z`. En fonction des valeurs de la variable `X` et de la variable `Z`, la tâche C ou la tâche B s'exécute.  
  
 ![Expressions sur les contraintes de précédence](media/mw-dts-04.gif "Expressions sur les contraintes de précédence")  
  
 Vous pouvez ajouter ou modifier une expression à l’aide de **l’Éditeur de contrainte de précédence** dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] et la fenêtre Propriétés fournie par [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Cependant, la fenêtre Propriétés ne propose aucune vérification de la syntaxe de l'expression.  
  
 Si une contrainte de précédence inclut une expression, une icône s’affiche sur la surface de dessin de l’onglet **Flux de contrôle** , en regard de la contrainte de précédence et l’info-bulle de l’icône affiche l’expression.  
  
## <a name="combining-execution-values-and-expressions"></a>Combinaison de valeurs d'exécution et d'expressions  
 Le tableau qui suit décrit les effets de la combinaison d'une contrainte de valeur d'exécution et d'une expression dans une contrainte de précédence.  
  
|Opération d'évaluation|Résultat d'évaluation de la contrainte|Résultat d'évaluation de l'expression|L'exécutable contraint s'exécute|  
|--------------------------|-----------------------------|-----------------------------|---------------------------------|  
|Contrainte|True|Néant|True|  
|Contrainte|False|Néant|False|  
|Expression|Néant|True|True|  
|Expression|Néant|False|False|  
|Contrainte et expression|True|True|True|  
|Contrainte et expression|True|False|False|  
|Contrainte et expression|False|True|False|  
|Contrainte et expression|False|False|False|  
|Contrainte ou expression|True|True|True|  
|Contrainte ou expression|True|False|True|  
|Contrainte ou expression|False|True|True|  
|Contrainte ou expression|False|False|False|  
  
### <a name="to-add-an-expression-to-a-precedence-constraint"></a>Pour ajouter une expression à une contrainte de précédence  
  
-   [Utiliser une expression dans une contrainte de précédence](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
-   [Définir les propriétés d’une contrainte de précédence](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
## <a name="external-resources"></a>Ressources externes  
 Article technique, [SSIS Expression Examples](http://go.microsoft.com/fwlink/?LinkId=220761), sur social.technet.microsoft.com  
  
## <a name="see-also"></a>Voir aussi  
 [Plusieurs contraintes de précédence](../../2014/integration-services/multiple-precedence-constraints.md)   
 [Contraintes de précédence](control-flow/precedence-constraints.md)  
  
  
