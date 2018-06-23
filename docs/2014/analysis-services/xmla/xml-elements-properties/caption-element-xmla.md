---
title: Caption, élément (XMLA) | Documents Microsoft
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
- Caption Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Caption
- http://schemas.microsoft.com/analysisservices/2003/engine#Caption
- microsoft.xml.analysis.caption
helpviewer_keywords:
- Caption element
ms.assetid: 3d10ee68-98ab-4da0-a409-800dea2f1c32
caps.latest.revision: 15
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 9a67a57b29bf014326848b49e40bdbe5bc283dd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042753"
---
# <a name="caption-element-xmla"></a>Élément Caption (XMLA)
  Contient des informations sur la légende du parent [HierarchyInfo](hierarchyinfo-element-xmla.md) ou [membre](member-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <Caption>...</Caption>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[HierarchyInfo](hierarchyinfo-element-xmla.md), [Member](member-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour les éléments `HierarchyInfo`, l'élément `Caption` contient le nom de la propriété qui fournit les légendes des membres de la hiérarchie. Sa valeur est équivalente à la propriété MEMBER_CAPTION définie pour les ensembles de lignes d'axe dans la spécification OLE DB pour OLAP.  
  
 Pour les éléments `Member`, l'élément `Caption` contient la légende de l'élément `Member` parent dans le langage spécifié pour la session XMLA (XML for Analysis). Si aucune légende n'est disponible, cet élément contient le nom unique du membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  