---
title: Élément LogFileRollover (ASSL) | Microsoft Docs
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
- LogFileRollover Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- LogFileRollover
helpviewer_keywords:
- LogFileRollover element
ms.assetid: 5484e167-b891-431a-bbae-946ea6eb4a3c
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 12ed8df0217baeb5f760273ad6998e2344f4fbb8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299019"
---
# <a name="logfilerollover-element-assl"></a>Élément LogFileRollover (ASSL)
  Spécifie si l’enregistrement de [Trace](../objects/trace-element-assl.md) sortie doit être remplacé par un nouveau fichier ou doit s’arrêter lorsque la taille maximale du fichier journal qui est spécifiée dans [LogFileSize](logfilesize-element-assl.md) est atteinte.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Trace>  
   ...  
   <LogFileRollover>...</LogFileRollover>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|False|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Trace](../objects/trace-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Si l'élément `LogFileRollover` a la valeur True, un nouveau fichier est démarré lorsque la taille du fichier journal dépasse la valeur spécifiée dans l'élément `LogFileSize` de l'élément parent `Trace` ; sinon, l'enregistrement s'arrête.  
  
 L’élément qui correspond au parent de `LogFileRollover` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>Voir aussi  
 [Effectue le suivi des élément &#40;ASSL&#41;](../collections/traces-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
