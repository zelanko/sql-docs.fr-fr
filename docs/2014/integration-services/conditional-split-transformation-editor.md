---
title: Éditeur de transformation de fractionnement conditionnel | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.conditionalsplittransformation.f1
helpviewer_keywords:
- Conditional Split Transformation Editor
ms.assetid: c30e1633-537a-4837-9991-6203c6f2a21e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 920ec41ae30d53853cfb757fb7fc33610953dc86
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66060888"
---
# <a name="conditional-split-transformation-editor"></a>Éditeur de transformation de fractionnement conditionnel
  Utilisez la boîte de dialogue **Éditeur de transformation de fractionnement conditionnel** pour créer des expressions, définir l'ordre dans lequel les expressions sont évaluées et nommer les sorties d'un fractionnement conditionnel. Cette boîte de dialogue comprend des fonctions mathématiques, de chaînes de caractères et de date/heure, ainsi que des opérateurs utilisés pour créer des expressions. La première condition évaluée comme vraie détermine la sortie vers laquelle une ligne est dirigée.  
  
> [!NOTE]  
>  La transformation de fractionnement conditionnel dirige chaque ligne d'entrée vers une seule sortie. Si vous entrez plusieurs conditions, la transformation envoie chaque ligne à la première sortie pour laquelle la condition est remplie et ne tient pas compte des conditions suivantes pour cette ligne. Si vous devez évaluer successivement plusieurs conditions, vous devrez peut-être enchaîner plusieurs transformations de fractionnement conditionnel dans le flux de données.  
  
 Pour en savoir plus sur la transformation de fractionnement conditionnel, consultez [Transformation de fractionnement conditionnel](data-flow/transformations/conditional-split-transformation.md).  
  
## <a name="options"></a>Options  
 **JSON**  
 Sélectionnez une ligne et utilisez les touches de direction à droite pour modifier l'ordre dans lequel les expressions sont évaluées.  
  
 **Nom de la sortie**  
 Donnez un nom à la sortie. Par défaut, il s'agit d'une liste de cas numérotée ; vous pouvez néanmoins choisir un nom unique et illustratif.  
  
 **Condition**  
 Tapez une expression ou créez-en une en faisant glisser les colonnes, variables et fonctions disponibles.  
  
 Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.  
  
 **Rubriques connexes :**  [Integration Services &#40;expressions de&#41; ssis](expressions/integration-services-ssis-expressions.md), [opérateurs &#40;&#41;d’expression SSIS ](expressions/operators-ssis-expression.md)et [fonctions &#40;Expression SSIS&#41;](expressions/functions-ssis-expression.md)  
  
 **Nom de sortie par défaut**  
 Tapez un nom pour la sortie par défaut ou utilisez le nom par défaut.  
  
 **Configurer la sortie d’erreur**  
 Spécifiez comment gérer les erreurs dans la boîte de dialogue [Configurer la sortie d’erreur](../../2014/integration-services/configure-error-output.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Fractionner un dataset à l'aide de la transformation de fractionnement conditionnel](data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
