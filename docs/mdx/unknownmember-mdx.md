---
title: UnknownMember (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UnknownMember
dev_langs:
- kbMDX
helpviewer_keywords:
- UnknownMember function
ms.assetid: 5ae39cbe-65c8-4a59-9548-71b28ecf6eb5
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 131993b1038229138df3e7d084b5d842693b7f0f
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="unknownmember-mdx"></a>UnknownMember (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le membre inconnu associé à un niveau ou un membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member expression syntax  
Member_Expression.UnknownMember  
  
Hierarchy_expression syntax  
Hierarchy_Expression.UnknownMember  
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Hierarchy_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] crée un membre inconnu pour associer des données de table de faits à une hiérarchie lorsque la hiérarchie n’est pas connue. Le membre inconnu peut se trouver à l'un des niveaux suivants :  
  
-   Au niveau supérieur des hiérarchies d'attribut qui ne sont pas agrégées.  
  
-   Au premier niveau en dessous du **tous les** niveau pour les hiérarchies naturelles.  
  
-   À n'importe quel niveau pour les hiérarchies non naturelles.  
  
 Si une expression de membre est spécifiée, le **UnknownMember** fonction retourne l’enfant du membre inconnu du membre spécifié. Si le membre spécifié n'existe pas, la fonction retourne la valeur NULL.  
  
 Si une expression de hiérarchie est spécifiée, la **UnknownMember** fonction retourne le membre inconnu au niveau supérieur s’il en existe.  
  
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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

