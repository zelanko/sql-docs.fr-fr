---
title: Les expressions (MDX Multidimensional) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- identifiers [MDX]
- expressions [MDX]
- expressions [MDX], about expressions
- MDX [Analysis Services], expressions
- Multidimensional Expressions [Analysis Services], expressions
ms.assetid: e20c34bc-30fa-4ac5-b896-9d4c9925ef59
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 608cba1c2819136f5bafa71be8ac5a347c5939cd
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="expressions-mdx"></a>Expressions (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Une expression est une combinaison d’identificateurs, de valeurs et d’opérateurs qui [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] peut évaluer pour obtenir un résultat. Les données peuvent être utilisées à différents endroits lors de l'accès ou la modification des données. Vous pouvez, par exemple, utiliser une expression en tant qu'élément des données à récupérer dans une requête ou en tant que condition de recherche de données répondant à un jeu de critères.  
  
## <a name="simple-and-complex-expressions"></a>Expressions simples et complexes  
 Dans la syntaxe MDX, une expression peut être simple ou complexe :  
  
 Une expression simple peut être l'une des expressions suivantes :  
  
 Constante  
 Dans la syntaxe MDX, une constante est un symbole représentant une valeur unique spécifique. Les valeurs de chaîne, numériques et de date peuvent être restituées sous forme de constantes. Contrairement aux constants numériques, les constantes de chaîne et de date doivent être délimitées par des guillemets simples (').  
  
 Fonction scalaire  
 Dans la syntaxe MDX, une fonction scalaire retourne une valeur unique au sein du contexte d'évaluation. Cette distinction est importante pour comprendre la manière dont MDX résout les fonctions scalaires, car la plupart des expressions, instructions et scripts MDX ne sont pas évalués sur un élément de données unique, mais bien de façon itérative sur un groupe d'éléments de données, tels que ces cellules ou des membres. Cependant, au moment de l'évaluation de la fonction scalaire, elle vérifie généralement un élément de données unique.  
  
 Identificateur d'objet  
 La syntaxe MDX est orientée objet en raison de la nature des données multidimensionnelles. Les identificateurs d'objet sont considérés comme des expressions simples dans la syntaxe MDX. Pour plus d’informations sur les identificateurs, consultez [identificateurs &#40; MDX &#41; ](../mdx/identifiers-mdx.md).  
  
 Une expression complexe peut être une combinaison de ces entités associées par des opérateurs.  
  
## <a name="expression-results"></a>Résultats des expressions  
 Pour une expression simple composée d'une seule constante ou variable ou d'une seule fonction scalaire ou nom de colonne, les type de données, classement, précision, échelle et valeur de l'expression sont ceux de l'élément référencé. Comme la syntaxe MDX ne prend directement en charge que le type de données OLE VARIANT, la contrainte ne doit se produire que lors de l'utilisation d'expressions simples.  
  
 Pour une expression complexe, la contrainte peut se produire lors de l'utilisation de plusieurs expressions simples possédant différents types de données.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 La requête suivante affiche des exemples de mesures calculées dont les définitions sont des expressions simples :  
  
 `WITH`  
  
 `MEMBER MEASURES.CONSTANTVALUE AS 1`  
  
 `MEMBER MEASURES.SCALARFUNCTION AS [Date].[Calendar Year].CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.OBJECTIDENTIFIER AS [Measures].[Internet Sales Amount]`  
  
 `SELECT {MEASURES.CONSTANTVALUE,MEASURES.SCALARFUNCTION,MEASURES.OBJECTIDENTIFIER } ON 0,`  
  
 `[Date].[Calendar Year].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 Une expression peut également être un calcul, tel que `[Measures].[Discount Amount] * 1.5`. L'exemple suivant illustre l'utilisation d'un calcul pour définir un membre dans une instruction MDX SELECT :  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Amount] * 1.5  
SELECT   
   [Measures].[Special Discount] on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[À l’aide de Cube et les Expressions de sous-cube](../mdx/using-cube-and-subcube-expressions.md)|Définit les expressions de cube et de sous-cube.|  
|[À l’aide d’Expressions de Dimension](../mdx/using-dimension-expressions.md)|Définit les expressions de dimension.|  
|[Utilisation d’Expressions de membre](../mdx/using-member-expressions.md)|Définit les expressions de membre.|  
|[À l’aide d’Expressions de Tuple](../mdx/using-tuple-expressions.md)|Définit les expressions de tuple.|  
|[À l’aide d’Expressions de jeu](../mdx/using-set-expressions.md)|Définit les expressions de jeu.|  
|[Utilisation d’Expressions scalaires](../mdx/using-scalar-expressions.md)|Définit les expressions scalaires.|  
|[Utilisation des valeurs vides](../mdx/working-with-empty-values.md)|Décrit une valeur vide et la manière dont les valeurs de ce type sont gérées.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du langage MDX &#40; MDX &#41;](../mdx/mdx-language-reference-mdx.md)   
 [Principes de base de requête MDX &#40; Analysis Services &#41;](../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  

