---
title: Enfants (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: CHILDREN
dev_langs: kbMDX
helpviewer_keywords: Children function
ms.assetid: ce2c3069-914c-44a3-8a4c-5cbd4fb71e4c
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b6d6333f35abf27d4dce14a6cf2dc6f4866debf2
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="children-mdx"></a>Children (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le jeu des enfants d'un membre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.Children  
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Le **enfants** fonction retourne un jeu naturellement ordonné qui contient les enfants d’un membre spécifié. Si le membre spécifié n'a pas d'enfants, cette fonction retourne un jeu vide.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne les enfants du membre United States de la hiérarchie Geography dans la dimension Geography.  
  
```  
SELECT [Geography].[Geography].[Country].&[United States].Children ON 0  
FROM [Adventure Works]  
```  
  
 L’exemple suivant retourne tous les membres de la **mesures** dimension sur l’axe des colonnes, cela inclut tous les membres calculés et le jeu de tous les enfants de la `[Product].[Model Name]` hiérarchie sur l’axe des lignes à partir d’attributs le **Adventure Works** cube.  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
  
```  
  
|Version|Historique|  
|-------------|-------------|  
|[!INCLUDE[ssBOL2005_R03](../includes/ssbol2005-r03-md.md)]|**Contenu modifié :**<br /> : Mise à jour de la syntaxe et les arguments pour améliorer la clarté.<br /><br /> — Ajout d’exemples mis à jour.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
