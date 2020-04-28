---
title: Intersect (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f253dad526c509edff5c837b61ae2faae07d5758
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68105360"
---
# <a name="intersect-mdx"></a>Intersect (MDX)


  Retourne l'intersection de deux ensembles d'entrée, en conservant éventuellement les doublons.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Intersect(Set_Expression1 , Set_Expression2 [ , ALL ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Set_Expression2*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 La fonction **Intersect** retourne l’intersection de deux jeux. Par défaut, cette fonction supprime les doublons des deux ensembles avant l'intersection. Les deux ensembles spécifiés doivent avoir le même dimensionnement.  
  
 L’indicateur **All** facultatif conserve les doublons. Si **All** est spécifié, la fonction **Intersect** croise les éléments non dupliqués comme d’habitude, et croise chaque doublon dans le premier jeu qui a un doublon correspondant dans le deuxième jeu. Les deux ensembles spécifiés doivent avoir le même dimensionnement.  
  
## <a name="example"></a>Exemple  
 La requête suivante retourne les années 2003 et 2004, les deux membres qui apparaissent dans les deux ensembles spécifiés :  
  
 `SELECT`  
  
 `INTERSECT(`  
  
 `{[Date].[Calendar Year].&[2001], [Date].[Calendar Year].&[2002],[Date].[Calendar Year].&[2003]}`  
  
 `, {[Date].[Calendar Year].&[2002],[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]})`  
  
 `ON 0`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 La requête suivante est inopérante, car les deux jeux spécifiés contiennent des membres rattachés à des hiérarchies différentes :   
  
 `SELECT`  
  
 `INTERSECT(`  
  
 `{[Date].[Calendar Year].&[2001]}`  
  
 `, {[Customer].[City].&[Abingdon]&[ENG]})`  
  
 `ON 0`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
