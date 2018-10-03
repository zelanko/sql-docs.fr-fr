---
title: Élément ServerMode | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: c2f8cb39-dad7-433b-b7b7-fb1625f76a84
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6e714c9f5bbc7626030d83faa7d0058c7aa13752
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140179"
---
# <a name="servermode-element"></a>Élément ServerMode
  L'élément de serveur `ServerMode` spécifie le mode dans lequel le serveur est exécuté.  
  
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
|Éléments parents|[Server](../../scripting/objects/server-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le serveur s'exécute dans l'un des modes suivants :  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Multidimensionnel*|Mode multidimensionnel et d'exploration de données|  
|*Tabulaire*|Mode tabulaire|  
|*SharePoint*|Mode SharePoint|  
  
## <a name="see-also"></a>Voir aussi  
 [Server](../../scripting/objects/server-element-assl.md)  
  
  
