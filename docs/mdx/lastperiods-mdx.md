---
description: LastPeriods (MDX)
title: LastPeriods (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 60e8adf1dba453fb536f95a4fa113e16f6950f62
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494882"
---
# <a name="lastperiods-mdx"></a>LastPeriods (MDX)


  Retourne le jeu des membres antérieurs à et incluant un membre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
LastPeriods(Index [ ,Member_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Index*  
 Expression numérique valide qui spécifie un nombre de périodes.  
  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Si le nombre de périodes spécifié est positif, la fonction **LastPeriods** retourne un jeu de membres qui commencent par le membre qui diffère de l' *index* -1 de l’expression de membre spécifiée, et se termine par le membre spécifié. Le nombre de membres retournés par la fonction est égal à *index*.  
  
 Si le nombre de périodes spécifié est négatif, la fonction **LastPeriods** retourne un jeu de membres qui commencent par le membre spécifié et se termine par le membre qui est à l’issue de (- *index* -1) du membre spécifié. Le nombre de membres retournés par la fonction est égal à la valeur absolue de l' *index*.  
  
 Si le nombre de périodes spécifié est égal à zéro, la fonction **LastPeriods** retourne le jeu vide. Contrairement à la fonction **lag** , qui retourne le membre spécifié si 0 est spécifié.  
  
 Si aucun membre n’est spécifié, la fonction **LastPeriods** utilise **Time. CurrentMember**. Si aucune dimension n'est marquée en tant que dimension Time, la fonction analyse et s'exécute sans erreur mais provoque une erreur de cellule dans l'application cliente.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous retourne la valeur de mesure par défaut pour les deuxième, troisième et quatrième trimestres de l'année fiscale 2002.  
  
```  
SELECT LastPeriods(3,[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]) ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  Cet exemple peut également être écrit à l'aide de l'opérateur « : » (deux-points) :  
>   
>  `[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]: [Date].[Fiscal].[Fiscal Quarter].[Q2 FY 2002]`  
  
 L'exemple suivant retourne la valeur de mesure par défaut du premier trimestre de l'année fiscale 2002. Bien que le nombre de périodes spécifié soit trois, seule une période peut être retournée puisqu'il n'existe aucune période précédente dans l'année fiscale.  
  
```  
SELECT LastPeriods  
   (3,[Date].[Fiscal].[Fiscal Quarter].[Q1 FY 2002]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
