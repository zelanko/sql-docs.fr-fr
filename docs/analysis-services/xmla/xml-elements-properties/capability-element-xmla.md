---
title: Élément Capability (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile"
ms.openlocfilehash: dca8f668f64ab8ced157cf817be1f9f8f6390133
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38062977"
---
# <a name="capability-element-xmla"></a>Élément Capability (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Indique la prise en charge pour une fonctionnalité de protocole dans le parent [ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md) élément d’en-tête.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ProtocolCapabilities>  
   ...  
   <Capability>...</Capability>  
   ...  
</ProtocolCapabilities>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques d’éléments  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le **fonctionnalité** élément indique que l’utilisation d’une fonctionnalité particulière, tels que le fichier binaire ou la compression, est pris en charge soit par l’application incluant le **ProtocolCapabilities** élément d’en-tête dans le En-tête SOAP de la demande SOAP ou par l’instance d’Analysis Services incluant les **ProtocolCapabilities** élément d’en-tête dans l’en-tête SOAP de la réponse SOAP. La valeur de la **fonctionnalité** élément est le nom de la capacité à prendre en charge.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend en charge les fonctionnalités répertoriées dans le tableau suivant.  
  
|Nom de fonctionnalité|Description|  
|---------------------|-----------------|  
|sx|Prise en charge du format XML binaire|  
|xpress|Prise en charge de la compression|  
  
## <a name="see-also"></a>Voir aussi
 [Gestion des connexions et Sessions &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Propriétés &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
