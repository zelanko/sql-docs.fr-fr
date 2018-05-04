---
title: LastPeriods (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LASTPERIODS
dev_langs:
- kbMDX
helpviewer_keywords:
- LastPeriods function
ms.assetid: a15df7a1-b261-48ed-aacc-d2804db8dbf7
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: c4d2f7fdb3d91341dcd4849bf1a47bafcacc4dc4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="lastperiods-mdx"></a>LastPeriods (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne le jeu des membres antérieurs à et incluant un membre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
LastPeriods(Index [ ,Member_Expression ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Index*  
 Expression numérique valide qui spécifie un nombre de périodes.  
  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Si le nombre de périodes spécifié est positif, le **LastPeriods** fonction retourne un jeu de membres qui commence par le membre qui est en retard *Index* -1 à partir de l’expression de membre spécifié et se termine par le membre spécifié. Le nombre de membres retournés par la fonction est égal à *Index*.  
  
 Si le nombre de périodes spécifié est négatif, le **LastPeriods** fonction retourne un jeu de membres qui commence par le membre spécifié et se termine par le membre arrivant en premier (- *Index* - 1) à partir du membre spécifié. Le nombre de membres retournés par la fonction est égal à la valeur absolue de *Index*.  
  
 Si le nombre de périodes spécifié est égal à zéro, le **LastPeriods** fonction retourne le jeu vide. Contrairement à la **Lag** fonction, qui retourne le membre spécifié si 0 est spécifié.  
  
 Si un membre n’est pas spécifié, le **LastPeriods** fonction utilise **Time.CurrentMember**. Si aucune dimension n'est marquée en tant que dimension Time, la fonction analyse et s'exécute sans erreur mais provoque une erreur de cellule dans l'application cliente.  
  
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
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)  
  
  
