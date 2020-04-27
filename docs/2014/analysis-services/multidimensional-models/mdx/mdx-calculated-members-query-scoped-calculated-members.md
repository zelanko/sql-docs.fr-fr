---
title: Création de membres calculés d’étendue de requête (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- query-scoped calculated members [MDX]
ms.assetid: c4507149-e67b-4e5d-9192-cc911acd9adc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e6153b78b0dda1a72e2f7dfd790fa8bcecd0bb37
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66074531"
---
# <a name="creating-query-scoped-calculated-members-mdx"></a>Création de membres calculés d'étendue de requête (MDX)
  Si un membre calculé n'est nécessaire que pour une seule requête MDX (Multidimensional Expressions), vous pouvez le définir à l'aide du mot clé WITH. Un membre calculé créé à l'aide du mot clé WITH n'existe plus une fois que l'exécution de la requête est terminée.  
  
 Comme l'explique cette rubrique, la syntaxe du mot clé WITH est très souple, et accepte même qu'un membre calculé soit basé sur un autre membre calculé.  
  
> [!NOTE]  
>  Pour plus d’informations sur les membres calculés, consultez [Création de membres calculés dans MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).  
  
## <a name="with-keyword-syntax"></a>Syntaxe du mot clé WITH  
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
  
## <a name="with-keyword-examples"></a>Exemple de mot clé WITH  
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
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](/sql/mdx/mdx-function-reference-mdx)   
 [Instruction SELECT &#40;&#41;MDX](/sql/mdx/mdx-data-manipulation-select)   
 [Création de membres calculés au niveau de la session &#40;MDX&#41;](mdx-calculated-members-session-scoped-calculated-members.md)  
  
  
