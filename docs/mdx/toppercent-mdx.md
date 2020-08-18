---
description: TopPercent (MDX)
title: Pourcentage (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5f0ae1e59a46c03300018f3243926bb30cef0398
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412858"
---
# <a name="toppercent-mdx"></a>TopPercent (MDX)


  Trie un jeu en ordre décroissant et retourne un jeu de tuples avec les valeurs les plus élevées dont le total cumulé est égal ou supérieur à un pourcentage spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
TopPercent(Set_Expression, Percentage, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Percentage*  
 Expression numérique valide qui précise le pourcentage de tuples à retourner.  
  
> [!IMPORTANT]  
>  Le *pourcentage* doit être une valeur positive ; les valeurs négatives génèrent une erreur.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 La fonction Coen- **pourcentage** calcule la somme de l’expression numérique spécifiée évaluée sur le jeu spécifié, en triant le jeu dans l’ordre décroissant. Elle retourne ensuite les éléments dotés des valeurs les plus élevées et dont le pourcentage cumulé du total de la valeur additionnée correspond au moins au pourcentage indiqué. Enfin, elle retourne le plus petit sous-ensemble d'un jeu dont le total cumulé est égal au moins au pourcentage précisé. Les éléments retournés sont triés du plus grand au plus petit.  
  
> [!WARNING]  
>  Si *numeric_expression*  retourne une valeur négative, le **pourcentage** de valeur de la colonne ne retourne qu’une (1) ligne.  
>   
>  Consultez le deuxième exemple pour une présentation détaillée de ce comportement.  
  
> [!IMPORTANT]  
>  À l’instar de la fonction [BottomPercent](../mdx/bottompercent-mdx.md) , la fonction Coen- **pourcentage** arrête toujours la hiérarchie.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant retourne les villes les mieux classées représentant 10 % des ventes des revendeurs pour la catégorie Bike. Le résultat est trié par ordre décroissant, en commençant par la ville associé aux meilleures ventes.  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopPercent  
   ({[Geography].[Geography].[City].Members}  
   , 10  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].[Bikes])  
```  
  
 L’expression ci-dessus génère les résultats suivants :  
  
|City|Reseller Sales Amount|  
|-|---------------------------|  
|Toronto|$3 508 904,84|  
|London|$1 521 530,09|  
|Seattle|$1 209 418,16|  
|Paris|$1 170 425,18|  
  
 L'ensemble de données d'origine peut être obtenu avec la requête suivante et retourne 588 lignes :  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
Order  
   ({[Geography].[Geography].[City].Members}  
   , [Measures].[Reseller Sales Amount]  
   , BDESC  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].[Bikes])  
  
```  
  
## <a name="example"></a>Exemple  
 La procédure pas à pas suivante permet de comprendre l’effet des valeurs négatives dans le *numeric_expression*. D'abord, établissons le contexte sous-jacent au comportement.  
  
 La requête suivante retourne une table contenant le montant des ventes (Sales Amount), le coût total du produit (Total Product Cost) et le profit brut (Gross Profit) des revendeurs, triés par ordre de profit décroissant. Notez qu'il y a uniquement des valeurs négatives pour les profits ; par conséquent, la plus petite perte apparaît en haut.  
  
```  
SELECT { [Measures].[Reseller Sales Amount], [Measures].[Reseller Total Product Cost], [Measures].[Reseller Gross Profit] } ON columns  
     ,  ORDER( [Product].[Product Categories].[Bikes].[Touring Bikes].children, [Measures].[Reseller Gross Profit], BDESC )   ON rows  
FROM [Adventure Works]  
  
```  
  
 La requête ci-dessus retourne les résultats suivants ; les lignes de la section centrale ont été supprimées pour faciliter la lisibilité.  
  
|Vélos de tourisme|Reseller Sales Amount|Reseller Total Product Cost|Reseller Gross Profit|  
|-|---------------------------|---------------------------------|---------------------------|  
|Touring-2000 Blue, 50|$157 444,56|$163 112,57|($5 668,01)|  
|Tourisme-2000 bleu, 46|$321 027,03|$333 021,50|($11 994,47)|  
|Tourisme-3000 bleu, 62|$87 773,61|$100 133,52|($12 359,91)|  
|...|...|...|...|  
|Tourisme-1000 jaune, 46|$1 016 312,83|$1 234 454,27|($218 141,44)|  
|Touring-1000 Yellow, 60|$1 184 363,30|$1 443 407,51|($259 044,21)|  
  
 Maintenant, si vous deviez présenter les vélos les mieux classés représentant 100 % du profit, vous écririez la requête suivante :  
  
```  
SELECT { [Measures].[Reseller Sales Amount], [Measures].[Reseller Total Product Cost], [Measures].[Reseller Gross Profit] } ON columns  
     ,  TOPPERCENT( [Product].[Product Categories].[Bikes].[Touring Bikes].children, 100,[Measures].[Reseller Gross Profit] )   ON rows  
FROM [Adventure Works]  
  
```  
  
 Notez que la requête demande cent pour cent (100 %) ; ce qui signifie que toutes les lignes doivent être retournées. Toutefois, étant donné qu’il y a des valeurs négatives dans le *numeric_expression* , une seule ligne est retournée.  
  
|Vélos de tourisme|Reseller Sales Amount|Reseller Total Product Cost|Reseller Gross Profit|  
|-|---------------------------|---------------------------------|---------------------------|  
|Touring-2000 Blue, 50|$157 444,56|$163 112,57|($5 668,01)|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
