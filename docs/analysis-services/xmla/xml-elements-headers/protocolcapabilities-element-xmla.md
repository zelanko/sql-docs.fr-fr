---
title: "Élément ProtocolCapabilities (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ProtocolCapabilities Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.protocolcapabilities
- http://schemas.microsoft.com/analysisservices/2003/engine#ProtocolCapabilities
- urn:schemas-microsoft-com:xml-analysis#ProtocolCapabilities
helpviewer_keywords:
- ProtocolCapabilities element
ms.assetid: f923896a-3f32-46a3-9543-388c30b3465d
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5d2ff72b1fdc3a3e3a4b09a046933d3ead88fc78
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# Élément ProtocolCapabilities (XMLA)
  Utilise l’en-tête SOAP dans un message de demande SOAP pour identifier les fonctionnalités de protocole entre une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] et une application cliente.  
  
 **Namespace**`http://schemas.microsoft.com/analysisservices/2003/engine`  
  
## Syntaxe  
  
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
  
## Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|[Fonctionnalité](../../../analysis-services/xmla/xml-elements-properties/capability-element-xmla.md)|  
  
## Notes  
 Le **ProtocolCapabilities** élément permet aux applications de client négocier les fonctionnalités de protocole, telles que XML binaire ou de la prise en charge de la compression, avec un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance à tout moment. La négociation de protocole implique les étapes suivantes :  
  
1.  L'application cliente identifie sa fonctionnalité de protocole en envoyant une demande SOAP qui inclut l'élément **ProtocolCapabilities** dans le cadre de l'en-tête SOAP.  
  
2.  L'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] reçoit et traite la demande SOAP.  
  
3.  Si le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance a la même fonctionnalité de protocole que celle demandée, elle transmet une réponse SOAP qui inclut le même **ProtocolCapabilities** élément envoyé dans la demande SOAP, et le protocole a été négocié correctement. Dans le cas inverse, les fonctionnalités de protocole ne sont pas négociées comme il se doit et l'instance retourne une erreur SOAP.  
  
 Après la négociation des fonctionnalités de protocole, la durée pendant laquelle l’application cliente et le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilisation de l’instance un protocole spécifique dépend de la session implicite ou explicite :  
  
-   Une session explicite est créé à l’aide de la [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) élément d’en-tête. Pour ce type de session, le protocole négocié est utilisé jusqu'à l'envoi d'un nouvel élément **ProtocolCapabilities** par l'application cliente ou jusqu'à la fin de la session.  
  
-   Une session implicite est créée par une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Elle n'est pas définie de manière explicite par l'application cliente lorsque vous soumettez une demande SOAP. Dans le cadre de ce type de session, le protocole négocié est employé uniquement jusqu'à ce que la demande SOAP soit terminée.  
  
 Les fonctionnalités de protocole n'ont pas à être négociées de manière explicite, ce qui signifie qu'une application cliente n'a pas pour obligation d'inclure un élément **ProtocolCapabilities** dans le cadre de la demande SOAP. Si une demande SOAP n’inclut pas un **ProtocolCapabilities** élément, le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance répond en adoptant le même format que la demande SOAP.  
  
## Voir aussi  
 [La gestion des connexions et Sessions &#40; XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [En-têtes &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  

