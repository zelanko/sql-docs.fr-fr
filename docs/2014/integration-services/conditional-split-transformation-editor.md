---
title: Éditeur de Transformation de fractionnement conditionnel | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.conditionalsplittransformation.f1
helpviewer_keywords:
- Conditional Split Transformation Editor
ms.assetid: c30e1633-537a-4837-9991-6203c6f2a21e
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: be0e756eaaf0a97dd041d94f254fd7bf80854b23
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045200"
---
# <a name="conditional-split-transformation-editor"></a>Éditeur de transformation de fractionnement conditionnel
  Utilisez la boîte de dialogue **Éditeur de transformation de fractionnement conditionnel** pour créer des expressions, définir l'ordre dans lequel les expressions sont évaluées et nommer les sorties d'un fractionnement conditionnel. Cette boîte de dialogue comprend des fonctions mathématiques, de chaînes de caractères et de date/heure, ainsi que des opérateurs utilisés pour créer des expressions. La première condition évaluée comme vraie détermine la sortie vers laquelle une ligne est dirigée.  
  
> [!NOTE]  
>  La transformation de fractionnement conditionnel dirige chaque ligne d'entrée vers une seule sortie. Si vous entrez plusieurs conditions, la transformation envoie chaque ligne à la première sortie pour laquelle la condition est remplie et ne tient pas compte des conditions suivantes pour cette ligne. Si vous devez évaluer successivement plusieurs conditions, vous devrez peut-être enchaîner plusieurs transformations de fractionnement conditionnel dans le flux de données.  
  
 Pour en savoir plus sur la transformation de fractionnement conditionnel, consultez [Transformation de fractionnement conditionnel](data-flow/transformations/conditional-split-transformation.md).  
  
## <a name="options"></a>Options  
 **JSON**  
 Sélectionnez une ligne et utilisez les touches de direction à droite pour modifier l'ordre dans lequel les expressions sont évaluées.  
  
 **Nom de sortie**  
 Donnez un nom à la sortie. Par défaut, il s'agit d'une liste de cas numérotée ; vous pouvez néanmoins choisir un nom unique et illustratif.  
  
 **Condition**  
 Tapez une expression ou créez-en une en faisant glisser les colonnes, variables et fonctions disponibles.  
  
 Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.  
  
 **Rubriques connexes :**  [Expressions Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md), [Opérateurs &#40;Expression SSIS&#41;](expressions/operators-ssis-expression.md), et [Fonctions &#40;Expression SSIS&#41;](expressions/functions-ssis-expression.md)  
  
 **Nom de sortie par défaut**  
 Tapez un nom pour la sortie par défaut ou utilisez le nom par défaut.  
  
 **Configurer l'affichage des erreurs**  
 Spécifiez comment gérer les erreurs dans la boîte de dialogue [Configurer la sortie d’erreur](../../2014/integration-services/configure-error-output.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Fractionner un dataset à l'aide de la transformation de fractionnement conditionnel](data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  