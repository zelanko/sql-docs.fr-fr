---
title: Élément role (XMLA) | Documents Microsoft
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
ms.assetid: 2b851ad5-cc46-4a2e-8873-d8556faca809
caps.latest.revision: 5
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: bc1b3e4733625334e284946338beaaa7f65e7f0d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154018"
---
# <a name="role-element--xmla"></a>Élément role (XMLA)
  Identifie une extrémité d’une relation un-à-plusieurs pour être utilisé par le parent [RelationshipEnd](../../scripting/data-type/relationshipend-data-type-assl.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<RelationshipEnd  
   ...  
   <Role>...</Role>  
   ...  
</RelationshipEnd>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|1 : élément requis qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[RelationshipEnd](../../scripting/data-type/relationshipend-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
  