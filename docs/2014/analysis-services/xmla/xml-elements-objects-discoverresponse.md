---
title: Élément DiscoverResponse (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DiscoverResponse Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DiscoverResponse
- microsoft.xml.analysis.discoverresponse
- urn:schemas-microsoft-com:xml-analysis#DiscoverResponse
helpviewer_keywords:
- DiscoverResponse element
ms.assetid: 20e10a82-dbd1-4ead-b92d-f84b4b2f10c6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 763724fb08a849000cb960435847a84447ba5674
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105389"
---
# <a name="discoverresponse-element-xmla"></a>Élément DiscoverResponse (XMLA)
  Contient les informations retournées par une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en réponse à une [Discover](xml-elements-methods-discover.md) appel de méthode.  
  
 **Espace de noms** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DiscoverResponse>  
   <return>  
</DiscoverResponse>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément obligatoire qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[retour](xml-elements-properties/return-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 L'élément `DiscoverResponse` est l'élément le plus haut dans le corps d'une réponse SOAP pour la méthode `Discover`.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément ExecuteResponse &#40;XMLA&#41;](xml-elements-objects-executeresponse.md)   
 [Objets &#40;XMLA&#41;](xml-elements-objects.md)  
  
  
