---
title: Élément BeginSession (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- BeginSession Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginSession
- urn:schemas-microsoft-com:xml-analysis#BeginSession
- microsoft.xml.analysis.beginsession
helpviewer_keywords:
- BeginSession element
ms.assetid: 49873a97-58d7-42a9-ab7f-e045e2856737
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9194333e376dc8ab685057847c3f4156330d5dfa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48180059"
---
# <a name="beginsession-element-xmla"></a>Élément BeginSession (XMLA)
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément d'en-tête `BeginSession` fait partie d'une demande SOAP envoyée à une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] et démarre explicitement une nouvelle session sur cette instance. L’en-tête SOAP retourné par la réponse SOAP contient un [Session](session-element-xmla.md) élément qui identifie la nouvelle session. Ce nouvel identificateur de session peut être stocké et envoyé dans les demandes SOAP suivantes à l'aide de l'élément d'en-tête `Session`.  
  
 Si l'élément d'en-tête `BeginSession` n'est pas envoyé, aucune session n'est démarrée explicitement. Si une session n'est pas démarrée explicitement, les transactions sur cette session ne peuvent pas être gérées. En d’autres termes, vous ne pouvez pas utiliser le code XML suivant pour les commandes Analysis (XMLA) : [BeginTransaction](../xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../xml-elements-commands/committransaction-element-xmla.md), et [RollbackTransaction](../xml-elements-commands/rollbacktransaction-element-xmla.md). Toutes les méthodes et les commandes XMLA exécutées sur une session démarrée implicitement sont considérées comme des transactions atomiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément EndSession &#40;XMLA&#41;](endsession-element-xmla.md)   
 [Élément session &#40;XMLA&#41;](session-element-xmla.md)   
 [Gestion des connexions et Sessions &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [En-têtes &#40;XMLA&#41;](xml-elements-headers.md)  
  
  
