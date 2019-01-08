---
title: Échantillonnage du pourcentage, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.percentagesamplingtrans.f1
helpviewer_keywords:
- testing mining models
- sampling seeds [Integration Services]
- data mining [Analysis Services], sample data sets
- Percentage Sampling transformation
- sample data sets [Integration Services]
- datasets [Integration Services], sample
- training mining models
ms.assetid: 59767e52-f732-4b3f-8602-be50d0a64ef2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0b7f433313392c826babcbeb7eeaf9033b046b64
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52805511"
---
# <a name="percentage-sampling-transformation"></a>transformation de l'échantillonnage du pourcentage
  La transformation de l'échantillonnage du pourcentage crée un échantillon d'ensemble de données en sélectionnant un pourcentage des lignes d'entrée de transformation. L'échantillon d'ensemble de données est une sélection aléatoire de lignes dans l'entrée de transformation, visant à rendre l'échantillon résultant représentatif de l'entrée.  
  
> [!NOTE]  
>  Outre le pourcentage spécifié, la transformation de l'échantillonnage du pourcentage utilise un algorithme pour déterminer si une ligne doit être incluse dans l'échantillon en sortie. Par conséquent, le nombre de lignes dans l'échantillon en sortie peut ne pas refléter exactement le pourcentage spécifié. Par exemple, la spécification de la valeur 10 % pour un ensemble de données d'entrée composé de 25 000 lignes peut ne pas générer un échantillon de 2 500 lignes ; celui-ci peut avoir un peu plus ou un peu moins de lignes.  
  
 La transformation de l'échantillonnage du pourcentage est spécialement utile pour l'exploration de données. Cette transformation vous permet de diviser de façon aléatoire un jeu de données en deux jeux de données : un pour mettre au point le modèle d'exploration de données, l'autre pour le tester.  
  
 La transformation de l'échantillonnage du pourcentage permet également de créer des échantillons d'ensembles de données en vue de développer des packages. Vous pouvez appliquer la transformation de l'échantillonnage du pourcentage à un flux de données afin de réduire uniformément la taille de l'ensemble de données tout en conservant les caractéristiques de ses données. Le package de test peut ensuite s'exécuter plus rapidement car il utilise un ensemble de données réduit mais représentatif.  
  
## <a name="configuration-the-percentage-sampling-transformation"></a>Configuration de la transformation de l'échantillonnage du pourcentage  
 Vous pouvez spécifier une valeur d'échantillonnage de départ afin de modifier le comportement du générateur de nombres aléatoires qu'utilise la transformation pour sélectionner les lignes. Si la même valeur d'échantillonnage de départ est utilisée, la transformation crée toujours le même échantillon en sortie. Si aucune valeur de départ n'est spécifiée, la transformation utilise le nombre de cycles du système d'exploitation pour créer le nombre aléatoire. Par conséquent, vous pouvez utiliser une valeur de départ standard pour vérifier les résultats de la transformation pendant le développement et le test d'un package, puis opter pour une valeur de départ aléatoire lorsque le package passe en production.  
  
 Cette transformation est similaire à la transformation d'échantillonnage de lignes, qui crée un échantillon d'ensemble de données en sélectionnant un nombre spécifié de lignes d'entrée. Pour plus d’informations, consultez [Transformation d’échantillonnage de lignes](row-sampling-transformation.md).  
  
 La transformation de l'échantillonnage du pourcentage inclut la propriété personnalisée `SamplingValue`. La propriété peut être mise à jour par une expression de propriété lors du chargement du package. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41; ](../../expressions/integration-services-ssis-expressions.md), [Expressions de propriété dans des packages](../../expressions/use-property-expressions-in-packages.md) et [Propriétés personnalisées des transformations](transformation-custom-properties.md).  
  
 La transformation a une entrée et deux sorties. Elle ne prend pas en charge de sortie d'erreur.  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans la boîte de dialogue **Éditeur de transformation d’échantillonnage par pourcentage** , consultez [Transformation de l’échantillonnage du pourcentage](../../percentage-sampling-transformation-editor.md).  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../../common-properties.md)  
  
-   [Propriétés personnalisées des transformations](transformation-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md).  
  
  
