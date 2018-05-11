---
title: Élément ImpersonationInfo (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a5325ddcddf408043875907b3e094f477d01eee4
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="impersonationinfo-element-assl"></a>Élément ImpersonationInfo (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Fournit les informations permettant de déterminer le comportement d'emprunt d'identité lors de l'accès ou de l'exécution d'un assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Assembly> <!-- or one of the elements listed in the Element Relationships table -->  
   <ImpersonationInfo>  
      <!-- Child elements are only those that are inherited from ImpersonationInfo -->  
   </ImpersonationInfo>  
</Assembly>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[Élément ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Assembly](../../../analysis-services/scripting/data-type/assembly-data-type-assl.md), [source de données](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
