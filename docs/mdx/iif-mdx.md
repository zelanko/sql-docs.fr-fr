---
title: IIf (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IIF
dev_langs:
- kbMDX
helpviewer_keywords:
- IIf function
ms.assetid: ec7b35e6-f4c5-40bf-93c8-b83c1cc26fe2
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0b520aa3c3761c8dd8452b1732923b7415bcbca6
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="iif-mdx"></a>IIf (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Évalue différentes expressions de branche, selon qu'une condition booléenne renvoie true ou false.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IIf(Logical_Expression, Expression1 [HINT <hints>], Expression2 [HINT <hints>])  
```  
  
## <a name="arguments"></a>Arguments  
 La fonction IIf utilise trois arguments : iif (\<condition >, \<puis créer une branche >, \<autre branche >).  
  
 *Logical_Expression*  
 Une condition qui prend la valeur **true** (1) ou **false** (0). Ce doit être une expression logique MDX (Multidimensional Expressions) valide.  
  
 *Indicateur de expression1 [hâtif | Strict | Lazy]]*  
 Utilisé lors de l’expression logique renvoie **true**. Expression1 doit être une expression MDX (Multidimensional Expressions) valide.  
  
 *Indicateur de expression2 [hâtif | Strict | Lazy]]*  
 Utilisé lors de l’expression logique renvoie **false**. Expression2 doit être une expression MDX (Multidimensional Expressions) valide.  
  
## <a name="remarks"></a>Notes  
 La condition spécifiée par l’expression logique prend la valeur de **false** lorsque la valeur de cette expression est zéro. Toute autre valeur prend la valeur de **true**.  
  
 Lorsque la condition est **true**, le **IIf** fonction retourne la première expression. Sinon, la fonction retourne la seconde expression.  
  
 Les expressions spécifiées peuvent retourner des valeurs ou des objets MDX. De plus, leurs types ne doivent pas obligatoirement correspondre.  
  
 Le **IIf** fonction n’est pas recommandée pour la création d’un jeu de membres selon des critères de recherche. Utilisez plutôt le [filtre](../mdx/filter-mdx.md) (fonction) pour évaluer chaque membre d’un jeu spécifié par rapport à une expression logique et retourner un sous-ensemble de membres.  
  
> [!NOTE]  
>  Si l'une des expressions prend la valeur NULL, le jeu de résultats est NULL une fois cette condition satisfaite.  
  
 HINT est un modificateur facultatif qui détermine comment et quand l'expression est évaluée. Il vous permet de modifier le plan de requête par défaut en spécifiant la façon dont l'expression est évaluée.  
  
-   EAGER évalue l'expression dans le sous-espace IIF d'origine.  
  
-   STRICT évalue l'expression uniquement dans le sous-espace limité créé par l'expression de condition logique.  
  
-   LAZY évalue l'expression en mode cellule-par-cellule.  
  
 Tandis que EAGER et STRICT s'appliquent uniquement aux branches then-else de IIF, LAZY s'applique à toutes les expressions MDX. Toutes les expressions MDX peuvent être suivies par HINT LAZY, qui évaluent cette expression en mode cellule-par-cellule.  
  
 EAGER et STRICT s'excluent mutuellement dans l'indicateur ; ils peuvent être utilisés dans la même fonction IIF(,,) sur des expressions différentes.  
  
 Pour plus d’informations, consultez [indicateurs de requête de fonction IIF dans SQL Server Analysis Services 2008](http://go.microsoft.com/fwlink/?LinkId=269540) et [des Plans d’exécution et indicateurs de Plan pour la fonction MDX IIF et l’instruction CASE](http://go.microsoft.com/fwlink/?LinkId=269565).  
  
## <a name="examples"></a>Exemples  
 La requête suivante montre une utilisation simple de **IIF** à l’intérieur d’une mesure calculée pour retourner l’une des deux valeurs de chaîne différentes lorsque la mesure Internet Sales Amount est supérieure ou inférieure à 10 000 $:  
  
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
  
 Voici un exemple de **IIF** qui retourne un des deux jeux à l’intérieur de la fonction Generate pour créer un jeu complexe de tuples sur les lignes :  
  
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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

