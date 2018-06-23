---
title: Élément WritebackTableCreation (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- WritebackTableCreation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#WritebackTableCreation
- microsoft.xml.analysis.writebacktablecreation
- http://schemas.microsoft.com/analysisservices/2003/engine#WritebackTableCreation
helpviewer_keywords:
- WritebackTableCreation element
ms.assetid: e9579d63-e28c-4d4e-9f4a-21c5da24c276
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 95b9639b34002aa69366f87cac48427624f7d0dd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140080"
---
# <a name="writebacktablecreation-element-xmla"></a>Élément WritebackTableCreation (XMLA)
  Détermine si une table d’écriture différée est créée au cours de la [processus](../xml-elements-commands/process-element-xmla.md) opération.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Process>  
...  
   <WritebackTableCreation>...</WritebackTableCreation>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Traiter](../xml-elements-commands/process-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les options de traitement disponibles pour les objets sur une instance d’Analysis Services, consultez [traitement d’un objet de modèle multidimensionnel](../../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 La valeur de l'élément `WritebackTableCreation` est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Créer*|Création d'une nouvelle table d'écriture différée si aucune n'existe. Si une table d'écriture différée existe déjà, une erreur se produit.|  
|*CreateAlways*|Création d'une nouvelle table d'écriture différée et remplacement de toutes les tables d'écriture différée existantes.|  
|*UseExisting*|Utilisation de la table d'écriture différée existante s'il en existe déjà une. Si aucune n'existe, une erreur se produit.|  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  