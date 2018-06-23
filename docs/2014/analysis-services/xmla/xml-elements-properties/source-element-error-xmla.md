---
title: Source de l’élément (erreur) (XMLA) | Documents Microsoft
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
- Source Element (Error)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Source
- http://schemas.microsoft.com/analysisservices/2003/engine#Source
- microsoft.xml.analysis.source
helpviewer_keywords:
- Source element
ms.assetid: eed47b9f-0501-4baf-8cac-3ea839a859c3
caps.latest.revision: 9
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5652a7107a17f253c6d813cfdddce8d4edfefec7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142886"
---
# <a name="source-element-error-xmla"></a>Élément Source (Error) (XMLA)
  Contient le nom du composant qui a créé l'élément [Error](error-element-xmla.md) parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Error>  
   ...  
   <Source>...</Source>  
   ...  
</Error>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Erreur](error-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  