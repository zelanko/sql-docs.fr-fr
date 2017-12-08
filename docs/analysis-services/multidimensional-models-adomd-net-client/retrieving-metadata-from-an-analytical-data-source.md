---
title: "Récupération de métadonnées à partir d’une Source de données analytiques | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- metadata [ADOMD.NET]
- retrieving metadata
ms.assetid: 00043ebd-7164-4ceb-b945-6e44378ea00a
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c7c280b4b4a996d68bb403ea6210322604452e5d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="retrieving-metadata-from-an-analytical-data-source"></a>Récupération de métadonnées à partir d'une source de données analytiques
  Les métadonnées s'avèrent importantes pour les applications qui récupèrent et utilisent des données analytiques. Lorsqu'il s'agit de récupérer les données d'une source de données, la dimensionnalité de telles données est prévisible, même en présence de dataset imbriqués. Les jeux de résultats d'une base de données relationnelle présentent généralement une structure bidimensionnelle ou scalaire. Toutefois, les données extraites de sources de données analytiques peuvent avoir une dimensionnalité variable, organisées selon des hiérarchies d'une grande profondeur potentielle.  
  
 Pour gérer la complexité de la récupération de métadonnées à partir de sources de données analytiques, ADOMD.NET propose deux formes de récupération de métadonnées :  
  
 **Le modèle d’objet**  
 Le modèle objet ADOMD.NET est généralement plus facile à utiliser que les ensembles de lignes de schéma. Dans la plupart des scénarios, vous pouvez accéder aux métadonnées de différents objets de base de données par la simple utilisation du modèle objet. ADOMD.NET expose le modèle objet par le biais de la classe <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 Pour plus d’informations : [fonctionne avec le modèle objet ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-adomd-net-object-model.md)  
  
 **Ensembles de lignes de schéma**  
 Une autre méthode de récupération de métadonnées, complète mais plus difficile, est celle qui consiste à utiliser des ensembles de lignes de schéma. Un ensemble de lignes de schéma est un ensemble de lignes OLE DB qui encapsule la description de tous les objets d'un type particulier dans la base de données. Les informations de schéma contenues dans une source de données analytiques englobent notamment les bases de données ou les catalogues disponibles à partir de la source de données, les cubes et les modèles d'exploration d'une base de données, les rôles qui existent pour les cubes au niveau de la source de données, et ainsi de suite. Ces métadonnées peuvent être récupérées à l’aide de la <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A> méthode, soit en passant une **GUID** ou XML pour le nom de l’analyse (XMLA).  
  
 Pour plus d’informations : [utilisation des ensembles de lignes de schéma dans ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)  
  
 Chacune de ces méthodes de récupération de métadonnées accède aux différents types de métadonnées. Le tableau suivant décrit les différentes métadonnées disponibles pour chaque méthode, ainsi que les méthodes utilisées pour y accéder.  
  
