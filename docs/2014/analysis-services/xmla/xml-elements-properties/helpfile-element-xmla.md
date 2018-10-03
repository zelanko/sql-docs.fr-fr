---
title: Élément HelpFile (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- HelpFile Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#HelpFile
- http://schemas.microsoft.com/analysisservices/2003/engine#HelpFile
- microsoft.xml.analysis.helpfile
helpviewer_keywords:
- HelpFile element
ms.assetid: 537ea7a8-5064-4a31-b0cd-ab7e891fef09
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 71489a574aa344d81ffedfa438818bdfbaddb514
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48134569"
---
# <a name="helpfile-element-xmla"></a>Élément HelpFile (XMLA)
  Contient le chemin d'accès ou l'URL menant au fichier ou à la rubrique d'aide qui décrit l'élément [Error](error-element-xmla.md) parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Error>  
   ...  
   <HelpFile>...</HelpFile>  
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
  
  
