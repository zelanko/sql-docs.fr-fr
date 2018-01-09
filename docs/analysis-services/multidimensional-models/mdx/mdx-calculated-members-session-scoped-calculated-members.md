---
title: "Création d’une Session spécifique de membres (MDX) calculés | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CREATE MEMBER statement
- session-scoped calculated members [MDX]
ms.assetid: 2875ed89-2c26-4645-8ed9-8848479d110f
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 273553132fd9a3cd32900fef28800d28c9f6c1d5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-calculated-members---session-scoped-calculated-members"></a>MDX calculé membres : membres calculés d’étendue de Session
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Pour créer un membre calculé qui est disponible dans une session MDX (Multidimensional Expressions), vous utilisez la [CREATE MEMBER](../../../mdx/mdx-data-definition-create-member.md) instruction. Un membre calculé créé à l'aide de l'instruction CREATE MEMBER n'est supprimé qu'après la fermeture de la session MDX.  
  
 Comme décrit dans cette rubrique, la syntaxe de l'instruction CREATE MEMBER est explicite et conviviale.  
  
> [!NOTE]  
>  Pour plus d’informations sur les membres calculés, consultez [Création de membres calculés dans MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-building-calculated-members.md).  
  
## <a name="create-member-syntax"></a>Syntaxe CREATE MEMBER  
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
  
## <a name="create-member-example"></a>Exemple de syntaxe CREATE MEMBER  
 L'exemple suivant utilise l'instruction CREATE MEMBER pour créer le membre calculé `LastFourStores` . Ce dernier retourne la somme des unités vendues dans les quatre derniers magasins et sera disponible tout au long de la session du cube.  
  
```  
Create Session Member [Store].[Measures].LastFourStores as   
sum(([Stores].[ByLocation].Lag(3) :  
[Stores].[ByLocation].NextMember), [Measures].[Units Sold])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Création de membres calculés d’étendue de requête &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members.md)  
  
  
