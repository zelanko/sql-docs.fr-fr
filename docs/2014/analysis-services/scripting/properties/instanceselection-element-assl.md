---
title: Élément InstanceSelection (ASSL) | Microsoft Docs
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
- InstanceSelection Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- InstanceSelection element
ms.assetid: 908a2da9-274c-40d2-87dc-4641cb8d77e6
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e9babb9e5066d00b8a396d52dfb2dbdfc2f0b4cf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279765"
---
# <a name="instanceselection-element-assl"></a>Élément InstanceSelection (ASSL)
  Fournit un indicateur aux applications clientes qui suggère le mode d'affichage d'une liste d'éléments d'après le nombre d'éléments attendus dans la liste.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <InstanceSelection>...</InstanceSelection>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Aucun*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Aucun*|Ne pas afficher de liste de sélection. Autoriser les utilisateurs à entrer des valeurs directement.|  
|*Liste déroulante*|Le nombre d'éléments est suffisamment faible pour permettre l'affichage dans une liste déroulante.|  
|*Listee*|Le nombre d'éléments est trop important pour une liste déroulante mais ne nécessite pas de filtrage.|  
|*FilteredList*|le nombre d'éléments est suffisamment important pour demander aux utilisateurs de filtrer les éléments à afficher.|  
|*MandatoryFilter*|Le nombre d'éléments est tellement important que l'affichage doit en permanence être filtré.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `InstanceSelection` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.InstanceSelection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
