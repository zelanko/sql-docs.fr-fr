---
title: Élément LogFileRollover (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 97a472f44cf840093d2b7f92bd7184e41561274a
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="logfilerollover-element-assl"></a>Élément LogFileRollover (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Spécifie si l’enregistrement de [Trace](../../../analysis-services/scripting/objects/trace-element-assl.md) sortie doit être remplacé par un nouveau fichier ou doit s’arrêter lorsque la taille maximale du fichier journal qui est spécifié dans [LogFileSize](../../../analysis-services/scripting/properties/logfilesize-element-assl.md) est atteinte.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Trace>  
   ...  
   <LogFileRollover>...</LogFileRollover>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|False|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Trace](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Si l'élément **LogFileRollover** a la valeur True, un nouveau fichier est démarré lorsque la taille du fichier journal dépasse la valeur spécifiée dans l'élément **LogFileSize** de l'élément parent **Trace** ; sinon, l'enregistrement s'arrête.  
  
 L’élément qui correspond au parent de **LogFileRollover** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément traces & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/collections/traces-element-assl.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
