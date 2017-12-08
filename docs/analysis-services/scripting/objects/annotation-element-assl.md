---
title: "Élément d’annotation (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Annotation Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Annotation
helpviewer_keywords: Annotation element
ms.assetid: 7d75291a-47b4-498a-8ba4-3d093b8513b2
caps.latest.revision: "43"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9583acd747910621f79622383f9eda6232dff5e2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
|Éléments enfants|[Nom](../../../analysis-services/scripting/properties/name-element-assl.md), [valeur](../../../analysis-services/scripting/properties/value-element-assl.md), [visibilité](../../../analysis-services/scripting/properties/visibility-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Le **Annotation** élément permet d’étendre le schéma ASSL pour tous les objets autres que ceux utilisés uniquement pour la définition d’un type de données complexes. Le **valeur** élément de la **Annotation** élément peut contenir un XML valide à partir de n’importe quel espace de noms XML autre qu’ASSL et soumis aux règles suivantes :  
  
-   Les données XML peuvent contenir uniquement des éléments.  
  
-   Chaque élément doit avoir un nom unique. Il est recommandé que la valeur de la **nom** élément de la **Annotation** l’élément fait référence à l’espace de noms cible.  
  
 Ces règles sont imposées pour autoriser le contenu de la **Annotation** paires d’élément doit être exposée comme un ensemble de nom/valeur via d’autres interfaces, telles que les objets DSO (Decision Support).  
  
 Les commentaires et l’espace blanc dans le **Annotation** élément qui ne sont pas compris dans un élément enfant ne peuvent pas être conservé. De plus, tous les éléments doivent être accessibles en lecture-écriture ; les éléments en lecture seule seront ignorés.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Annotation>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
