---
title: Server, élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Server Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- server
helpviewer_keywords:
- Server element
ms.assetid: 92ca67f6-817e-4a75-9244-8f8bcf412190
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 39c4d780ade53dcb16d446237aa467f131614176
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106709"
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Nom](../properties/name-element-assl.md), [ID](../properties/id-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [Description](../properties/description-element-assl.md), [Annotations](../collections/annotations-element-assl.md), [ProductName](../properties/productname-element-assl.md), [édition](../properties/edition-element-assl.md), [EditionId](../../xmla/xml-elements-properties/editionid-element.md), [Version](../properties/version-element-assl.md), [ServerMode](../../xmla/xml-elements-properties/editionid-element.md), [ProductLevel](../../xmla/xml-elements-properties/productlabel-element.md), [bases de données](../collections/databases-element-assl.md), [assemblys](../collections/assemblies-element-assl.md), [Traces](../collections/traces-element-assl.md), [rôles](../collections/roles-element-assl.md), [ServerProperties](../collections/serverproperties-element-assl.md)>|  
  
## <a name="remarks"></a>Notes  
 L'élément `Server` représente une instance d'[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] et intervient en tant que nœud supérieur dans l'organisation hiérarchique du nœud ASSL (Analysis Services Scripting Language).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Server>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
