---
title: Générer (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c7a6008129d6b0a4c59412428c31f6e5de625f1f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68005903"
---
# <a name="generate-mdx"></a>Generate (MDX)


  Applique un jeu à chaque membre d'un autre jeu, puis effectue la jointure par union des jeux résultants. Cette fonction retourne également une chaîne concaténée créée par l'évaluation d'une expression de chaîne sur un jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set expression syntax  
Generate( Set_Expression1 ,  Set_Expression2 [ , ALL ]  )  
  
String expression syntax  
Generate( Set_Expression1 ,  String_Expression [ ,Delimiter ]  )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Set_Expression2*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *String_Expression*  
 Expression de chaîne valide qui correspond généralement au nom du membre actuel (CurrentMember.Name) de chaque tuple dans le jeu spécifié.  
  
 *Delimiter*  
 Délimiteur valide exprimé en tant qu'expression de chaîne.  
  
## <a name="remarks"></a>Notes  
 Si un deuxième jeu est spécifié, la fonction **generate** retourne un jeu généré en appliquant les tuples du deuxième jeu à chaque tuple du premier jeu, puis en joignant les jeux résultants par Union. Si **All** est spécifié, la fonction conserve les doublons dans le jeu résultant.  
  
 Si une expression de chaîne est spécifiée, la fonction **generate** retourne une chaîne générée en évaluant l’expression de chaîne spécifiée par rapport à chaque tuple du premier jeu, puis en concaténant les résultats. Vous pouvez éventuellement délimiter la chaîne en séparant chaque résultat dans la chaîne concaténée obtenue.  
  
## <a name="examples"></a>Exemples  
  
### <a name="set"></a>Définissez  
 Dans l'exemple suivant, la requête retourne un jeu qui contient le montant des ventes sur Internet de Mesure quatre fois, parce qu'il y a quatre membres dans le jeu [Date].[Calendar Year].[Calendar Year].MEMBERS :  
  
```  
SELECT   
GENERATE( [Date].[Calendar Year].[Calendar Year].MEMBERS  
, {[Measures].[Internet Sales Amount]}, ALL)  
ON 0  
FROM [Adventure Works]  
```  
  
 La suppression de ALL modifie la requête afin que le Montant des ventes sur Internet soit retourné une fois uniquement :  
  
```  
SELECT   
GENERATE( [Date].[Calendar Year].[Calendar Year].MEMBERS  
, {[Measures].[Internet Sales Amount]})  
ON 0  
FROM [Adventure Works]  
```  
  
 L’utilisation pratique la plus courante de la **génération** consiste à évaluer une expression d’ensemble complexe, telle que TopCount, sur un ensemble de membres. L'exemple de requête suivant affiche les 10 premiers produits pour chaque année civile sur les lignes :  
  
```  
SELECT   
{[Measures].[Internet Sales Amount]}  
ON 0,  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS  
, TOPCOUNT(  
[Date].[Calendar Year].CURRENTMEMBER  
*  
[Product].[Product].[Product].MEMBERS  
,10, [Measures].[Internet Sales Amount]))  
ON 1  
FROM [Adventure Works]  
```  
  
 Notez qu’une valeur Top 10 différente est affichée pour chaque année, et que l’utilisation de la fonction **generate** est la seule façon d’obtenir ce résultat. La simple jonction croisée des années civiles et du jeu des 10 premiers produits affichent les 10 premiers produits pour toutes les périodes, pour chaque année, comme illustré dans l'exemple suivant :  
  
```  
SELECT   
{[Measures].[Internet Sales Amount]}  
ON 0,  
[Date].[Calendar Year].[Calendar Year].MEMBERS  
*   
TOPCOUNT(  
[Product].[Product].[Product].MEMBERS  
,10, [Measures].[Internet Sales Amount])  
ON 1  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>String  
 L’exemple suivant illustre l’utilisation de la commande **generate** pour retourner une chaîne :  
  
```  
WITH   
MEMBER MEASURES.GENERATESTRINGDEMO AS  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS,  
[Date].[Calendar Year].CURRENTMEMBER.NAME)  
MEMBER MEASURES.GENERATEDELIMITEDSTRINGDEMO AS  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS,  
[Date].[Calendar Year].CURRENTMEMBER.NAME, " AND ")  
SELECT   
{MEASURES.GENERATESTRINGDEMO, MEASURES.GENERATEDELIMITEDSTRINGDEMO}  
ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  Cette forme de la fonction **generate** peut être utile lors du débogage des calculs, car elle vous permet de retourner une chaîne affichant les noms de tous les membres d’un jeu. Cela peut être plus facile à lire que la représentation MDX stricte d’un ensemble que la fonction [SetToStr &#40;mdx&#41;](../mdx/settostr-mdx.md) retourne.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
