---
title: Élément DisplayFlag (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d4a65524e6e7dd94ba7fad989d4bbf71e0e11abd
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="displayflag-element-assl"></a>Élément DisplayFlag (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contient un indicateur en lecture seule qui indique si les composants d’interface utilisateur doivent afficher associé [ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ServerProperty>  
   ...  
   <DisplayFlag>...</DisplayFlag>  
   ...  
</ServerProperty>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de **DisplayFlag** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément ServerProperties & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)   
 [Server, élément & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
