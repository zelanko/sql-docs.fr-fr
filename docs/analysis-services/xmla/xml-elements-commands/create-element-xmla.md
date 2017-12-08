---
title: "Élément Create (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
apiname: Create Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Create
- urn:schemas-microsoft-com:xml-analysis#Create
- microsoft.xml.analysis.create
helpviewer_keywords: Create command (XMLA)
ms.assetid: a623d362-a1ac-40e4-8816-65fac89cb391
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e3b4a1197d023e38b9fdbee2c9d895452cd97d30
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="create-element-xmla"></a>Élément Create (XMLA)
  Contient des éléments d’Analysis Services Scripting Language (ASSL) utilisés par le **Execute** méthode pour créer des objets sur un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.  
  
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[ObjectDefinition](../../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md), [ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)|  
  
## <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|AllowOverwrite|Attribut **Boolean** facultatif. Si la valeur True, les objets définis dans le **ObjectDefinition** peuvent remplacer des objets existants sur le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance. Si cet attribut est omis ou possède la valeur False, la présence d'un objet existant génère une erreur.|  
|Portée|Attribut **Enum** facultatif. Définit la durée des objets définis dans l'élément **ObjectDefinition** . Si cet attribut est omis, les objets définis dans le **ObjectDefinition** sont conservés dans le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance. La valeur suivante est disponible :<br /><br /> *Session*: les objets définis dans le **ObjectDefinition** l’élément existe uniquement pour la durée du code XML pour la session Analysis (XMLA).<br />                  Notez que lorsque vous utilisez la *Session* définition, le **ObjectDefinition** élément ne peut contenir [Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md), [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md), ou [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) éléments ASSL.|  
  
## <a name="remarks"></a>Notes  
 Chaque opération **Create** crée un objet principal sous un parent défini par l'élément **ParentObject** . Si l'objet parent est omis, il est considéré comme l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] de destination. Ceci génère une erreur si le parent d'un objet principal ne correspond pas à l'instance de destination.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée une base de données vide nommée **base de données Test** sur une [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.  
  
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
 [Commandes &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
