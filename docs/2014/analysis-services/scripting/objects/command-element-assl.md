---
title: Commande élément (ASSL) | Documents Microsoft
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
- Command Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Command
helpviewer_keywords:
- Command element
ms.assetid: 277598b5-9939-4d7f-8c75-06470c3fabdd
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 556462d93b991818e31e543049a05f7d1c7eaa8a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042572"
---
# <a name="command-element-assl"></a>Élément Command (ASSL)
  Définit une commande qui est disponible pour une utilisation dans le contexte de l’élément parent de la [commandes](../collections/commands-element-assl.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Commands>  
   <Command>  
      <Text>...</Text>  
   </Command>  
</Commands >  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Commandes](../collections/commands-element-assl.md)|  
|Éléments enfants|[Texte](../properties/text-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Command>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  