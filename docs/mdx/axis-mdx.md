---
description: Axis (MDX)
title: Axe (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 47e0da231b0792e0099f5e6ee4fe8eda9fb45f9d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421933"
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
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
