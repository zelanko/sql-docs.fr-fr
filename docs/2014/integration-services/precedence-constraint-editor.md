---
title: Éditeur de contrainte de précédence | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.precedenceconstraint.f1
helpviewer_keywords:
- Precedence Constraint Editor dialog box
ms.assetid: b10d4330-6e35-4037-b309-ef56efcd60c5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7d2046882eeed6b04cd1b1c4035b89eccbddc4f6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66056687"
---
# <a name="precedence-constraint-editor"></a>Éditeur de contrainte de précédence
  Utilisez la boîte de dialogue **Éditeur de contrainte de précédence** pour configurer les contraintes de précédence.  
  
## <a name="options"></a>Options  
 **Opération d’évaluation**  
 Spécifiez l'opération d'évaluation utilisée par la contrainte de précédence. Ces opérations sont : **Contrainte**, **Expression**, **Expression et contrainte** et **Expression ou contrainte**.  
  
 **Valeur**  
 Spécifiez la valeur de contrainte : **Réussite**, **Échec** ou **À l'achèvement**.  
  
> [!NOTE]  
>  La ligne de contrainte de précédence est verte pour **Réussite**, mise en surbrillance pour **Échec**et bleue pour **À l’achèvement**.  
  
 **Expression**  
 Si vous utilisez les opérations **Expression**, **Expression et contrainte**ou **Expression ou contrainte**, tapez une expression ou lancez le Générateur d’expressions pour créer l’expression. L'expression doit prendre une valeur de type Boolean.  
  
 **Tester**  
 Validez l'expression.  
  
 **ET logique**  
 Sélectionnez cette option pour spécifier que plusieurs contraintes de précédence sur le même exécutable doivent être évaluées ensemble. Toutes les contraintes doivent prendre la valeur `True`.  
  
> [!NOTE]  
>  Ce type de contrainte de précédence s'affiche sous forme de ligne pleine verte, mise en surbrillance ou bleue.  
  
 **OU logique**  
 Sélectionnez cette option pour spécifier que plusieurs contraintes de précédence sur le même exécutable doivent être évaluées ensemble. Une contrainte au moins doit prendre la valeur `True`.  
  
> [!NOTE]  
>  Ce type de contrainte de précédence s'affiche sous forme de ligne pointillée verte, mise en surbrillance ou bleue.  
  
## <a name="see-also"></a>Voir aussi  
 [Contraintes de précédence](control-flow/precedence-constraints.md)   
 [Tâches Integration Services](control-flow/integration-services-tasks.md)   
 [Conteneurs Integration Services](control-flow/integration-services-containers.md)   
 [Expressions Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md)  
  
  
