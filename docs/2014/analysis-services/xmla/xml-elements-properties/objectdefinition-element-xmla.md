---
title: Élément ObjectDefinition (XMLA) | Microsoft Docs
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
- ObjectDefinition Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#ObjectDefinition
- http://schemas.microsoft.com/analysisservices/2003/engine#ObjectDefinition
- microsoft.xml.analysis.objectdefinition
helpviewer_keywords:
- ObjectDefinition element
ms.assetid: 1911868c-a018-4308-8cf9-972a57f610a1
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3c4fe23e2f77dd28823094cf6a77067d9365e6ac
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37190789"
---
# <a name="objectdefinition-element-xmla"></a>Élément ObjectDefinition (XMLA)
  Contient un ou plusieurs éléments Analysis Services Scripting Language (ASSL), utilisés pour créer ou modifier des objets dans une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Create> <!-- or Alter -->  
   ...  
   <ObjectDefinition>  
      <!-- One or more ASSL elements -->  
   </ObjectDefinition>  
   ...  
</Create>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ALTER](../xml-elements-commands/alter-element-xmla.md), [créer](../xml-elements-commands/create-element-xmla.md)|  
|Éléments enfants|Éléments ASSL requis. Un ou plusieurs éléments ASSL utilisés pour définir des objets [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Pour plus d’informations sur ASSL, consultez [propriétés &#40;XMLA&#41;](xml-elements-properties.md).|  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée une base de données vide nommée `Test Database` sur une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
```  
  
      <Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
   <ObjectDefinition>  
      <Database xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
         <Name>Test Database</Name>  
         <Description>A test database.</Description>  
      </Database>  
   </ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
