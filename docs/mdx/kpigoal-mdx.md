---
title: KPIGoal (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f818731fdc2d7b7b6ee6b000fd4e85b150c9f92c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68105245"
---
# <a name="kpigoal-mdx"></a>KPIGoal (MDX)


  Retourne le membre chargé de calculer la valeur de la portion objectif de l'indicateur de performance clé spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
KPIGoal(KPI_Name)  
```  
  
## <a name="arguments"></a>Arguments  
 *Nom_icp*  
 Expression de chaîne valide qui spécifie le nom d'un indicateur de performance clé.  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne la valeur, l'objectif, l'état et la tendance de l'indicateur de performance clé de la mesure Channel Revenue pour les descendants des trois membres de la hiérarchie d'attribut Fiscal Year :  
  
```  
SELECT  
   { KPIValue("Channel Revenue"),   
     KPIGoal("Channel Revenue"),  
     KPIStatus("Channel Revenue"),   
     KPITrend("Channel Revenue")  
   } ON Columns,  
Descendants  
   ( { [Date].[Fiscal].[Fiscal Year].&[2002],  
       [Date].[Fiscal].[Fiscal Year].&[2003],  
       [Date].[Fiscal].[Fiscal Year].&[2004]   
     }, [Date].[Fiscal].[Fiscal Quarter]  
   ) ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
