---
title: Utilisation de valeurs vides | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ae8d6262f6502add09376b76a767a3076c830cb8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68125848"
---
# <a name="working-with-empty-values"></a>Manipulation de valeurs vides


  Une valeur vide indique qu'un membre, tuple ou cellule spécifique est vide. Une valeur de cellule vide signifie soit que les données de la cellule spécifiée sont introuvables dans la table de faits sous-jacente, soit que le tuple de la cellule spécifiée représente une combinaison de membres qui n'est pas applicable à ce cube.  
  
> [!NOTE]  
>  Même si une valeur vide est différente d'une valeur zéro, une valeur vide est généralement considérée comme telle la plupart du temps.  
  
 Le requête suivant illustre le comportement des valeurs vides et nulles :  
  
```  
WITH  
//A calculated Product Category that always returns 0  
MEMBER [Product].[Category].[All Products].ReturnZero AS 0  
//Will return true for any null value  
MEMBER MEASURES.ISEMPTYDemo AS ISEMPTY([Measures].[Internet Tax Amount])  
//Will true for any null or zero value  
//To be clear: the expression 0=null always returns true in MDX  
MEMBER MEASURES.IsZero AS [Measures].[Internet Tax Amount]=0  
SELECT  
{[Measures].[Internet Tax Amount],MEASURES.ISEMPTYDemo,MEASURES.IsZero}  
ON COLUMNS,  
[Product].[Category].[Category].ALLMEMBERS  
ON ROWS  
FROM [Adventure Works]  
WHERE([Date].[Calendar].[Calendar Year].&[2001])  
```  
  
 Les informations suivantes s'appliquent aux valeurs vides :  
  
-   La fonction [IsEmpty](../mdx/isempty-mdx.md) retourne la **valeur true** si et seulement si la cellule identifiée par le tuple spécifié dans la fonction est vide. Dans le cas contraire, la fonction retourne **false**.  
  
    > [!NOTE]  
    >  La fonction **IsEmpty** ne peut pas déterminer si une expression de membre retourne une valeur null. Pour déterminer si un membre null est retourné à partir d’une expression, utilisez l’opérateur [is](../mdx/is-mdx.md).  
  
-   lorsque la valeur de cellule vide est l'opérande d'un opérateur numérique quelconque (+, -, *, /), elle est considérée comme le chiffre zéro si l'autre opérande est une valeur non vide. Si les deux opérandes sont vides, l'opérateur numérique retourne la valeur de cellule vide ;  
  
-   lorsque la valeur de cellule vide est l'opérande de l'opérateur de concaténation de chaîne (+), elle est considérée comme une chaîne vide si l'autre opérande est une valeur non vide. Si les deux opérandes sont vides, l'opérateur de concaténation de chaîne retourne la valeur de cellule vide ;  
  
-   lorsque la valeur de cellule vide est un opérande d'un opérateur de comparaison quelconque (=, <>, >=, \<=, >, <), la valeur de cellule vide est considérée comme zéro ou une chaîne vide, selon que le type de données de l’autre opérande est numérique ou chaîne, respectivement. Si les deux opérandes sont vides, ils sont considérés comme le chiffre zéro ;  
  
-   lors d'un classement de valeurs numériques, la valeur de cellule vide occupe la même position que le chiffre zéro. S'ils sont tous deux présents, la valeur de cellule vide se place avant le chiffre zéro ;  
  
-   lors d'un classement de valeurs de type chaîne, la valeur de cellule vide occupe la même position que la chaîne vide. Si elles sont toutes deux présentes, la valeur de cellule vide se place avant la chaîne vide.  
  
