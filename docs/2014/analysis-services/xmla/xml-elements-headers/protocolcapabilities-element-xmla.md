---
title: Élément ProtocolCapabilities (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ProtocolCapabilities Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.protocolcapabilities
- http://schemas.microsoft.com/analysisservices/2003/engine#ProtocolCapabilities
- urn:schemas-microsoft-com:xml-analysis#ProtocolCapabilities
helpviewer_keywords:
- ProtocolCapabilities element
ms.assetid: f923896a-3f32-46a3-9543-388c30b3465d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 12e4cac0c9846582c40213048e71c7f3793ff736
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219039"
---
# <a name="protocolcapabilities-element-xmla"></a>Élément ProtocolCapabilities (XMLA)
  Utilise l’en-tête SOAP dans un message de demande SOAP pour identifier les fonctionnalités de protocole entre une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] et une application cliente.  
  
 **Namespace** http://schemas.microsoft.com/analysisservices/2003/engine  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <ProtocolCapabilities xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
         <Capability>...</Capability>  
      </ProtocolCapabilities>  
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Fonctionnalité](../xml-elements-properties/capability-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 L'élément `ProtocolCapabilities` permet aux applications clientes de négocier à tout moment des fonctionnalités de protocole, notamment la prise en charge du code XML binaire ou de la compression, avec une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. La négociation de protocole implique les étapes suivantes :  
  
1.  L’application cliente identifie sa fonctionnalité de protocole en envoyant une demande SOAP qui inclut le `ProtocolCapabilities` élément dans le cadre de l’en-tête SOAP.  
  
2.  L'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] reçoit et traite la demande SOAP.  
  
3.  Si l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] dispose de la même fonctionnalité de protocole que celle demandée, elle transmet une réponse SOAP qui inclut le même élément `ProtocolCapabilities` que l'élément envoyé dans la demande SOAP. La négociation du protocole est alors réussie. Dans le cas inverse, les fonctionnalités de protocole ne sont pas négociées comme il se doit et l'instance retourne une erreur SOAP.  
  
 Après la négociation des fonctionnalités de protocole, la durée pendant laquelle l’application cliente et le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilisation de l’instance un protocole particulier dépend de la session explicite ou implicite :  
  
-   Une session explicite est créé à l’aide de la [BeginSession](session-element-xmla.md) élément d’en-tête. Pour une session explicite, le protocole négocié est utilisé jusqu'à ce que l’application cliente envoie une nouvelle `ProtocolCapabilities` élément ou la session se termine.  
  
-   Une session implicite est créée par une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Elle n'est pas définie de manière explicite par l'application cliente lorsque vous soumettez une demande SOAP. Dans le cadre de ce type de session, le protocole négocié est employé uniquement jusqu'à ce que la demande SOAP soit terminée.  
  
 Les fonctionnalités de protocole n'ont pas à être négociées de manière explicite, Autrement dit, une application cliente ne devra pas inclure un `ProtocolCapabilities` élément dans le cadre de la demande SOAP. Si une demande SOAP n'inclut pas d'élément `ProtocolCapabilities`, l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] répond en adoptant le même format que la demande SOAP.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des connexions et Sessions &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [En-têtes &#40;XMLA&#41;](xml-elements-headers.md)  
  
  
