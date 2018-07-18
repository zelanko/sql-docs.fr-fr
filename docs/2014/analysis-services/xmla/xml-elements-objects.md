---
title: Objets (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- objects [XML for Analysis]
- XML for Analysis, objects
- XMLA, objects
ms.assetid: 768188ef-85d4-432a-9390-be05c835137f
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3fdaa8cc81b642212c6aa404a8b6d39e3872c743
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37205899"
---
# <a name="objects-xmla"></a>Objects (XMLA)
  Le protocole XML for Analysis (XMLA) utilise deux méthodes, `Discover` et `Execute`, pour offrir un moyen standard pour les applications d’accéder aux informations sur une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Étant donné que ces méthodes sont appelées en utilisant le protocole SOAP Simple Object Access Protocol (), ils acceptent l’entrée et fournir la sortie au format XML.  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques suivantes décrivent les objets XMLA implémentés par [!INCLUDE[ssAS](../../includes/ssas-md.md)].  
  
|Méthode|Description|  
|------------|-----------------|  
|[Élément DiscoverResponse &#40;XMLA&#41;](xml-elements-objects-discoverresponse.md)|Contient les informations retournées par une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en réponse à une [Discover](xml-elements-methods-discover.md) appel de méthode.|  
|[Élément ExecuteResponse &#40;XMLA&#41;](xml-elements-objects-executeresponse.md)|Contient les informations retournées par une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en réponse à une [Execute](xml-elements-methods-execute.md) appel de méthode.|  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments XML &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [Types de données XML &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [Éléments XML &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)  
  
  
