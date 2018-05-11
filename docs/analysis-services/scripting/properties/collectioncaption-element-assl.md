---
title: Élément CollectionCaption (ASSL) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0db69ee63b84ae9ad9c082eb7fea16c26e84ea98
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="collectioncaption-element-assl"></a>Élément CollectionCaption (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1 : élément facultatif qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[RelationshipEndTranslation](../../../analysis-services/scripting/data-type/relationshipendtranslation-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de **CollectionCaption** dans l’objets AMO (Analysis Management) modèle objet est : Microsoft.AnalysisServices.relationshipendtranslation.  
  
  
