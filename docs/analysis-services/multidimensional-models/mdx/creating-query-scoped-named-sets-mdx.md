---
title: "Cr&#233;ation de jeux nomm&#233;s d&#39;&#233;tendue de requ&#234;te (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "jeux nommés d'étendue de requête [MDX]"
  - "WITH (mot clé)"
ms.assetid: 78bc1e9a-1bc4-4a5a-ab0b-cf430c8fbfe1
caps.latest.revision: 36
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Cr&#233;ation de jeux nomm&#233;s d&#39;&#233;tendue de requ&#234;te (MDX)
  Si un jeu nommé n'est nécessaire que pour une seule requête MDX (Multidimensional Expressions), vous pouvez le définir à l'aide du mot clé WITH. Un jeu nommé créé à l'aide du mot clé WITH n'existe plus une fois que l'exécution de la requête est terminée.  
  
 Comme l'explique cette rubrique, la syntaxe de WITH est très souple, et accepte même l'utilisation de fonctions pour définir le jeu nommé.  
  
> [!NOTE]  
>  Pour plus d’informations sur les jeux nommés, consultez [Création de jeux nommés à l’aide d’expressions MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/building-named-sets-in-mdx-mdx.md).  
  
## Syntaxe du mot clé WITH  
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
  
## Exemple de mot clé WITH  
 La requête MDX ci-après examine les ventes unitaires des différents vins Chardonnay et Chablis dans **FoodMart 2000**, l'exemple de base de données de Microsoft SQL Server 2000 Analysis Services. Cette requête, bien que relativement simple en termes d'ensemble de résultats, est longue et lourde à gérer.  
  
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
  
### Utilisation de fonctions en association avec le mot clé WITH  
 Il vous est possible de définir explicitement chaque membre d'un jeu nommé, mais cette approche risque de produire une instruction très longue. Pour faciliter la création et la maintenance d'un jeu nommé, vous pouvez définir ses membres à l'aide de fonctions MDX.  
  
 Par exemple, l'exemple de requête MDX suivant utilise les fonctions MDX [Filter](../../../mdx/filter-mdx.md), [CurrentMember](../../../mdx/currentmember-mdx.md)et [Name](../../../mdx/name-mdx.md) ainsi que la fonction InStr VBA pour créer le jeu nommé `[ChardonnayChablis]` . Cette version du jeu nommé `[ChardonnayChablis]` est identique à la version explicitement définie présentée plus haut dans cette rubrique.  
  
```  
WITH SET [ChardonnayChablis] AS  
   'Filter([Product].Members, (InStr(1, [Product].CurrentMember.Name, "chardonnay") <> 0) OR (InStr(1, [Product].CurrentMember.Name, "chablis") <> 0))'  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
  
```  
  
## Voir aussi  
 [Instruction SELECT &#40;MDX&#41;](../Topic/SELECT%20Statement%20\(MDX\).md)   
 [Création de jeux nommés dans l’étendue de session &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/creating-session-scoped-named-sets-mdx.md)  
  
  