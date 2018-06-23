---
title: Élément EndSession (XMLA) | Documents Microsoft
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
api_name:
- EndSession Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#EndSession
- urn:schemas-microsoft-com:xml-analysis#EndSession
- microsoft.xml.analysis.endsession
helpviewer_keywords:
- EndSession element
ms.assetid: e64f1da4-5c83-40a2-b15e-837f5451bafa
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 1f54f1ec23fbb07744ffea1009f4df1aef11b6f4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045434"
---
# <a name="endsession-element-xmla"></a>Élément EndSession (XMLA)
  Utilise l’en-tête SOAP dans un message de demande SOAP pour terminer une session existante sur une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 **Espace de noms** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <EndSession  
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
|SessionId|Attribut `String` obligatoire qui identifie la session à terminer. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] fait appel à un identificateur global unique (GUID) pour identifier une session.|  
  
## <a name="remarks"></a>Notes  
 L'élément d'en-tête `EndSession` fait partie de la demande SOAP envoyée à une session existante démarrée explicitement sur une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Si l'élément d'en-tête `EndSession` est envoyé mais contient un identificateur de session qui n'est plus valide, une erreur SOAP indiquant que la session est introuvable est retournée.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément BeginSession &#40;XMLA&#41;](session-element-xmla.md)   
 [Élément session &#40;XMLA&#41;](session-element-xmla.md)   
 [Gestion des connexions et Sessions &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [En-têtes &#40;XMLA&#41;](xml-elements-headers.md)  
  
  