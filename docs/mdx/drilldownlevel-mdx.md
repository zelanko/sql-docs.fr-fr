---
title: DrilldownLevel (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6fdbc6ef265d51484160ab57a87e5672362326cc
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970070"
---
# <a name="drilldownlevel-mdx"></a>DrilldownLevel (MDX)


  Explore les membres d'un jeu un niveau en dessous du niveau le plus bas représenté dans le jeu.  
  
 La spécification du niveau d’exploration est facultative, mais si vous définissez le niveau, vous pouvez utiliser une **expression de niveau** ou le **niveau d’index**. Ces arguments s'excluent mutuellement. Enfin, si des membres calculés sont présents dans la requête, vous pouvez spécifier un argument pour les inclure dans l'ensemble de lignes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DrilldownLevel(Set_Expression [,[Level_Expression] ,[Index]] [,INCLUDE_CALC_MEMBERS])  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Level_Expression*  
 (Facultatif). Une expression MDX qui identifie explicitement le niveau à explorer. Si vous spécifiez une expression de niveau, ignorez l'argument d'index du niveau inférieur.  
  
 *Index*  
 (Facultatif). Expression numérique valide qui spécifie le nombre de hiérarchies pour lesquelles procéder à une extraction vers le bas au sein du jeu. Vous pouvez utiliser le niveau d'index de Level_Expression pour identifier explicitement le niveau jusqu'où explorer.  
  
 *Include_Calc_Members*  
 (Facultatif). Un indicateur spécifiant s'il faut inclure les membres calculés (s'ils existent) au niveau d'exploration.  
  
