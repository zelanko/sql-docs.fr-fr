---
title: IsEmpty (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8b31b884e0f86bf2aebe4859cd1c7a441669e813
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905992"
---
# <a name="isempty-mdx"></a>IsEmpty (MDX)


  Retourne une valeur indiquant si l'expression évaluée est la valeur de la cellule vide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IsEmpty(Value_Expression)   
```  
  
## <a name="arguments"></a>Arguments  
 *Value_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne généralement les coordonnées des cellules d'un membre ou d'un tuple.  
  
## <a name="remarks"></a>Notes  
 La fonction **IsEmpty** retourne la valeur **true** si l’expression évaluée est une valeur de cellule vide. Dans le cas contraire, cette fonction retourne **false**.  
  
> [!NOTE]  
>  La propriété par défaut d'un membre est la valeur du membre.  
  
 La fonction **IsEmpty** est le seul moyen de tester de manière fiable une cellule vide, car la valeur de cellule vide a [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]une signification particulière dans.  
  
> [!IMPORTANT]  
>  Si l’évaluation de l’expression de valeur retourne une erreur, la fonction retourne **false**. Une expression de valeur peut retourner une erreur, notamment si la référence des propriétés désigne une propriété non valide ou inexistante.  
  
 Pour plus d'informations sur les cellules vides, consultez la documentation OLE DB.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant retourne TRUE si le Montant des ventes sur Internet pour le membre actuel dans la hiérarchie Fiscal de la dimension Date retourne une cellule vide :  
  
 `WITH MEMBER MEASURES.ISEMPTYDEMO AS`  
  
 `IsEmpty([Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.ISEMPTYDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de valeurs vides](../mdx/working-with-empty-values.md)   
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
