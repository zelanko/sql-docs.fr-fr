---
title: Élément Capability (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Capability Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Capability
- http://schemas.microsoft.com/analysisservices/2003/engine#Capability
- microsoft.xml.analysis.capability
helpviewer_keywords:
- Capability element
ms.assetid: 544a733e-77fc-48a0-8f92-9cd1fdbcf824
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7c6fd189a44ec34283e87cd220f2c582f982ffa9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105339"
---
# <a name="capability-element-xmla"></a>Élément Capability (XMLA)
  Indique la prise en charge pour une fonctionnalité de protocole dans le parent [ProtocolCapabilities](../xml-elements-headers/protocolcapabilities-element-xmla.md) élément d’en-tête.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ProtocolCapabilities>  
   ...  
   <Capability>...</Capability>  
   ...  
</ProtocolCapabilities>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ProtocolCapabilities](../xml-elements-headers/protocolcapabilities-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le `Capability` élément indique que l’utilisation d’une fonctionnalité particulière, tels que le fichier binaire ou la compression, est pris en charge soit par l’application incluant le `ProtocolCapabilities` élément d’en-tête dans l’en-tête SOAP de la demande SOAP ou par l’instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] incluant la `ProtocolCapabilities` élément d’en-tête dans l’en-tête SOAP de la réponse SOAP. La valeur de l'élément `Capability` est le nom de la fonctionnalité à prendre en charge.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend en charge les fonctionnalités répertoriées dans le tableau suivant.  
  
|Nom de fonctionnalité|Description|  
|---------------------|-----------------|  
|sx|Prise en charge du format XML binaire|  
|xpress|Prise en charge de la compression|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des connexions et Sessions &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
