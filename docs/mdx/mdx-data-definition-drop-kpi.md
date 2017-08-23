---
title: Instruction DROP KPI (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- KPI
- DROP
- DROP KPI
- DROP_KPI
helpviewer_keywords:
- DROP KPI statement
- key performance indicators [MDX]
ms.assetid: d19c6809-b8a6-459d-8554-b41854f7cc45
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bf7e54fa8be329af95fba08aa972caf42fa088a8
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-definition---drop-kpi"></a>Définition de données MDX - DROP KPI
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime l'indicateur de performance clé (KPI) spécifié pour le cube spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP KPI CURRENTCUBE | Cube_Name.KPI_Name   
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Name*  
 Chaîne valide qui spécifie le nom du cube.  
  
 *Nom_icp*  
 Chaîne valide qui spécifie le nom du KPI à supprimer.  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER une instruction de l’indicateur de performance clé &#40; MDX &#41;](../mdx/mdx-data-definition-create-kpi.md)   
 [Instructions MDX de définition de données &#40; MDX &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  

