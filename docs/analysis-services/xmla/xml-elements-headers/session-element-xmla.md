---
title: Élément session (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eca14da555b90b90f692eec384939578d30bd89d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="session-element-xmla"></a>Élément Session (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Utilise l'en-tête SOAP dans un message de demande SOAP pour identifier une session explicite existante sur une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|Aucun|  
  
## <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|SessionId|Attribut **String** obligatoire qui identifie la session à employer. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] fait appel à un identificateur global unique (GUID) pour identifier une session.|  
  
## <a name="remarks"></a>Notes  
 Le **Session** élément d’en-tête identifie une session existante démarrée explicitement sur le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance. L'élément **Session** fait partie de l'en-tête SOAP dans les types de messages suivants :  
  
-   Une réponse SOAP contenant un élément d'en-tête SOAP [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) .  
  
-   Une demande SOAP permettant d'identifier la session sur laquelle exécuter la méthode [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) ou [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) .  
  
 Un identificateur de session ne garantit pas qu'une session reste valide. La session spécifiée dans l'élément **Session** peut expirer. Par exemple, une session peut expirer si la session dépasse le délai d'attente imparti ou si la connexion associée à la session est fermée. Si la session arrive à expiration et n'est plus valide, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] y met un terme et restaure toutes les transactions en cours de traitement. Tous les messages SOAP transmis avec un identificateur de session qui n'est plus valide échouent avec une erreur SOAP indiquant que la session spécifiée est introuvable.  
  
 Si un **Session** élément n’est pas envoyé dans le cadre d’une demande SOAP, le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance commence implicitement une session pendant la durée de la **Discover** ou **Execute** appel de méthode, puis se termine cette session une fois l’appel de méthode terminé.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément EndSession & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [La gestion des connexions et Sessions & #40 ; XMLA & #41 ;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [En-têtes & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
