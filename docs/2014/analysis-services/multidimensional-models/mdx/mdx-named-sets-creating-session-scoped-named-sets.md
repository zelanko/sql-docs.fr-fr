---
title: Création de jeux nommés dans l’étendue de session (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- CREATE SET statement
- session-scoped named sets [MDX]
ms.assetid: b751e1e4-6d4c-4d36-a28d-ffdaaee0f1c7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 545bbdb171388f06c28644e0b8caa48db95e7e7f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66074047"
---
# <a name="creating-session-scoped-named-sets-mdx"></a>Création de jeux nommés dans l'étendue de session (MDX)
  Pour créer un jeu nommé disponible dans l’ensemble d’une session MDX (Multidimensional Expressions), utilisez l’instruction [CREATE SET](/sql/mdx/mdx-data-definition-create-set) . Un jeu nommé créé à l'aide de l'instruction CREATE SET n'est supprimé qu'après la fermeture de la session MDX.  
  
 Comme décrit dans cette rubrique, la syntaxe du mot clé WITH est explicite et simple d'utilisation.  
  
> [!NOTE]  
>  Pour plus d’informations sur les jeux nommés, consultez [Création de jeux nommés à l’aide d’expressions MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).  
  
## <a name="create-set-syntax"></a>Syntaxe de CREATE SET  
 Utilisez la syntaxe suivante pour l'instruction CREATE SET :  
  
```  
CREATE SESSION SET [CURRENTCUBE. | <cube name>.]<Set Identifier> AS <Set Expression>  
```  
  
 Dans la syntaxe de l'instruction CREATE SET, le paramètre `cube name` contient le nom du cube qui comprend les membres du jeu nommé. Si le paramètre `cube name` n'est pas spécifié, le cube actuel est utilisé comme cube contenant le membre du jeu nommé. En outre, le paramètre `Set_Identifier` contient l'alias du jeu nommé et le paramètre `Set_Expression` contient l'expression d'ensemble à laquelle l'alias du jeu nommé fait référence.  
  
## <a name="create-set-example"></a>Exemple avec CREATE SET  
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
  
## <a name="see-also"></a>Voir aussi  
 [Création de jeux nommés d’étendue de requête &#40;MDX&#41;](mdx-named-sets-creating-query-scoped-named-sets.md)  
  
  
