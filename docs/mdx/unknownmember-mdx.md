---
description: UnknownMember (MDX)
title: UnknownMember (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0489556836b943ba91d4e17b3a164aeca0c648d2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341145"
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
 Analysis Services crée un membre inconnu pour associer les données de la table de faits à une hiérarchie lorsque la hiérarchie n’est pas connue. Le membre inconnu peut se trouver à l'un des niveaux suivants :  
  
-   Au niveau supérieur des hiérarchies d'attribut qui ne sont pas agrégées.  
  
-   Au premier niveau sous le niveau **tous** pour les hiérarchies naturelles.  
  
-   À n'importe quel niveau pour les hiérarchies non naturelles.  
  
 Si une expression de membre est spécifiée, la fonction **UnknownMember** retourne l’enfant de membre inconnu du membre spécifié. Si le membre spécifié n'existe pas, la fonction retourne la valeur NULL.  
  
 Si une expression de hiérarchie est spécifiée, la fonction **UnknownMember** retourne le membre inconnu au niveau supérieur, s’il en existe un.  
  
 Si le membre inconnu n’existe pas sur le niveau ou le membre, la fonction **UnknownMember** crée un membre null.  
  
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
  
  
