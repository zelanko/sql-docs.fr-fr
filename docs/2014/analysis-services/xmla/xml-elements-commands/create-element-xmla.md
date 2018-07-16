---
title: Créer l’élément (XMLA) | Microsoft Docs
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
- Create Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Create
- urn:schemas-microsoft-com:xml-analysis#Create
- microsoft.xml.analysis.create
helpviewer_keywords:
- Create command (XMLA)
ms.assetid: a623d362-a1ac-40e4-8816-65fac89cb391
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a3679fd48885b3538996b38286709e14b665bef0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247730"
---
# <a name="create-element-xmla"></a>Élément Create (XMLA)
  Contient des éléments Analysis Services Scripting Language (ASSL) utilisés par le `Execute` méthode pour créer des objets sur un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <Create Scope="enum" AllowOverwrite="boolean">  
      <ParentObject>...</ParentObject>  
      <ObjectDefinition>...</ObjectDefinition>  
   </Create>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Commandee](../xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[ObjectDefinition](../xml-elements-properties/objectdefinition-element-xmla.md), [ParentObject](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="attributes"></a>Attributs  
  
|Attribute|Description|  
|---------------|-----------------|  
|AllowOverwrite|Facultatif `Boolean` attribut. S'il possède la valeur True, les objets définis dans l'élément `ObjectDefinition` peuvent remplacer des objets existants sur l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Si cet attribut est omis ou possède la valeur False, la présence d'un objet existant génère une erreur.|  
|Portée|Facultatif `Enum` attribut. Définit la durée des objets définis dans l'élément `ObjectDefinition`. Si cet attribut est omis, les objets définis dans l'élément `ObjectDefinition` sont conservés dans l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Les valeurs suivantes sont disponibles :<br /><br /> -   *session*<br />     Les objets définis dans l'élément `ObjectDefinition` existent uniquement pendant la durée de la session XMLA (XML for Analysis). **Remarque :** lorsque vous utilisez le *Session* définition, le `ObjectDefinition` élément ne peut contenir [Dimension](../../scripting/objects/dimension-element-assl.md), [Cube](../../scripting/objects/cube-element-assl.md), ou [MiningModel ](../../scripting/objects/miningmodel-element-assl.md) Éléments ASSL.|  
  
## <a name="remarks"></a>Notes  
 Chaque opération `Create` crée un objet principal sous un parent défini par l'élément `ParentObject`. Si l'objet parent est omis, il est considéré comme l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] de destination. Ceci génère une erreur si le parent d'un objet principal ne correspond pas à l'instance de destination.  
  
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
 [Commandes &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
