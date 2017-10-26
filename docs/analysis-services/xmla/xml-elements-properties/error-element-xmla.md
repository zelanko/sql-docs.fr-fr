---
title: "Élément Error (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Error Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.error
- http://schemas.microsoft.com/analysisservices/2003/engine#Error
- urn:schemas-microsoft-com:xml-analysis#Error
helpviewer_keywords:
- Error element
ms.assetid: add670cb-cab2-42be-91a3-d0c385f29d16
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 214dc93af2f02f4bd47ac9d0199b0254fe2ab024
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="error-element-xmla"></a>Élément Error (XMLA)
  Contient des informations sur une erreur retournée par une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Message>  
   <Error   
      ErrorCode="unsignedint"   
      Severity="string"   
      Description="string"  
      Source="string"  
      HelpFile="string"  
   />  
</Message>  
<!-- or -->  
<Cell><!-- or row -->  
   <!-- A child element -->  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception"  
         < ErrorCode>...</ErrorCode>  
         < Description>...</Description>  
         < Source>...</Source>  
         < HelpFile>...</HelpFile>  
      </Error>  
   <!-- /A child element -- >  
</Cell>  
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
|Éléments enfants|Consultez le tableau ci-dessous.|  
  
|Ancêtre|Éléments enfants|  
|--------------|--------------------|  
|[Message](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|Aucune|  
|[Cellule](../../../analysis-services/xmla/xml-elements-properties/cell-element-mddataset-xmla.md), [ligne](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|[Description](../../../analysis-services/xmla/xml-elements-properties/description-element-xmla.md), [ErrorCode](../../../analysis-services/xmla/xml-elements-properties/errorcode-element-xmla.md), [HelpFile](../../../analysis-services/xmla/xml-elements-properties/helpfile-element-xmla.md), [Source](../../../analysis-services/xmla/xml-elements-properties/source-element-error-xmla.md)|  
  
## <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|ErrorCode|Requis **UnsignedInt** attribut (uniquement lorsque **Message** est l’élément parent.) Contient le code de retour numérique de l'erreur.|  
|Severity|Facultatif **chaîne** attribut (uniquement lorsque **Message** est l’élément parent.) Affiche la gravité de l'erreur.|  
| Description|Facultatif **chaîne** attribut (uniquement lorsque **Message** est l’élément parent.) Contient le texte descriptif de l'erreur.|  
|Source|Facultatif **chaîne** attribut (uniquement lorsque **Message** est l’élément parent.) Contient le nom du composant qui a déclenché l'erreur.|  
|HelpFile|Facultatif **chaîne** attribut (uniquement lorsque **Message** est l’élément parent.) Contient le chemin d'accès ou l'URL menant au fichier ou à la rubrique d'aide qui décrit l'erreur.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Warning &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md)   
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

