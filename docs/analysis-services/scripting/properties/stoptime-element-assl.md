---
title: Élément StopTime (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c6228b09c529535e0f50a263f60c5ee819b3cdda
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="stoptime-element-assl"></a>Élément StopTime (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Spécifie la date et l’heure à laquelle un [Trace](../../../analysis-services/scripting/objects/trace-element-assl.md) élément doit s’arrêter.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Trace>  
   ...  
   <StopTime>...</StopTime>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|DateTime|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Trace](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|Éléments enfants|Aucun|  
  
 L’élément qui correspond au parent de **StopTime** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément traces & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/collections/traces-element-assl.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
