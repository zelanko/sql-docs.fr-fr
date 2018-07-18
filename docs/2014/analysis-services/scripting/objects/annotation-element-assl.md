---
title: Élément d’annotation (ASSL) | Microsoft Docs
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
- Annotation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Annotation
helpviewer_keywords:
- Annotation element
ms.assetid: 7d75291a-47b4-498a-8ba4-3d093b8513b2
caps.latest.revision: 43
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0453688aab37831c54bad3080a34409b078740bf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37304499"
---
# <a name="annotation-element-assl"></a>Élément Annotation (ASSL)
  Contient des éléments utilisés pour étendre le schéma ASSL (Analysis Services Scripting Language).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Annotations>  
   <Annotation>  
      <Name>...</Name>  
      <Visibility>...</Visibility>  
      <Value>...</Value>  
   </Annotation>  
</Annotations >  
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
|Éléments parents|[Annotations](../collections/annotations-element-assl.md)|  
|Éléments enfants|[Nom](../properties/name-element-assl.md), [valeur](../properties/value-element-assl.md), [visibilité](../properties/visibility-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L'élément `Annotation` permet d'étendre le schéma ASSL pour tous les objets autres que ceux utilisés uniquement pour la définition d'un type de données complexe. L'élément `Value` de l'élément `Annotation` peut contenir des données XML valides provenant de n'importe quel espace de noms XML autre qu'ASSL et soumises aux règles suivantes :  
  
-   Les données XML peuvent contenir uniquement des éléments.  
  
-   Chaque élément doit avoir un nom unique. Il est recommandé que la valeur de l'élément `Name` de l'élément `Annotation` fasse référence à l'espace de noms cible.  
  
 Ces règles sont imposées dans le but d'autoriser la présentation du contenu de l'élément `Annotation` sous la forme d'un jeu de paires nom/valeur sur d'autres interfaces, telles que Decision Support Objects (DSO).  
  
 Les commentaires et l'espace blanc dans l'élément `Annotation` qui ne sont pas compris dans un élément enfant ne peuvent pas être conservés. De plus, tous les éléments doivent être accessibles en lecture-écriture ; les éléments en lecture seule seront ignorés.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Annotation>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
