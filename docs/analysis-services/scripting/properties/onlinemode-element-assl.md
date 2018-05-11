---
title: Élément OnlineMode (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d566ff327a08b6c9c0cd7f0f7ee8d0cd5c219abc
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="onlinemode-element-assl"></a>Élément OnlineMode (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Spécifie si la base de données est remise en ligne immédiatement dès le début de la reconstruction du cache ou seulement lorsque la reconstruction du cache est terminée.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ProactiveCaching>  
   ...  
   <OnlineMode>...</OnlineMode>  
   ...  
</ProactiveCaching>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Immédiate*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Immédiate*|La base de données est remise en ligne immédiatement lorsque la reconstruction du cache est initiée.|  
|*OnCacheComplete*|La base de données n'est remise en ligne que lorsque la reconstruction du cache est terminée.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **OnlineMode** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément ProactiveCaching &#40;ASSL&#41;](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)  
  
  
