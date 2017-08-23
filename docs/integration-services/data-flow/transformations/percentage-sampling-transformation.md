---
title: "Transformation d’échantillonnage du pourcentage | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.percentagesamplingtrans.f1
helpviewer_keywords:
- testing mining models
- sampling seeds [Integration Services]
- data mining [Analysis Services], sample data sets
- Percentage Sampling transformation
- sample data sets [Integration Services]
- datasets [Integration Services], sample
- training mining models
ms.assetid: 59767e52-f732-4b3f-8602-be50d0a64ef2
caps.latest.revision: 46
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b304a50eeec9908427b7fd42319b88d78b151ff0
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="percentage-sampling-transformation"></a>transformation de l'échantillonnage du pourcentage
  La transformation de l'échantillonnage du pourcentage crée un échantillon d'ensemble de données en sélectionnant un pourcentage des lignes d'entrée de transformation. L'échantillon d'ensemble de données est une sélection aléatoire de lignes dans l'entrée de transformation, visant à rendre l'échantillon résultant représentatif de l'entrée.  
  
> [!NOTE]  
>  Outre le pourcentage spécifié, la transformation de l'échantillonnage du pourcentage utilise un algorithme pour déterminer si une ligne doit être incluse dans l'échantillon en sortie. Par conséquent, le nombre de lignes dans l'échantillon en sortie peut ne pas refléter exactement le pourcentage spécifié. Par exemple, la spécification de la valeur 10 % pour un ensemble de données d'entrée composé de 25 000 lignes peut ne pas générer un échantillon de 2 500 lignes ; celui-ci peut avoir un peu plus ou un peu moins de lignes.  
  
 La transformation de l'échantillonnage du pourcentage est spécialement utile pour l'exploration de données. Cette transformation vous permet de diviser de façon aléatoire un jeu de données en deux jeux de données : un pour mettre au point le modèle d'exploration de données, l'autre pour le tester.  
  
 La transformation de l'échantillonnage du pourcentage permet également de créer des échantillons d'ensembles de données en vue de développer des packages. Vous pouvez appliquer la transformation de l'échantillonnage du pourcentage à un flux de données afin de réduire uniformément la taille de l'ensemble de données tout en conservant les caractéristiques de ses données. Le package de test peut ensuite s'exécuter plus rapidement car il utilise un ensemble de données réduit mais représentatif.  
  
## <a name="configuration-the-percentage-sampling-transformation"></a>Configuration de la transformation de l'échantillonnage du pourcentage  
 Vous pouvez spécifier une valeur d'échantillonnage de départ afin de modifier le comportement du générateur de nombres aléatoires qu'utilise la transformation pour sélectionner les lignes. Si la même valeur d'échantillonnage de départ est utilisée, la transformation crée toujours le même échantillon en sortie. Si aucune valeur de départ n'est spécifiée, la transformation utilise le nombre de cycles du système d'exploitation pour créer le nombre aléatoire. Par conséquent, vous pouvez utiliser une valeur de départ standard pour vérifier les résultats de la transformation pendant le développement et le test d'un package, puis opter pour une valeur de départ aléatoire lorsque le package passe en production.  
  
 Cette transformation est similaire à la transformation d'échantillonnage de lignes, qui crée un échantillon d'ensemble de données en sélectionnant un nombre spécifié de lignes d'entrée. Pour plus d’informations, consultez [Transformation d’échantillonnage de lignes](../../../integration-services/data-flow/transformations/row-sampling-transformation.md).  
  
 La transformation d’échantillonnage par pourcentage inclut la propriété personnalisée **SamplingValue** . La propriété peut être mise à jour par une expression de propriété lors du chargement du package. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41; ](../../../integration-services/expressions/integration-services-ssis-expressions.md), [Utiliser des expressions de propriété dans les packages](../../../integration-services/expressions/use-property-expressions-in-packages.md) et [Propriétés personnalisées des transformations](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
 La transformation a une entrée et deux sorties. Elle ne prend pas en charge de sortie d'erreur.  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans la boîte de dialogue **Éditeur de transformation d’échantillonnage par pourcentage** , consultez [Transformation de l’échantillonnage du pourcentage](../../../integration-services/data-flow/transformations/percentage-sampling-transformation-editor.md).  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programme, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Propriétés personnalisées des transformations](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  