## <a name="dealing-with-empty-values-in-mdx-statements-and-cubes"></a>Traitement des valeurs vides dans les instructions et cubes MDX  
 Dans les instructions MDX (Multidimensional Expressions), vous pouvez rechercher les valeurs vides, puis effectuer certains calculs sur les cellules contenant des données valides (c'est-à-dire non vides). L'élimination de valeurs vides lors des calculs peut s'avérer importante pour certains calculs (tels que les moyennes) risquant d'être faussés par la présence de valeurs de cellule vides.  
  
 Si les valeurs vides sont stockées dans vos données de table de faits sous-jacentes, par défaut, elles seront converties en zéro lorsque le cube est traité. Vous pouvez utiliser l’option de **traitement null** sur une mesure pour contrôler si les faits NULL sont convertis en 0, convertis en une valeur vide ou si une erreur est levée au cours du traitement. Si vous ne souhaitez pas que les valeurs de cellule vides apparaissent dans vos résultats de requête, vous devez créer des requêtes, des membres calculés ou des instructions de script MDX qui éliminent les valeurs vides ou les remplacent par une autre valeur.  
  
 Pour supprimer des lignes ou des colonnes vides dans une requête, vous pouvez utiliser l'instruction NON EMPTY avant la définition de l'ensemble des axes. Par exemple, la requête suivante retourne seulement la catégorie de produit Vélos parce que c'est la seule catégorie ayant fait l'objet de ventes dans l'année civile 2001 :  
  
 `SELECT`  
  
 `{[Measures].[Internet Tax Amount]}`  
  
 `ON COLUMNS,`  
  
 `//Comment out the following line to display all the empty rows for other Categories`  
  
 `NON EMPTY`  
  
 `[Product].[Category].[Category].MEMBERS`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Date].[Calendar].[Calendar Year].&[2001])`  
  
 Plus généralement, pour supprimer des tuple vides d'un jeu vous pouvez utiliser la fonction NonEmpty. La requête suivante affiche deux mesures calculées, une qui compte le nombre de catégories Produit et la seconde affiche le nombre de catégories Produit qui ont des valeurs pour la mesure [Montant des taxes sur Internet] et l'année civile 2001 :  
  
 `WITH`  
  
 `MEMBER MEASURES.CategoryCount AS`  
  
 `COUNT([Product].[Category].[Category].MEMBERS)`  
  
 `MEMBER MEASURES.NonEmptyCategoryCountFor2001 AS`  
  
 `COUNT(`  
  
 `NONEMPTY(`  
  
 `[Product].[Category].[Category].MEMBERS`  
  
 `,([Date].[Calendar].[Calendar Year].&[2001], [Measures].[Internet Tax Amount])`  
  
 `))`  
  
 `SELECT`  
  
 `{MEASURES.CategoryCount,MEASURES.NonEmptyCategoryCountFor2001 }`  
  
 `ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
 Pour plus d’informations, consultez [&#40;&#41;MDX non Empty ](../mdx/nonempty-mdx.md).  
  
## <a name="empty-values-and-comparison-operators"></a>Valeurs vides et opérateurs de comparaison  
 En présence de valeurs vides dans les données, les opérateurs logiques et ceux de comparaison peuvent retourner UNKNOWN plutôt que TRUE ou FALSE. Cette logique tri-valuée nécessaire est source de nombreuses erreurs dans les applications. Ces tableaux présentent les effets dus à l'introduction de valeurs vides dans les comparaisons.  
  
 Ce tableau représente les résultats de l'application d'un opérateur AND à deux opérandes booléens.  
  
|AND|TRUE|EMPTY|FALSE|  
|---------|----------|-----------|-----------|  
|**TRUE**|TRUE|FALSE|FALSE|  
|**VIDÉ**|FALSE|EMPTY|FALSE|  
|**FALSE**|FALSE|FALSE|FALSE|  
  
 Ce tableau représente les résultats de l'application d'un opérateur OR à deux opérandes booléens.  
  
|OR|TRUE|FALSE|  
|--------|----------|-----------|  
|**TRUE**|TRUE|TRUE|  
|**VIDÉ**|TRUE|TRUE|  
|**FALSE**|TRUE|FALSE|  
  
 Ce tableau illustre la manière dont l'opérateur NOT négocie ou annule le résultat d'un opérateur booléen.  
  
|Expression booléenne à laquelle l'opérateur NOT est appliqué|est évalué à|  
|-------------------------------------------------------------|------------------|  
|TRUE|FALSE|  
|EMPTY|EMPTY|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)   
 [Référence des opérateurs MDX &#40;&#41;MDX](../mdx/mdx-operator-reference-mdx.md)   
 [Expressions &#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
