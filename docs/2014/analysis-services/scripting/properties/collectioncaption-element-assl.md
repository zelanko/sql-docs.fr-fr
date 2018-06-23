---
title: Élément CollectionCaption (ASSL) | Documents Microsoft
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
ms.assetid: 33929373-11df-4f89-8d2e-d63923c44f53
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bba7c2ab2cffb2287b1eff84c5e9fc9f385119cb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141889"
---
# <a name="collectioncaption-element-assl"></a>Élément CollectionCaption (ASSL)
  Contient le nom au pluriel de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<RelationshipEndTranslation>  
   <CollectionCaption>...</CollectionCaption>  
</RelationshipEndTranslation>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[RelationshipEndTranslation](../objects/translation-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `CollectionCaption` dans l’objets AMO (Analysis Management) modèle objet est : Microsoft.AnalysisServices.relationshipendtranslation.  
  
  