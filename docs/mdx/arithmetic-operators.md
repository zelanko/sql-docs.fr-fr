---
description: Opérateurs arithmétiques
title: Opérateurs arithmétiques | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 995e7ce1cb6a3c5d06db1042c00f945ec01e1be6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494992"
---
# <a name="arithmetic-operators"></a>Opérateurs arithmétiques


  Vous pouvez utiliser des opérateurs arithmétiques dans la syntaxe MDX (Multidimensional Expressions) pour tout calcul arithmétique, notamment une addition, une soustraction, une multiplication et une division.  
  
 MDX prend en charge les opérateurs arithmétiques répertoriés dans le tableau suivant.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[+ (Ajout)](../mdx/add-mdx.md)|Additionne deux nombres.|  
|[/ (Diviser)](../mdx/divide-mdx-operator-reference.md)|Divise un nombre par un autre nombre.|  
|[* (Multiplication)](../mdx/multiply-mdx.md)|Multiplie deux nombres.|  
|[- (Soustraction)](../mdx/subtract-mdx.md)|Soustrait deux nombres.|  
|^ (Puissance) |Élève un nombre à une puissance égale à un autre nombre.|  
  
> [!NOTE]  
>  MDX n'inclut pas de fonction pour obtenir la racine carrée d'un nombre. Pour obtenir la racine carrée d'un nombre, élevez-le à la puissance 0.5 à l'aide de l'opérateur ^.  
  
## <a name="order-of-precedence"></a>Ordre de priorité  
 Les règles suivantes déterminent l'ordre de priorité des opérateurs arithmétiques dans une expression MDX :  
  
-   Lorsqu'une expression contient plusieurs opérateurs arithmétiques, MDX exécute d'abord la multiplication et la division, puis la soustraction et l'addition.  
  
-   Lorsque tous les opérateurs arithmétiques dans une expression ont le même niveau de priorité, l’ordre d’exécution est de gauche à droite.  
  
-   Les expressions entre parenthèses ont la priorité sur toutes les autres opérations.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40;&#41;MDX ](../mdx/mdx-operator-reference-mdx.md)   
 [Opérateurs &#40;syntaxe MDX&#41;](../mdx/operators-mdx-syntax.md)  
  
  
