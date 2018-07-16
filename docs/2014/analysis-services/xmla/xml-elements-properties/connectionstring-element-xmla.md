---
title: ConnectionString, élément (XMLA) | Microsoft Docs
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
api_name:
- ConnectionString Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.connectionstring
- urn:schemas-microsoft-com:xml-analysis#ConnectionString
- http://schemas.microsoft.com/analysisservices/2003/engine#ConnectionString
helpviewer_keywords:
- ConnectionString element
ms.assetid: 3b0575aa-79ed-4f14-ae7e-dd587af4cdb1
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e7345d2a35d80a2ce4d72875c4afb082b57ec1a4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37293209"
---
# <a name="connectionstring-element-xmla"></a>Élément ConnectionString (XMLA)
  Contient une chaîne de connexion utilisée par le parent [emplacement](location-element-xmla.md) ou [Source](source-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Location> <!-- or Source -->  
   ...  
   <ConnectionString>...</ConnectionString>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité - ancêtre ou Parent|Cardinalité|  
|[Emplacement](location-element-xmla.md)|1-1 : élément requis qui apparaît une fois et une seule.|  
|[Source](source-element-xmla.md)|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Emplacement](location-element-xmla.md), [Source](source-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour les éléments `Location`, l'élément `ConnectionString` contient la chaîne de connexion utilisée par la commande `Restore` ou `Synchronize`, respectivement pour mettre à jour une source de données locale ou se connecter à une instance distante.  
  
 Pour les éléments `Source`, l'élément `ConnectionString` contient la chaîne de connexion utilisée par la commande `Synchronize` pour se connecter à l'instance source.  
  
 Pour plus d’informations sur la sauvegarde et restauration d’objets, consultez [sauvegarde, restauration et synchronisation de bases de données de &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Restore &#40;XMLA&#41;](../xml-elements-commands/restore-element-xmla.md)   
 [Élément Synchronize &#40;XMLA&#41;](../xml-elements-commands/synchronize-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
