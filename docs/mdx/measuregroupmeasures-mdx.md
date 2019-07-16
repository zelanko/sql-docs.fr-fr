---
title: MeasureGroupMeasures (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 45d7adc5e1f4e103790d9d067bc4876fb5b134d2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68033877"
---
# <a name="measuregroupmeasures-mdx"></a>MeasureGroupMeasures (MDX)


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
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
