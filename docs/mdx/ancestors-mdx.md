---
title: "Ancêtres (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ANCESTORS
dev_langs: kbMDX
helpviewer_keywords: Ancestors function
ms.assetid: abdf2e9c-72c8-4f2e-a823-d42efc4cc7d5
caps.latest.revision: "46"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 5e6a0df3cf90fbab7aedbc199ce8e091ec4ceef4
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="ancestors-mdx"></a>Ancestors (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Cette fonction retourne le jeu de tous les ancêtres d'un membre spécifié à un niveau ou une distance spécifiée du membre. Avec [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], le jeu retourné consiste toujours à un seul membre - [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne prend pas en charge plusieurs parents pour un seul membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Level syntax  
Ancestors(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestors(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
 *Distance*  
 Expression numérique valide qui spécifie la distance depuis le membre spécifié.  
  
## <a name="remarks"></a>Notes  
 Avec la **ancêtres** (fonction), vous fournissez la fonction avec une expression de membre MDX, puis une expression MDX d’un niveau qui est un ancêtre de ce membre ou une expression numérique qui représente le nombre de niveaux au-dessus de ce membre. Avec ces informations, le **ancêtres** fonction retourne le jeu de membres (jeu composé d’un membre seront) à ce niveau.  
  
> [!NOTE]  
>  Pour retourner un membre ancêtre, plutôt que d’un jeu d’ancêtres, utilisez le [ancêtre](../mdx/ancestor-mdx.md) (fonction).  
  
 Si une expression de niveau est spécifiée, la **ancêtres** fonction retourne le jeu de tous les ancêtres du membre spécifié au niveau spécifié. Si un membre spécifié n'apparaît pas dans la même hiérarchie en tant que niveau spécifié, la fonction retourne une erreur.  
  
 Si vous spécifiez une distance, le **ancêtres** fonction retourne le jeu de tous les membres qui sont le nombre d’étapes spécifiés plus haut dans la hiérarchie spécifiée par l’expression de membre. Un membre peut être spécifié en tant que membre d’une hiérarchie d’attribut, une hiérarchie définie par l’utilisateur, ou, dans certains cas, une hiérarchie parent-enfant. Un nombre 1 retourne le jeu des membres au niveau parent ; un nombre 2 retourne le jeu des membres situés au niveau grand-parent (si ce niveau existe). Un nombre 0 retourne le jeu comprenant uniquement le membre lui-même.  
  
> [!NOTE]  
>  Utilisez cette forme de la **ancêtres** fonction pour les cas dans lequel le niveau du parent est inconnu et ne peut pas être nommé.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise le **ancêtres** fonction pour retourner la mesure Internet Sales Amount pour un membre, de son parent et de son grand-parent. Cet exemple se base sur des expressions de niveau pour spécifier les niveaux à retourner. Les niveaux se trouvent dans la même hiérarchie que le membre spécifié dans l'expression de membre.  
  
```  
SELECT {  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Category]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Subcategory]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Product])  
    } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 L’exemple suivant utilise le **ancêtres** fonction pour retourner la mesure Internet Sales Amount pour un membre, de son parent et de son grand-parent. Cet exemple se base sur des expressions numériques pour spécifier les niveaux retournés. Les niveaux se trouvent dans la même hiérarchie que le membre spécifié dans l'expression de membre.  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],2  
      ),  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],1  
      ),  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],0  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM  [Adventure Works]  
```  
  
 L’exemple suivant utilise le **ancêtres** fonction pour retourner la mesure Internet Sales Amount pour le parent d’un membre d’une hiérarchie d’attribut. Cet exemple se base sur une expression numérique pour spécifier le niveau retourné. Du fait que le membre dans l'expression de membre correspond à un membre issu d'une hiérarchie d'attribut, son parent est le niveau [All].  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product].[Mountain-100 Silver, 38],1  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
