---
title: Multiplicity, élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 441e3829-9009-4b32-a8c6-fa580663387f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e2e4335e6e8087fd94809678f5d3b04f9aee02ea
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076169"
---
# <a name="multiplicity-element-assl"></a>Élément Multiplicity (ASSL)
  Indique si les attributs du RelationshipEnd sont sur le côté « un » ou sur le côté « plusieurs » d'une relation.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<RelationshipEnd>  
   ...  
   <Multiplicity>...</Multiplicity>  
   ...  
</RelationshipEnd>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut||  
|Cardinalité|1 : élément requis qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[RelationshipEnd](../data-type/relationshipend-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Un*|Fin de clé primaire.|  
|*Nombreux*|Fin de clé étrangère.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `role` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.Multiplicity>.  
  
  
