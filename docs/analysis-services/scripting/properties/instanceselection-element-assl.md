---
title: Élément InstanceSelection (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- InstanceSelection Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- InstanceSelection element
ms.assetid: 908a2da9-274c-40d2-87dc-4641cb8d77e6
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b2f8fe5f8041f7a807fe0640dee55e9d2534e425
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="instanceselection-element-assl"></a>Élément InstanceSelection (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Aucun*|Ne pas afficher de liste de sélection. Autoriser les utilisateurs à entrer des valeurs directement.|  
|*Liste déroulante*|Le nombre d'éléments est suffisamment faible pour permettre l'affichage dans une liste déroulante.|  
|*Listee*|Le nombre d'éléments est trop important pour une liste déroulante mais ne nécessite pas de filtrage.|  
|*FilteredList*|le nombre d'éléments est suffisamment important pour demander aux utilisateurs de filtrer les éléments à afficher.|  
|*MandatoryFilter*|Le nombre d'éléments est tellement important que l'affichage doit en permanence être filtré.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **InstanceSelection** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.InstanceSelection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
