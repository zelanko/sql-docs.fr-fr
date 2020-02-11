---
title: LookupCube (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ec18b600c369de872df5f6eadf06ef6c30c88efa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68098514"
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
 Expression de chaîne valide qui spécifie le nom d’un cube.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
 *String_Expression*  
 Expression de chaîne valide qui correspond généralement à une expression MDX (Multidimensional Expressions) valide des coordonnées des cellules qui retourne une chaîne.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est spécifiée, la fonction **LookupCube** évalue l’expression numérique spécifiée dans le cube spécifié et retourne la valeur numérique résultante.  
  
 Si une expression de chaîne est spécifiée, la fonction **LookupCube** évalue l’expression de chaîne spécifiée dans le cube spécifié et retourne la valeur de chaîne résultante.  
  
 La fonction **LookupCube** fonctionne sur les cubes dans la même base de données que le cube source sur lequel s’exécute la requête MDX qui contient la fonction **LookupCube** .  
  
> [!IMPORTANT]  
>  Vous devez fournir tous les membres actuels nécessaires dans l'expression numérique ou de chaîne puisque le contexte de la requête actuelle n'est pas reporté dans le cube interrogé.  
  
 Tout calcul à l’aide de la fonction **LookupCube** risque de nuire aux performances. Au lieu d'utiliser cette fonction, envisagez de modifier la conception votre solution afin que toutes les données dont vous avez besoin soient présentes dans un cube.  
  
## <a name="examples"></a>Exemples  
 La requête suivante illustre l'utilisation de LookupCube :  
  
 `WITH MEMBER MEASURES.LOOKUPCUBEDEMO AS`  
  
 `LOOKUPCUBE("Adventure Works", "[Measures].[In" + "ternet Sales Amount]")`  
  
 `SELECT MEASURES.LOOKUPCUBEDEMO  ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
