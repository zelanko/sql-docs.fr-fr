---
title: Définir les propriétés d’une contrainte de précédence | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Precedence Constraint Editor dialog box
- precedence constraints [Integration Services], properties
ms.assetid: d990f600-5c09-4cd5-8528-0a58d79dc9f2
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 679e61c37df7d31b80f47fff186589ce0081f838
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84963119"
---
# <a name="set-the-properties-of-a-precedence-constraint"></a>Définir les propriétés d'une contrainte de précédence
  Pour définir des propriétés sur des contraintes de précédence, vous pouvez utiliser l'un des outils suivants :  
  
-   Vous pouvez utiliser la boîte de dialogue **Éditeur de contrainte de précédence** .  
  
-   Vous pouvez utiliser la fenêtre Propriétés. La fenêtre Propriétés répertorie des propriétés permettant de configurer des contraintes de précédence qui ne sont pas disponibles dans la boîte de dialogue **Éditeur de contrainte de précédence** . Dans cette fenêtre, vous pouvez entrer une description et un nom pour la contrainte de précédence et configurer l'annotation à afficher pour la contrainte de précédence sur l'aire de conception.  
  
 Les procédures ci-dessous montrent comment définir des propriétés sur des contraintes de précédence en utilisant chacun de ces outils.  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-precedence-constraint-editor"></a>Pour définir les propriétés d'une contrainte de précédence à l'aide de l'éditeur de contrainte de précédence  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de contrôle** .  
  
4.  Double-cliquez sur la contrainte de précédence.  
  
     **L’Éditeur de contrainte de précédence** s’ouvre.  
  
5.  Dans la liste déroulante **Opération d’évaluation** , sélectionnez une opération d’évaluation.  
  
6.  Dans la `Value` liste déroulante, sélectionnez le résultat d’exécution de l’exécutable de précédence.  
  
7.  Si l’opération d’évaluation utilise une expression, dans la `Expression` zone, tapez une expression, puis cliquez sur **tester** pour évaluer l’expression.  
  
    > [!NOTE]  
    >  Les noms de variable respectent la casse.  
  
8.  Si plusieurs tâches ou conteneurs sont connectés à l’exécutable avec restriction, sélectionnez **logique and** pour spécifier que les résultats d’exécution de tous les exécutables précédents doivent avoir la valeur `true` . Sélectionnez **or logique** pour spécifier qu’un seul résultat d’exécution doit correspondre à `true` .  
  
9. Cliquez sur **OK** pour fermer la boîte de dialogue **Éditeur de contrainte de précédence**.  
  
10. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-properties-window"></a>Pour définir les propriétés d'une contrainte de précédence à l'aide de la fenêtre Propriétés  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package à modifier.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flow Control** . Sur l’aire de conception de l’onglet **Flow Control** , cliquez avec le bouton droit sur la contrainte de précédence, puis cliquez sur **Propriétés**. Dans la fenêtre Propriétés, modifiez les valeurs des propriétés.  
  
4.  Dans la fenêtre **Propriétés** , configurez les propriétés de lecture/écriture suivantes pour les contraintes de précédence :  
  
    |Propriété Lecture/écriture|Action de configuration|  
    |--------------------------|--------------------------|  
    |Description|Fournissez une description.|  
    |EvalOp|Sélectionnez une opération d'évaluation. Si l' `Expression` opération, **ExpressionAndConstant**ou **ExpressionOrConstant** est sélectionnée, vous pouvez spécifier une expression.|  
    |Expression|Si l'opération d'évaluation inclut une expression, fournissez une expression. L'expression doit prendre une valeur de type Boolean. Pour plus d’informations sur le langage des expressions, consultez [Expressions Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).|  
    |LogicalAnd|Défini `LogicalAnd` pour spécifier si la contrainte de précédence est évaluée de concert avec d’autres contraintes de précédence, lorsque plusieurs exécutables précèdent et sont liés à l’exécutable avec contrainte|  
    |Nom|Mettez à jour le nom de la contrainte de précédence.|  
    |ShowAnnotation|Spécifiez le type d'annotation à utiliser. Sélectionnez **Never** pour désactiver les annotations, **AsNeeded** pour activer l’annotation à la demande, **ConstraintName** pour annoter automatiquement en utilisant la valeur de la propriété Name, **ConstraintDescription** pour annoter automatiquement en utilisant la valeur de la propriété Description et **ConstraintOptions** pour annoter automatiquement en utilisant les valeurs des propriétés Value et Expression.|  
    |Value|Si l’opération d’évaluation spécifiée dans la propriété EvalOP inclut une contrainte, sélectionnez le résultat d’exécution de l’exécutable de contrainte.|  
  
5.  Fermez la fenêtre Propriétés.  
  
6.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Contraintes de précédence](control-flow/precedence-constraints.md)   
 [Connecter des tâches et des conteneurs à l’aide d’une contrainte de précédence par défaut](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [Définir la valeur d’une contrainte de précédence à l’aide du menu contextuel](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)   
 [Utiliser une expression dans une contrainte de précédence](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  
