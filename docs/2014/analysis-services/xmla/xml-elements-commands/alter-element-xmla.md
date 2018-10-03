---
title: Élément ALTER (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Alter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Alter
- microsoft.xml.analysis.alter
- urn:schemas-microsoft-com:xml-analysis#Alter
helpviewer_keywords:
- Alter command
ms.assetid: 84e58385-c9ba-48fa-a867-94d35b777a56
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a9bdf13c64834100db14357a5a0ac7f47a6f9bf3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205789"
---
# <a name="alter-element-xmla"></a>Élément Alter (XMLA)
  Contient des éléments Analysis Services Scripting Language (ASSL) utilisés par le [Execute](../xml-elements-methods-execute.md) méthode pour modifier des objets sur une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <Alter Scope="enum" AllowCreate="boolean" ObjectExpansion="enum">  
      <Object>...</Object>  
      <ObjectDefinition>...</ObjectDefinition>  
   </Alter>  
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
|Éléments enfants|[Objet](../xml-elements-properties/object-element-xmla.md), [ObjectDefinition](../xml-elements-properties/objectdefinition-element-xmla.md)|  
  
## <a name="attributes"></a>Attributs  
  
|Attribute|Description|  
|---------------|-----------------|  
|AllowCreate|(Attribut `Boolean` facultatif) Indique si les objets définis dans la commande `Alter` doivent être créés s'ils n'existent pas déjà.<br /><br /> S'il possède la valeur True, les objets définis dans l'élément `ObjectDefinition` sont créés dans l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] s'ils n'existent pas déjà. En d'autres termes, la commande `Alter` est traitée comme une commande `Create` si les objets n'existent pas déjà dans l'instance.<br /><br /> Si cet attribut est omis ou possède la valeur `false`, une erreur survient si les objets n'existent pas déjà.|  
|ObjectExpansion|(Attribut `Enum` facultatif) Définit l'étendue de la modification que doit effectuer la méthode `Execute`.<br /><br /> Si la valeur *ObjectProperties*, le `ObjectDefinition` élément doit contenir uniquement la définition complète de l’objet principal à modifier, y compris les objets secondaires subordonnés. Les objets principaux subordonnés de l'objet à modifier restent inchangés. **Remarque :** lorsque vous utilisez le *ObjectProperties* avec la [ClrAssembly](../../scripting/data-type/assembly-data-type-assl.md) type de données, le [données](../../scripting/objects/data-element-assl.md) élément associé [ ClrAssemblyFile](../../scripting/data-type/clrassemblyfile-data-type-assl.md) types de données pas nécessairement être spécifié. Si vous ne le spécifiez pas, le type de données `ClrAssembly` utilise les fichiers existants. <br /><br /> Si la valeur *ExpandFull*, le `ObjectDefinition` élément doit contenir non seulement la définition de l’objet à modifier, mais également les définitions de tous les objets principaux qui sont des descendants de l’objet à modifier. **Remarque :** le *ExpandFull* paramètre ne peut pas être utilisé avec le [Server](../../scripting/objects/server-element-assl.md) élément.|  
|Portée|(Attribut `Enum` facultatif) Définit la durée des objets définis dans l'élément `ObjectDefinition`.<br /><br /> Si la valeur *Session*, les objets définis dans le `ObjectDefinition` existent uniquement pendant la durée de la session XMLA. **Remarque :** lorsque vous utilisez le *Session* définition, le `ObjectDefinition` élément ne peut contenir [Dimension](../../scripting/objects/dimension-element-assl.md), [Cube](../../scripting/objects/cube-element-assl.md), ou [MiningModel ](../../scripting/objects/miningmodel-element-assl.md) Éléments ASSL. <br /><br /> Si cet attribut est omis, les objets définis dans l'élément `ObjectDefinition` sont conservés dans l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
## <a name="remarks"></a>Notes  
 Chaque `Alter` commande modifie la définition d’un objet principal sous l’objet parent spécifié par le [ParentObject](../xml-elements-properties/parentobject-element-xmla.md) élément.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
