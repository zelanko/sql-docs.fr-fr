---
title: En-têtes [XMLA] | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
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
- XMLA, headers
- SOAP headers [XML for Analysis]
- XML for Analysis, headers
- headers [XML for Analysis]
ms.assetid: 36407b5c-d98d-47e4-8d36-d8896e15a748
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1b04b85e3267e7432f37c5f70e823c859a82a952
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37291295"
---
# <a name="headers-xmla"></a>En-têtes [XMLA]
  Le protocole XMLA (XML for Analysis) utilise des éléments XML dans l'en-tête SOAP pour gérer des fonctionnalités au niveau du protocole, telles que la prise en charge de la session et la négociation des fonctionnalités prises en charge.  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques suivantes décrivent les éléments d’en-tête XMLA implémentés par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Méthode|Description|  
|------------|-----------------|  
|[Élément BeginSession &#40;XMLA&#41;](session-element-xmla.md)|Utilise un en-tête SOAP dans un message de demande SOAP pour démarrer une nouvelle session sur une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Élément EndSession &#40;XMLA&#41;](endsession-element-xmla.md)|Utilise l'en-tête SOAP dans un message de demande SOAP pour terminer une session existante sur une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Élément session &#40;XMLA&#41;](session-element-xmla.md)|Utilise l'en-tête SOAP dans un message de demande SOAP pour identifier une session explicite existante sur une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Élément ProtocolCapabilities &#40;XMLA&#41;](protocolcapabilities-element-xmla.md)|Utilise l'en-tête SOAP dans un message de demande SOAP pour identifier des fonctionnalités de protocole entre une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] et une application cliente.|  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments XML &#40;XMLA&#41;](../../dev-guide/xml-elements-xmla.md)   
 [Types de données XML &#40;XMLA&#41;](../xml-data-types/xml-data-types-xmla.md)   
 [Éléments XML &#40;XMLA&#41;](../../dev-guide/xml-elements-xmla.md)  
  
  
