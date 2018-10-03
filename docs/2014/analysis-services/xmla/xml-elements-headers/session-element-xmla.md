---
title: Élément de session (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Session Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.session
- http://schemas.microsoft.com/analysisservices/2003/engine#Session
- urn:schemas-microsoft-com:xml-analysis#Session
helpviewer_keywords:
- Session element
ms.assetid: 884ed090-968e-41d3-97e5-6d12787467da
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a2f18754a2ef7d44a2a85bb9da78378bc631ecd0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080389"
---
# <a name="session-element-xmla"></a>Élément Session (XMLA)
  Utilise l’en-tête SOAP dans un message de demande SOAP pour identifier une session explicite existante sur une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 **Espace de noms** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <Session  
         xmlns="urn:schemas-microsoft-com:xml-analysis"  
         SessionId="string" />  
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
|Éléments enfants|None|  
  
## <a name="attributes"></a>Attributs  
  
|Attribute|Description|  
|---------------|-----------------|  
|SessionId|Attribut `String` obligatoire qui identifie la session à employer. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] fait appel à un identificateur global unique (GUID) pour identifier une session.|  
  
## <a name="remarks"></a>Notes  
 L'élément d'en-tête `Session` identifie une session existante démarrée explicitement sur l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. L'élément `Session` fait partie de l'en-tête SOAP dans les types de messages suivants :  
  
-   Une réponse SOAP contenant un [BeginSession](session-element-xmla.md) élément d’en-tête SOAP.  
  
-   Une demande SOAP pour identifier la session sur laquelle exécuter le [Discover](../xml-elements-methods-discover.md) ou [Execute](../xml-elements-methods-execute.md) (méthode).  
  
 Un identificateur de session ne garantit pas qu'une session reste valide. La session spécifiée dans l'élément `Session` peut expirer. Par exemple, une session peut expirer si la session dépasse le délai d'attente imparti ou si la connexion associée à la session est fermée. Si la session arrive à expiration et n'est plus valide, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] y met un terme et restaure toutes les transactions en cours de traitement. Tous les messages SOAP transmis avec un identificateur de session qui n'est plus valide échouent avec une erreur SOAP indiquant que la session spécifiée est introuvable.  
  
 Si un élément `Session` n'est pas envoyé dans le cadre d'une demande SOAP, l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] lance implicitement une session pendant la durée de l'appel de méthode `Discover` ou `Execute`, puis met fin à la session une fois l'appel de méthode terminé.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément EndSession &#40;XMLA&#41;](endsession-element-xmla.md)   
 [Gestion des connexions et Sessions &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [En-têtes &#40;XMLA&#41;](xml-elements-headers.md)  
  
  
