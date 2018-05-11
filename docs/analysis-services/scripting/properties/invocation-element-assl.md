---
title: Élément invocation (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7bd2f244068919e428bccedc6114e1d7656a5ab3
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="invocation-element-assl"></a>Élément Invocation (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Spécifie la manière dont un élément [Action](../../../analysis-services/scripting/objects/action-element-assl.md) doit être appelé.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Action>  
   ...  
   <Invocation>...</Invocation>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Interactive*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Action](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le mode d'invocation d'une action dépend de l'application cliente. Le **Invocation** élément suggère à une application cliente, comment une action doit être gérée et n’indique pas à l’instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] comment appeler une action.  
  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Interactive*|Appelé de manière interactive par l'utilisateur.|  
|*OnOpen*|Appelé lors de l'ouverture de l'objet par une application cliente.|  
|*Traitement par lots*|Appelé par une commande de traitement par lots.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **Invocation** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
