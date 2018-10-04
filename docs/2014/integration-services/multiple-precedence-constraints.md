---
title: Plusieurs contraintes de précédence | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- multiple precedence constraints
- precedence executables [Integration Services]
- precedence constraints [Integration Services], multiple
- constrained executables [Integration Services]
ms.assetid: 71c53ead-3d19-4bc1-aafd-e5b32595b420
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 368d8faf917094ce1dd306cc4ffd385eb3254363
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084859"
---
# <a name="multiple-precedence-constraints"></a>Contraintes de précédence multiples
  Une contrainte de précédence connecte deux exécutables : deux tâches, deux conteneurs, ou un de chaque. Ils sont connus sous le nom d'exécutable de précédence et d'exécutable contraint. Un exécutable contraint peut comprendre plusieurs contraintes de précédence. Pour plus d’informations, consultez [Contraintes de précédence](control-flow/precedence-constraints.md).  
  
 Assembler des scénarios de contraintes complexes par regroupement de contraintes permet d'implémenter un flux de contrôle complexe dans les packages. Par exemple, dans l’illustration suivante, la tâche D est liée à la tâche A par une `Success` contrainte, la tâche D est liée à la tâche B par une `Failure` contrainte et la tâche D est liée à la tâche C par une `Success` contrainte. Les contraintes de précédence entre la tâche D et la tâche A, entre la tâche D et la tâche B, et entre la tâche D et la tâche C participent à une relation *et* logique. Par conséquent, pour que la tâche D s'exécute, la tâche A doit s'exécuter avec succès, la tâche B doit échouer et la tâche C doit s'exécuter avec succès.  
  
 ![Tâches liées par des contraintes de précédence](media/precedenceconstraints.gif "Tâches liées par des contraintes de précédence")  
  
## <a name="logicaland-property"></a>Propriété LogicalAnd  
 Si une tâche ou un conteneur comporte plusieurs contraintes, la propriété `LogicalAnd` indique si une contrainte de précédence est évaluée seule ou de concert avec les autres contraintes.  
  
 Vous pouvez définir le `LogicalAnd` à l’aide de la propriété le **éditeur de contrainte de précédence** dans [!INCLUDE[ssIS](../includes/ssis-md.md)] concepteur, ou dans la fenêtre de propriétés qui [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] fournit.  
  
## <a name="related-tasks"></a>Tâches associées  
 [Définir les propriétés d’une contrainte de précédence](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
  
