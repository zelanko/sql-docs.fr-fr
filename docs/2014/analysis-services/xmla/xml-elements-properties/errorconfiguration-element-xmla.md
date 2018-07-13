---
title: Élément ErrorConfiguration (XMLA) | Microsoft Docs
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
- ErrorConfiguration Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#ErrorConfiguration
- urn:schemas-microsoft-com:xml-analysis#ErrorConfiguration
- microsoft.xml.analysis.errorconfiguration
helpviewer_keywords:
- ErrorConfiguration element
ms.assetid: 5e350f5f-3a14-49b4-80c0-208c61f336d5
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a93464ed9f6d2708246e8d04c833b9261b7c71fd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169280"
---
# <a name="errorconfiguration-element-xmla"></a>Élément ErrorConfiguration (XMLA)
  Spécifie les paramètres de gestion des erreurs peuvent se produire pendant une [Batch](../xml-elements-commands/batch-element-xmla.md) ou [processus](../xml-elements-commands/process-element-xmla.md) opération.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Batch> <!-- or Process -->  
   ...  
   <ErrorConfiguration>  
      <KeyErrorLimit>...</KeyErrorLimit>  
      <KeyErrorLogFile>...</KeyErrorLogFile>  
      <KeyErrorAction>...</KeyErrorAction>  
      <KeyErrorLimitAction>...</KeyErrorLimitAction>  
      <KeyNotFound>...</KeyNotFound>  
      <KeyDuplicate>...</KeyDuplicate>  
      <NullKeyConvertedToUnknown>...</NullKeyConvertedToUnknown>  
      <NullKeyNotAllowed>...<NullKeyNotAllowed>  
   </ErrorConfiguration>  
   ...  
</Batch>  
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
|Éléments parents|[Batch](../xml-elements-commands/batch-element-xmla.md), [Process](../xml-elements-commands/process-element-xmla.md)|  
|Éléments enfants|[KeyDuplicate](../../scripting/properties/keyduplicate-element-assl.md), [KeyErrorAction](../../scripting/objects/action-element-assl.md), [KeyErrorLimit](../../scripting/properties/keyerrorlimit-element-assl.md), [KeyErrorLimitAction](../../scripting/properties/keyerrorlimitaction-element-assl.md), [KeyErrorLogFile](../../scripting/objects/file-element-assl.md), [ KeyNotFound](../../scripting/properties/keynotfound-element-assl.md), [NullKeyConvertedToUnknown](../../scripting/properties/nullkeyconvertedtounknown-element-assl.md), [NullKeyNotAllowed](../../scripting/properties/nullkeynotallowed-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 La structure de cet élément est identique à la structure de l'élément `ErrorConfiguration` en langage ASSL (Analysis Services Scripting Language). Pour plus d’informations sur la `ErrorConfiguration` élément, consultez [ErrorConfiguration élément &#40;ASSL&#41;](../../scripting/objects/errorconfiguration-element-assl.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
