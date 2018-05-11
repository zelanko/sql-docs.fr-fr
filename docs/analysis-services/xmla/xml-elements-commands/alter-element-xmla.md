---
title: Élément ALTER (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bea5dd730bda2c5ad6f8ea0edc58b884f50dac83
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="alter-element-xmla"></a>Élément Alter (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient des éléments ASSL (Analysis Services Scripting Language) utilisés par la méthode [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) pour modifier des objets dans une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[Objet](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [ObjectDefinition](../../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md)|  
  
## <a name="attributes"></a>Attributs  
  
|Attribut| Description|  
|---------------|-----------------|  
|AllowCreate|(Attribut **Boolean** facultatif) Indique si les objets définis dans la commande **Alter** doivent être créés s'ils n'existent pas déjà.<br /><br /> Si défini sur true, les objets définis dans le **ObjectDefinition** sont créés dans le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] de l’instance s’ils n’existent pas déjà. En d'autres termes, la commande **Alter** est traitée comme une commande **Create** si les objets n'existent pas déjà dans l'instance.<br /><br /> Si cet attribut est omis ou possède la valeur **false**, une erreur survient si les objets n'existent pas déjà.|  
|ObjectExpansion|(Attribut **Enum** facultatif) Définit l'étendue de la modification que doit effectuer la méthode **Execute** .<br /><br /> Si cet attribut est défini sur *ObjectProperties*, l'élément **ObjectDefinition** doit contenir uniquement la définition complète de l'objet principal à modifier, y compris les objets secondaires subordonnés. Les objets principaux subordonnés de l'objet à modifier restent inchangés.<br /><br /> Remarque : Lorsque vous utilisez la *ObjectProperties* avec la [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md) type de données, le [données](../../../analysis-services/scripting/objects/data-element-assl.md) élément associé au [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) des types de données ne doivent pas être spécifiés. Si vous ne le spécifiez pas, le type de données **ClrAssembly** utilise les fichiers existants.<br /><br /> Si cet attribut est défini sur *ExpandFull*, l'élément **ObjectDefinition** ne doit pas contenir seulement la définition de l'objet à modifier mais aussi les définitions de tous les objets principaux qui sont des descendants de l'objet à modifier.<br /><br /> Remarque : Le *ExpandFull* paramètre ne peut pas être utilisé avec le [Server](../../../analysis-services/scripting/objects/server-element-assl.md) élément.|  
|Portée|(Attribut **Enum** facultatif) Définit la durée des objets définis dans l'élément **ObjectDefinition** .<br /><br /> S'il est défini sur *Session*, les objets définis dans l'élément **ObjectDefinition** existent uniquement pour la durée de la session XMLA.<br /><br /> Remarque : Lorsque vous utilisez la *Session* définition, le **ObjectDefinition** élément ne peut contenir [Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md), [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md), ou [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) éléments ASSL.<br /><br /> Si cet attribut est omis, les objets définis dans le **ObjectDefinition** sont conservés dans le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.|  
  
## <a name="remarks"></a>Notes  
 Chaque **Alter** commande modifie la définition d’un objet principal sous l’objet parent spécifié par le [ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md) élément.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
