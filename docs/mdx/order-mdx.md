---
description: Order (MDX)
title: Ordre (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4db745ea01a56d68fe259ebb2fffb5aae250abd4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471741"
---
# <a name="order-mdx"></a>Order (MDX)


  Organise les membres d'un jeu spécifié, en conservant ou non la hiérarchie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Numeric expression syntax  
Order(Set_Expression, Numeric_Expression   
[ , { ASC | DESC | BASC | BDESC } ] )  
  
String expression syntax  
Order(Set_Expression, String_Expression   
[ , { ASC | DESC | BASC | BDESC } ] )  
  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
 *String_Expression*  
 Expression de chaîne valide qui correspond généralement à une expression MDX (Multidimensional Expressions) valide des coordonnées des cellules qui retournent un nombre exprimé sous forme de chaîne.  
  
## <a name="remarks"></a>Notes  
 La fonction **Order** peut être hiérarchique (comme spécifié à l’aide de l’indicateur **ASC** ou **desc** ) ou non hiérarchique (comme spécifié à l’aide de l’indicateur **BASC** ou **BDESC** ; la valeur **B** correspond à « Break Hierarchy »). Si **ASC** ou **desc** est spécifié, la fonction **Order** trie d’abord les membres en fonction de leur position dans la hiérarchie, puis trie chaque niveau. Si **BASC** ou **BDESC** est spécifié, la fonction **Order** organise les membres de l’ensemble sans tenir compte de la hiérarchie. Dans aucun indicateur n’est spécifié, **ASC** est la valeur par défaut.  
  
 Si la fonction **Order** est utilisée avec un ensemble où deux hiérarchies ou plus sont jointure croisée et que l’indicateur **desc** est utilisé, seuls les membres de la dernière hiérarchie du jeu sont triés. Il s'agit là d'une différence par rapport à Analysis Services 2000 où toutes les hiérarchies du jeu étaient triées.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne, à partir du cube **Adventure Works** , le nombre de commandes Reseller pour tous les trimestres calendaires de la hiérarchie Calendar sur la dimension Date. La fonction **Order** réorganise le jeu pour l’axe Rows. La fonction **Order** trie le jeu par `[Reseller Order Count]` dans l’ordre hiérarchique décroissant, comme déterminé par la `[Calendar]` hiérarchie.  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,DESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Notez que dans cet exemple, lorsque l’indicateur **desc** est modifié en **BDESC**, la hiérarchie est rompue et la liste des trimestres civils est retournée sans tenir compte de la hiérarchie :  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,BDESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 L'exemple ci-dessous retourne la mesure Reseller Sales pour les cinq premières sous-catégories de vente de produits, quelle que soit la hiérarchie et conformément à la mesure Reseller Gross Profit (marge brute du revendeur). La fonction de **sous-ensemble** est utilisée pour retourner uniquement les 5 premiers tuples dans le jeu après que le résultat a été ordonné à l’aide de la fonction **Order** .  
  
 `SELECT Subset`  
  
 `(Order`  
  
 `([Product].[Product Categories].[SubCategory].members`  
  
 `,[Measures].[Reseller Gross Profit]`  
  
 `,BDESC`  
  
 `)`  
  
 `,0`  
  
 `,5`  
  
 `) ON 0`  
  
 `FROM [Adventure Works]`  
  
 L’exemple suivant utilise la fonction **Rank** pour classer les membres de la hiérarchie City, en fonction de la mesure Reseller Sales Amount, puis les affiche dans l’ordre de classement. En utilisant la fonction **Order** pour trier en premier le jeu de membres de la hiérarchie City, le tri n’est effectué qu’une seule fois et suivi d’une analyse linéaire avant d’être présenté dans l’ordre de tri.  
  
```  
WITH   
SET OrderedCities AS Order  
   ([Geography].[City].[City].members  
   , [Measures].[Reseller Sales Amount], BDESC  
   )  
MEMBER [Measures].[City Rank] AS Rank  
   ([Geography].[City].CurrentMember, OrderedCities)  
SELECT {[Measures].[City Rank],[Measures].[Reseller Sales Amount]}  ON 0   
,Order  
   ([Geography].[City].[City].MEMBERS  
   ,[City Rank], ASC)  
    ON 1  
FROM [Adventure Works]  
```  
  
 L’exemple suivant retourne le nombre de produits dans le jeu qui sont uniques, à l’aide de la fonction **Order** pour ordonner les tuples non vides avant d’utiliser la fonction **Filter** . La fonction **CurrentOrdinal** est utilisée pour comparer et éliminer les liens.  
  
```  
WITH MEMBER [Measures].[PrdTies] AS Count  
   (Filter  
      (Order  
        (NonEmpty  
          ([Product].[Product].[Product].Members  
          , {[Measures].[Reseller Order Quantity]}  
          )  
       , [Measures].[Reseller Order Quantity]  
       , BDESC  
       ) AS OrdPrds  
    , (OrdPrds.CurrentOrdinal < OrdPrds.Count   
       AND [Measures].[Reseller Order Quantity] =   
          ( [Measures].[Reseller Order Quantity]  
            , OrdPrds.Item  
               (OrdPrds.CurrentOrdinal  
               )  
            )  
         )  
         OR (OrdPrds.CurrentOrdinal > 1   
            AND [Measures].[Reseller Order Quantity] =   
               ([Measures].[Reseller Order Quantity]  
               , OrdPrds.Item  
                  (OrdPrds.CurrentOrdinal-2)  
                )  
             )  
          )  
       )  
SELECT {[Measures].[PrdTies]} ON 0  
FROM [Adventure Works]  
```  
  
 Pour comprendre le fonctionnement de l’indicateur **desc** avec les jeux de tuples, examinez d’abord les résultats de la requête suivante :  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
,[Measures].[Tax Amount], DESC)  
ON 1  
FROM [Adventure Works]  
  
```  
  
 Sur l'axe des lignes, vous pouvez voir que les groupes du secteur de vente ont été classés par ordre décroissant par Montant des taxes, comme suit : Amérique du Nord, Europe, Pacifique, NA. Voyons maintenant ce qui se passe si nous faisons une jointure entre le jeu de groupes de secteurs de vente et l’ensemble de sous-catégories de produits et si vous appliquez la fonction de **commande** de la même façon, comme suit :  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
*  
{[Product].[Product Categories].[subCategory].Members}  
,[Measures].[Tax Amount], DESC)  
ON 1  
FROM [Adventure Works]  
  
```  
  
 Alors que le jeu de sous-catégories de produits a été trié par ordre décroissant, hiérarchique, les groupes du secteur de vente ne sont plus triés et s'affichent dans l'ordre dans lequel ils apparaissent dans la hiérarchie : Europe, NA, Amérique du Nord et Pacifique. Cela vient du fait que seule la dernière hiérarchie du jeu de tuples, sous-catégories de produits, est triée. Pour reproduire le comportement de Analysis Services 2000, utilisez une série de fonctions **generate** imbriquées pour trier chaque ensemble avant qu’il ne soit jointure croisée, par exemple :  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
GENERATE(  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
,[Measures].[Tax Amount], DESC)  
,  
ORDER(  
[Sales Territory].[Sales Territory].CURRENTMEMBER  
*  
{[Product].[Product Categories].[subCategory].Members}  
,[Measures].[Tax Amount], DESC))  
ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
