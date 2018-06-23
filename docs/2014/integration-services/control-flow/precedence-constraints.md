---
title: Contraintes de précédence | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- control flow [Integration Services], precedence constraints
- precedence constraints [Integration Services]
- constraints [Integration Services]
- sequence execution options [Integration Services]
- containers [Integration Services], precedence constraints
ms.assetid: c5ce5435-fd89-4156-a11f-68470a69aa9f
caps.latest.revision: 50
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: cd1a3a39045330283b12aa74acbce64b1420c6ba
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154661"
---
# <a name="precedence-constraints"></a>Contraintes de précédence
  Les contraintes de précédence lient les exécutables, les conteneurs et les tâches des packages dans un flux de contrôle et spécifient les conditions qui déterminent si les exécutables s'exécutent. Un exécutable peut être une boucle For, une boucle Foreach, un conteneur de séquence, une tâche ou un gestionnaire d'événement. Les gestionnaires d'événements utilisent également les contraintes de précédence pour lier leurs exécutables dans un flux de contrôle.  
  
 Une contrainte de précédence lie deux exécutables : l'exécutable de précédence et l'exécutable contraint. L'exécutable de précédence s'exécute avant l'exécutable contraint et le résultat de l'exécution de l'exécutable de précédence peut déterminer si l'exécutable contraint s'exécute. Le schéma suivant illustre deux exécutables liés par une contrainte de précédence.  
  
 ![Exécutables connectés par le biais d’une contrainte de précédence](../media/ssis-pcsimple.gif "Exécutables connectés par le biais d’une contrainte de précédence")  
  
 Dans un flux de contrôle linéaire, c'est-à-dire sans branchement, les contraintes de précédence déterminent à elles seules la séquence d'exécution des tâches. Dans un flux de contrôle avec branchements, le moteur d'exécution [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] détermine l'ordre d'exécution des tâches et des conteneurs qui suivent immédiatement le branchement. Le moteur d'exécution détermine également l'ordre d'exécution des flux de travail non connectés dans un flux de contrôle.  
  
 L'architecture à conteneurs imbriqués d'[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] permet à tous les conteneurs (à l'exception du conteneur d'hôte de tâche qui encapsule une seule tâche) d'inclure d'autres conteneurs, chacun avec son propre flux de contrôle. Les conteneurs de boucles For, de boucles Foreach et de séquence peuvent inclure plusieurs tâches et d'autres conteneurs, qui à leur tour peuvent inclure plusieurs tâches et conteneurs. Par exemple, un package avec une tâche de script et un conteneur de séquence possède une contrainte de précédence qui lie la tâche de script et le conteneur de séquence. Le conteneur de séquence contient trois tâches de script et ses contraintes de précédence lient les trois tâches de script dans un flux de contrôle. Le schéma suivant illustre les contraintes de précédence dans un package avec deux niveaux d'imbrication.  
  
 ![Contraintes de précédence dans un package](../media/mw-dts-12.gif "Contraintes de précédence dans un package")  
  
 Le package étant situé au sommet de la hiérarchie de conteneurs [!INCLUDE[ssIS](../../../includes/ssis-md.md)], plusieurs packages ne peuvent pas être liés par des contraintes de précédence ; toutefois, vous pouvez ajouter une tâche d’exécution de package à un package et lier indirectement un autre package au flux de contrôle.  
  
 Vous pouvez configurer des contraintes de précédence de plusieurs manières :  
  
-   Spécifiez une opération d'évaluation. La contrainte d'évaluation utilise une valeur de contrainte, une expression ou les deux pour déterminer si l'exécutable contraint s'exécute.  
  
-   Si la contrainte de précédence utilise un résultat d'exécution, vous pouvez spécifier le résultat d'exécution comme étant un succès, un échec ou à l'achèvement.  
  
-   Si la contrainte de précédence utilise un résultat d'évaluation, vous pouvez fournir une expression qui correspond à une valeur booléenne.  
  
-   Spécifiez si la contrainte de précédence est évaluée seule ou avec d'autres contraintes qui s'appliquent à l'exécutable contraint.  
  
## <a name="evaluation-operations"></a>Opérations d'évaluation  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] propose les opérations d'évaluation suivantes :  
  
-   Une contrainte qui utilise uniquement le résultat d'exécution de l'exécutable de précédence pour déterminer si l'exécutable contraint s'exécute. Le résultat d'exécution de l'exécutable de précédence peut être achèvement, réussite ou échec. Il s'agit de l'opération par défaut.  
  
-   Une expression qui est évaluée pour déterminer si l'exécutable contraint s'exécute. Si le résultat de l'évaluation est true, l'exécutable contraint s'exécute.  
  
-   Une expression et une contrainte qui allient les exigences des résultats d'exécution de l'exécutable de précédence et les résultats de retour de l'évaluation de l'expression.  
  
-   Une expression ou une contrainte qui utilisent les résultats d'exécution de l'exécutable de précédence ou les résultats de retour de l'évaluation de l'expression.  
  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Le concepteur utilise la couleur pour identifier le type de contrainte de précédence. La contrainte Success (réussite) est verte, la contrainte Failure (échec) est rouge et la contrainte Completion (fin) est bleue. Pour afficher les étiquettes de texte indiquant le type de contrainte dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)], vous devez configurer les fonctionnalités d’accessibilité du Concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
 L’expression doit être une expression [!INCLUDE[ssIS](../../../includes/ssis-md.md)] valide et elle peut inclure des fonctions, des opérateurs, et des variables système et personnalisées. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41; ](../expressions/integration-services-ssis-expressions.md) et [Variables Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md).  
  
## <a name="execution-results"></a>Résultats d'exécution  
 La contrainte de précédence peut utiliser les résultats d'exécution suivants seuls ou avec une expression.  
  
-   L'achèvement requiert uniquement que l'exécutable de précédence soit terminé, quel que soit le résultat, pour que l'exécutable contraint s'exécute.  
  
-   Le succès requiert que l'exécutable de précédence se termine avec succès pour que l'exécutable contraint s'exécute.  
  
-   L'échec requiert que l'exécutable de précédence échoue pour que l'exécutable contraint s'exécute.  
  
> [!NOTE]  
>  Seules les contraintes de priorité sont membres du même `Precedence Constraint` collection peut être regroupée dans une condition AND logique. Par exemple, vous ne pouvez pas combiner des contraintes de précédence à partir de deux conteneurs de boucles Foreach.  
  
## <a name="configuration-of-the-precedence-constraint"></a>Configuration de la contrainte de précédence  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)], consultez [Éditeur de contrainte de précédence](../precedence-constraint-editor.md).  
  
 Pour plus d'informations sur la définition par programme de ces propriétés, consultez <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.  
  
## <a name="related-tasks"></a>Related Tasks  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Définir les propriétés d’une contrainte de précédence](../set-the-properties-of-a-precedence-constraint.md)  
  
-   [Définir la valeur d’une contrainte de précédence en utilisant le Menu contextuel](../set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)  
  
-   [Connecter des tâches et des conteneurs à l’aide d’une contrainte de précédence par défaut](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)  
  
     Cette rubrique fournit des informations sur la définition du comportement par défaut des contraintes de précédence et sur la connexion d'exécutables à l'aide de contraintes de précédence par défaut.  
  
## <a name="related-content"></a>Contenu associé  
 Article technique, [SSIS Expression Examples](http://go.microsoft.com/fwlink/?LinkId=220761), sur social.technet.microsoft.com  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des Expressions aux contraintes de précédence](../add-expressions-to-precedence-constraints.md)   
 [Plusieurs contraintes de précédence](../multiple-precedence-constraints.md)  
  
  