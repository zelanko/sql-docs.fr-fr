---
description: Children (MDX)
title: Enfants (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9a37bc27564baf9d75e10af78fb477ea08be092e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466511"
---
# <a name="children-mdx"></a>Children (MDX)


  Retourne le jeu des enfants d'un membre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.Children  
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 La fonction **Children** retourne un jeu naturellement ordonné qui contient les enfants d’un membre spécifié. Si le membre spécifié n'a pas d'enfants, cette fonction retourne un jeu vide.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne les enfants du membre United States de la hiérarchie Geography dans la dimension Geography.  
  
```  
SELECT [Geography].[Geography].[Country].&[United States].Children ON 0  
FROM [Adventure Works]  
```  
  
 L’exemple suivant retourne tous les membres de la dimension **Measures** sur l’axe des colonnes, y compris tous les membres calculés et l’ensemble de tous les enfants de la `[Product].[Model Name]` hiérarchie d’attribut sur l’axe des lignes du cube **Adventure Works** .  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
  
```  
  
|Libérer|Historique|  
|-------------|-------------|  
|[!INCLUDE[ssBOL2005_R03](../includes/ssbol2005-r03-md.md)]|**Contenu modifié :**<br /> -Syntaxe et arguments mis à jour pour améliorer la clarté.<br /><br /> -Ajout d’exemples mis à jour.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
