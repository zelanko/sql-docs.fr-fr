---
title: Élément ReadSourceData (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ReadSourceData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ReadSourceData element
ms.assetid: 7da4665a-fba3-4aae-8dee-678dc14d3b05
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8c341162a62eb74dc0b07863959e0e5318daf0a7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48166511"
---
# <a name="readsourcedata-element-assl"></a>Élément ReadSourceData (ASSL)
  Détermine comment des noms uniques sont générés pour les hiérarchies qui sont contenus dans le [CubePermission](../objects/cubepermission-element-assl.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubePermission>  
   ...  
   <ReadSourceData>...</ReadSourceData>  
   ...  
</CubePermission>  
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
|Élément parent|[CubePermission](../objects/cubepermission-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Aucun*|Aucun accès aux données disponibles dans le test de calcul 0 n'est autorisé.|  
|*Autorisé*|L'accès aux données disponibles dans le test de calcul 0 est autorisé.|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `ReadSourceData` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.CubePermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de cube &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Dimension élément &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
