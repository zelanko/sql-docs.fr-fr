---
title: Éléments syntaxiques MDX (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 263238a0d8430928fad99042dfa0ffd06921a33b
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893320"
---
# <a name="mdx-syntax-elements-mdx"></a>Éléments de la syntaxe MDX (MDX)


  Les expressions MDX (Multidimensional Expressions) comportent plusieurs éléments utilisés par la plupart des instructions ou ayant des répercussions sur ces dernières :  
  
|Terme|Définition|  
|----------|----------------|  
|[Identificateurs](../mdx/identifiers-mdx.md)|Les identificateurs sont les noms d'objets tels que des cubes, des dimensions, des membres et des mesures.|  
|**Types de données**|Définissent les types de données contenus dans des cellules, des propriétés de membre et des propriétés de cellule. La syntaxe MDX ne prend en charge que le type de données OLE VARIANT. Pour plus d'informations sur les contraintes, la conversion et la manipulation du type de données VARIANT, consultez « VARIANT and VARIANTARG » (en anglais) dans la documentation du Kit de développement Platform SDK.|  
|[Expressions &#40;MDX&#41;](../mdx/expressions-mdx.md)|Les expressions sont des unités de syntaxe qui Analysis Services peuvent être résolues en valeurs uniques (scalaires) ou en objets. Elles comprennent des fonctions qui retournent une valeur unique, une expression d'ensemble, etc.|  
|[Opérateurs](../mdx/operators-mdx-syntax.md)|Les opérateurs sont des éléments de syntaxe ajoutés à une ou plusieurs expressions MDX simples pour en créer de plus complexes.|  
|[Fonctions](../mdx/functions-mdx-syntax.md)|Les fonctions sont des éléments de syntaxe qui acceptent une ou plusieurs valeurs d'entrée (voire aucune) et retournent une valeur scalaire ou un objet. Les exemples incluent la fonction [Sum](../mdx/sum-mdx.md) pour l’ajout de plusieurs valeurs, la fonction [members](../mdx/members-set-mdx.md) pour retourner un jeu de membres à partir d’une dimension ou d’un niveau, et ainsi de suite.|  
|[Commentaires](../mdx/comments-mdx-syntax.md)|Les commentaires sont des parties de texte insérées dans des instructions ou des scripts MDX afin d'expliquer le but d'une instruction. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]n’exécute pas de commentaires.|  
|[Mots clés réservés](../mdx/reserved-keywords-mdx-syntax.md)|Les mots clés réservés sont des mots dont l'utilisation est réservée à MDX et qui ne doivent pas être utilisés comme nom d'objet dans des instructions MDX.|  
|[Membres, tuples et jeux](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx)|Les membres, tuples et jeux sont des concepts essentiels des données multidimensionnelles que vous devez comprendre avant de créer une requête MDX.|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les expressions multidimensionnelles &#40;MDX&#41;](../mdx/multidimensional-expressions-mdx-reference.md)  
  
  
