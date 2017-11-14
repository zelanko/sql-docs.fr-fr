---
title: "Élément Capability (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Capability Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Capability
- http://schemas.microsoft.com/analysisservices/2003/engine#Capability
- microsoft.xml.analysis.capability
helpviewer_keywords:
- Capability element
ms.assetid: 544a733e-77fc-48a0-8f92-9cd1fdbcf824
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 50a1509e5b4b51778e329dec7bea9554cfca4234
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="capability-element-xmla"></a>Élément Capability (XMLA)
  Indique la prise en charge pour une fonctionnalité de protocole dans le parent [ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md) élément d’en-tête.  
  
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
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **fonctionnalité** élément indique qu’une fonctionnalité particulière, telles que la compression, ou binaire est prise en charge soit par l’application qui a inclus le **ProtocolCapabilities** élément d’en-tête dans l’en-tête SOAP de la demande SOAP, ou par l’instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] incluant la **ProtocolCapabilities** élément d’en-tête dans l’en-tête SOAP de la réponse SOAP. La valeur de la **fonctionnalité** élément est le nom de la capacité à prendre en charge.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend en charge les fonctionnalités répertoriées dans le tableau suivant.  
  
|Nom de fonctionnalité| Description|  
|---------------------|-----------------|  
|sx|Prise en charge du format XML binaire|  
|xpress|Prise en charge de la compression|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des connexions et Sessions &#40; XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

