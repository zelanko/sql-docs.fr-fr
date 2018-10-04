---
title: Objets (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- ASSL, objects
- objects [Analysis Services Scripting Language]
- Analysis Services Scripting Language, objects
ms.assetid: 0f672b93-c317-47e5-b44d-ecea9b587c98
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 302ad689a3e54a7a9937929b9c20f975fc3cd98f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079609"
---
# <a name="objects-assl"></a>Objets (ASSL)
  Cette section de référence contient des informations de syntaxe et d'utilisation pour chaque élément qui se comporte comme un objet dans le schéma ASSL (Analysis Services Scripting Language).  
  
 Bien que le schéma ASSL renferme uniquement des éléments XML à partir du point de vue d’un développeur, les éléments décrits dans cette section correspondent à des objets, tels que `Database`, `Cube`, et `Dimension` objets, dans la hiérarchie d’objets contenus par un instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Les objets ne sont jamais des éléments de niveau feuille au sein du schéma ASSL mais disposent d'éléments enfants et d'éléments qui correspondent à des propriétés d'objet.  
  
 Dans certains cas, un élément de niveau feuille susceptible d'apparaître comme une propriété dans le schéma est classé en tant qu'objet puisque le type de l'élément est un type d'objet. Par exemple, l'élément `Source` d'un objet `Dimension` est de type `DimensionBinding`.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Élément|Description|  
|-------------|-----------------|  
|[Compte élément &#40;ASSL&#41;](account-element-assl.md)|Contient des détails sur un type de compte dans un [base de données](database-element-assl.md) élément.|  
|[Élément action &#40;ASSL&#41;](action-element-assl.md)|Contient des informations sur une action disponible dans un [Cube](cube-element-assl.md) élément ou un [Perspective](perspective-element-assl.md) élément.|  
|[Élément aggregation &#40;ASSL&#41;](aggregation-element-assl.md)|Définit une agrégation unique pour un [Partition](partition-element-assl.md) élément.|  
|[Élément AggregationDesign &#40;ASSL&#41;](aggregationdesign-element-assl.md)|Définit un ensemble de définitions d'agrégation qu'il est possible de partager sur plusieurs partitions dans une base de données.|  
|[Élément AggregationInstance &#40;ASSL&#41;](aggregationinstance-element-assl.md)|Définit une instance d'agrégation pour une partition.|  
|[Élément AlgorithmParameter &#40;ASSL&#41;](algorithmparameter-element-assl.md)|Définit un paramètre pour l’algorithme utilisé par un [MiningModel](miningmodel-element-assl.md) élément.|  
|[Élément AllMemberTranslation &#40;ASSL&#41;](translation-element-assl.md)|Contient une traduction pour la légende du membre All d’un [hiérarchie](hierarchy-element-assl.md) élément.|  
|[Élément d’annotation &#40;ASSL&#41;](annotation-element-assl.md)|Contient des éléments utilisés pour étendre le schéma ASSL.|  
|[Élément assembly &#40;ASSL&#41;](assembly-element-assl.md)|Représente un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly ou une bibliothèque de liens dynamiques (DLL) COM associée une [Server](server-element-assl.md) élément ou un [base de données](database-element-assl.md) élément.|  
|[Attribut d’élément &#40;ASSL&#41;](attribute-element-assl.md)|Contient la description d'un attribut.|  
|[Élément AttributeAllMemberTranslation &#40;ASSL&#41;](attributeallmembertranslation-element-assl.md)|Contient une traduction pour la légende du membre All d’un [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) élément.|  
|[Élément AttributePermission &#40;ASSL&#41;](attributepermission-element-assl.md)|Définit les autorisations que les membres d’un [rôle](role-element-assl.md) élément avoir sur les attributs d’une dimension individuelle dans un [Cube](cube-element-assl.md) élément.|  
|[Élément AttributeRelationship &#40;ASSL&#41;](attributerelationship-element-assl.md)|Fournit des détails sur la relation entre deux attributs.|  
|[Bloquer l’élément &#40;ASSL&#41;](block-element-assl.md)|Contient tout ou partie du contenu binaire d’un [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) élément.|  
|[Élément Calculation &#40;ASSL&#41;](calculation-element-assl.md)|Associe un calcul à un [Perspective](perspective-element-assl.md) élément.|  
|[Élément CalculationProperty &#40;ASSL&#41;](calculationproperty-element-assl.md)|Contient une collection de propriétés d’interface utilisateur pour un calcul utilisé dans un [MdxScript](mdxscript-element-assl.md) élément.|  
|[Élément CaptionColumn &#40;ASSL&#41;](column-element-assl.md)|Définit la colonne qui fournit la légende de l'attribut.|  
|[Élément CellPermission &#40;ASSL&#41;](cellpermission-element-assl.md)|Décrit les autorisations que les membres d’un [rôle](role-element-assl.md) élément avoir sur les cellules individuelles d’un [Cube](cube-element-assl.md) élément.|  
|[Élément column &#40;ASSL&#41;](column-element-assl.md)|Décrit une colonne dans la collection de colonnes associée à l'élément parent.|  
|[Commande élément &#40;ASSL&#41;](command-element-assl.md)|Définit une commande qui est disponible dans le contexte de l'élément parent de la collection Commands.|  
|[Élément de cube &#40;ASSL&#41;](cube-element-assl.md)|Définit un cube régulier, virtuel ou lié dans un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [base de données](database-element-assl.md) élément.|  
|[Élément CubePermission &#40;ASSL&#41;](cubepermission-element-assl.md)|Définit les autorisations des membres d’un particulier [rôle](role-element-assl.md) élément dans un spécifique [Cube](cube-element-assl.md) élément.|  
|[Élément CustomRollupColumn &#40;ASSL&#41;](customrollupcolumn-element-assl.md)|Définit les détails de la colonne qui fournissent une formule de cumul personnalisée.|  
|[Élément CustomRollupPropertiesColumn &#40;ASSL&#41;](customrolluppropertiescolumn-element-assl.md)|Définit les détails d'une colonne qui fournissent les propriétés d'une formule de cumul personnalisée.|  
|[Élément de données &#40;ASSL&#41;](data-element-assl.md)|Contient (dans la collection d’enfants `Block` éléments) le contenu binaire d’un [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) élément.|  
|[Élément de base de données &#40;ASSL&#41;](database-element-assl.md)|Définit une base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Élément DatabasePermission &#40;ASSL&#41;](databasepermission-element-assl.md)|Définit les autorisations par défaut dans un [base de données](database-element-assl.md) élément pour un spécifique [rôle](role-element-assl.md) élément.|  
|[Élément DataSource &#40;ASSL&#41;](datasource-element-assl.md)|Définit une source de données dans un [base de données](database-element-assl.md) élément.|  
|[Élément DataSourcePermission &#40;ASSL&#41;](datasourcepermission-element-assl.md)|Définit les autorisations par défaut dans un [DataSource](../data-type/datasource-data-type-assl.md) type de données pour un spécifique [rôle](role-element-assl.md) élément.|  
|[Élément DataSourceView &#40;ASSL&#41;](datasourceview-element-assl.md)|Définit une vue de source de données utilisée par un [base de données](database-element-assl.md) élément.|  
|[Dimension élément &#40;ASSL&#41;](dimension-element-assl.md)|Définit une dimension.|  
|[Élément DimensionPermission &#40;ASSL&#41;](dimensionpermission-element-assl.md)|Définit les autorisations qui appartiennent à un particulier [rôle](role-element-assl.md) élément pour une dimension de base de données spécifique ou d’une dimension de cube.|  
|[Élément ErrorConfiguration &#40;ASSL&#41;](errorconfiguration-element-assl.md)|Spécifie des paramètres pour gérer les erreurs qui peuvent se produire lors du traitement de l'élément parent.|  
|[Élément d’événement &#40;ASSL&#41;](event-element-assl.md)|Définit un événement à capturer dans le cadre d’un [Trace](trace-element-assl.md) élément.|  
|[Fichier d’élément &#40;ASSL&#41;](file-element-assl.md)|Définit un des fichiers qui composent un [ClrAssembly](../data-type/assembly-data-type-assl.md) élément.|  
|[Élément ForeignKeyColumn &#40;ASSL&#41;](keycolumn-element-assl.md)|Identifie la jointure à une table parente pour une source de données relationnelle.|  
|[Group, élément &#40;ASSL&#41;](group-element-assl.md)|Définit un groupe de membres liés à un attribut.|  
|[Élément Hierarchy &#40;ASSL&#41;](hierarchy-element-assl.md)|Définit une hiérarchie dans une dimension|  
|[Élément IncrementalProcessingNotification &#40;ASSL&#41;](incrementalprocessingnotification-element-assl.md)|Contient des informations pour le [ProactiveCaching](proactivecaching-element-assl.md) élément sur une requête à exécuter pour déterminer la progression du traitement incrémentiel.|  
|[Élément KeyColumn &#40;ASSL&#41;](keycolumn-element-assl.md)|Contient la définition d'une colonne qui est la clé d'un attribut ou en fait partie.|  
|[Élément KPI &#40;ASSL&#41;](kpi-element-assl.md)|Définit un indicateur de performance clé (KPI) dans un [Cube](cube-element-assl.md) élément ou un [Perspective](perspective-element-assl.md) élément.|  
|[Élément de niveau &#40;ASSL&#41;](level-element-assl.md)|Définit un niveau dans un [hiérarchie](hierarchy-element-assl.md) élément.|  
|[Élément MdxScript &#40;ASSL&#41;](mdxscript-element-assl.md)|Contient des informations sur un script MDX (Multidimensional Expressions) qui est associé à un [Cube](cube-element-assl.md) élément.|  
|[Mesurer l’élément &#40;ASSL&#41;](measure-element-assl.md)|Définit une mesure.|  
|[Élément MeasureGroup &#40;ASSL&#41;](measuregroup-element-assl.md)|Définit un ensemble de mesures au même niveau de granularité.|  
|[Élément Member &#40;ASSL&#41;](member-element-assl.md)|Contient le nom d'un membre d'un élément [Group](group-element-assl.md) ou d'un élément [Role](role-element-assl.md) .|  
|[Élément MiningModel &#40;ASSL&#41;](miningmodel-element-assl.md)|Définit un modèle d'exploration de données unique.|  
|[Élément MiningModelPermission &#40;ASSL&#41;](miningmodelpermission-element-assl.md)|Définit les autorisations de membres d’un [rôle](role-element-assl.md) élément avoir sur un individu [MiningModel](miningmodel-element-assl.md) élément.|  
|[Élément MiningStructure &#40;ASSL&#41;](miningstructure-element-assl.md)|Définit la structure d'un ensemble de modèles d'exploration de données.|  
|[Élément MiningStructurePermission &#40;ASSL&#41;](miningstructurepermission-element-assl.md)|Définit les autorisations que les membres d’un [rôle](role-element-assl.md) élément avoir sur un individu [MiningStructure](miningstructure-element-assl.md) élément.|  
|[Élément ModelingFlag &#40;ASSL&#41;](modelingflag-element-assl.md)|Contient un indicateur de modélisation pour une colonne dans une structure d'exploration de données ou un modèle d'exploration de données.|  
|[Élément NameColumn &#40;ASSL&#41;](namecolumn-element-assl.md)|Identifie la colonne qui fournit le nom de l'élément parent.|  
|[Élément NamingTemplateTranslation &#40;ASSL&#41;](namingtemplatetranslation-element-assl.md)|Fournit une traduction localisée de la `NamingTemplate` élément pour un parent [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) type de données.|  
|[Élément de la partition &#40;ASSL&#41;](partition-element-assl.md)|Définit une partition d’un [MeasureGroup](measuregroup-element-assl.md) élément ou une liaison de partition dans une sortie de ligne [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)élément.|  
|[Élément perspective &#40;ASSL&#41;](perspective-element-assl.md)|Définit des détails pour un point de vue d’un [Cube](cube-element-assl.md) élément.|  
|[Élément ProactiveCaching &#40;ASSL&#41;](proactivecaching-element-assl.md)|Définit des paramètres de mise en cache proactive pour l'élément parent.|  
|[Élément QueryNotification &#40;ASSL&#41;](querynotification-element-assl.md)|Contient des informations pour le [ProactiveCaching](proactivecaching-element-assl.md) élément sur une requête à exécuter pour déterminer si une source de données a été modifiée.|  
|[Élément ReportFormatParameter &#40;ASSL&#41;](reportformatparameter-element-asl.md)|Contient le nom et la valeur d’un paramètre qui spécifie comment un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] rapport est mis en forme au moment de l’exécution.|  
|[Élément ReportParameter &#40;ASSL&#41;](reportparameter-element-assl.md)|Contient le nom et la valeur d'un paramètre qui est transmis à un rapport [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] au moment de l'exécution.|  
|[Élément role &#40;ASSL&#41;](role-element-assl.md)|Contient des informations à propos d'un rôle de sécurité.|  
|[Élément de serveur &#40;ASSL&#41;](server-element-assl.md)|Décrit une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Élément ServerProperty &#40;ASSL&#41;](serverproperty-element-assl.md)|Définit une propriété de serveur associée à un [Server](server-element-assl.md) élément.|  
|[Élément SkippedLevelsColumn &#40;ASSL&#41;](skippedlevelscolumn-element-assl.md)|Fournit les détails d'une colonne qui stocke le nombre de niveaux omis (vides) entre chaque membre et son parent.|  
|[Élément SourceMeasureGroup &#40;ASSL&#41;](sourcemeasuregroup-element-assl.md)|Identifie le groupe de mesures servant de source de données à une colonne de structure d'exploration de données.|  
|[Élément TableNotification &#40;ASSL&#41;](tablenotification-element-assl.md)|Contient des informations pour le [ProactiveCaching](proactivecaching-element-assl.md) élément sur une table ou vue dans une source de données qui a été modifiée.|  
|[Élément trace &#40;ASSL&#41;](trace-element-assl.md)|Définit une trace qui peut être interrogée.|  
|[Élément Translation &#40;ASSL&#41;](translation-element-assl.md)|Fournit une traduction localisée pour le parent de la collection [Translations](../collections/translations-element-assl.md) .|  
|[Élément UnaryOperatorColumn &#40;ASSL&#41;](unaryoperatorcolumn-element-assl.md)|Définit les détails d'une colonne qui fournit un opérateur unaire.|  
|[Élément UnknownMemberTranslation &#40;ASSL&#41;](unknownmembertranslation-element-assl.md)|Contient une traduction de la légende de la [UnknownMember](../properties/unknownmember-element-assl.md) élément pour un [Dimension](dimension-element-assl.md) élément.|  
|[Élément ValueColumn &#40;ASSL&#41;](valuecolumn-element-assl.md)|Identifie la colonne qui fournit la valeur de l'élément parent.|  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchie Analysis Services Scripting Language XML élément &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
