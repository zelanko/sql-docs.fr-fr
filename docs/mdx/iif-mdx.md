---
title: IIf (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 87b7b030776c1c18bb13307bf97db721fe472bd3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68105336"
---
# <a name="iif-mdx"></a>IIf (MDX)


  Évalue différentes expressions de branche, selon qu'une condition booléenne renvoie true ou false.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IIf(Logical_Expression, Expression1 [HINT <hints>], Expression2 [HINT <hints>])  
```  
  
## <a name="arguments"></a>Arguments  
 La fonction IIf accepte trois arguments : IIF (\<condition>, \<Then Branch>, \<sinon Branch>).  
  
 *Logical_Expression*  
 Condition qui prend la **valeur true** (1) ou **false** (0). Ce doit être une expression logique MDX (Multidimensional Expressions) valide.  
  
 *Expression1 (indicateur) [hâtif | Strict | Lazy]]*  
 Utilisé lorsque l’expression logique prend la **valeur true**. Expression1 doit être une expression MDX (Multidimensional Expressions) valide.  
  
 *Option Expression2 [hâtif | Strict | Lazy]]*  
 Utilisé lorsque l’expression logique prend la **valeur false**. Expression2 doit être une expression MDX (Multidimensional Expressions) valide.  
  
## <a name="remarks"></a>Notes  
 La condition spécifiée par l’expression logique prend la valeur **false** lorsque la valeur de cette expression est égale à zéro. Toute autre valeur prend la valeur **true**.  
  
 Lorsque la condition a la **valeur true**, la fonction **IIf** retourne la première expression. Sinon, la fonction retourne la seconde expression.  
  
 Les expressions spécifiées peuvent retourner des valeurs ou des objets MDX. De plus, leurs types ne doivent pas obligatoirement correspondre.  
  
 La fonction **IIf** n’est pas recommandée pour la création d’un ensemble de membres en fonction de critères de recherche. Utilisez plutôt la fonction [Filter](../mdx/filter-mdx.md) pour évaluer chaque membre d’un jeu spécifié par rapport à une expression logique et retourner un sous-ensemble de membres.  
  
> [!NOTE]  
>  Si l'une des expressions prend la valeur NULL, le jeu de résultats est NULL une fois cette condition satisfaite.  
  
 HINT est un modificateur facultatif qui détermine comment et quand l'expression est évaluée. Il vous permet de modifier le plan de requête par défaut en spécifiant la façon dont l'expression est évaluée.  
  
-   EAGER évalue l'expression dans le sous-espace IIF d'origine.  
  
-   STRICT évalue l'expression uniquement dans le sous-espace limité créé par l'expression de condition logique.  
  
-   LAZY évalue l'expression en mode cellule-par-cellule.  
  
 Tandis que EAGER et STRICT s'appliquent uniquement aux branches then-else de IIF, LAZY s'applique à toutes les expressions MDX. Toutes les expressions MDX peuvent être suivies par HINT LAZY, qui évaluent cette expression en mode cellule-par-cellule.  
  
 EAGER et STRICT s'excluent mutuellement dans l'indicateur ; ils peuvent être utilisés dans la même fonction IIF(,,) sur des expressions différentes.  
  
 Pour plus d’informations, consultez [indicateurs de requête de la fonction IIf dans SQL Server Analysis Services 2008](https://go.microsoft.com/fwlink/?LinkId=269540) et [plans d’exécution et indicateurs de plan pour la fonction MDX IIF et l’instruction case](https://go.microsoft.com/fwlink/?LinkId=269565).  
  
## <a name="examples"></a>Exemples  
 La requête suivante illustre une utilisation simple de **IIf** à l’intérieur d’une mesure calculée pour retourner une des deux valeurs de chaîne différentes lorsque la mesure Internet Sales Amount est supérieure ou inférieure à $10000 :  
  
 `WITH MEMBER MEASURES.IIFDEMO AS`  
  
 `IIF([Measures].[Internet Sales Amount]>10000`  
  
 `, "Sales Are High", "Sales Are Low")`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.IIFDEMO} ON 0,`  
  
 `[Date].[Date].[Date].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 Une utilisation très courante d'IIF est de gérer les erreurs de 'division par zéro' dans les mesures calculées, comme dans l'exemple suivant :  
  
 `WITH`  
  
 `//Returns 1.#INF when the previous period contains no value`  
  
 `//but the current period does`  
  
 `MEMBER MEASURES.[Previous Period Growth With Errors] AS`  
  
 `([Measures].[Internet Sales Amount]-([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER))`  
  
 `/`  
  
 `([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER)`  
  
 `,FORMAT_STRING='PERCENT'`  
  
 `//Traps division by zero and returns null when the previous period contains`  
  
 `//no value but the current period does`  
  
 `MEMBER MEASURES.[Previous Period Growth] AS`  
  
 `IIF(([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER)=0,`  
  
 `NULL,`  
  
 `([Measures].[Internet Sales Amount]-([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER))`  
  
 `/`  
  
 `([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER)`  
  
 `),FORMAT_STRING='PERCENT'`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.[Previous Period Growth With Errors], MEASURES.[Previous Period Growth]} ON 0,`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004],`  
  
 `[Date].[Calendar].[Date])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Product].[Product Categories].[Subcategory].&[26])`  
  
 Voici un exemple de **IIf** qui retourne l’un des deux jeux à l’intérieur de la fonction Generate pour créer un jeu complexe de tuples sur les lignes :  
  
 `SELECT {[Measures].[Internet Sales Amount]} ON 0,`  
  
 `//If Internet Sales Amount is zero or null`  
  
 `//returns the current year and the All Customers member`  
  
 `//else returns the current year broken down by Country`  
  
 `GENERATE(`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS`  
  
 `, IIF([Measures].[Internet Sales Amount]=0,`  
  
 `{([Date].[Calendar Year].CURRENTMEMBER, [Customer].[Country].[All Customers])}`  
  
 `, {{[Date].[Calendar Year].CURRENTMEMBER} * [Customer].[Country].[Country].MEMBERS}`  
  
 `))`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Product].[Product Categories].[Subcategory].&[26])`  
  
 Enfin, cet exemple indique comment utiliser les indicateurs de plan :  
  
 `WITH MEMBER MEASURES.X AS`  
  
 `IIF(`  
  
 `[Measures].[Internet Sales Amount]=0`  
  
 `, NULL`  
  
 `, (1/[Measures].[Internet Sales Amount]) HINT EAGER)`  
  
 `SELECT {[Measures].x} ON 0,`  
  
 `[Customer].[Customer Geography].[Country].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
