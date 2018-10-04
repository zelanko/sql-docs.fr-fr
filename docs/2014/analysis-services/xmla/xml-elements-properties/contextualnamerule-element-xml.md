---
title: Élément ContextualNameRule (XML) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: eb567ef8-f412-4d34-837a-75e53b88b3ce
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8843e2eafd32ac9e4bdb4cc7e4cbf97a04ea3f51
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054209"
---
# <a name="contextualnamerule-element-xml"></a>Élément ContextualNameRule (XML)
  Fournit un indicateur sur le meilleur moyen de construire un nom composite pour l'attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <ContextualNameRule>...</ContextualNameRule>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|-1|  
|Cardinalité|0-1 : élément facultatif qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[RelationshipEndVisualizationProperties](../../scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Fournit un indicateur aux applications clientes sur le mode de création de noms non ambigus pour cet attribut.  
  
 La valeur de l'élément `ContextualNameRule` est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Aucun*|Utilisez le nom de l’attribut.|  
|*Contexte*|Utilisez le nom de la relation entrante.|  
|*Fusion*|Selon les règles du langage d'application, concatène le nom de la relation entrante et le nom de l'attribut.|  
  
  
