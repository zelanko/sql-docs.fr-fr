---
title: Élément ExecuteResponse (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 32f1994fb9205743d759fe4ae9aef294b851d26c
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="xml-elements---objects---executeresponse"></a>XML éléments - objets - ExecuteResponse
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient les informations retournées par une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en réponse à une [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) appel de méthode.  
  
 **Espace de noms** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ExecuteResponse>  
   <return>  
</ExecuteResponse>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément obligatoire qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|[de retour](../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Le **ExecuteResponse** élément est l’élément le plus élevé dans le corps d’une réponse SOAP pour le **Execute** (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément DiscoverResponse &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)   
 [Objets &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-objects.md)  
  
  
