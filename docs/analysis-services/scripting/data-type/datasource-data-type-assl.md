---
title: Type de données DataSource (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DataSource Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DataSource data type
ms.assetid: 05e8de8d-452d-4128-98a6-4437df227fec
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 68997a04b74297bdd56991110d5a1fe2d77dd33c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="datasource-data-type-assl"></a>Type de données DataSource (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Définit un type de données primitif abstrait qui représente une source de données dans un [base de données](../../../analysis-services/scripting/objects/database-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataSource>  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreateTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <ManagedProvider>...</ManagedProvider>  
   <ConnectionString>...</ConnectionString>  
   <ConnectionStringSecurity>...</ConnectionStringSecurity>  
   <ImpersonationInfo>...</ImpersonationInfo>  
   <Isolation>...</Isolation>  
   <MaxActiveConnections>...</MaxActiveConnections>  
   <Description>...</Description>  
   <Timeout>...</Timeout>  
   <Annotations>...</Annotations>  
   <DataSourcePermission>...</DataSourcePermission>  
</DataSource>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|[RelationalDataSource](../../../analysis-services/scripting/data-type/relationaldatasource-data-type-assl.md), [OlapDataSource](../../../analysis-services/scripting/data-type/olapdatasource-data-type-assl.md), [PushedDataSource](../../../analysis-services/scripting/data-type/pusheddatasource-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [ConnectionString](../../../analysis-services/scripting/properties/connectionstring-element-assl.md), [ConnectionStringSecurity](../../../analysis-services/scripting/properties/connectionstringsecurity-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [DataSourcePermission](../../../analysis-services/scripting/collections/datasourcepermissions-element-assl.md), [Description](../../../analysis-services/scripting/properties/description-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [ImpersonationInfo](../../../analysis-services/scripting/properties/impersonationinfo-element-assl.md), [Isolation](../../../analysis-services/scripting/properties/isolation-element-assl.md), [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [ManagedProvider](../../../analysis-services/scripting/properties/managedprovider-element-assl.md), [MaxActiveConnections](../../../analysis-services/scripting/properties/maxactiveconnections-element-assl.md), [nom](../../../analysis-services/scripting/properties/name-element-assl.md), [délai d’attente](../../../analysis-services/scripting/properties/timeout-element-assl.md)|  
|Éléments dérivés|None|  
  
## <a name="remarks"></a>Notes   
 Lors de la définition de liaisons hors ligne, l'élément **Name** est facultatif. Le fait de ne pas avoir à spécifier d'élément **Name** permet de définir des sources de données dans la liaison pour des cubes, des partitions, etc. Pour les sources de données contenues par un élément **Database** , **Name** est un élément requis.  
  
 Pour plus d'informations sur les sources de données, consultez [Data Sources in Multidimensional Models](../../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.DataSource>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
