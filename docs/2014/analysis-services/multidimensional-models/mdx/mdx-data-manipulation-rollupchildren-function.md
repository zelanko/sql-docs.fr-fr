---
title: Utilisation de la fonction RollupChildren (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], RollupChildren function
- RollupChildren function
- custom member properties [MDX]
- IIf function
ms.assetid: 03c624d4-f277-451d-9995-623a07ea2f86
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 45db581de7b7aef2822597ef60d3b43ebad3acbd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66074264"
---
# <a name="working-with-the-rollupchildren-function-mdx"></a>Utilisation de la fonction RollupChildren (MDX)
  Le MDX (Multidimensional Expressions) [RollupChildren](/sql/mdx/rollupchildren-mdx) (fonction) [Script pour rechercher et remplacer] des enfants d’un membre, en appliquant un opérateur unaire différent à chaque enfant et retourne la valeur de ce cumul sous la forme d’un nombre. L'opérateur unaire peut être fourni par une propriété de membre associée au membre enfant, ou être une expression de type chaîne directement fournie à la fonction.  
  
## <a name="rollupchildren-function-examples"></a>Exemples de fonctions RollupChildren  
 L'utilisation de la fonction `RollupChildren` dans les instructions MDX (Multidimensional Expressions) est simple à expliquer, mais elle peut avoir d'importantes répercussions sur les requêtes MDX.  
  
 L'effet de la fonction `RollupChildren` est perceptible dans les requêtes MDX conçues pour effectuer des analyses sélectives portant sur des données de cube existantes. Par exemple, le tableau suivant contient une liste de membres enfants du membre parent Net Sales, ainsi que leurs opérateurs unaires entre parenthèses (représentés par la propriété de membre `UNARY_OPERATOR`).  
  
|Membre parent|Membre enfant|  
|-------------------|------------------|  
|Ventes nettes|Domestic Sales (+)<br /><br /> Domestic Returns (-)<br /><br /> Foreign Sales (+)<br /><br /> Foreign Returns (-)|  
  
 Dans le cadre du cumul, le total des ventes nettes fourni en l'occurrence par le membre parent Net Sales est exprimé par les valeurs des ventes brutes réalisées sur le marché national et à l'étranger, moins les invendus réalisés sur le marché national et à l'étranger.  
  
 Cependant, vous souhaitez fournir une estimation rapide et simple des ventes brutes réalisées sur le marché national et à l'étranger majorées de 10 %, sans tenir compte des invendus réalisés sur le marché national et à l'étranger. Pour calculer cette valeur, vous pouvez utiliser la fonction `RollupChildren` des deux manières suivantes : avec une propriété de membre personnalisée ou avec la fonction `IIf`.  
  
### <a name="using-a-custom-member-property"></a>Utilisation d'une propriété de membre personnalisée  
 Si le calcul de cumuls est appelé à être souvent utilisé, une méthode consiste à créer pour une fonction donnée une propriété de membre qui stocke les opérateurs à utiliser pour chaque enfant. Le tableau suivant présente les opérateurs unaires corrects et décrit le résultat attendu.  
  
|Opérateur|Résultat|  
|--------------|------------|  
|+|total = total + enfant actuel|  
|-|total = total - enfant actuel|  
|*|total = total * enfant actuel|  
|/|total = total / enfant actuel|  
|~|L'enfant n'est pas utilisé dans le cumul. La valeur de l'enfant est ignorée.|  
  
 Par exemple, une propriété de membre appelée `SALES_OPERATOR` est créée, à laquelle sont attribués des opérateurs unaires, comme le montre le tableau suivant.  
  
|Membre parent|Membre enfant|  
|-------------------|------------------|  
|Ventes nettes|Domestic Sales (+)<br /><br /> Domestic Returns (~)<br /><br /> Foreign Sales (+)<br /><br /> Foreign Returns (~)|  
  
 Grâce à cette nouvelle propriété de membre, l'instruction MDX suivante effectue l'estimation des ventes brutes rapidement et efficacement (en ignorant les invendus réalisés sur le marché national et à l'étranger) :  
  
```  
RollupChildren([Net Sales], [Net Sales].CurrentMember.Properties("SALES_OPERATOR")) * 1.1  
```  
  
 Lorsque la fonction est appelée, la valeur de chaque enfant s'applique à un total à l'aide de l'opérateur stocké dans la propriété de membre. Les membres correspondant aux invendus réalisés sur le marché national et à l'étranger sont ignorés, et le total du cumul renvoyé par la fonction `RollupChildren` est multiplié par 1,1.  
  
### <a name="using-the-iif-function"></a>Utilisation de la fonction IIf  
 Si l’opération de cet exemple n’est pas souvent utilisée ou si l’opération s’applique uniquement à une seule requête MDX, la [IIf](/sql/mdx/iif-mdx) fonction peut être utilisée avec le `RollupChildren` (fonction) pour fournir le même résultat. La requête MDX suivante fournit le même résultat que l'instruction MDX précédente, mais sans avoir recours à une propriété de membre personnalisée :  
  
```  
RollupChildren([Net Sales], IIf([Net Sales].CurrentMember.Properties("UNARY_OPERATOR") = "-", "~", [Net Sales].CurrentMember.Properties("UNARY_OPERATOR))) * 1.1  
```  
  
 L'instruction MDX examine l'opérateur unaire du membre enfant. S'il est utilisé pour une soustraction (comme dans le cas des membres correspondant aux invendus réalisés sur le marché national et à l'étranger), l'opérateur unaire tilde (~) est remplacé par la fonction `IIf`. Sinon, la fonction `IIf` utilise l'opérateur unaire du membre enfant. Enfin, le total du cumul renvoyé est multiplié par 1,1 afin de fournir la valeur estimée des ventes brutes sur le marché national et à l'étranger.  
  
## <a name="see-also"></a>Voir aussi  
 [Manipulation de données &#40;MDX&#41;](mdx-data-manipulation-manipulating-data.md)  
  
  
