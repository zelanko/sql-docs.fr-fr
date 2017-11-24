---
title: MeasureGroupMeasures (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords: MeasureGroupMeasures function
ms.assetid: 69d9b205-1ca7-4741-9ca9-c7926bc87ead
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: baacb5ee83ecd45bc994cc462b04d35d6d3ca15a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="measuregroupmeasures-mdx"></a>MeasureGroupMeasures (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne un jeu de mesures appartenant au groupe de mesures spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
MEASUREGROUPMEASURES(MeasureGroupName)  
```  
  
## <a name="arguments"></a>Arguments  
 *MeasureGroupName*  
 Expression de chaîne valide contenant le nom du groupe de mesures à partir duquel l'ensemble des mesures doit être extrait.  
  
## <a name="remarks"></a>Notes  
 La chaîne définie doit correspondre exactement au nom du groupe de mesures. L'usage de crochets avec espaces pour les noms des groupes de mesures n'est pas nécessaire.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne toutes les mesures du groupe de mesures Internet Sales (ventes Internet) dans le cube Adventure Works.  
  
```  
SELECT MeasureGroupMeasures('Internet Sales') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