## <a name="remarks"></a>Remarques  
 La fonction **DrilldownLevel** retourne un jeu de membres enfants dans un ordre hiérarchique, en fonction des membres inclus dans le jeu spécifié. L'ordre est conservé parmi les membres d'origine dans le jeu spécifié, à ceci près que tous les membres enfants inclus dans le jeu de résultats de la fonction sont placés immédiatement sous leur membre parent.  
  
 Pour une structure de données hiérarchique multiniveau donnée, vous pouvez choisir explicitement un niveau jusqu'où explorer. Il y a deux moyens mutuellement exclusifs de spécifier le niveau. La première approche consiste à définir l’argument **Level_Expression** à l’aide d’une expression MDX qui retourne le niveau, une autre approche consiste à spécifier l’argument d' **index** , à l’aide d’une expression numérique qui spécifie le niveau par numéro.  
  
 Si une expression de niveau est spécifiée, la fonction construit un jeu dans un ordre hiérarchique en récupérant uniquement les enfants des membres situés au niveau spécifié. Si une expression de niveau est spécifiée et qu'il n'y a pas de membre à ce niveau, l'expression de niveau est ignorée.  
  
 Si vous spécifiez une valeur d'index, la fonction construit un jeu dans l'ordre hiérarchique en récupérant seulement les enfants des membres situés au niveau le plus bas suivant de la hiérarchie référencée dans le jeu spécifié, étant donné un index de base zéro.  
  
 Si aucune expression de niveau ou valeur d'index n'est spécifiée, la fonction génère un jeu dans l'ordre hiérarchique en extrayant uniquement les enfants des membres situés au niveau le plus bas de la première dimension référencée dans le jeu spécifié.  
  
 L’interrogation de la propriété XMLA MdpropMdxDrillFunctions vous permet de vérifier le niveau de prise en charge fourni par le serveur pour les fonctions de perçage. Pour plus d’informations, consultez [Propriétés XMLA prises en charge &#40;&#41;XMLA](https://docs.microsoft.com/analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) .  
  
## <a name="examples"></a>Exemples  
 Vous pouvez essayer les exemples suivants dans la fenêtre de requête MDX dans SSMS, en utilisant le cube Adventure Works.  
  
 **Exemple 1 : illustre la syntaxe minimale**  
  
 Le premier exemple illustre la syntaxe minimale pour **DrilldownLevel**. Le seul argument requis est une expression définie. Notez que lorsque vous exécutez cette requête, vous récupérez le parent [toutes les catégories] et les membres du niveau suivant : [accessoires], [vélos], etc. Bien que cet exemple soit simple, il montre l’objectif de base de la fonction **DrilldownLevel** , qui descend jusqu’au niveau suivant.  
  
```  
SELECT DRILLDOWNLEVEL({[Product].[Product Categories]} * {[Sales Territory].[Sales Territory]}}) ON COLUMNS  
FROM [Adventure Works]  
```  
  
 Exemple 2 : syntaxe alternative utilisant un niveau d’index explicite  
  
 Cet exemple montre la syntaxe alternative, où le niveau d'index est spécifié via une expression numérique. Dans ce cas, le niveau d'index est 0. Pour un index de base zéro, il s'agit de l'index de niveau le plus bas.  
  
```  
SELECT  
DRILLDOWNLEVEL({[Product].[Product Categories]} * {[Sales Territory].[Sales Territory]},,0) ON COLUMNS  
FROM [Adventure Works]  
```  
  
 Notez que le jeu de résultats est identique à celui de la requête précédente. En règle générale, la définition du niveau d'index n'est pas nécessaire, sauf si vous voulez que l'exploration commence à un niveau spécifique. Réexécutez la requête précédente en définissant la valeur de l'index à 1, puis à 2. Avec la valeur de l'index définie à 1, vous voyez que l'exploration commence au deuxième niveau de la hiérarchie. Avec la valeur de l'index définie à 2, l'exploration commence au troisième niveau de la hiérarchie, le niveau le plus élevé dans cet exemple. Plus l'expression numérique est élevée, plus le niveau de l'index est élevé.  
  
 **Exemple 3 : illustre une expression de niveau**  
  
 L'exemple suivant montre comment utiliser une expression de niveau. Pour un jeu qui représente une structure hiérarchique, l'utilisation d'une expression de niveau vous permet de choisir un niveau dans la hiérarchie pour commencer l'exploration.  
  
 Dans cet exemple, le niveau d’exploration commence à [City], en tant que deuxième argument de la fonction **DrilldownLevel** . Quand vous exécutez cette requête, l'exploration commence au niveau [City], pour les états Washington et Oregon. Pour la fonction **DrilldownLevel** , le jeu de résultats comprend également des membres au niveau supérieur, [codes postaux].  
  
```  
SELECT [Measures].[Internet Sales Amount] ON COLUMNS,  
   NON EMPTY (  
   DRILLDOWNLEVEL(  
       {[Customer].[Customer Geography].[Country].[United States],  
           DESCENDANTS(  
             { [Customer].[Customer Geography].[State-Province].[Washington],    
               [Customer].[Customer Geography].[State-Province].[Oregon]},   
               [Customer].[Customer Geography].[City]) } ,  
[Customer].[Customer Geography].[City] ) )  ON ROWS  
FROM [Adventure Works]  
```  
  
 **Exemple 4 : inclusion de membres calculés**  
  
 Le dernier exemple montre un membre calculé, qui apparaît en bas du jeu de résultats lorsque vous ajoutez l’indicateur **include_calculated_members** . Notez que l'indicateur est spécifié comme quatrième paramètre.  
  
 Cet exemple fonctionne, car le membre calculé est au même niveau que les membres non calculés. Le membre calculé [West Coast] est composé de membres de [United States], plus tous les membres du niveau inférieur à [United States].  
  
```  
WITH MEMBER   
[Customer].[Customer Geography].[Country].&[United States].[West Coast] AS  
[Customer].[Customer Geography].[State-Province].&[OR]&[US] +  
[Customer].[Customer Geography].[State-Province].&[WA]&[US] +  
[Customer].[Customer Geography].[State-Province].&[CA]&[US]  
SELECT [Measures].[Internet Order Count] ON 0,  
DRILLDOWNLEVEL([Customer].[Customer Geography].[Country].&[United States],,,INCLUDE_CALC_MEMBERS) on 1  
FROM [Adventure Works]  
```  
  
 Si vous supprimez seulement l'indicateur et que vous réexécutez la requête, vous obtenez les mêmes résultats sans le membre calculé, [West Coast].  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
