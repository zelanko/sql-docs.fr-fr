---
title: Élément ContextualNameRule (XML) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e25061be21fdeea6d303ffce8f9ce9f66f687a34
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="contextualnamerule-element-xml"></a>Élément ContextualNameRule (XML)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
|Éléments parents|[RelationshipEndVisualizationProperties](../../../analysis-services/scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Fournit un indicateur aux applications clientes sur le mode de création de noms non ambigus pour cet attribut.  
  
 La valeur de la **ContextualNameRule** élément est limitée à une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Aucun*|Utilisez le nom de l’attribut.|  
|*Contexte*|Utilisez le nom de la relation entrante.|  
|*Fusion*|Selon les règles du langage d'application, concatène le nom de la relation entrante et le nom de l'attribut.|  
  
  
