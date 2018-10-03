---
title: Types de données XML du script Language (ASSL) Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Analysis Services Scripting Language XML Data Types
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ASSL, data types
- Analysis Services Scripting Language, data types
- data types [Analysis Services Scripting Language]
ms.assetid: 8e527916-932e-48ec-9010-f22cd4b721e2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f5ff2f0989aa2c88a69351d698c847ca6e835285
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48179249"
---
# <a name="analysis-services-scripting-language-xml-data-types-assl"></a>Types de données XML Analysis Services Scripting Language (ASSL)
  Cette section de référence contient des informations de syntaxe et d'utilisation pour chaque élément agissant en tant que type dans le schéma ASSL (Analysis Services Scripting Language).  
  
 Bien que le schéma ASSL renferme uniquement des éléments XML du point de vue du développeur, les éléments décrits dans cette section correspondent à des types, tels que `Binding` et `Permission`, employés pour définir les éléments enfants et les propriétés d'autres objets.  
  
 Les éléments de type, tels que les éléments objets, ne sont jamais des éléments de niveau feuille au sein du schéma ASSL mais disposent d'éléments enfants et d'éléments qui correspondent aux propriétés des objets.  
  
 Toutefois un élément de type n’apparaît jamais en tant qu’élément dans un script qui définit ou décrit [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objets. Il apparaît plutôt en tant que type d'autres éléments objets et est généralement désigné par l'attribut `type` du schéma de l'instance du schéma XML à l'aide de `xsi:type` ou de `xs:type`. Par exemple, `<Assembly xsi:type="ClrAssembly">...</Assembly>`.  
  
 Dans certains cas, un type provient d'un autre type. Par exemple, le type `CubeBinding` provient du type `Binding` parent.  
  
|Élément|Description|  
|-------------|-----------------|  
|[Type de données action &#40;ASSL&#41;](action-data-type-assl.md)|Définit un type de données primitif abstrait qui représente une action dans un [Cube](../objects/cube-element-assl.md) élément ou un [Perspective](../objects/perspective-element-assl.md) élément.|  
|[Type de données AggregationAttribute &#40;ASSL&#41;](aggregationattribute-data-type-assl.md)|Définit un type de données primitif qui représente l’association entre un [agrégation](../objects/aggregation-element-assl.md) élément et un attribut.|  
|[Type de données AggregationDesignAttribute &#40;ASSL&#41;](aggregationdesignattribute-data-type-assl.md)|Définit un type de données primitif qui représente l’association entre un attribut et un [AggregationDesignDimension](dimension-data-type-assl.md) élément.|  
|[Type de données AggregationDesignDimension &#40;ASSL&#41;](dimension-data-type-assl.md)|Définit un type de données primitif qui représente la relation entre une dimension de cube et un [AggregationDesign](../objects/aggregationdesign-element-assl.md) élément.|  
|[Type de données AggregationDimension &#40;ASSL&#41;](aggregationdimension-data-type-assl.md)|Définit un type de données primitif qui représente la relation entre une dimension et un [agrégation](../objects/aggregation-element-assl.md) élément.|  
|[Type de données AggregationInstanceAttribute &#40;ASSL&#41;](aggregationinstanceattribute-data-type-assl.md)|Définit un type de données primitif qui fournit des informations sur un attribut utilisé par une instance d'agrégation.|  
|[Type de données AggregationInstanceCubeDimension &#40;ASSL&#41;](cubedimension-data-type-assl.md)|Définit un type de données primitif qui fournit des informations sur une dimension de cube utilisée par une instance d'agrégation.|  
|[Type de données AggregationInstanceMeasure &#40;ASSL&#41;](aggregationinstancemeasure-data-type-assl.md)|Définit un type de données primitif qui fournit des informations sur une mesure utilisée par une instance d'agrégation.|  
|[Type de données assembly &#40;ASSL&#41;](assembly-data-type-assl.md)|Définit un type de données primitif abstrait qui représente un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly ou une bibliothèque de liens dynamiques (DLL) COM associée une [Server](../objects/server-element-assl.md) ou [base de données](../objects/database-element-assl.md) élément.|  
|[Type de données de AttributeBinding &#40;ASSL&#41;](binding-data-type-assl.md)|Définit un type de données dérivé qui représente une liaison pour un [attribut](../objects/attribute-element-assl.md) élément.|  
|[Type de données AttributeTranslation &#40;ASSL&#41;](translation-data-type-assl.md)|Définit un type de données dérivé représentant une traduction associée une [attribut](../objects/attribute-element-assl.md) élément|  
|[Type de données de liaison &#40;ASSL&#41;](binding-data-type-assl.md)|Définit un type de données primitif abstrait qui représente une relation de dépendance entre deux objets dans laquelle les données ou les métadonnées d'un objet dépendent des données ou des métadonnées d'un objet lié.|  
|[Type de données ClrAssembly &#40;ASSL&#41;](clrassembly-data-type-assl.md)|Définit un type de données dérivé qui représente un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly associé à un [base de données](../objects/database-element-assl.md) ou [Server](../objects/server-element-assl.md) élément|  
|[Type de données ClrAssemblyFile &#40;ASSL&#41;](clrassemblyfile-data-type-assl.md)|Définit un type de données primitif qui représente un des fichiers qui composent un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly ([ClrAssembly](clrassembly-data-type-assl.md) élément).|  
|[Type de données ColumnBinding &#40;ASSL&#41;](columnbinding-data-type-assl.md)|Définit un type de données dérivé qui représente la liaison d’une colonne dans une vue de source de données à un [DataItem](dataitem-data-type-assl.md) élément.|  
|[Type de données ComAssembly &#40;ASSL&#41;](comassembly-data-type-assl.md)|Définit un type de données dérivé qui représente une bibliothèque COM associée à un [Server](../objects/server-element-assl.md) ou [base de données](../objects/database-element-assl.md) élément.|  
|[Type de données CubeAttribute &#40;ASSL&#41;](cubeattribute-data-type-assl.md)|Définit un type de données primitif qui représente un attribut associé à un [Cube](../objects/cube-element-assl.md) élément.|  
|[Type de données CubeAttributeBinding &#40;ASSL&#41;](cubebinding-data-type-out-of-line-assl.md)|Définit un type de données dérivé représentant la liaison d'un attribut dans une dimension de cube à une colonne d'action ou à une colonne de la structure d'exploration de données.|  
|[Type de données CubeBinding &#40;hors ligne&#41; &#40;ASSL&#41;](cubebinding-data-type-out-of-line-assl.md)|Définit un type de données primitif qui représente la relation entre un [Cube](../objects/cube-element-assl.md) élément et un [DataSource](../objects/datasource-element-assl.md) élément.|  
|[Type de données CubeDimension &#40;ASSL&#41;](cubedimension-data-type-assl.md)|Définit un type de données primitif représentant la relation entre une dimension et un cube.|  
|[Type de données CubeDimensionBinding &#40;ASSL&#41;](dimensionbinding-data-type-assl.md)|Définit un type de données dérivé qui représente la liaison d’un [Dimension](../objects/dimension-element-assl.md), [mesure](../objects/measure-element-assl.md), ou [MiningModel](../objects/miningmodel-element-assl.md) élément à une dimension de cube.|  
|[Type de données CubeDimensionPermission &#40;ASSL&#41;](permission-data-type-assl.md)|Définit un type de données primitif qui représente les autorisations d'un rôle unique dans une dimension spécifique au sein d'un cube.|  
|[Type de données CubeHierarchy &#40;ASSL&#41;](hierarchy-data-type-assl.md)|Définit un type de données primitif qui représente les informations concernant un [hiérarchie](../objects/hierarchy-element-assl.md) élément dans un [Cube](../objects/cube-element-assl.md) élément.|  
|[Type de données DataBlock &#40;ASSL&#41;](datablock-data-type-assl.md)|Définit un type de données primitif qui représente une collection de blocs de données utilisé pour stocker le contenu binaire d’un [ClrAssemblyFile](clrassemblyfile-data-type-assl.md) élément.|  
|[Type de données DataItem &#40;ASSL&#41;](dataitem-data-type-assl.md)|Définit un type de données primitif qui représente les caractéristiques associées aux données d'un élément de données, tel qu'une colonne ou un attribut.|  
|[Type de données DataMiningMeasureGroupDimension &#40;ASSL&#41;](measuregroupdimension-data-type-assl.md)|Définit un type de données dérivé représentant la relation entre un groupe de mesures et une dimension d'exploration de données.|  
|[Type de données de la source de données &#40;ASSL&#41;](datasource-data-type-assl.md)|Définit un type de données primitif abstrait qui représente une source de données dans un [base de données](../objects/database-element-assl.md) élément.|  
|[Type de données DataSourceViewBinding &#40;ASSL&#41;](datasourceviewbinding-data-type-assl.md)|Définit un type de données dérivé représentant une liaison entre une vue de source de données et l'élément parent.|  
|[Type de données DegenerateMeasureGroupDimension &#40;ASSL&#41;](degeneratemeasuregroupdimension-data-type-assl.md)|Définit un type de données dérivé représentant la relation entre une dimension dégénérée (soit, en définitif, une dimension) et un groupe de mesures.|  
|[Type de données de dimension &#40;ASSL&#41;](dimension-data-type-assl.md)|Définit un type de données primitif représentant une dimension de base de données.|  
|[Type de données DimensionAttribute &#40;ASSL&#41;](dimensionattribute-data-type-assl.md)|Définit un type de données primitif représentant un attribut dans une dimension.|  
|[Type de données DimensionBinding &#40;ASSL&#41;](dimensionbinding-data-type-assl.md)|Définit un type de données dérivé qui représente la liaison entre une source de données et un [Dimension](../objects/dimension-element-assl.md) élément.|  
|[Type de données DimensionPermission &#40;ASSL&#41;](permission-data-type-assl.md)|Définit un type de données dérivé représentant les autorisations attribuées à une dimension de base de données.|  
|[Type de données DrillThroughAction &#40;ASSL&#41;](drillthroughaction-data-type-assl.md)|Définit un type de données dérivé représentant une action d'extraction.|  
|[Type de données DSVTableBinding &#40;ASSL&#41;](tablebinding-data-type-assl.md)|Définit un type de données dérivé qui représente la liaison entre une table et un [DataSourceView](../objects/datasourceview-element-assl.md) élément.|  
|[Type de données EventColumn &#40;ASSL&#41;](eventcolumn-data-type-assl.md)|Définit un type de données primitif qui représente une colonne d’informations à capturer pour un [événement](../objects/event-element-assl.md) élément en tant que partie d’un [Trace](../objects/trace-element-assl.md) élément.|  
|[Type de données de hiérarchie &#40;ASSL&#41;](hierarchy-data-type-assl.md)|Définit un type de données primitif représentant une hiérarchie dans une dimension.|  
|[Type de données ImpersonationInfo &#40;ASSL&#41;](impersonationinfo-data-type-assl.md)|Définit un type de données primitif fournissant des informations employées pour emprunter l'identité d'un utilisateur.|  
|[Type de données IncrementalProcessingNotification &#40;ASSL&#41;](incrementalprocessingnotification-data-type-assl.md)|Définit un type de données dérivé qui représente les informations pour le [ProactiveCaching](../objects/proactivecaching-element-assl.md) élément sur une requête à exécuter pour déterminer la progression du traitement incrémentiel.|  
|[Type de données InheritedBinding &#40;ASSL&#41;](inheritedbinding-data-type-assl.md)|Définit un type de données dérivé indiquant qu’un [MeasureGroupAttribute](measuregroupattribute-data-type-assl.md) élément hérite ses liaisons de l’attribut.|  
|[Type de données ManyToManyMeasureGroupDimension &#40;ASSL&#41;](manytomanymeasuregroupdimension-data-type-assl.md)|Définit un type de données dérivé représentant la relation entre une dimension plusieurs à plusieurs et un groupe de mesures.|  
|[Type de données MeasureBinding &#40;ASSL&#41;](measurebinding-data-type-assl.md)|Définit un type de données dérivé représentant la liaison d'une mesure à l'élément parent.|  
|[Type de données MeasureGroupAttribute &#40;ASSL&#41;](measuregroupattribute-data-type-assl.md)|Définit un type de données primitif représentant la relation entre un attribut et un groupe de mesures.|  
|[Type de données MeasureGroupBinding &#40;ASSL&#41;](measuregroupbinding-data-type-assl.md)|Définit un type de données dérivé qui représente une liaison à un [MeasureGroup](../objects/group-element-assl.md) élément.|  
|[Type de données MeasureGroupBinding &#40;hors ligne&#41; &#40;ASSL&#41;](measuregroupbinding-data-type-out-of-line-assl.md)|Définit un type de données primitif représentant une liaison à un groupe de mesures.|  
|[Type de données MeasureGroupDimension &#40;ASSL&#41;](measuregroupdimension-data-type-assl.md)|Définit un type de données primitif abstrait représentant la relation entre une dimension et un groupe de mesures.|  
|[Type de données MeasureGroupDimensionBinding &#40;ASSL&#41;](measuregroupdimensionbinding-data-type-assl.md)|Définit un type de données dérivé représentant une liaison entre une dimension et un groupe de mesures.|  
|[Type de données MeasureGroupHierarchy &#40;ASSL&#41;](measuregrouphierarchy-data-type-assl.md)|Définit un type de données primitif qui fournit des informations sur une hiérarchie dans un groupe de mesures.|  
|[Type de données MiningModelColumn &#40;ASSL&#41;](miningmodelcolumn-data-type-assl.md)|Définit un type de données primitif qui représente des informations sur une colonne dans un [MiningModel](../objects/miningmodel-element-assl.md) élément.|  
|[Type de données MiningModelingFlag &#40;ASSL&#41;](miningmodelingflag-data-type-assl.md)|Définit un type de données primitif qui représente les indicateurs de modélisation pour une [ModelingFlag](../objects/modelingflag-element-assl.md) élément.|  
|[Type de données MiningStructureColumn &#40;ASSL&#41;](miningstructurecolumn-data-type-assl.md)|Définit un type de données primitif abstrait qui représente des informations sur une colonne dans un [MiningStructure](../objects/miningstructure-element-assl.md) élément.|  
|[Type de données OlapDataSource &#40;ASSL&#41;](olapdatasource-data-type-assl.md)|Définit un type de données dérivé qui représente un multidimensionnelles [DataSource](../objects/datasource-element-assl.md) élément.|  
|[Type de données PartitionBinding &#40;ASSL&#41;](partitionbinding-data-type-assl.md)|Définit un type de données dérivé qui représente une liaison à un [Partition](../objects/partition-element-assl.md) élément.|  
|[Type de données d’autorisation &#40;ASSL&#41;](permission-data-type-assl.md)|Définit un type de données primitif abstrait qui fournit des informations sur une autorisation individuelle.|  
|[Type de données PerspectiveAction &#40;ASSL&#41;](perspectiveaction-data-type-assl.md)|Définit un type de données primitif qui représente des informations sur une action dans un [Perspective](../objects/perspective-element-assl.md) élément.|  
|[Type de données PerspectiveAttribute &#40;ASSL&#41;](perspectiveattribute-data-type-assl.md)|Définit un type de données primitif qui représente des informations sur un attribut dans un [PerspectiveDimension](perspectivedimension-data-type-assl.md) élément.|  
|[Type de données PerspectiveCalculation &#40;ASSL&#41;](perspectivecalculation-data-type-assl.md)|Définit un type de données primitif qui représente la relation entre un calcul et un [Perspective](../objects/perspective-element-assl.md) élément.|  
|[Type de données PerspectiveDimension &#40;ASSL&#41;](perspectivedimension-data-type-assl.md)|Définit un type de données primitif qui fournit des informations sur une dimension dans une perspective.|  
|[Type de données PerspectiveHierarchy &#40;ASSL&#41;](perspectivehierarchy-data-type-assl.md)|Définit un type de données primitif qui représente des informations sur une hiérarchie dans un [PerspectiveDimension](perspectivedimension-data-type-assl.md) élément.|  
|[Type de données PerspectiveKpi &#40;ASSL&#41;](perspectivekpi-data-type-assl.md)|Définit un type de données primitif qui représente des informations sur un indicateur de performance clé (KPI) dans un [Perspective](../objects/perspective-element-assl.md) élément.|  
|[Type de données PerspectiveMeasure &#40;ASSL&#41;](perspectivemeasure-data-type-assl.md)|Définit un type de données primitif qui représente des informations sur une mesure dans un [PerspectiveMeasureGroup](perspectivemeasuregroup-data-type-assl.md) élément.|  
|[Type de données PerspectiveMeasureGroup &#40;ASSL&#41;](perspectivemeasuregroup-data-type-assl.md)|Définit un type de données primitif qui représente des informations sur un groupe de mesures dans un [Perspective](../objects/perspective-element-assl.md) élément.|  
|[Type de données ProactiveCachingBinding &#40;ASSL&#41;](proactivecachingbinding-data-type-assl.md)|Définit un type de données dérivé abstrait qui représente les informations de la [ProactiveCaching](../objects/proactivecaching-element-assl.md) élément sur les modifications de source de données qui exigent une reconstruction du cache, ou sur l’état du processus de reconstruction.|  
|[Type de données ProactiveCachingIncrementalProcessingBinding &#40;ASSL&#41;](proactivecachingincrementalprocessingbinding-data-type-assl.md)|Définit un type de données dérivé qui représente une liaison à la [ProactiveCaching](../objects/proactivecaching-element-assl.md) élément sur l’état du processus de reconstruction du cache.|  
|[Type de données ProactiveCachingInheritedBinding &#40;ASSL&#41;](proactivecachinginheritedbinding-data-type-assl.md)|Définit un type de données dérivé qui représente les informations de la [ProactiveCaching](../objects/proactivecaching-element-assl.md) élément sur les modifications de source de données dans les tables et les vues identifiées par le biais des liaisons de données existantes qui exigent une reconstruction du cache.|  
|[Type de données ProactiveCachingObjectNotificationBinding &#40;ASSL&#41;](proactivecachingobjectnotificationbinding-data-type-assl.md)|Définit un type de données dérivé abstrait qui représente les informations de la [ProactiveCaching](../objects/proactivecaching-element-assl.md) élément sur les modifications de source de données, dans les tables et vues spécifiées ou dans les tables et les vues identifiées par le biais des liaisons de données existantes qui exigent une reconstruction du cache.|  
|[Type de données ProactiveCachingQueryBinding &#40;ASSL&#41;](querybinding-data-type-assl.md)|Définit un type de données dérivé qui représente les informations de la [ProactiveCaching](../objects/proactivecaching-element-assl.md) élément sur les modifications de source de données dans les tables et les vues identifiées lors de l’exécution de requêtes spécifiées qui exigent une reconstruction du cache.|  
|[Type de données ProactiveCachingTablesBinding &#40;ASSL&#41;](proactivecachingtablesbinding-data-type-assl.md)|Définit un type de données dérivé qui représente les informations de la [ProactiveCaching](../objects/proactivecaching-element-assl.md) élément sur les modifications de source de données dans les tables et vues qui exigent une reconstruction du cache spécifiées.|  
|[Type de données PushedDataSource &#40;ASSL&#41;](pusheddatasource-data-type-assl.md)|Définit un type de données primitif qui représente une source de données (comme un [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package) utilisé pour « pousser » des données dans un [Cube](../objects/cube-element-assl.md) élément.|  
|[Type de données QueryBinding &#40;ASSL&#41;](querybinding-data-type-assl.md)|Définit un type de données dérivé qui représente l’association d’un [DataSource](../objects/datasource-element-assl.md) élément avec un [QueryDefinition](../properties/querydefinition-element-assl.md) élément.|  
|[Type de données ReferenceMeasureGroupDimension &#40;ASSL&#41;](referencemeasuregroupdimension-data-type-assl.md)|Définit un type de données dérivé représentant une dimension indirectement liée à la table de faits par le biais d'une dimension intermédiaire. (Par exemple, un groupe de mesures Ventes peut référencer une dimension Géographie liée par le biais de la dimension Client.)|  
|[Type de données RegularMeasureGroupDimension &#40;ASSL&#41;](regularmeasuregroupdimension-data-type-assl.md)|Définit un type de données dérivé représentant une relation régulière entre une dimension et un groupe de mesures.|  
|[Type de données RelationalDataSource &#40;ASSL&#41;](relationaldatasource-data-type-assl.md)|Définit un type de données dérivé qui représente un [DataSource](../objects/datasource-element-assl.md) élément basé sur une source de données relationnelles.|  
|[Type de données ReportAction &#40;ASSL&#41;](reportaction-data-type-assl.md)|Définit un type de données dérivé représentant une action qui génère un rapport [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Type de données RowBinding &#40;ASSL&#41;](rowbinding-data-type-assl.md)|Définit un type de données dérivé qui représente une liaison aux lignes d’une table dans un [DataSourceView](../objects/datasourceview-element-assl.md) élément.|  
|[Type de données ScalarMiningStructureColumn &#40;ASSL&#41;](scalarminingstructurecolumn-data-type-assl.md)|Définit un type de données dérivé qui représente un [MiningStructureColumn](miningstructurecolumn-data-type-assl.md) élément qui contient des valeurs scalaires, par opposition aux tables imbriquées associées le [TableMiningStructureColumn](tableminingstructurecolumn-data-type-assl.md) élément qui contient des tables imbriquées.|  
|[Type de données StandardAction &#40;ASSL&#41;](standardaction-data-type-assl.md)|Définit un type de données dérivé qui représente tout [Action](../objects/action-element-assl.md) les éléments autres qu’un [DrillThroughAction](drillthroughaction-data-type-assl.md) élément ou un [ReportAction](reportaction-data-type-assl.md) élément.|  
|[Type de données TableBinding &#40;ASSL&#41;](tablebinding-data-type-assl.md)|Définit un type de données dérivé représentant une liaison à une table.|  
|[Type de données TableMiningStructureColumn &#40;ASSL&#41;](tableminingstructurecolumn-data-type-assl.md)|Définit un type de données dérivé qui représente un [MiningStructureColumn](miningstructurecolumn-data-type-assl.md) élément qui contient des tables imbriquées par opposition aux valeurs scalaires associées à la [ScalarMiningStructureColumn](scalarminingstructurecolumn-data-type-assl.md) élément qui contient des valeurs scalaires.|  
|[Type de données TabularBinding &#40;ASSL&#41;](tabularbinding-data-type-assl.md)|Définit un type de données dérivé abstrait représentant une liaison à un élément tabulaire, tel qu'une table ou une dimension de cube.|  
|[Type de données TimeAttributeBinding &#40;ASSL&#41;](timebinding-data-type-assl.md)|Définit un type de données dérivé représentant une liaison d'espace réservé pour les éléments de données créés dans une dimension de temps du serveur, tels que les colonnes clés d'un attribut.|  
|[Type de données TimeBinding &#40;ASSL&#41;](timebinding-data-type-assl.md)|Définit un type de données dérivé représentant une liaison à des périodes.|  
|[Type de données Translation &#40;ASSL&#41;](translation-data-type-assl.md)|Définit un type de données primitif représentant une traduction localisée.|  
|[Type de données UserDefinedGroupBinding &#40;ASSL&#41;](userdefinedgroupbinding-data-type-assl.md)|Définit un type de données dérivé représentant un groupement défini par l'utilisateur pour un attribut.|  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchie Analysis Services Scripting Language XML élément &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
