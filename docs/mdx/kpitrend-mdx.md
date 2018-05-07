---
title: KPITrend (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- KPITrend function
ms.assetid: 0afd4513-af6e-4517-8e69-177bc7807d03
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 473f5e63c9cb9a6d22fcc1b4b607c35abbc0b659
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="kpitrend-mdx"></a>KPITrend (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne la valeur normalisée qui représente la portion tendance de l'indicateur de performance clé spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
KPITrend(KPI_Name)  
```  
  
## <a name="arguments"></a>Arguments  
 *Nom_icp*  
 Expression de chaîne valide qui précise le nom de l'indicateur de performance clé.  
  
## <a name="remarks"></a>Notes  
 La valeur de tendance est généralement une valeur normalisée comprise entre -1 et 1.  
  
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
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)  
  
  
