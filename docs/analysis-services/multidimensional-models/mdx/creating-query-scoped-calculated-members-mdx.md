---
title: "Cr&#233;ation de membres calcul&#233;s d&#39;&#233;tendue de requ&#234;te (MDX) | Microsoft Docs"
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
  - "WITH (mot clé)"
  - "membres calculés d'étendue de requête [MDX]"
ms.assetid: c4507149-e67b-4e5d-9192-cc911acd9adc
caps.latest.revision: 29
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Cr&#233;ation de membres calcul&#233;s d&#39;&#233;tendue de requ&#234;te (MDX)
  Si un membre calculé n'est nécessaire que pour une seule requête MDX (Multidimensional Expressions), vous pouvez le définir à l'aide du mot clé WITH. Un membre calculé créé à l'aide du mot clé WITH n'existe plus une fois que l'exécution de la requête est terminée.  
  
 Comme l'explique cette rubrique, la syntaxe du mot clé WITH est très souple, et accepte même qu'un membre calculé soit basé sur un autre membre calculé.  
  
> [!NOTE]  
>  Pour plus d’informations sur les membres calculés, consultez [Création de membres calculés dans MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/building-calculated-members-in-mdx-mdx.md).  
  
## Syntaxe du mot clé WITH  
 Utilisez la syntaxe suivante pour ajouter le mot clé WITH à une instruction MDX SELECT :  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ] SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]FROM <SELECT subcube clause> [ <SELECT slicer axis clause> ][ <SELECT cell property list clause> ]  
<SELECT WITH clause> ::=  
   ( [ CALCULATED ] MEMBER <CREATE MEMBER body clause>) | <CREATE MEMBER body clause> ::= Member_Identifier AS 'MDX_Expression'  
   [ <CREATE MEMBER property clause> [ , <CREATE MEMBER property clause> ... ] ]  
<CREATE MEMBER property clause> ::=  
   ( MemberProperty_Identifier = Scalar_Expression )  
  
```  
  
 Dans la syntaxe du mot clé WITH, la valeur de `Member_Identifier` est le nom complet du membre calculé. Ce nom complet comprend la dimension ou le niveau auquel le membre calculé est associé. La valeur `MDX_Expression` retourne la valeur du membre calculé après l'évaluation de l'expression. Vous pouvez également, si vous le souhaitez, spécifier les valeurs des propriétés de cellules intrinsèques d'un membre calculé en fournissant le nom de la propriété de cellule dans la valeur `MemberProperty_Identifier` et la valeur de la propriété de cellule dans la valeur `Scalar_Expression` .  
  
## Exemple de mot clé WITH  
 La requête MDX ci-dessous définit un membre calculé, `[Measures].[Special Discount]`, en calculant une remise spéciale basée sur le montant de la remise d'origine.  
  
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
  
 Vous pouvez également créer des membres calculés en n'importe quel point d'une hiérarchie. L'exemple de requête MDX ci-dessous définit le membre calculé `[BigSeller]` pour un cube Sales hypothétique. Ce membre calculé détermine si un magasin spécifié dispose d'au moins 100 unités de vente dans le domaine des vins et bières. Cependant, la requête crée le membre calculé `[BigSeller]` non comme un membre enfant de la dimension `[Product]` , mais comme un enfant du membre `[Beer and Wine]` .  
  
```  
WITH   
   MEMBER [Product].[Beer and Wine].[BigSeller] AS  
  IIf([Product].[Beer and Wine] > 100, "Yes","No")  
SELECT  
   {[Product].[BigSeller]} ON COLUMNS,  
   Store.[Store Name].Members ON ROWS  
FROM Sales  
  
```  
  
 Les membres calculés ne doivent pas forcément dépendre uniquement des membres existants dans un cube. Un membre calculé peut également être basé sur d'autres membres calculés définis dans la même expression MDX. Par exemple, la requête MDX ci-dessous utilise la valeur créée dans le premier membre calculé, `[Measures].[Special Discount]`, pour générer la valeur du second membre calculé, `[Measures].[Special Discounted Amount]`.  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Percentage] * 1.5,   
   FORMAT_STRING = 'Percent'  
  
   MEMBER [Measures].[Special Discounted Amount] AS  
   [Measures].[Reseller Average Unit Price] * [Measures].[Special Discount],   
   FORMAT_STRING = 'Currency'  
  
SELECT   
   {[Measures].[Special Discount], [Measures].[Special Discounted Amount]} on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
  
```  
  
## Voir aussi  
 [Informations de référence sur les fonctions MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)   
 [Instruction SELECT &#40;MDX&#41;](../Topic/SELECT%20Statement%20\(MDX\).md)   
 [Création de membres calculés au niveau de la session &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/creating-session-scoped-calculated-members-mdx.md)  
  
  