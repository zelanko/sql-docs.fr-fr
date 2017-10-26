---
title: "Élément Warning (XMLA) | Documents Microsoft"
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
- Warning Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Warning
- microsoft.xml.analysis.warning
- http://schemas.microsoft.com/analysisservices/2003/engine#Warning
helpviewer_keywords:
- Warning element
ms.assetid: a34a6caa-4b68-486b-8f50-cdc124c65888
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b5bd57e1ca9819f750f2538eba53b437aa8191a8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="warning-element-xmla"></a>Élément Warning (XMLA)
  Contient des informations sur un avertissement retourné par une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Message>  
   <Warning   
      ErrorCode="unsignedint"   
      Severity="string"   
      Description="string"  
      Source="string"  
      HelpFile="string"  
   />  
</Message>  
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
|Éléments parents|[Message](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
|Éléments enfants|Aucun|  
  
## <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|ErrorCode|Attribut **UnsignedInt** requis. Contient le code de retour numérique de l'avertissement.|  
|Gravité|Attribut **String** facultatif. Affiche la gravité de l'avertissement.|  
|Description|Attribut **String** facultatif. Contient le texte descriptif de l'avertissement.|  
|Source|Attribut **String** facultatif. Contient le nom du composant qui a généré l'avertissement.|  
|HelpFile|Attribut **String** facultatif. Contient le chemin d'accès ou l'URL menant au fichier ou à la rubrique d'aide qui décrit l'avertissement.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Error &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md)   
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

