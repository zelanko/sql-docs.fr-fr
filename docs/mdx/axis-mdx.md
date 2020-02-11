---
title: Axe (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fa65c1531be29273c0a838b978109bbd1c8a2b18
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68016981"
---
# <a name="axis-mdx"></a>Axis (MDX)


  Retourne l'ensemble des tuples sur un axe spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Axis(Axis_Number)  
```  
  
## <a name="arguments"></a>Arguments  
 *Axis_Number*  
 Expression numérique valide qui précise le numéro d'axe.  
  
## <a name="remarks"></a>Notes  
 La fonction **Axis** utilise la position de base zéro d’un axe pour retourner le jeu de tuples sur un axe. Par exemple, `Axis(0)` retourne l'axe COLUMNS, `Axis(1)` retourne l'axe ROWS, et ainsi de suite. La fonction **Axis** ne peut pas être utilisée sur l’axe de filtre. Cette fonction peut être utilisée pour faire connaître à des membres calculés le contexte de la requête en cours d'exécution. Par exemple, vous pouvez avoir besoin d'un membre calculé qui fournit la somme des membres sélectionnés seulement sur l'axe des lignes. Elle peut également être utilisée pour faire dépendre la définition d'un axe de la définition d'un autre. Par exemple, en classant le contenu de l'axe des lignes selon la valeur du premier élément sur l'axe des colonnes.  
  
> [!NOTE]  
>  Un axe ne peut référencer qu'un axe antérieur. Par exemple, `Axis(0)` doit se produire après l'évaluation de l'axe COLUMNS, comme sur un axe ROW ou PAGE.  
  
## <a name="examples"></a>Exemples  
 L'exemple de requête suivant montre comment utiliser la fonction Axis :  
  
 `WITH MEMBER MEASURES.AXISDEMO AS`  
  
 `SETTOSTR(AXIS(1))`  
  
 `SELECT MEASURES.AXISDEMO ON 0,`  
  
 `[Date].[Calendar Year].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 L'exemple suivant illustre l'utilisation de la fonction Axis au sein d'un membre calculé :  
  
 `WITH MEMBER MEASURES.AXISDEMO AS`  
  
 `SUM(AXIS(1), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.AXISDEMO} ON 0,`  
  
 `{[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
