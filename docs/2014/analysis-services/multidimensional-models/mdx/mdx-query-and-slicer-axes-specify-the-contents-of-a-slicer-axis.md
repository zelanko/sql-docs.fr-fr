---
title: Spécification du contenu d’un axe de secteur (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slicer axis
- filtering data [MDX]
ms.assetid: c56b0a70-cdec-427f-990e-425290344e7d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8620c54970ea14a2ac01c85262a372d2b3db0d68
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546261"
---
# <a name="specifying-the-contents-of-a-slicer-axis-mdx"></a>Spécification du contenu d'un axe de secteur (MDX)
  L'axe de secteur filtre les données retournées par l'instruction SELECT MDX (Multidimensional Expressions), en restreignant les données retournées de telle sorte que seules les données communes aux membres spécifiés soient retournées. Il peut être perçu comme un axe supplémentaire invisible dans une requête. L'axe de secteur est défini dans la clause WHERE de l'instruction SELECT de MDX.  
  
## <a name="slicer-axis-syntax"></a>Syntaxe de l'axe de secteur  
 Pour spécifier de façon explicite un axe de secteur, utilisez la clause `<SELECT slicer axis clause>` dans MDX, comme dans la syntaxe suivante :  
  
```  
<SELECT slicer axis clause> ::=  WHERE Set_Expression  
```  
  
 Dans la syntaxe d'axe de secteur indiquée, `Set_Expression` peut prendre soit une expression de tuple, qui est traitée comme un jeu pour les besoins d'évaluation de la clause, soit une expression d'ensemble. Si une expression d'ensemble est spécifiée, MDX tentera d'évaluer le jeu, en agrégeant les cellules du résultat dans chaque tuple du jeu. En d'autres termes, MDX tentera d'utiliser la fonction [Aggregate](/sql/mdx/aggregate-mdx) sur le jeu, agrégeant chaque mesure par sa fonction d'agrégation associée. En outre, si l'expression d'ensemble ne peut pas être exprimée comme une jointure croisée des membres d'une hiérarchie d'attributs, MDX traite les cellules exclues de l'expression d'ensemble pour le découpage comme NULL, pour les besoins de l'évaluation.  
  
> [!IMPORTANT]  
>  Contrairement à la clause WHERE dans SQL, la clause WHERE d'une instruction MDX SELECT ne filtre jamais directement ce qui est retourné sur l'axe des lignes d'une requête. Pour filtrer ce qui s'affiche sur l'axe des lignes ou des colonnes d'une requête, vous pouvez utiliser diverses fonctions MDX, par exemple FILTER, NONEMPTY et TOPCOUNT.  
  
### <a name="implicit-slicer-axis"></a>Axe de secteur implicite  
 Si un membre d'une hiérarchie du cube n'est pas explicitement inclus dans un axe de requête, le membre par défaut de cette hiérarchie est implicitement inclus dans l'axe de secteur. Pour plus d’informations sur les membres par défaut, consultez [Définir un membre par défaut](../attribute-properties-define-a-default-member.md).  
  
## <a name="examples"></a>Exemples  
 La requête suivante n'inclut pas de clause WHERE, et retourne la valeur de la mesure Internet Sales Amount pour toutes les années civiles :  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
 L'ajout d'une clause WHERE, comme suit :  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Country].&[United States])  
  
```  
  
 ne modifie pas ce qui est retourné sur les lignes ou les colonnes de la requête ; cela modifie les valeurs retournées pour chaque cellule. Dans cet exemple, la requête est découpée de façon à retourner la valeur du montant des ventes sur Internet (Internet Sales Amount) de toutes les années civiles (Calendar Years), mais uniquement pour les clients (Customers) qui habitent aux États-Unis. Il est possible d'ajouter plusieurs membres de différentes hiérarchies à la clause WHERE. La requête suivante affiche la valeur du montant des ventes sur Internet (Internet Sales Amount) de toutes les années civiles (Calendar Years) pour les clients (Customers) qui habitent aux États-Unis et qui ont acheté des produits (Products) de la catégorie des vélos (Bikes) :  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Country].&[United States], [Product].[Category].&[1])  
```  
  
 Si vous voulez utiliser plusieurs membres de la même hiérarchie, vous devez inclure un jeu dans la clause WHERE. Par exemple, la requête suivante affiche la valeur du montant des ventes sur Internet (Internet Sales Amount) de toutes les années civiles (Calendar Years) pour les clients (Customers) qui ont acheté des produits (Products) de la catégorie des vélos (Bikes) et qui habitent aux États-Unis ou au Royaume-Uni :  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE(  
{[Customer].[Customer Geography].[Country].&[United States]  
, [Customer].[Customer Geography].[Country].&[United Kingdom]}  
, [Product].[Category].&[1])  
  
```  
  
 Comme indiqué précédemment, l'utilisation d'un jeu dans la clause WHERE effectue implicitement un agrégat des valeurs pour tous les membres du jeu. Dans le cas présent, la requête affiche les valeurs agrégées pour les États-Unis et le Royaume-Uni dans chaque cellule.  
  
  
