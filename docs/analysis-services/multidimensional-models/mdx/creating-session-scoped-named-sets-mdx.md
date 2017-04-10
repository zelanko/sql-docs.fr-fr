---
title: "Cr&#233;ation de jeux nomm&#233;s dans l&#39;&#233;tendue de session (MDX) | Microsoft Docs"
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
  - "instruction CREATE SET"
  - "jeux nommés dans l'étendue de session [MDX]"
ms.assetid: b751e1e4-6d4c-4d36-a28d-ffdaaee0f1c7
caps.latest.revision: 29
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Cr&#233;ation de jeux nomm&#233;s dans l&#39;&#233;tendue de session (MDX)
  Pour créer un jeu nommé disponible dans l’ensemble d’une session MDX (Multidimensional Expressions), utilisez l’instruction [CREATE SET](../Topic/CREATE%20SET%20Statement%20\(MDX\).md). Un jeu nommé créé à l'aide de l'instruction CREATE SET n'est supprimé qu'après la fermeture de la session MDX.  
  
 Comme décrit dans cette rubrique, la syntaxe du mot clé WITH est explicite et simple d'utilisation.  
  
> [!NOTE]  
>  Pour plus d’informations sur les jeux nommés, consultez [Création de jeux nommés à l’aide d’expressions MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/building-named-sets-in-mdx-mdx.md).  
  
## Syntaxe de CREATE SET  
 Utilisez la syntaxe suivante pour l'instruction CREATE SET :  
  
```  
CREATE SESSION SET [CURRENTCUBE. | <cube name>.]<Set Identifier> AS <Set Expression>  
```  
  
 Dans la syntaxe de l'instruction CREATE SET, le paramètre `cube name` contient le nom du cube qui comprend les membres du jeu nommé. Si le paramètre `cube name` n'est pas spécifié, le cube actuel est utilisé comme cube contenant le membre du jeu nommé. En outre, le paramètre `Set_Identifier` contient l'alias du jeu nommé et le paramètre `Set_Expression` contient l'expression d'ensemble à laquelle l'alias du jeu nommé fait référence.  
  
## Exemple avec CREATE SET  
 L'exemple suivant utilise l'instruction CREATE SET pour créer le jeu nommé `SetCities_2_3` en se basant sur le cube Store. Les membres du jeu nommé `SetCities_2_3` sont les magasins situés dans City 2 et City 3.  
  
```  
create Session set [Store].[SetCities_2_3] as  
{[Data Stores].[ByLocation].[State].&[CA].&[City 02],  
[Data Stores].[ByLocation].[State].&[NH].&[City 03]}  
```  
  
 Si vous utilisez l'instruction CREATE SET pour définir le jeu nommé `SetCities_2_3` , ce dernier reste disponible pendant toute la durée de la session MDX active. L'exemple suivant est celui d'une requête valide qui retourne les membres City 2 et City 3 ; par ailleurs, celle-ci peut être exécutée à tout moment après la création du jeu nommé `SetCities_2_3` et avant la fermeture de la session.  
  
```  
select SetCities_2_3 on 0 from [Store]  
```  
  
## Voir aussi  
 [Création de jeux nommés d’étendue de requête &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/creating-query-scoped-named-sets-mdx.md)  
  
  