---
title: KPIValue (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords: KPIValue function
ms.assetid: c4f8532c-4c24-4ad5-8847-4522511e0039
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 4e02510740e79519c15ddee8ca3107d275c311eb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="kpivalue-mdx"></a>KPIValue (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le membre chargé de calculer la valeur de l'indicateur de performance clé spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
KPIValue(KPI_Name)  
```  
  
## <a name="arguments"></a>Arguments  
 *Nom_icp*  
 Expression de chaîne valide qui précise le nom de l'indicateur de performance clé.  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne la valeur, l'objectif, l'état et la tendance de l'indicateur de performance clé de la mesure Channel Revenue pour les descendants des trois membres de la hiérarchie d'attribut Fiscal Year.  
  
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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
