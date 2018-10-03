---
title: Erreur, élément (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Error Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.error
- http://schemas.microsoft.com/analysisservices/2003/engine#Error
- urn:schemas-microsoft-com:xml-analysis#Error
helpviewer_keywords:
- Error element
ms.assetid: add670cb-cab2-42be-91a3-d0c385f29d16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5b9b961a0d8d5a33cb0869b72e0250dee5456ca7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210149"
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Boîte de](message-element-xmla.md)|  
  
## <a name="child-elements"></a>Éléments enfants  
  
|Ancêtre|Éléments enfants|  
|--------------|--------------------|  
|[Boîte de](message-element-xmla.md)|None|  
|[Cellule](cell-element-mddataset-xmla.md), [ligne](description-element-xmla.md), [ErrorCode](errorcode-element-xmla.md), [HelpFile](file-element-xmla.md), [Source](source-element-error-xmla.md)|  
  
## <a name="attributes"></a>Attributs  
  
|Attribute|Description|  
|---------------|-----------------|  
|ErrorCode|Requis `UnsignedInt` attribut (uniquement lorsque `Message` est l’élément parent.) Contient le code de retour numérique de l'erreur.|  
|Severity|Facultatif `String` attribut (uniquement lorsque `Message` est l’élément parent.) Affiche la gravité de l'erreur.|  
|Description|Facultatif `String` attribut (uniquement lorsque `Message` est l’élément parent.) Contient le texte descriptif de l'erreur.|  
|Source|Facultatif `String` attribut (uniquement lorsque `Message` est l’élément parent.) Contient le nom du composant qui a déclenché l'erreur.|  
|HelpFile|Facultatif `String` attribut (uniquement lorsque `Message` est l’élément parent.) Contient le chemin d'accès ou l'URL menant au fichier ou à la rubrique d'aide qui décrit l'erreur.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Warning &#40;XMLA&#41;](warning-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
