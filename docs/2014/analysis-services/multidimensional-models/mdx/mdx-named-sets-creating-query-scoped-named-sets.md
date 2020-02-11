---
title: Création de jeux nommés d’étendue de requête (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- query-scoped named sets [MDX]
- WITH keyword
ms.assetid: 78bc1e9a-1bc4-4a5a-ab0b-cf430c8fbfe1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a611d3d20d269bb9c3fa3a1f764181b1660713b0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66074068"
---
# <a name="creating-query-scoped-named-sets-mdx"></a>Création de jeux nommés d'étendue de requête (MDX)
  Si un jeu nommé n'est nécessaire que pour une seule requête MDX (Multidimensional Expressions), vous pouvez le définir à l'aide du mot clé WITH. Un jeu nommé créé à l'aide du mot clé WITH n'existe plus une fois que l'exécution de la requête est terminée.  
  
 Comme l'explique cette rubrique, la syntaxe de WITH est très souple, et accepte même l'utilisation de fonctions pour définir le jeu nommé.  
  
> [!NOTE]  
>  Pour plus d’informations sur les jeux nommés, consultez [Création de jeux nommés à l’aide d’expressions MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).  
  
## <a name="with-keyword-syntax"></a>Syntaxe du mot clé WITH  
 Utilisez la syntaxe suivante pour ajouter le mot clé WITH à l'instruction SELECT MDX :  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ]   
SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]  
FROM <SELECT subcube clause>   
[ <SELECT slicer axis clause> ]  
[ <SELECT cell property list clause> ]  
  
<SELECT WITH clause> ::=  
   ( SET Set_Identifier AS 'Set_Expression')  
  
```  
  
 Dans la syntaxe du mot clé WITH, le paramètre `Set_Identifier` contient l'alias du jeu nommé. Le paramètre `Set_Expression` contient l'expression à laquelle l'alias du jeu nommé se réfère.  
  
## <a name="with-keyword-example"></a>Exemple de mot clé WITH  
 La requête MDX ci-après examine les ventes unitaires des différents vins Chardonnay et Chablis dans `FoodMart 2000`, l'exemple de base de données de Microsoft SQL Server 2000 Analysis Services. Cette requête, bien que relativement simple en termes d'ensemble de résultats, est longue et lourde à gérer.  
  
```  
SELECT  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]} ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
 Pour faciliter la maintenance de la requête MDX ci-dessus, vous pouvez créer un jeu nommé pour cette requête, à l'aide du mot clé WITH. L'exemple de code ci-après montre comment utiliser le mot clé WITH pour créer un jeu nommé, `[ChardonnayChablis]`, et comment ce jeu nommé rend l'instruction SELECT plus courte et plus facile à gérer.  
  
```  
WITH SET [ChardonnayChablis] AS  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]}  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
### <a name="using-functions-together-with-the-with-keyword"></a>Utilisation de fonctions en association avec le mot clé WITH  
 Il vous est possible de définir explicitement chaque membre d'un jeu nommé, mais cette approche risque de produire une instruction très longue. Pour faciliter la création et la maintenance d'un jeu nommé, vous pouvez définir ses membres à l'aide de fonctions MDX.  
  
 Par exemple, l'exemple de requête MDX suivant utilise les fonctions MDX [Filter](/sql/mdx/filter-mdx), [CurrentMember](/sql/mdx/current-mdx)et [Name](/sql/mdx/members-string-mdx) ainsi que la fonction InStr VBA pour créer le jeu nommé `[ChardonnayChablis]` . Cette version du jeu nommé `[ChardonnayChablis]` est identique à la version explicitement définie présentée plus haut dans cette rubrique.  
  
```  
WITH SET [ChardonnayChablis] AS  
   'Filter([Product].Members, (InStr(1, [Product].CurrentMember.Name, "chardonnay") <> 0) OR (InStr(1, [Product].CurrentMember.Name, "chablis") <> 0))'  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction SELECT &#40;&#41;MDX](/sql/mdx/mdx-data-manipulation-select)   
 [Création de jeux nommés d’étendue de session &#40;MDX&#41;](mdx-named-sets-creating-session-scoped-named-sets.md)  
  
  
