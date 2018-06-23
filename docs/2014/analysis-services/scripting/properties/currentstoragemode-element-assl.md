---
title: Élément CurrentStorageMode (ASSL) | Documents Microsoft
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
- CurrentStorageMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CurrentStorageMode
helpviewer_keywords:
- CurrentStorageMode element
ms.assetid: 050c21e4-368b-4ff0-b0c5-349f93fe9747
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cce7bfd399c0c986a79e919c6227ee604e9ff470
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045244"
---
# <a name="currentstoragemode-element-assl"></a>Élément CurrentStorageMode (ASSL)
  Détermine le mode de stockage actuel pour l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Dimension> <!-- or Partition -->  
   <CurrentStorageMode>...</CurrentStorageMode>  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*ROLAP*|  
|Cardinalité|0-1 : élément facultatif qui peut se produire qu’une seule fois ou pas du tout.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Dimension](../objects/dimension-element-assl.md), [Partition](../objects/partition-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément `CurrentStorageMode` indique le mode de stockage utilisé actuellement pour la mise en cache proactive et s'applique à tous les attributs de l'élément parent.  
  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*MOLAP*|Le parent utilise le mode OLAP multidimensionnel (MOLAP).|  
|*ROLAP*|Le parent utilise le mode OLAP relationnel (ROLAP).|  
|*HOLAP*|Le parent utilise le mode OLAP hybride (HOLAP). **Remarque :** cette valeur est uniquement valide pour [Partition](../objects/partition-element-assl.md) éléments parents.|  
  
 L'énumération qui correspond aux valeurs autorisées de l'élément `CurrentStorageMode` dans le modèle objet AMO (Analysis Management Objects) est <xref:Microsoft.AnalysisServices.StorageMode>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  