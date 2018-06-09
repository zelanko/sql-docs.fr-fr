---
title: LookupCube (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8f8338a542bf9e15816205930704c45a536a5629
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741718"
---
# <a name="lookupcube-mdx"></a>LookupCube (MDX)


  Retourne la valeur d'une expression MDX (Multidimensional Expressions) évaluée sur un autre cube spécifié dans la même base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Numeric expression syntax  
LookupCube(Cube_Name, Numeric_Expression )  
  
String expression syntax  
LookupCube(Cube_Name, String_Expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Name*  
 Une expression de chaîne valide qui spécifie le nom d’un cube.  
  
 *Numeric_expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
 *String_Expression*  
 Expression de chaîne valide qui correspond généralement à une expression MDX (Multidimensional Expressions) valide des coordonnées des cellules qui retourne une chaîne.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est spécifiée, la **LookupCube** fonction évalue l’expression numérique spécifiée dans le cube spécifié et retourne la valeur numérique qui en résulte.  
  
 Si une expression de chaîne est spécifiée, le **LookupCube** fonction évalue l’expression de chaîne spécifiée dans le cube spécifié et retourne la valeur de chaîne qui en résulte.  
  
 Le **LookupCube** fonctionne sur des cubes dans la même base de données que le cube source sur lequel la requête MDX qui contient le **LookupCube** fonction est en cours d’exécution.  
  
> [!IMPORTANT]  
>  Vous devez fournir tous les membres actuels nécessaires dans l'expression numérique ou de chaîne puisque le contexte de la requête actuelle n'est pas reporté dans le cube interrogé.  
  
 Tout calcul à l’aide de la **LookupCube** fonction est susceptible de souffrir de performances médiocres. Au lieu d'utiliser cette fonction, envisagez de modifier la conception votre solution afin que toutes les données dont vous avez besoin soient présentes dans un cube.  
  
## <a name="examples"></a>Exemples  
 La requête suivante illustre l'utilisation de LookupCube :  
  
 `WITH MEMBER MEASURES.LOOKUPCUBEDEMO AS`  
  
 `LOOKUPCUBE("Adventure Works", "[Measures].[In" + "ternet Sales Amount]")`  
  
 `SELECT MEASURES.LOOKUPCUBEDEMO  ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
