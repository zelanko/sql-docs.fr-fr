---
title: Collections (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- collections [Analysis Services Scripting Language]
- Analysis Services Scripting Language, collections
- ASSL, collections
ms.assetid: 072b8c6b-1550-4cab-ae64-ba0e3e60b059
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2ba3025c75d392ed1d3e818c932a6edcdba0f801
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042373"
---
# <a name="collections-assl"></a>Collections (ASSL)
  Cette section de référence contient des informations de syntaxe et d’utilisation pour chaque élément qui se comporte comme une collection dans le schéma ASSL (Analysis Services Scripting Language).  
  
 Bien que le schéma ASSL renferme uniquement des éléments XML, les éléments décrits dans cette section correspondent, du point de vue du développeur, à des collections d'objets comme les collections `Dimensions` et `Cubes`.  
  
 Les collections sont essentiellement des collections d'éléments objets dans lesquelles un nom au pluriel est utilisé pour désigner la collection (exemple : `Cubes`) et le même nom au singulier est employé pour désigner les éléments contenus dans la collection (exemple : `Cube`).  
  
 Dans certains cas toutefois, le schéma ne respecte pas cette règle générale. Par exemple, la collection `ClassifiedColumns` contient des éléments `ClassifiedColumnID`.  
  
 Dans d'autres cas, une collection contient des éléments qui correspondent à des propriétés d'objet et non à des objets. Par exemple, la collection `Aliases` contient des propriétés `Alias` qui sont chacune une valeur de chaîne simple.  
  
|Élément|Description|  
|-------------|-----------------|  
|[Comptes d’élément &#40;ASSL&#41;](accounts-element-assl.md)|Contient la collection des types de compte sont définies dans un [base de données](../objects/database-element-assl.md) élément.|  
|[Élément actions &#40;ASSL&#41;](actions-element-assl.md)|Contient la collection d’actions pour un [Cube](../objects/cube-element-assl.md) ou [Perspective](../objects/perspective-element-assl.md) élément.|  
|[Élément AggregationDesigns &#40;ASSL&#41;](aggregationdesigns-element-assl.md)|Contient la collection des conceptions d'agrégation qu'il est possible de partager sur plusieurs partitions dans une base de données.|  
|[Élément AggregationInstances &#40;ASSL&#41;](aggregationinstances-element-assl.md)|Contient la collection d’instances d’agrégation qui sont définies dans un [Partition](../objects/partition-element-assl.md) élément.|  
|[Élément Aggregations &#40;ASSL&#41;](aggregations-element-assl.md)|Contient la collection des agrégations définies pour un [AggregationDesign](../objects/aggregationdesign-element-assl.md) élément.|  
|[Élément AlgorithmParameters &#40;ASSL&#41;](algorithmparameters-element-assl.md)|Contient la collection de paramètres pour l’algorithme utilisé par un [MiningModel](../objects/miningmodel-element-assl.md) élément.|  
|[Élément Aliases &#40;ASSL&#41;](aliases-element-assl.md)|Contient la collection de [Alias](../properties/alias-element-assl.md) éléments associés à un [compte](../objects/account-element-assl.md) élément|  
|[Élément AllMemberTranslations &#40;ASSL&#41;](translations-element-assl.md)|Contient la collection de [traduction](../objects/translation-element-assl.md) éléments pour la légende du membre All d’un [hiérarchie](../objects/hierarchy-element-assl.md) élément.|  
|[Élément annotations &#40;ASSL&#41;](annotations-element-assl.md)|Contient la collection de [Annotation](../objects/annotation-element-assl.md) éléments associés à l’élément parent.|  
|[Élément Assemblies &#40;ASSL&#41;](assemblies-element-assl.md)|Contient la collection de [Assembly](../objects/assembly-element-assl.md) éléments associés à un [Server](../objects/server-element-assl.md) élément ou un [base de données](../objects/database-element-assl.md) élément.|  
|[Élément AttributeAllMemberTranslations &#40;ASSL&#41;](attributeallmembertranslations-element-assl.md)|Contient la collection de traductions pour la légende du membre All de la dimension.|  
|[Élément AttributePermissions &#40;ASSL&#41;](attributepermissions-element-assl.md)|Contient la collection d’autorisations d’attribut pour un individu [rôle](../objects/role-element-assl.md) élément sur une dimension spécifique d’un [Cube](../objects/cube-element-assl.md) élément.|  
|[Élément AttributeRelationships &#40;ASSL&#41;](relationships-element-assl.md)|Contient la collection de [AttributeRelationship](../objects/attributerelationship-element-assl.md) éléments pour l’attribut.|  
|[Attributs d’élément &#40;ASSL&#41;](attributes-element-assl.md)|Contient la collection d'attributs pour la dimension associée.|  
|[Bloque l’élément &#40;ASSL&#41;](blocks-element-assl.md)|Contient la collection de blocs de données binaires qui représentent le contenu binaire d’un [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) élément.|  
|[Élément CalculationProperties &#40;ASSL&#41;](calculationproperties-element-assl.md)|Contient la collection de [CalculationProperty](../objects/calculationproperty-element-assl.md) éléments associés à un [MdxScript](../objects/mdxscript-element-assl.md) élément.|  
|[Élément calculations &#40;ASSL&#41;](calculations-element-assl.md)|Contient la collection de [PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md) éléments associés à un [Perspective](../objects/perspective-element-assl.md) élément.|  
|[Élément CellPermissions &#40;ASSL&#41;](cellpermissions-element-assl.md)|Contient la collection d’autorisations pour les cellules dans le type [Cube](../objects/cube-element-assl.md) élément.|  
|[Élément ClassifiedColumns &#40;ASSL&#41;](columns-element-assl.md)|Contient la collection de colonnes associées classées par le [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) élément.|  
|[Élément Columns &#40;ASSL&#41;](columns-element-assl.md)|Contient la collection de colonnes associée à l'élément parent.|  
|[Commandes d’élément &#40;ASSL&#41;](commands-element-assl.md)|Contient la collection d'éléments [Command](../objects/command-element-assl.md) associée à un élément [MdxScript](../objects/mdxscript-element-assl.md) .|  
|[Élément CubePermissions &#40;ASSL&#41;](cubepermissions-element-assl.md)|Contient la collection d’autorisations applicable à un [Cube](../objects/cube-element-assl.md) élément.|  
|[Cubes élément &#40;ASSL&#41;](cubes-element-assl.md)|Contient la collection de [Cube](../objects/cube-element-assl.md) éléments associés à un [base de données](../objects/database-element-assl.md) élément.|  
|[Élément DatabasePermissions &#40;ASSL&#41;](databasepermissions-element-assl.md)|Contient la collection de [DatabasePermission](../objects/databasepermission-element-assl.md) éléments associés à un [base de données](../objects/database-element-assl.md) élément.|  
|[Bases de données élément &#40;ASSL&#41;](databases-element-assl.md)|Contient la collection de [base de données](../objects/database-element-assl.md) éléments associés à un [Server](../objects/server-element-assl.md) élément.|  
|[Élément DataSources &#40;ASSL&#41;](datasources-element-assl.md)|Contient la collection de [DataSourcePermission](../objects/datasourcepermission-element-assl.md) éléments associés à un [source de données](../data-type/datasource-data-type-assl.md) type de données.|  
|[Élément DataSourcePermissions &#40;ASSL&#41;](datasourcepermissions-element-assl.md)|Contient la collection de [DataSource](../objects/datasource-element-assl.md) éléments associés à un [base de données](../objects/database-element-assl.md) élément.|  
|[Élément DataSourceViews &#40;ASSL&#41;](datasourceviews-element-assl.md)|Contient la collection de [DataSourceView](../objects/datasourceview-element-assl.md) éléments associés à un [base de données](../objects/database-element-assl.md) élément.|  
|[Élément DimensionPermissions &#40;ASSL&#41;](dimensionpermissions-element-assl.md)|Contient la collection d’autorisations applicable à un [Dimension](../objects/dimension-element-assl.md) élément ou un [CubePermission](../objects/cubepermission-element-assl.md) élément.|  
|[Dimensions d’élément &#40;ASSL&#41;](dimensions-element-assl.md)|Contient la collection de dimensions associée à l'élément parent.|  
|[Élément Events &#40;ASSL&#41;](events-element-assl.md)|Définit la collection d’éléments d’événement à capturer par un [Trace](../objects/trace-element-assl.md).|  
|[Fichiers d’élément &#40;ASSL&#41;](files-element-assl.md)|Contient la collection de [fichier](../objects/file-element-assl.md) les éléments qui composent un [ClrAssembly](../data-type/assembly-data-type-assl.md) élément.|  
|[Élément ForeignKeyColumns &#40;ASSL&#41;](keycolumns-element-assl.md)|Contient la collection des colonnes qui identifient la jointure à la table parente pour une source de données relationnelle.|  
|[Élément groupes &#40;ASSL&#41;](groups-element-assl.md)|Contient la collection des groupes de membres liés à un attribut.|  
|[Élément Hierarchies &#40;ASSL&#41;](hierarchies-element-assl.md)|Contient la collection de [hiérarchie](../objects/hierarchy-element-assl.md) éléments associés à l’élément parent.|  
|[Élément IncrementalProcessingNotifications &#40;ASSL&#41;](incrementalprocessingnotifications-element-assl.md)|Contient la collection de [IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md) les éléments qui fournissent des informations pour le [ProactiveCaching](../objects/proactivecaching-element-assl.md) élément sur les requêtes à exécuter afin de déterminer la progression de traitement incrémentiel.|  
|[Élément KeyColumns &#40;ASSL&#41;](keycolumns-element-assl.md)|Contient la collection de [KeyColumn](../objects/column-element-assl.md) définitions d’élément pour un objet parent.|  
|[Élément KPIs &#40;ASSL&#41;](kpis-element-assl.md)|Contient la collection de [Kpi](../objects/kpi-element-assl.md) éléments associés à l’élément parent.|  
|[Niveaux d’élément &#40;ASSL&#41;](levels-element-assl.md)|Contient la collection de [niveau](../objects/level-element-assl.md) éléments dans un [hiérarchie](../objects/hierarchy-element-assl.md) élément.|  
|[Élément MdxScripts &#40;ASSL&#41;](mdxscripts-element-assl.md)|Contient la collection de [MdxScript](../objects/mdxscript-element-assl.md) éléments associés à un [Cube](../objects/cube-element-assl.md) élément.|  
|[Élément MeasureGroups &#40;ASSL&#41;](measuregroups-element-assl.md)|Contient la collection de [MeasureGroup](../objects/group-element-assl.md) éléments associés à l’élément parent.|  
|[Mesure l’élément &#40;ASSL&#41;](measures-element-assl.md)|Contient la collection de [mesure](../objects/measure-element-assl.md) éléments associés à l’élément parent.|  
|[Élément Members &#40;ASSL&#41;](members-element-assl.md)|Contient la collection d'éléments [Member](../objects/member-element-assl.md) de l'élément parent.|  
|[Élément MiningModelPermissions &#40;ASSL&#41;](miningmodelpermissions-element-assl.md)|Contient la collection d’autorisations pour un [MiningModel](../objects/miningmodel-element-assl.md) élément.|  
|[Élément MiningModels &#40;ASSL&#41;](miningmodels-element-assl.md)|Contient la collection de [MiningModel](../objects/miningmodel-element-assl.md) éléments associés à un [MiningStructure](../objects/miningstructure-element-assl.md).|  
|[Élément MiningStructurePermissions &#40;ASSL&#41;](miningstructurepermissions-element-assl.md)|Contient la collection d’autorisations sur un [MiningStructure](../objects/miningstructure-element-assl.md) élément.|  
|[Élément MiningStructures &#40;ASSL&#41;](miningstructures-element-assl.md)|Contient la collection de [MiningStructure](../objects/miningstructure-element-assl.md) éléments dans un [base de données](../objects/database-element-assl.md) élément.|  
|[Élément ModelingFlags &#40;ASSL&#41;](modelingflags-element-assl.md)|Contient la collection de [ModelingFlag](../objects/modelingflag-element-assl.md) les éléments d’une colonne dans un [MiningStructure](../objects/miningstructure-element-assl.md) ou un [MiningModel](../objects/miningmodel-element-assl.md).|  
|[Élément NamingTemplateTranslations &#40;ASSL&#41;](namingtemplatetranslations-element-assl.md)|Fournit une collection de traductions localisées pour le [NamingTemplate](../properties/namingtemplate-element-assl.md) élément du parent [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md).|  
|[Partitions élément &#40;ASSL&#41;](partitions-element-assl.md)|Contient la collection de [Partition](../objects/partition-element-assl.md) éléments utilisés par un [MeasureGroup](../objects/group-element-assl.md) élément ou la collection de liaisons de partition qui composent une hors ligne [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)élément.|  
|[Élément perspectives &#40;ASSL&#41;](perspectives-element-assl.md)|Contient la collection de [Perspective](../objects/perspective-element-assl.md) éléments associés à un [Cube](../objects/cube-element-assl.md) élément.|  
|[Élément QueryNotifications &#40;ASSL&#41;](querynotifications-element-assl.md)|Contient la collection de [QueryNotification](../objects/querynotification-element-assl.md) les éléments qui fournissent des informations pour le [ProactiveCaching](../objects/proactivecaching-element-assl.md) élément sur les requêtes à exécuter pour déterminer si une source de données a été modifiée.|  
|[Élément ReportFormatParameters &#40;ASSL&#41;](reportformatparameters-element-assl.md)|Contient la collection d'éléments [ReportFormatParameter](../objects/reportformatparameter-element-asl.md) pour un élément [ReportAction](../data-type/action-data-type-assl.md) .|  
|[Élément ReportParameters &#40;ASSL&#41;](reportparameters-element-assl.md)|Contient la collection de [ReportParameter](../objects/reportparameter-element-assl.md) éléments pour une [ReportAction](../data-type/action-data-type-assl.md) élément.|  
|[Élément roles &#40;ASSL&#41;](roles-element-assl.md)|Contient la collection d'éléments [Role](../objects/role-element-assl.md) définie sous l'élément parent.|  
|[Élément ServerProperties &#40;ASSL&#41;](serverproperties-element-assl.md)|Contient la collection de [ServerProperty](../objects/serverproperty-element-assl.md) éléments associés à un [Server](../objects/server-element-assl.md) élément.|  
|[Élément TableNotifications &#40;ASSL&#41;](tablenotifications-element-assl.md)|Contient la collection de [TableNotification](../objects/tablenotification-element-assl.md) les éléments qui fournissent des informations pour le [ProactiveCaching](../objects/proactivecaching-element-assl.md) élément sur les tables ou vues dans une source de données qui ont été modifiées.|  
|[Effectue le suivi élément &#40;ASSL&#41;](traces-element-assl.md)|Contient la collection d'éléments [Trace](../objects/trace-element-assl.md) associée à un élément [Server](../objects/server-element-assl.md) .|  
|[Élément translations &#40;ASSL&#41;](translations-element-assl.md)|Contient la collection de [traduction](../objects/translation-element-assl.md) éléments associés à l’élément parent.|  
|[Élément UnknownMemberTranslations &#40;ASSL&#41;](unknownmembertranslations-element-assl.md)|Contient la collection de traductions pour la légende de la [UnknownMember](../properties/unknownmember-element-assl.md) élément d’une dimension.|  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchie Analysis Services Scripting Language XML élément &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  