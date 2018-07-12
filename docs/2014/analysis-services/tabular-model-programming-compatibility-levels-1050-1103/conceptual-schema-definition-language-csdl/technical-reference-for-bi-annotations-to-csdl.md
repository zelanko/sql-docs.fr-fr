---
title: Référence technique pour les Annotations BI du langage CSDL | Microsoft Docs
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
ms.assetid: 63b3e069-6ba5-474e-b769-47b7cc87b7dd
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 78300a412d7db986edd76172c7cf49e6c86aaec9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192381"
---
# <a name="technical-reference-for-bi-annotations-to-csdl"></a>Guide de référence technique pour les annotations BI du langage CSDL
  Cette section répertorie les éléments, l'attribut et les propriétés dans le CSDL qui sont utilisés pour représenter les modèles tabulaires [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Certains éléments sont nouveaux ; d'autres ont été annotés ou étendus pour la prise en charge de la modélisation Business Intelligence.  
  
 Pour une vue d’ensemble des modèles tabulaires et comment les entités, les relations et les formules sont représentées dans le langage CSDL, consultez [Annotations CSDL pour Business Intelligence &#40;CSDLBI&#41;](../csdl-annotations-for-business-intelligence-csdlbi.md).  
  
## <a name="extended-csdl-elements-complex-types"></a>Éléments CSDL étendus : types complexes  
 Les éléments suivants de CSDL ont été ajoutés ou étendus pour la prise en charge des modèles de données Business Intelligence, tabulaires et multidimensionnels.  
  
-   [Élément AssociationSet &#40;CSDLBI&#41;](associationset-element-csdlbi.md)  
  
-   [Élément BaseProperty &#40;CSDLBI&#41;](property-element-csdlbi.md)  
  
-   [Élément DefaultDetails &#40;CSDLBI&#41;](defaultdetails-element-csdlbi.md)  
  
-   [Élément DisplayKey &#40;CSDLBI&#41;](displaykey-element-csdlbi.md)  
  
-   [Élément EntityContainer &#40;CSDLBI&#41;](entitycontainer-element-csdlbi.md)  
  
-   [Élément EntitySet &#40;CSDLBI&#41;](entityset-element-csdlbi.md)  
  
-   [Élément EntityType &#40;CSDLBI&#41;](entitytype-element-csdlbi.md)  
  
-   [Élément Hierarchy &#40;CSDLBI&#41;](hierarchy-element-csdlbi.md)  
  
-   [Élément KPI &#40;CSDLBI&#41;](kpi-element-csdlbi.md)  
  
-   [Élément KpiGoal &#40;CSDLBI&#41;](kpigoal-element-csdlbi.md)  
  
-   [Élément KpiStatus &#40;CSDLBI&#41;](kpistatus-element-csdlbi.md)  
  
-   [Élément de niveau &#40;CSDLBI&#41;](level-element-csdlbi.md)  
  
-   [Mesurer l’élément &#40;CSDLBI&#41;](measure-element-csdlbi.md)  
  
-   [Élément Member &#40;CSDLBI&#41;](member-element-csdlbi.md)  
  
-   [Élément MemberRef &#40;CSDLBI&#41;](memberref-element-csdlbi.md)  
  
-   [Élément NavigationProperty &#40;CSDLBI&#41;](navigationproperty-element-csdlbi.md)  
  
-   [Élément de propriété &#40;CSDLBI&#41;](property-element-csdlbi.md)  
  
-   [Élément PropertyRef &#40;CSDLBI&#41;](propertyref-element-csdlbi.md)  
  
## <a name="simple-type-and-subtypes"></a>Type simple et sous-types  
 Le tableau suivant répertorie les types simples et certains types complexes mineurs inclus dans les définitions des types complexes répertoriés ci-dessus. La documentation de chaque type simple ou sous-type répertorié dans la colonne gauche est fournie dans les éléments parents répertoriés dans la colonne droite.  
  
|Type simple|Disponible dans la rubrique|  
|-----------------|--------------------|  
|Alignment|[Élément BaseProperty &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|CompareOptions|[Élément EntityContainer &#40;CSDLBI&#41;](entitycontainer-element-csdlbi.md)|  
|Sommaire|[Élément EntityType &#40;CSDLBI&#41;](entitytype-element-csdlbi.md)|  
|ContextualNameRule|[Élément Member &#40;CSDLBI&#41;](member-element-csdlbi.md)|  
|DefaultAggregationFunction|[Élément de propriété &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|DirectQueryMode|[Élément EntityContainer &#40;CSDLBI&#41;](entitycontainer-element-csdlbi.md)|  
|GroupingBehavior|[Élément de propriété &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|MemberRefs|[Élément MemberRef &#40;CSDLBI&#41;](memberref-element-csdlbi.md)|  
|PropertyRefs|[Élément PropertyRef &#40;CSDLBI&#41;](propertyref-element-csdlbi.md)|  
|SortDirection|[Élément BaseProperty &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|État|[Élément AssociationSet &#40;CSDLBI&#41;](associationset-element-csdlbi.md)|  
|Stability|[Élément de propriété &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|SortDirection|[Élément BaseProperty &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts CSDLBI](../csdlbi-concepts.md)  
  
  
