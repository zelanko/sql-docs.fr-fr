---
title: Type d’élément (Binding) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Type Element (Binding)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: b5f5c485-dc83-4d66-a8d2-e96e96d068f9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 407c8e53a842baca13671256a8125b696d7f1e91
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48225221"
---
# <a name="type-element-binding-assl"></a>Élément Type (Binding) (ASSL)
  Contient le type de la liaison d'attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AttributeBinding> <!-- or CubeAttributeBinding -->  
   ...  
   <Type>...</Type>  
   ...  
</AttributeBinding>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[AttributeBinding](../data-type/binding-data-type-assl.md), [CubeAttributeBinding](../data-type/cubeattributebinding-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Tous*|Tous les niveaux|  
|*Clé*|Clés de membre|  
|*Nom*|Nom de membre|  
|*Value*|Valeur de membre|  
|*traduction*|Traductions de membre|  
|*UnaryOperator*|Opérateurs unaires|  
|*SkippedLevels*|Niveaux ignorés|  
|*CustomRollup*|Formules de cumul personnalisées|  
|*CustomRollupProperties*|Propriétés de cumul personnalisées|  
  
 Les éléments qui correspondent aux parents de `Type` dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.AttributeBinding> et <xref:Microsoft.AnalysisServices.CubeAttributeBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données de liaison &#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
