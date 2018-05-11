---
title: Élément UnknownMember (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7af2c63cf4e7bd6532f0233e6e6c65075769dff7
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="unknownmember-element-assl"></a>Élément UnknownMember (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Indique si le membre inconnu est visible.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Dimension>  
      ...  
   <UnknownMember>...</UnknownMember>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Aucun*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Visible*|Le membre inconnu existe et est affiché.|  
|*Hidden*|Le membre inconnu existe mais n'est pas affiché.|  
|*Aucun*|Le membre inconnu n'est pas utilisé.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **UnknownMember** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.UnknownMemberBehavior>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément UnknownMemberName &#40;ASSL&#41;](../../../analysis-services/scripting/properties/unknownmembername-element-assl.md)   
 [Élément UnknownMemberTranslation &#40;ASSL&#41;](../../../analysis-services/scripting/objects/unknownmembertranslation-element-assl.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
