---
title: Élément StorageLocation (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 99e079a02814cb054a528bf34142a15bc3e0664d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="storagelocation-element-assl"></a>Élément StorageLocation (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contient l'emplacement de stockage du système de fichiers pour le contenu de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cube><!-- or MeasureGroup, Partition -->  
      ...  
   <StorageLocation>...</StorageLocation>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Consultez le tableau ci-dessous.|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
|Ancêtre ou parent|Valeur par défaut|  
|------------------------|-------------------|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|Aucune|  
|[Groupe de mesures](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|Valeur de **StorageLocation** de l'élément parent **Cube** .|  
|[Partition](../../../analysis-services/scripting/objects/partition-element-assl.md)|Valeur de **StorageLocation** de l'élément parent **MeasureGroup** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [Partition](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Les éléments qui correspondent aux parents de **StorageLocation** dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.MeasureGroup>, et <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
