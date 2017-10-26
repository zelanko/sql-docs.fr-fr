---
title: "Élément ConnectionString (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ConnectionString Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.connectionstring
- urn:schemas-microsoft-com:xml-analysis#ConnectionString
- http://schemas.microsoft.com/analysisservices/2003/engine#ConnectionString
helpviewer_keywords:
- ConnectionString element
ms.assetid: 3b0575aa-79ed-4f14-ae7e-dd587af4cdb1
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b6c6227db17c74b4c33d07abfcd809ae01bc3a9a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="connectionstring-element-xmla"></a>Élément ConnectionString (XMLA)
  Contient une chaîne de connexion utilisée par le parent [emplacement](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) ou [Source](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md) élément.  
  
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
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|Consultez le tableau ci-dessous.|  
  
|Ancêtre ou parent|Cardinalité|  
|------------------------|-----------------|  
|[Emplacement](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|1-1 : élément requis qui apparaît une fois et une seule.|  
|[Source](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Emplacement](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [Source](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Pour **emplacement** éléments, le **ConnectionString** élément contient la chaîne de connexion utilisée par le **restaurer** ou **synchroniser** commande Mettre à jour une source de données local ou se connecter à une instance distante.  
  
 Pour **Source** éléments, le **ConnectionString** élément contient la chaîne de connexion utilisée par le **synchroniser** commande pour vous connecter à l’instance source.  
  
 Pour plus d’informations sur la sauvegarde et restauration des objets, consultez [sauvegarde, restauration et synchroniser les bases de données &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Restaurer l’élément &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Synchroniser, élément &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

