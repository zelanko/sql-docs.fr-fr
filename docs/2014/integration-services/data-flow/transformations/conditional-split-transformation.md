---
title: Fractionnement conditionnel, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.conditionalsplittrans.f1
helpviewer_keywords:
- Conditional Split transformation
- route rows to different outputs [Integration Services]
ms.assetid: 3f8b5825-226f-413c-ba8f-0bb931ca3770
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: dcfbbac9eacc96384a723088cf8f20cc939bdc48
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62900823"
---
# <a name="conditional-split-transformation"></a>transformation de fractionnement conditionnel
  La transformation de fractionnement conditionnel peut aiguiller les lignes de données vers différentes sorties, suivant le contenu des données. La mise en œuvre de la transformation de fractionnement conditionnel s'apparente à une structure de décision CASE dans un langage de programmation. La transformation évalue les expressions puis, sur la base des résultats, dirige la ligne de données vers la sortie spécifiée. Cette transformation offre également une sortie par défaut, vers laquelle sont dirigées les lignes qui ne correspondent à aucune expression.  
  
## <a name="configuration-of-the-conditional-split-transformation"></a>Configuration de la transformation de fractionnement conditionnel  
 Vous pouvez configurer la transformation de fractionnement conditionnel comme suit :  
  
-   Indiquez une expression renvoyant une valeur booléenne pour chaque condition que la transformation doit tester.  
  
-   Spécifiez l'ordre dans lequel les conditions sont évaluées. L'ordre est significatif car une ligne est envoyée à la sortie correspondant à la première condition qui renvoie True.  
  
-   Spécifiez la sortie par défaut de la transformation. Il est nécessaire de spécifier une sortie par défaut pour la transformation.  
  
 Chaque ligne d'entrée ne peut être envoyée qu'à une sortie, en l'occurrence celle correspondant à la première condition qui renvoie True. Par exemple, les conditions suivantes dirigent toutes les lignes de la colonne **FirstName** commençant par la lettre *A* vers une sortie, celles commençant par la lettre *B* vers une autre sortie et toutes les autres vers la sortie par défaut.  
  
 Sortie 1  
  
 `SUBSTRING(FirstName,1,1) == "A"`  
  
 Sortie 2  
  
 `SUBSTRING(FirstName,1,1) == "B"`  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] comprend des fonctions et des opérateurs permettant de créer les expressions qui évaluent les données d’entrée et dirigent les données de sortie. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41;](../../expressions/integration-services-ssis-expressions.md).  
  
 La transformation de fractionnement conditionnel inclut la propriété personnalisée `FriendlyExpression`. La propriété peut être mise à jour par une expression de propriété lors du chargement du package. Pour plus d’informations, consultez [Expressions de propriété dans des packages](../../expressions/use-property-expressions-in-packages.md) et [Propriétés personnalisées des transformation](transformation-custom-properties.md).  
  
 Cette transformation possède une entrée, une ou plusieurs sorties et une sortie d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de transformation de fractionnement conditionnel** , consultez [Éditeur de transformation de fractionnement conditionnel](../../conditional-split-transformation-editor.md).  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../../common-properties.md)  
  
-   [Propriétés personnalisées des transformations](transformation-custom-properties.md)  
  
 Pour plus d'informations sur la définition des propriétés, cliquez sur l'une des rubriques suivantes :  
  
-   [Fractionner un dataset à l'aide de la transformation de fractionnement conditionnel](conditional-split-transformation.md)  
  
-   [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 [Fractionner un dataset à l'aide de la transformation de fractionnement conditionnel](conditional-split-transformation.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de données](../data-flow.md)   
 [Transformations Integration Services](integration-services-transformations.md)  
  
  