|GUID (utilisé dans les ensembles de lignes de schéma)|Nom XMLA (utilisé dans les ensembles de lignes de schéma)|Modèle objet ADOMD.NET|  
|-------------------------------------|------------------------------------------|----------------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Actions>|[MDSCHEMA_ACTIONS, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-actions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Catalogs>|[DBSCHEMA_CATALOGS, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db/dbschema-catalogs-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Columns>|[DBSCHEMA_COLUMNS, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db/dbschema-columns-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Connections>|**DISCOVER_CONNECTIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Cubes>|[MDSCHEMA_CUBES, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-cubes-rowset.md)|AdomdConnection.Cubes|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.DataSources>|[DISCOVER_DATASOURCES, ensemble de lignes](../../analysis-services/schema-rowsets/xml/discover-datasources-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.DBConnections>|**DISCOVER_DB_CONNECTIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Dimensions>|[MDSCHEMA_DIMENSIONS, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-dimensions-rowset.md)|AdomdConnection.Cubes[].Dimensions|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.DimensionStat>|**DISCOVER_DIMENSION_STAT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Enumerators>|[DISCOVER_ENUMERATORS, ensemble de lignes](../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Functions>|[MDSCHEMA_FUNCTIONS, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-functions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Hierarchies>|[MDSCHEMA_HIERARCHIES, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset.md)|AdomdConnection.Cubes[].Dimensions[].Hierarchies|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.InputDataSources>|[MDSCHEMA_INPUT_DATASOURCES, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Instances>|[DISCOVER_INSTANCES, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db-olap/discover-instances-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Jobs>|**DISCOVER_JOBS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Keywords>|[Ensemble de lignes DISCOVER_KEYWORDS &#40; OLE DB pour OLAP &#41;](../../analysis-services/schema-rowsets/ole-db-olap/discover-keywords-rowset-ole-db-for-olap.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Kpis>|[MDSCHEMA_KPIS, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-kpis-rowset.md)|AdomdConnection.Cubes[].KPIs|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Levels>|[MDSCHEMA_LEVELS, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-levels-rowset.md)|AdomdConnection.Cubes[].Dimensions[].Hierarchies[].Levels|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Literals>|[DISCOVER_LITERALS, ensemble de lignes](../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Locations>|**DISCOVER_LOCATIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Locks>|**DISCOVER_LOCKS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MasterKey>|**DISCOVER_MASTER_KEY**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MeasureGroupDimensions>|[MDSCHEMA_MEASUREGROUP_DIMENSIONS, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MeasureGroups>|[MDSCHEMA_MEASUREGROUPS, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroups-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Measures>|[MDSCHEMA_MEASURES, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measures-rowset.md)|AdomdConnection.Cubes[].Measures|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MemberProperties>|[MDSCHEMA_PROPERTIES, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-properties-rowset.md)|PropertyCollection disponible à partir de la plupart des principaux objets ADOMD.NET.|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Members>|[MDSCHEMA_MEMBERS, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-members-rowset.md)|AdomdConnection.Cubes[].Dimensions[].Hierarchies[].Levels[].GetMembers()|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MemoryGrant>|**DISCOVER_MEMORYGRANT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MemoryUsage>|**DISCOVER_MEMORYUSAGE**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningColumns>|[DMSCHEMA_MINING_COLUMNS, ensemble de lignes](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-columns-rowset.md)|AdomdConnection.MiningModels[].MiningModelColumns|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningFunctions>|[DMSCHEMA_MINING_FUNCTIONS, ensemble de lignes](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-functions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModelContent>|[DMSCHEMA_MINING_MODEL_CONTENT, ensemble de lignes](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)|AdomdConnection.MiningModels[].MiningContentNodes|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModelContentPmml>|[DMSCHEMA_MINING_MODEL_CONTENT_PMML, ensemble de lignes](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModels>|[DMSCHEMA_MINING_MODELS, ensemble de lignes](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-models-rowset.md)|AdomdConnection.MiningModels|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModelXml>|[DMSCHEMA_MINING_MODEL_XML, ensemble de lignes](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-xml-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningServiceParameters>|[DMSCHEMA_MINING_SERVICE_PARAMETERS, ensemble de lignes](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)|AdomdConnection.MiningServices[].MiningServiceParameters|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningServices>|[DMSCHEMA_MINING_SERVICES, ensemble de lignes](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)|AdomdConnection.MiningServices|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningStructureColumns>|[DMSCHEMA_MINING_STRUCTURE_COLUMNS, ensemble de lignes](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset.md)|AdomdConnection.MiningStructures[].MiningStructureColumns|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningStructures>|[DMSCHEMA_MINING_STRUCTURES, ensemble de lignes](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structures-rowset.md)|AdomdConnection.MiningStructures|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.PartitionDimensionStat>|**DISCOVER_PARTITION_DIMENSION_STAT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.PartitionStat>|**DISCOVER_PARTITION_STAT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.PerformanceCounters>|**DISCOVER_PERFORMANCE_COUNTERS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.ProviderTypes>|[DBSCHEMA_PROVIDER_TYPES, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db/dbschema-provider-types-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.SchemaRowsets>|[DISCOVER_SCHEMA_ROWSETS, ensemble de lignes](../../analysis-services/schema-rowsets/xml/discover-schema-rowsets-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Sessions>|**DISCOVER_SESSIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Sets>|[MDSCHEMA_SETS, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-sets-rowset.md)|AdomdConnection.Cubes[].NamedSets|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Tables>|[DBSCHEMA_TABLES, ensemble de lignes](../../analysis-services/schema-rowsets/ole-db/dbschema-tables-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TablesInfo>|**DBSCHEMA_TABLES_INFO**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TraceColumns>|**DISCOVER_TRACE_COLUMNS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TraceDefinitionProviderInfo>|**DISCOVER_TRACE_DEFINITION_PROVIDERINFO**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TraceEventCategories>|**DISCOVER_TRACE_EVENT_CATEGORIES**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Traces>|**DISCOVER_TRACES**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Transactions>|**DISCOVER_TRANSACTIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.XmlaProperties>|[DISCOVER_PROPERTIES, ensemble de lignes](../../analysis-services/schema-rowsets/xml/discover-properties-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.XmlMetadata>|[DISCOVER_XML_METADATA, ensemble de lignes](../../analysis-services/schema-rowsets/xml/discover-xml-metadata-rowset.md)||  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation du Client ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [Programmation du Client ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [Ensembles de lignes de schéma Analysis Services](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
