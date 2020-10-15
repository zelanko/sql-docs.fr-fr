---
title: Constantes dans les expressions (Générateur de rapports) | Microsoft Docs
description: Découvrez le texte littéral ou le texte prédéfini des constantes dans les expressions pour vos rapports dans le Générateur de rapports.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: b8ae650b-0f46-4848-b62b-15f8a40751b8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9b659b901764b48bd8db80c1e34ab58bb3897325
ms.sourcegitcommit: fe59f8dc27fd633f5dfce54519d6f5dcea577f56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91934623"
---
# <a name="constants-in-expressions-report-builder-and-ssrs"></a>Constantes dans les expressions (Générateur de rapports et SSRS)
  Une constante se compose de texte littéral ou de texte prédéfini. Le processeur de rapports a accès aux constantes prédéfinies afin que, lorsque vous les incluez dans une expression, les valeurs qu'elles représentent soient substituées dans l'expression avant son évaluation.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="literal-text"></a>Texte littéral  
 Dans une expression, le texte littéral est le texte qui figure entre guillemets doubles. Vous pouvez également taper le texte directement dans une zone de texte sans guillemets doubles s'il ne fait pas partie d'une expression. Si la valeur de la zone de texte ne commence pas par un signe égal (=), le texte est traité comme texte littéral. Le tableau suivant répertorie plusieurs exemples de texte littéral dans une expression.  
  
|Constant|Texte affiché|Texte de l'expression|  
|--------------|------------------|---------------------|  
|Report run at:|<\<Expr>>|`="Report run at: " & Globals!ExecutionTime`|  
|Adventure Works Cycles|Adventure Works Cycles|Adventure Works Cycles|  
|[Texte affiché entre crochets]|\\[Texte affiché entre crochets\\]|[Texte affiché entre crochets]|  
  
## <a name="rdl-constants"></a>Constantes RDL  
 Vous pouvez utiliser des constantes définies en RDL (Report Definition Language) dans une expression. Dans la boîte de dialogue **Expression** , les constantes apparaissent lorsque vous créez une expression pour une propriété de rapport qui accepte uniquement certaines valeurs valides, également appelées types énumérés. Le tableau suivant contient deux exemples.  
  
|Propriété|Description|Valeurs|  
|--------------|-----------------|------------|  
|TextAlign|Valeurs valides pour aligner le texte dans une zone de texte.|Général, Gauche, Centre, Droit|  
|BorderStyle|Valeurs valides pour une ligne ajoutée à un rapport.|Par défaut, Aucune, Pointillés, Tirets, Unie, Double, Tiret-point, Tiret-point-point|  
  
## <a name="visual-basic-constants"></a>Constantes Visual Basic  
 Vous pouvez utiliser des constantes définies dans la bibliothèque d'exécutables [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] dans une expression. Par exemple, vous pouvez utiliser la constante **DateInterval.Day**. Pour la date du 10 janvier 2008, l'expression suivante retourne le nombre 10 :  
  
 `=DatePart("d",Globals!ExecutionTime)`  
  
## <a name="clr-constants"></a>Constantes CLR  
 Vous pouvez utiliser des constantes définies dans les classes CLR (Common Language Runtime) [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] dans une expression. Le tableau suivant contient un exemple de couleur définie par le système.  
  
|Constant|Description|  
|--------------|-----------------|  
|MistyRose|Lorsque vous créez une expression pour une propriété de rapport basée sur la couleur d'arrière-plan, vous pouvez spécifier une couleur par nom. Les noms valides sont répertoriés dans la boîte de dialogue **Expression** .|  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue Expression](/previous-versions/sql/)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Boîte de dialogue Expression &#40;Générateur de rapports&#41;](./expressions-report-builder-and-ssrs.md)  
  
