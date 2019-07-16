---
title: UnknownMember (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a0332b200a74044dcd4e7d8d308923cc4b759738
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097284"
---
# <a name="unknownmember-mdx"></a>UnknownMember (MDX)


  Retourne le membre inconnu associé à un niveau ou un membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member expression syntax  
Member_Expression.UnknownMember  
  
Hierarchy_expression syntax  
Hierarchy_Expression.UnknownMember  
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Hierarchy_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
## <a name="remarks"></a>Notes  
 Analysis Services crée un membre inconnu pour associer des données de table de faits à une hiérarchie lorsque la hiérarchie n’est pas connue. Le membre inconnu peut se trouver à l'un des niveaux suivants :  
  
-   Au niveau supérieur des hiérarchies d'attribut qui ne sont pas agrégées.  
  
-   Le premier niveau ci-dessous le **tous les** niveau pour les hiérarchies naturelles.  
  
-   À n'importe quel niveau pour les hiérarchies non naturelles.  
  
 Si une expression de membre est spécifiée, le **UnknownMember** fonction retourne l’enfant du membre inconnu du membre spécifié. Si le membre spécifié n'existe pas, la fonction retourne la valeur NULL.  
  
 Si une expression de hiérarchie est spécifiée, le **UnknownMember** fonction retourne le membre inconnu au niveau supérieur s’il en existe.  
  
 Si le membre inconnu n’existe pas sur le niveau ou le membre, le **UnknownMember** fonction crée un membre null.  
  
> [!NOTE]  
>  Si le membre inconnu n'existe pas dans cette hiérarchie ou ce membre, une erreur est générée.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous retourne le membre inconnu du membre All Products dans la hiérarchie d'attribut Product pour tous les membres de la dimension de mesures.  
  
```  
SELECT [Product].[Product].[All Products].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
 L'exemple ci-dessous retourne le membre inconnu de la hiérarchie Product Categories pour tous les membres de la dimension de mesures.  
  
```  
SELECT [Product].[Product Categories].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
