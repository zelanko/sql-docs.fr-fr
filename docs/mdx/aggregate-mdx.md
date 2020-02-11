---
title: Aggregate (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6c75ab71456dc8b7ffc3efdf6bd157693de14881
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68017170"
---
# <a name="aggregate-mdx"></a>Aggregate (MDX)


  Retourne un nombre calculé par agrégation sur les cellules retournées par l'expression de jeu. Si aucune expression numérique n'est spécifiée, cette fonction agrège chaque mesure dans le contexte de requête actuel en utilisant l'opérateur d'agrégation par défaut spécifié pour chaque mesure. Si une expression numérique est précisée, cette fonction évalue d'abord, puis totalise l'expression numérique pour chaque cellule du jeu spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Aggregate(Set_Expression [ ,Numeric_Expression ])  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
## <a name="remarks"></a>Notes  
 Si un jeu de tuples vides ou un jeu vide est spécifié, cette fonction retourne une valeur vide.  
  
 Le tableau suivant décrit le comportement de la fonction d' **agrégation** avec différentes fonctions d’agrégation.  
  
|Opérateur d'agrégation|Résultats|  
|--------------------------|------------|  
|SUM|Retourne la somme des valeurs dans le jeu.|  
|Count|Retourne le nombre de valeurs dans le jeu.|  
|Max|Retourne la valeur maximale dans le jeu.|  
|Min|Retourne la valeur minimale dans le jeu.|  
|Fonctions d'agrégation semi-additives|Retourne le calcul du comportement semi-additif dans le jeu après projection de la forme sur l'axe temporel.|  
|Distinct Count|Agrège les données de faits qui contribuent au sous-cube lorsque l'axe de secteur comporte un jeu.<br /><br /> Retourne le comptage de valeurs pour chaque membre du jeu. Le résultat obtenu dépend de la sécurité dans les cellules agrégées et non de la sécurité dans les cellules requises pour le calcul. La sécurité des cellules dans le jeu déclenche une erreur ; la sécurité des cellules inférieure à la granularité du jeu spécifié est ignorée. Les calculs sur le jeu génèrent une erreur. Les calculs inférieurs à la granularité du jeu sont ignorés. Le comptage de valeurs dans un jeu qui inclut un membre et un ou plusieurs de ses enfants retourne le comptage de valeurs dans les faits qui contribuent au membre enfant.|  
|Attributs qui ne peuvent pas être agrégés|Retourne la somme des valeurs.|  
|Fonctions d'agrégation mixtes|Non pris en charge, déclenche une erreur.|  
|Opérateurs unaires|Non respectés ; les valeurs sont agrégées par addition.|  
|Mesures calculées|Ordre de résolution défini pour garantir l'application de la mesure calculée.|  
|Membres calculés|Application des règles normales, ce qui signifie que le dernier ordre de résolution est prioritaire.|  
|Affectations|L'agrégation des attributions a lieu selon la mesure d'agrégation des mesures. Si la fonction d'agrégation des mesures est un comptage de valeurs, l'attribution est totalisée.|  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne la somme du `Measures.[Order Quantity]` membre, agrégée sur les huit premiers mois de l’année civile 2003 qui sont contenus dans la `Date` dimension, à partir du cube **Adventure Works** .  
  
```  
WITH MEMBER [Date].[Calendar].[First8Months2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Year],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First8Months2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 L'exemple ci-après est agrégé sur les deux premiers mois du deuxième semestre de l'annéé civile 2003.  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Semester],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First2MonthsSecondSemester2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 L'exemple ci-dessous retourne le nombre de revendeurs dont les ventes ont baissé sur la période précédente en se basant sur les valeurs de membres State-Province (état-province) sélectionnées par l'utilisateur et évaluées à l'aide de la fonction Aggregate. Les fonctions **Hierarchize** et **DrilldownLevel** sont utilisées pour retourner des valeurs pour les ventes refusées pour les catégories de produits dans la dimension Product.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS   
   Count(  
      Filter(  
         Existing(Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] < ([Measures].[Reseller Sales Amount],  
            [Date].Calendar.PrevMember)  
            )  
         )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate (   
      {[Geography].[State-Province].&[WA]&[US],   
      [Geography].[State-Province].&[OR]&[US] }   
         )  
SELECT NON EMPTY Hierarchize (  
   AddCalculatedMembers (  
      {DrillDownLevel({[Product].[All Products]})}  
         )  
   )  
        DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
    [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
    [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [PeriodsToDate &#40;&#41;MDX](../mdx/periodstodate-mdx.md)   
 [&#41;MDX &#40;](../mdx/children-mdx.md)   
 [Hierarchize&#41;MDX &#40;](../mdx/hierarchize-mdx.md)   
 [Nombre &#40;défini&#41; &#40;&#41;MDX](../mdx/count-set-mdx.md)   
 [Filtre &#40;&#41;MDX](../mdx/filter-mdx.md)   
 [AddCalculatedMembers&#41;MDX &#40;](../mdx/addcalculatedmembers-mdx.md)   
 [DrilldownLevel&#41;MDX &#40;](../mdx/drilldownlevel-mdx.md)   
 [Propriétés &#40;MDX&#41;](../mdx/properties-mdx.md)   
 [PrevMember&#41;MDX &#40;](../mdx/prevmember-mdx.md)   
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
