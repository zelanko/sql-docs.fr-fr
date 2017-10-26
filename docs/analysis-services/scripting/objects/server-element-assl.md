---
title: "Élément de serveur (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Server Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- server
helpviewer_keywords:
- Server element
ms.assetid: 92ca67f6-817e-4a75-9244-8f8bcf412190
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8de09f74b1d9b7a6ded780f416201116c17a5667
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="server-element-assl"></a>Élément Server (ASSL)
  Décrit une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Server>  
   <!—These elements are common to each major object -->  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreatedTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <Description>...</Description>  
   <Annotations>...</Annotations>  
   <!-- server elements or properties -->  
   <ProductName>...</ProductName>  
   <Edition>...</Edition>  
   <EditionId>...</Edition>  
   <Version>...</Version>  
   <ServerMode>...</ServerMode>  
   <ProductLevel>...</Databases>  
   <Databases>...</Databases>  
   <Assemblies>...</Assemblies>  
   <Traces>...</Traces>  
   <Roles>...</Roles>  
   <ServerProperties>...</ServerProperties>  
</Server>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|[Nom](../../../analysis-services/scripting/properties/name-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [Description](../../../analysis-services/scripting/properties/description-element-assl.md), [Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [ProductName](../../../analysis-services/scripting/properties/productname-element-assl.md), [édition](../../../analysis-services/scripting/properties/edition-element-assl.md), [EditionId](../../../analysis-services/xmla/xml-elements-properties/editionid-element.md), [Version](../../../analysis-services/scripting/properties/version-element-assl.md), [ServerMode](../../../analysis-services/xmla/xml-elements-properties/editionid-element.md), [ProductLevel](../../../analysis-services/xmla/xml-elements-properties/productlabel-element.md), [bases de données](../../../analysis-services/scripting/collections/databases-element-assl.md), [assemblys](../../../analysis-services/scripting/collections/assemblies-element-assl.md), [Traces](../../../analysis-services/scripting/collections/traces-element-assl.md), [rôles](../../../analysis-services/scripting/collections/roles-element-assl.md), [ServerProperties](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)>|  
  
## <a name="remarks"></a>Notes  
 Le **Server** élément représente une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]et sert de nœud de premier niveau dans la hiérarchie de nœuds Analysis Services Scripting Language (ASSL).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Server>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

