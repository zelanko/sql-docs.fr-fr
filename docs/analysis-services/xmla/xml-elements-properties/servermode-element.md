---
title: "Élément ServerMode | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: c2f8cb39-dad7-433b-b7b7-fb1625f76a84
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 463af850c8af6e6db386f95be510b4eae23a5bbd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="servermode-element"></a>Élément ServerMode
  Le **ServerMode** élément serveur Spécifie le mode de fonctionne dans le serveur.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Server>  
...  
   <ddl300:ServerMode>...</ddl300:ServerMode>  
...  
</Server>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|(aucun)|  
|Cardinalité|0-1 : élément facultatif qui ne peut apparaître qu'une seule fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le serveur s'exécute dans l'un des modes suivants :  
  
|Value| Description|  
|-----------|-----------------|  
|*Multidimensionnel*|Mode multidimensionnel et d'exploration de données|  
|*Sous forme de tableau*|Mode tabulaire|  
|*SharePoint*|Mode SharePoint|  
  
## <a name="see-also"></a>Voir aussi  
 [Server](../../../analysis-services/scripting/objects/server-element-assl.md)  
  
  
