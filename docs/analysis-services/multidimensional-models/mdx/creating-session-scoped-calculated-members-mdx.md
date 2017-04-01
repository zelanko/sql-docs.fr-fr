---
title: "Cr&#233;ation de membres calcul&#233;s au niveau de la session (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
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
  - "CREATE MEMBER (instruction)"
  - "membres calculés au niveau de la session [MDX]"
ms.assetid: 2875ed89-2c26-4645-8ed9-8848479d110f
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Cr&#233;ation de membres calcul&#233;s au niveau de la session (MDX)
  Pour créer un membre calculé disponible dans l’ensemble d’une session MDX (Multidimensional Expressions), vous utilisez l’instruction [CREATE MEMBER](../Topic/CREATE%20MEMBER%20Statement%20\(MDX\).md). Un membre calculé créé à l'aide de l'instruction CREATE MEMBER n'est supprimé qu'après la fermeture de la session MDX.  
  
 Comme décrit dans cette rubrique, la syntaxe de l'instruction CREATE MEMBER est explicite et conviviale.  
  
> [!NOTE]  
>  Pour plus d’informations sur les membres calculés, consultez [Création de membres calculés dans MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/building-calculated-members-in-mdx-mdx.md).  
  
## Syntaxe CREATE MEMBER  
 Utilisez la syntaxe suivante pour ajouter l'instruction CREATE MEMBER à l'instruction MDX :  
  
```  
CREATE [SESSION] MEMBER [<cube-name>.]<fully-qualified-member-name> AS <expression> [,<property-definition-list>]  
<cube name> ::= CURRENTCUBE | <Cube Name>  
<property-definition-list> ::= <property-definition>  
  | <property-definition>, <property-definition-list>  
<property-definition> ::= <property-identifier> = <property-value>  
<property-identifier> ::= VISIBLE | SOLVEORDER | SOLVE_ORDER | FORMAT_STRING | NON_EMPTY_BEHAVIOR <ole db member properties>  
```  
  
 Dans la syntaxe de l'instruction CREATE MEMBER, la valeur `fully-qualified-member-name` est le nom complet du membre calculé. Ce nom comprend la dimension ou le niveau auquel le membre calculé est associé. La valeur `expression` retourne la valeur du membre calculé après l'évaluation de la valeur de l'expression.  
  
## Exemple de syntaxe CREATE MEMBER  
 L'exemple suivant utilise l'instruction CREATE MEMBER pour créer le membre calculé `LastFourStores` . Ce dernier retourne la somme des unités vendues dans les quatre derniers magasins et sera disponible tout au long de la session du cube.  
  
```  
Create Session Member [Store].[Measures].LastFourStores as   
sum(([Stores].[ByLocation].Lag(3) :  
[Stores].[ByLocation].NextMember), [Measures].[Units Sold])  
```  
  
## Voir aussi  
 [Création de membres calculés d’étendue de requête &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/creating-query-scoped-calculated-members-mdx.md)  
  
  