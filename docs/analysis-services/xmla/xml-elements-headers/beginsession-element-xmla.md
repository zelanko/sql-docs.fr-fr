---
title: Élément BeginSession (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BeginSession Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginSession
- urn:schemas-microsoft-com:xml-analysis#BeginSession
- microsoft.xml.analysis.beginsession
helpviewer_keywords:
- BeginSession element
ms.assetid: 49873a97-58d7-42a9-ab7f-e045e2856737
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 06d08989a7efbaa690853887ac2cc8b15e0f5c31
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="beginsession-element-xmla"></a>Élément BeginSession (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Utilise un en-tête SOAP dans un message de demande SOAP pour démarrer une nouvelle session sur une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 **Espace de noms** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <BeginSession  
         xmlns="urn:schemas-microsoft-com:xml-analysis" />  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **BeginSession** élément d’en-tête fait partie d’une demande SOAP envoyée à un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance et démarre explicitement une nouvelle session sur l’instance. L’en-tête SOAP retourné par la réponse SOAP contient un [Session](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md) élément qui identifie la nouvelle session. Ce nouvel identificateur de session est stocké et envoyé dans les demandes SOAP suivantes à l’aide de la **Session** élément d’en-tête.  
  
 Si le **BeginSession** élément d’en-tête n’est pas envoyée, une session n’est pas démarrée explicitement. Si une session n'est pas démarrée explicitement, les transactions sur cette session ne peuvent pas être gérées. En d’autres termes, vous ne pouvez pas utiliser le code XML suivant pour les commandes Analysis (XMLA) : [BeginTransaction](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md), et [RollbackTransaction](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md). Toutes les méthodes et les commandes XMLA exécutées sur une session démarrée implicitement sont considérées comme des transactions atomiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément EndSession & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [Élément session & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)   
 [La gestion des connexions et Sessions & #40 ; XMLA & #41 ;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [En-têtes & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
