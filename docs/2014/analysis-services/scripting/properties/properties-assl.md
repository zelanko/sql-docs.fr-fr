---
title: Propriétés (ASSL) | Microsoft Docs
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
- properties [Analysis Services Scripting Language]
- Analysis Services Scripting Language, properties
- ASSL, properties
ms.assetid: 9a38cdc9-a210-421a-90e9-6391876765fa
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8a000f4f4c9a73698f04a0bd88882db55b8661e1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37173500"
---
# <a name="properties-assl"></a>Propriétés (ASSL)
  Cette section de référence contient des informations de syntaxe et d'utilisation pour chaque élément agissant en tant que propriété d'objet dans le schéma ASSL (Analysis Services Scripting Language).  
  
 Bien que le schéma ASSL renferme uniquement des éléments XML, les éléments décrits dans cette section correspondent, du point de vue du développeur, à des propriétés qui décrivent des objets.  
  
 Les propriétés sont des éléments de niveau feuille au sein du schéma ASSL et ne disposent pas d'éléments enfants ou d'éléments qui correspondent à leurs propres propriétés.  
  
 Dans certains cas, un élément de niveau feuille susceptible d'apparaître comme une propriété dans le schéma est classé en tant qu'objet puisque le type de l'élément est un type d'objet. Par exemple, l'élément `Source` d'un objet `Dimension` est de type `DimensionBinding`.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Élément|Description|  
|-------------|-----------------|  
|[Accéder à élément &#40;ASSL&#41;](access-element-assl.md)|Indique le niveau d’accès accordé à un [CellPermission](../objects/cellpermission-element-assl.md) élément.|  
|[Élément de compte &#40;ImpersonationInfo&#41; &#40;ASSL&#41;](account-element-impersonationinfo-assl.md)|Contient le nom du compte d’utilisateur pour le [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md) type de données.|  
|[Élément AccountType &#40;ASSL&#41;](accounttype-element-assl.md)|Contient le nom d’un type de compte défini dans un [base de données](../objects/database-element-assl.md) élément.|  
|[Élément ActionID &#40;ASSL&#41;](id-element-assl.md)|Contient le nom d’un [Action](../objects/action-element-assl.md) élément défini sur un [Cube](../objects/cube-element-assl.md) élément qui est mis à disposition dans un [Perspective](../objects/perspective-element-assl.md) élément en tant qu’un [PerspectiveAction](../data-type/action-data-type-assl.md) élément.|  
|[Élément Administer &#40;ASSL&#41;](administer-element-assl.md)|Indique si l'autorisation associée inclut le droit d'administrer un élément `Database`.|  
|[Élément AggregateFunction &#40;ASSL&#41;](aggregatefunction-element-assl.md)|Définit le type de fonction d’agrégation utilisée par un [mesure](../objects/measure-element-assl.md) élément.|  
|[Élément AggregationDesignID &#40;ASSL&#41;](aggregationdesignid-element-assl.md)|Identifie le [AggregationDesign](../objects/aggregationdesign-element-assl.md) élément associé à la [Partition](../objects/partition-element-assl.md) élément.|  
|[Élément AggregationFunction &#40;ASSL&#41;](aggregationfunction-element-assl.md)|Contient la fonction d'agrégation à utiliser pour le type de compte.|  
|[Élément AggregationID &#40;ASSL&#41;](aggregationid-element-assl.md)|Identifie la définition d'agrégation de l'élément `AggregationDesign` utilisé pour créer l'instance d'agrégation.|  
|[Élément AggregationInstanceSource &#40;ASSL&#41;](aggregationinstancesource-element-assl.md)|Identifie la source de données des instances d'agrégation définies par l'utilisateur et liées à un élément `Partition`.|  
|[Élément AggregationPrefix &#40;ASSL&#41;](aggregationprefix-element-assl.md)|Définit le préfixe commun à utiliser pour les noms d'agrégation dans l'ensemble de l'élément parent associé.|  
|[Élément AggregationStorage &#40;ASSL&#41;](aggregationstorage-element-assl.md)|Identifie la méthode de stockage des agrégations.|  
|[Élément AggregationType &#40;ASSL&#41;](aggregationtype-element-assl.md)|Définit le type d'agrégation stocké par l'élément `Partition`.|  
|[Élément AggregationUsage &#40;ASSL&#41;](aggregationusage-element-assl.md)|Contrôles comment le Concepteur d’agrégation dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] crée des agrégations.|  
|[Élément Algorithm &#40;ASSL&#41;](algorithm-element-assl.md)|Définit l’algorithme utilisé par un [MiningModel](../objects/miningmodel-element-assl.md) élément.|  
|[Élément alias &#40;ASSL&#41;](alias-element-assl.md)|Définit un alias pour un [compte](../objects/account-element-assl.md) élément.|  
|[Élément AllMemberAggregationUsage &#40;ASSL&#41;](allmemberaggregationusage-element-assl.md)|Contrôle la manière dont le concepteur d'agrégation crée des agrégations dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Élément AllMemberName &#40;ASSL&#41;](name-element-assl.md)|Contient la légende dans la langue par défaut pour le membre All d’un [hiérarchie](../objects/hierarchy-element-assl.md) élément.|  
|[Élément AllowBrowsing &#40;ASSL&#41;](allowbrowsing-element-assl.md)|Définit si les membres d’un [rôle](../objects/role-element-assl.md) élément avoir l’autorisation Parcourir un `MiningModel` élément.|  
|[Élément AllowDrillThrough &#40;ASSL&#41;](allowdrillthrough-element-assl.md)|Détermine si l'extraction est autorisée sur l'élément parent.|  
|[Élément AllowDuplicateNames &#40;ASSL&#41;](allowduplicatenames-element-assl.md)|Détermine si les noms en double sont autorisés dans un élément `Hierarchy`.|  
|[Élément AllowedSet &#40;ASSL&#41;](allowedset-element-assl.md)|Contient une expression d'ensemble qui définit le jeu d'autorisations permises pour un élément `Role` sur un attribut.|  
|[Élément de l’application &#40;ASSL&#41;](application-element-assl.md)|Identifie l'application associée à un élément `Action`.|  
|[Élément AssociatedMeasureGroupID &#40;ASSL&#41;](measuregroupid-element-assl.md)|Contient l’identificateur (ID) de la [MeasureGroup](../objects/group-element-assl.md) élément associé à un [CalculationProperty](../objects/calculationproperty-element-assl.md) élément ou un [Kpi](../objects/kpi-element-assl.md) élément.|  
|[Élément AttributeAllMemberName &#40;ASSL&#41;](attributeallmembername-element-assl.md)|Contient la légende dans la langue par défaut du membre All de la dimension.|  
|[Élément AttributeHierarchyDisplayFolder &#40;ASSL&#41;](displayfolder-element-assl.md)|Identifie le dossier dans lequel la hiérarchie d'attribut associée est à afficher.|  
|[Élément AttributeHierarchyEnabled &#40;ASSL&#41;](enabled-element-assl.md)|Détermine si une hiérarchie d'attribut est activée pour l'attribut.|  
|[Élément AttributeHierarchyOptimizedState &#40;ASSL&#41;](state-element-assl.md)|Détermine le niveau d'optimisation appliqué à la hiérarchie d'attribut.|  
|[Élément AttributeHierarchyOrdered &#40;ASSL&#41;](attributehierarchyordered-element-assl.md)|Détermine si la hiérarchie d'attribut associée est ordonnée.|  
|[Élément AttributeHierarchyVisible &#40;ASSL&#41;](visible-element-assl.md)|Détermine si la hiérarchie d'attribut est visible par des applications clientes.|  
|[Élément AttributeID &#40;ASSL&#41;](attributeid-element-assl.md)|Contient l'ID de l'attribut associé à l'élément parent.|  
|[Élément de l’audit &#40;ASSL&#41;](audit-element-assl.md)|Spécifie qu’un [Trace](../objects/trace-element-assl.md) élément ne peut pas supprimer des événements, même si cela entraîne la diminution des performances sur le serveur.|  
|[Élément AutoRestart &#40;ASSL&#41;](autorestart-element-assl.md)|Détermine si un élément `Trace` doit redémarrer automatiquement lorsque le service [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] s'arrête et redémarre.|  
|[Élément BackColor &#40;ASSL&#41;](backcolor-element-assl.md)|Décrit les caractéristiques des couleurs d'affichage de l'élément parent.|  
|[Élément CacheMode &#40;ASSL&#41;](cachemode-element-assl.md)|Détermine le mécanisme de mise en cache utilisé pour les données d'apprentissage récupérées au cours du traitement d'une structure d'exploration de données.|  
|[Élément CalculationReference &#40;ASSL&#41;](calculationreference-element-assl.md)|Contient le nom du jeu nommé ou de la cellule calculée référencée par l'élément `CalculationProperty`.|  
|[Élément CalculationType &#40;ASSL&#41;](calculationtype-element-assl.md)|Décrit le type de calcul défini dans l'élément `CalculationProperty` associé.|  
|[Élément CalendarEndDate &#40;ASSL&#41;](calendarenddate-element-assl.md)|Définit la date de fin de la période du calendrier pour un [TimeBinding](../data-type/binding-data-type-assl.md) élément.|  
|[Élément CalendarLanguage &#40;ASSL&#41;](language-element-assl.md)|Définit la langue du calendrier utilisée pour l'élément `TimeBinding`.|  
|[Élément CalendarStartDate &#40;ASSL&#41;](calendarstartdate-element-assl.md)|Définit la date de début de la période du calendrier pour l'élément `TimeBinding`.|  
|[Élément de légende &#40;ASSL&#41;](caption-element-assl.md)|Contient la légende de l'élément parent associé.|  
|[Élément CaptionIsMdx &#40;ASSL&#41;](captionismdx-element-assl.md)|Définit si la légende de l'élément `Action` est une expression MDX (Multidimensional Expressions).|  
|[Élément Cardinality &#40;ASSL&#41;](cardinality-element-assl.md)|Indique la cardinalité de la relation décrite par un [AttributeRelationship](../objects/attributerelationship-element-assl.md) ou [RegularMeasureGroupDimension](../data-type/dimension-data-type-assl.md).|  
|[Élément CaseCubeDimensionID &#40;ASSL&#41;](dimensionid-element-assl.md)|Contient l'ID de la dimension de cube qui lie la dimension d'exploration de données au groupe de mesures.|  
|[Élément ClassifiedColumnID &#40;ASSL&#41;](classifiedcolumnid-element-assl.md)|Contient l’ID d’une colonne associée classée par le [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) élément.|  
|[Élément Collation &#40;ASSL&#41;](collation-element-assl.md)|Détermine le classement utilisé par l'élément parent.|  
|[Élément ColumnID &#40;ColumnBinding&#41; &#40;ASSL&#41;](columnid-element-columnbinding-assl.md)|Contient l'ID de la colonne dans la table à laquelle l'élément de données est lié.|  
|[Élément ColumnID &#40;EventColumn&#41; &#40;ASSL&#41;](columnid-element-eventcolumn-assl.md)|Contient l'ID de la colonne renfermant les informations à capturer pour un événement dans le cadre d'un élément `Trace`.|  
|[Élément de condition &#40;ASSL&#41;](condition-element-assl.md)|Contient une expression MDX qui détermine si l'élément parent `Action` s'applique à la cible.|  
|[Élément ConnectionString &#40;ASSL&#41;](connectionstring-element-assl.md)|Contient la chaîne de connexion chiffrée pour une [DataSource](../objects/datasource-element-assl.md) élément.|  
|[Élément ConnectionStringSecurity &#40;ASSL&#41;](connectionstringsecurity-element-assl.md)|Spécifie si le mot de passe de l'utilisateur est supprimé de la chaîne de connexion à la source de données pour des raisons de sécurité.|  
|[Élément de contenu &#40;ASSL&#41;](content-element-assl.md)|Décrit le contenu de la colonne dans la [MiningStructure](../objects/miningstructure-element-assl.md) élément.|  
|[Élément CreatedTimestamp &#40;ASSL&#41;](createdtimestamp-element-assl.md)|Contient l'horodateur de création en lecture seule de l'élément parent.|  
|[Élément CubeDimensionID &#40;ASSL&#41;](cubedimensionid-element-assl.md)|Identifie le [CubeDimension](../data-type/cubedimension-data-type-assl.md) élément associé à l’élément parent.|  
|[Élément CubeID &#40;ASSL&#41;](cubeid-element-assl.md)|Identifie le `Cube` élément associé à un [liaison](../data-type/binding-data-type-assl.md) élément.|  
|[Élément CurrentStorageMode &#40;ASSL&#41;](storagemode-element-assl.md)|Détermine le mode de stockage actuel pour l'élément parent.|  
|[Élément CurrentTimeMember &#40;ASSL&#41;](../objects/member-element-assl.md)|Définit le membre actuel d'une dimension de temps associée à un élément `Kpi`.|  
|[Élément DataAggregation &#40;ASSL&#41;](../objects/aggregation-element-assl.md)|Détermine si l'instance peut agréger des données persistantes ou des données mises en cache pour l'élément `MeasureGroup`.|  
|[Élément DatabaseID &#40;ASSL&#41;](databaseid-element-assl.md)|Identifie l'élément `Database` associé à un élément `Binding` hors ligne.|  
|[Élément DataSize &#40;ASSL&#41;](datasize-element-assl.md)|Contient la taille en octets d’un [DataItem](../data-type/dataitem-data-type-assl.md) élément.|  
|[Élément DataSourceID &#40;ASSL&#41;](datasourceid-element-assl.md)|Identifie l'élément `DataSource` associé à l'élément parent.|  
|[Élément DataSourceImpersonationInfo &#40;ASSL&#41;](impersonationinfo-element-assl.md)|Fournit les informations permettant de déterminer le comportement d'emprunt d'identité lors de la connexion à la source de données pour un élément `Database`.|  
|[Élément DataSourceViewID &#40;ASSL&#41;](datasourceviewid-element-assl.md)|Identifie le [DataSourceView](../objects/datasourceview-element-assl.md) élément associé à la `Binding` élément parent.|  
|[Élément DataType &#40;ASSL&#41;](datatype-element-assl.md)|Définit le type de données de l'élément associé.|  
|[Élément DbSchemaName &#40;ASSL&#41;](dbschemaname-element-assl.md)|Contient le nom du schéma utilisé par l’élément parent dans la table identifiée par le [DbTableName](dbtablename-element-assl.md) élément.|  
|[Élément DbTableName &#40;ASSL&#41;](dbtablename-element-assl.md)|Contient le nom de la table à laquelle l'élément parent est lié.|  
|[Par défaut élément &#40;ASSL&#41;](default-element-assl.md)|Détermine si l'élément `DrillThroughAction` correspond à l'action d'extraction appliquée par défaut.|  
|[Élément DefaultMeasure &#40;ASSL&#41;](defaultmeasure-element-assl.md)|Contient une expression de langage MDX qui définit la mesure par défaut d'un élément `Cube` ou `Perspective`.|  
|[Élément DefaultMember &#40;ASSL&#41;](defaultmember-element-assl.md)|Contient une expression MDX qui identifie le membre par défaut de l'élément parent.|  
|[Élément DefaultScript &#40;ASSL&#41;](defaultscript-element-assl.md)|Identifie la valeur par défaut [MdxScript](../objects/mdxscript-element-assl.md) élément dans le [MdxScripts](../collections/mdxscripts-element-assl.md) collection.|  
|[Élément DefaultValue &#40;ASSL&#41;](value-element-assl.md)|Contient la valeur par défaut en lecture seule associé [ServerProperty](../objects/serverproperty-element-assl.md) élément.|  
|[Élément DeniedSet &#40;ASSL&#41;](deniedset-element-assl.md)|Contient une expression d'ensemble qui définit la liste des autorisations refusées sur l'attribut associé.|  
|[Élément DependsOnDimensionID &#40;ASSL&#41;](dependsondimensionid-element-assl.md)|Contient l'identificateur(ID) d'une autre dimension dont la dimension parente (le cas échéant) dépend.|  
|[Élément description &#40;ASSL&#41;](description-element-assl.md)|Contient la description de l'élément parent.|  
|[Élément DimensionID &#40;ASSL&#41;](dimensionid-element-assl.md)|Contient l'ID de la dimension.|  
|[Élément DiscretizationBucketCount &#40;ASSL&#41;](discretizationbucketcount-element-assl.md)|Contient le nombre de compartiments où effectuer la discrétisation.|  
|[Élément DiscretizationMethod &#40;ASSL&#41;](discretizationmethod-element-assl.md)|Définit la méthode à utiliser pour la discrétisation.|  
|[Élément DisplayFlag &#40;ASSL&#41;](displayflag-element-assl.md)|Contient un indicateur en lecture seule qui précise si les composants de l'interface utilisateur doivent afficher l'élément `ServerProperty` associé.|  
|[Élément DisplayFolder &#40;ASSL&#41;](displayfolder-element-assl.md)|Spécifie le dossier dans lequel l'élément parent doit être répertorié. Les applications [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour les développeurs et les administrateurs peuvent prendre en charge l'utilisation des dossiers d'affichage pour permettre le classement visuel de plusieurs éléments.|  
|[Élément distribution &#40;ASSL&#41;](distribution-element-assl.md)|Contient une valeur spécifique au fournisseur qui décrit le mode de distribution des valeurs scalaires dans la colonne d'un élément `MiningStructure`.|  
|[Élément Edition &#40;ASSL&#41;](edition-element-assl.md)|Contient la version en lecture seule de l’instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] représenté par le [Server](../objects/server-element-assl.md) élément.|  
|[Activé élément &#40;ASSL&#41;](enabled-element-assl.md)|Indique si l'élément parent est activé.|  
|[Élément EndOfData &#40;ASSL&#41;](../objects/data-element-assl.md)|Indique la fin des données reçues à partir d’un [PushedDataSource](../data-type/datasource-data-type-assl.md) élément.|  
|[Élément EstimatedCount &#40;ASSL&#41;](estimatedcount-element-assl.md)|Affiche le nombre estimé de membres pour un attribut.|  
|[Élément EstimatedPerformanceGain &#40;ASSL&#41;](estimatedperformancegain-element-assl.md)|Affiche le pourcentage en lecture seule des gains de performance estimés pour la partition.|  
|[Élément EstimatedRows &#40;ASSL&#41;](estimatedrows-element-assl.md)|Contient le nombre estimé de lignes représentées par l'élément parent.|  
|[Élément EstimatedSize &#40;ASSL&#41;](estimatedsize-element-assl.md)|Affiche la taille en lecture seule estimée en octets de l'élément parent.|  
|[Élément EventID &#40;ASSL&#41;](eventid-element-assl.md)|Identifie de façon unique un [événement](../objects/event-element-assl.md) élément consiste à capturer dans le cadre d’un `Trace` élément.|  
|[Élément d’expression &#40;ASSL&#41;](expression-element-assl.md)|Contient une expression MDX qui définit le contenu de l'élément parent.|  
|[Filter, élément &#40;liaison&#41; &#40;ASSL&#41;](filter-element-binding-assl.md)|Contient une expression MDX qui filtre le contenu de l'élément parent.|  
|[Filter, élément &#40;Trace&#41; &#40;ASSL&#41;](filter-element-trace-assl.md)|Contient un fragment de document XML qui décrit le filtre `Trace`.|  
|[Élément FirstDayOfWeek &#40;ASSL&#41;](firstdayofweek-element-assl.md)|Définit le premier jour de la semaine pour un élément `TimeBinding`.|  
|[Élément FiscalFirstDayOfMonth &#40;ASSL&#41;](fiscalfirstdayofmonth-element-assl.md)|Définit le premier jour du mois fiscal pour un élément `TimeBinding`.|  
|[Élément FiscalFirstMonth &#40;ASSL&#41;](fiscalfirstmonth-element-assl.md)|Définit le premier mois de la période fiscale pour un élément `TimeBinding`.|  
|[Élément FiscalYearName &#40;ASSL&#41;](fiscalyearname-element-assl.md)|Définit la convention d'affectation de noms pour le nom de l'année fiscale d'un élément `TimeBinding`.|  
|[Élément FontFlags &#40;ASSL&#41;](fontflags-element-assl.md)|Décrit les caractéristiques des polices d'affichage de l'élément parent `CalculationProperty` ou `Measure`.|  
|[Élément FontName &#40;ASSL&#41;](fontname-element-assl.md)|Décrit les caractéristiques des polices d'affichage de l'élément parent `CalculationProperty` ou `Measure`.|  
|[Élément FontSize &#40;ASSL&#41;](fontsize-element-assl.md)|Décrit les caractéristiques des polices d'affichage de l'élément parent `CalculationProperty` ou `Measure`.|  
|[Élément ForceRebuildInterval &#40;ASSL&#41;](forcerebuildinterval-element-assl.md)|Détermine le temps entre le moment où une nouvelle image OLAP multidimensionnelle (MOLAP) devient disponible et celui où le processus de création d'images MOLAP démarre de manière inconditionnelle.|  
|[Élément ForeColor &#40;ASSL&#41;](forecolor-element-assl.md)|Décrit les caractéristiques des couleurs d'affichage de l'élément parent `CalculationProperty` ou `Measure`.|  
|[Élément de format &#40;ASSL&#41;](format-element-assl.md)|Contient le format requis pour l'élément `DataItem`.|  
|[Élément FormatString &#40;ASSL&#41;](formatstring-element-assl.md)|Décrit le format d'affichage d'un élément `CalculationProperty` ou d'un élément `Measure`.|  
|[Élément Goal &#40;ASSL&#41;](goal-element-assl.md)|Identifie l'objectif souhaité dans un élément `Kpi`.|  
|[Élément GranularityAttributeID &#40;ASSL&#41;](granularityattributeid-element-assl.md)|Contient l’ID de l’attribut associé au parent [MeasureGroupAttributeBinding](../data-type/measuregroupattributebinding-data-type-out-of-line-assl.md) type de données.|  
|[Élément HideMemberIf &#40;ASSL&#41;](hidememberif-element-assl.md)|Indique si et quand un membre d'un niveau doit être masqué par rapport aux applications clientes.|  
|[Élément HierarchyID &#40;ASSL&#41;](hierarchyid-element-assl.md)|Contient l’ID pour un [CubeHierarchy](../data-type/hierarchy-data-type-assl.md), [MeasureGroupHierarchy](../data-type/measuregrouphierarchy-data-type-assl.md), ou [PerspectiveHierarchy](../data-type/perspectivehierarchy-data-type-assl.md) élément.|  
|[Élément HierarchyUniqueNameStyle &#40;ASSL&#41;](hierarchyuniquenamestyle-element-assl.md)|Détermine la manière dont les noms uniques sont générés pour les hiérarchies contenues dans `CubeDimension`.|  
|[ID d’élément &#40;ASSL&#41;](id-element-assl.md)|Contient l'ID unique de l'élément parent.|  
|[Élément IgnoreUnrelatedDimensions &#40;ASSL&#41;](../collections/dimensions-element-assl.md)|Détermine si les dimensions non liées sont ignorées lorsque des membres de dimensions qui ne sont pas associées au groupe de mesures sont inclus dans une requête.|  
|[Élément ImpersonationInfo &#40;ASSL&#41;](impersonationinfo-element-assl.md)|Fournit les informations permettant de déterminer le comportement d'emprunt d'identité lors de l'accès ou de l'exécution d'un assembly.|  
|[Élément ImpersonationInfoSecurity &#40;ASSL&#41;](impersonationinfosecurity-element-assl.md)|Contient une valeur en lecture seule qui indique si des modifications ont été apportées aux informations d'identification de sécurité fournies dans le type de données `ImpersonationInfo`.|  
|[Élément ImpersonationMode &#40;ASSL&#41;](impersonationmode-element-assl.md)|Contient une valeur qui indique la méthode d'emprunt d'identité pour les éléments dérivés du type de données `ImpersonationInfo`.|  
|[Élément InstanceSelection &#40;ASSL&#41;](instanceselection-element-assl.md)|Fournit un indicateur aux applications clientes qui suggère le mode d'affichage d'une liste d'éléments d'après le nombre d'éléments attendus dans la liste.|  
|[Élément IntermediateCubeDimensionID &#40;ASSL&#41;](intermediatecubedimensionid-element-assl.md)|Contient l'ID de la dimension qui lie une dimension de référence à un groupe de mesures.|  
|[Élément IntermediateGranularityAttributeID &#40;ASSL&#41;](intermediategranularityattributeid-element-assl.md)|Contient l'ID de l'attribut de granularité dans la dimension de cube intermédiaire utilisée pour lier une dimension de référence à une dimension intermédiaire.|  
|[Élément InvalidXmlCharacters &#40;ASSL&#41;](invalidxmlcharacters-element-assl.md)|Spécifie la méthode de traitement des caractères XML dans les données sources qui ne sont pas valides.|  
|[Élément invocation &#40;ASSL&#41;](invocation-element-assl.md)|Spécifie la manière dont un élément `Action` doit être appelé.|  
|[Élément IsAggregatable &#40;ASSL&#41;](isaggregatable-element-assl.md)|Spécifie si les valeurs de la [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) élément peut être agrégé.|  
|[Élément IsKey &#40;ASSL&#41;](iskey-element-assl.md)|Indique si la colonne fournit la clé pour le cas dans un élément `MiningStructure`.|  
|[Élément isolation &#40;ASSL&#41;](isolation-element-assl.md)|Indique le niveau d’isolement pour un élément qui est dérivé de la [DataSource](../data-type/datasource-data-type-assl.md) type de données.|  
|[Élément KeyDuplicate &#40;ASSL&#41;](keyduplicate-element-assl.md)|Détermine la manière dont [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gère une erreur de clé dupliquée s'il en rencontre une au cours du traitement.|  
|[Élément KeyErrorAction &#40;ASSL&#41;](keyerroraction-element-assl.md)|Spécifie l'action que doit entreprendre [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] en cas d'erreur concernant une clé.|  
|[Élément KeyErrorLimit &#40;ASSL&#41;](keyerrorlimit-element-assl.md)|Contient le nombre d'erreurs acceptables au cours du traitement.|  
|[Élément KeyErrorLimitAction &#40;ASSL&#41;](keyerrorlimitaction-element-assl.md)|Spécifie l’action qui [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend lorsque le nombre d’erreurs de la clé est spécifié dans le [KeyErrorLimit](keyerrorlimit-element-assl.md) élément soit atteint.|  
|[Élément KeyErrorLogFile &#40;ASSL&#41;](../objects/file-element-assl.md)|Contient le nom de fichier pour l'enregistrement des erreurs de traitement dans un journal.|  
|[Élément KeyNotFound &#40;ASSL&#41;](keynotfound-element-assl.md)|Spécifie la manière dont [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] répond quand il rencontre une erreur d'intégrité référentielle.|  
|[Élément KeyUniquenessGuarantee &#40;ASSL&#41;](keyuniquenessguarantee-element-assl.md)|Indique si la validité de la relation entre la clé d'attribut et son nom (ainsi que la relation avec les attributs associés) est garantie.|  
|[Élément KpiID &#40;ASSL&#41;](kpiid-element-assl.md)|Contient un ID qui associe un élément `Kpi` à un élément `Perspective`.|  
|[Élément de langage &#40;ASSL&#41;](language-element-assl.md)|Contient l'identificateur de langue de l'élément parent.|  
|[Élément LastProcessed &#40;ASSL&#41;](lastprocessed-element-assl.md)|Affiche l'horodateur en lecture seule qui indique à quel moment la base de données qui contient l'élément parent a été traitée pour la dernière fois.|  
|[Élément LastSchemaUpdate &#40;ASSL&#41;](lastschemaupdate-element-assl.md)|Contient l'horodateur en lecture seule de la mise à jour des métadonnées de l'élément parent.|  
|[Élément LastUpdate &#40;ASSL&#41;](lastupdate-element-assl.md)|Contient un horodateur en lecture seule qui indique quand l'élément `Database` associé ou l'un des principaux objets que contient la base de données a été modifié pour la dernière fois.|  
|[Élément latency &#40;ASSL&#41;](latency-element-assl.md)|Définit la période de grâce entre la première notification et le moment où les images MOLAP sont détruites.|  
|[Élément LogFileAppend &#40;ASSL&#41;](logfileappend-element-assl.md)|Détermine si l'élément `Trace` ajoute sa sortie d'enregistrement au fichier journal existant ou la remplace.|  
|[Élément LogFileName &#40;ASSL&#41;](logfilename-element-assl.md)|Contient le nom du fichier journal de l'élément `Trace`.|  
|[Élément LogFileRollover &#40;ASSL&#41;](logfilerollover-element-assl.md)|Spécifie si l’enregistrement de `Trace` sortie doit être remplacé par un nouveau fichier ou doit s’arrêter lorsque la taille maximale du fichier journal qui est spécifiée dans [LogFileSize](logfilesize-element-assl.md) est atteinte.|  
|[Élément LogFileSize &#40;ASSL&#41;](logfilesize-element-assl.md)|Spécifie la taille maximale (en mégaoctets) du fichier journal.|  
|[Élément ManagedProvider &#40;ASSL&#41;](managedprovider-element-assl.md)|Contient le nom du fournisseur managé utilisé par un élément dérivé du type de données `DataSource`.|  
|[Élément ManufacturingExtraMonthQuarter &#40;ASSL&#41;](manufacturingextramonthquarter-element-assl.md)|Définit le mois de la période de fabrication à laquelle un mois supplémentaire est attribué pour un élément `TimeBinding`.|  
|[Élément ManufacturingFirstMonth &#40;ASSL&#41;](manufacturingfirstmonth-element-assl.md)|Définit le premier mois de fabrication pour un élément `TimeBinding`.|  
|[Élément ManufacturingFirstWeekOfMonth &#40;ASSL&#41;](manufacturingfirstweekofmonth-element-assl.md)|Définit la première semaine du mois de fabrication pour un élément `TimeBinding`.|  
|[Élément MasterDatasourceID &#40;ASSL&#41;](masterdatasourceid-element-assl.md)|Contient l'identificateur (ID) de la source de données principale d'un élément `Database`.|  
|[Élément Materialization &#40;ASSL&#41;](materialization-element-assl.md)|Indique le type de relation de dimension entre le groupe de mesures et la dimension de référence.|  
|[Élément MaxActiveConnections &#40;ASSL&#41;](maxactiveconnections-element-assl.md)|Contient le nombre maximal de connexions simultanées autorisées par un élément dérivé du type de données `DataSource`.|  
|[Élément MdxMissingMemberMode &#40;ASSL&#41;](mdxmissingmembermode-element-assl.md)|Détermine le mode de gestion des membres manquants pour les instructions MDX.|  
|[Élément MeasureExpression &#40;ASSL&#41;](measureexpression-element-assl.md)|Contient l'expression MDX qui définit une mesure.|  
|[Élément MeasureGroupID &#40;ASSL&#41;](measuregroupid-element-assl.md)|Associe un élément `MeasureGroup` à l'élément parent, la liaison ou la liaison hors ligne.|  
|[Élément MeasureID &#40;ASSL&#41;](measureid-element-assl.md)|Associe un élément `Measure` à l'élément parent.|  
|[Élément Measurequalification &#40;ASSL&#41;](measurequalificaton-element-assl.md)|Détermine si un préfixe est appliqué aux mesures dans l'élément `MeasureGroup`.|  
|[Élément MemberNamesUnique &#40;ASSL&#41;](membernamesunique-element-assl.md)|Détermine si les noms des membres sous l'élément parent doivent être uniques.|  
|[Élément MemberUniqueNameStyle &#40;ASSL&#41;](memberuniquenamestyle-element-assl.md)|Détermine la manière dont les noms uniques sont générés pour les membres des hiérarchies que contient l'élément `CubeDimension`.|  
|[Élément MembersWithData &#40;ASSL&#41;](memberswithdata-element-assl.md)|Détermine si les membres de données pour les membres non-feuilles de l'attribut parent sont affichés ou non.|  
|[Élément MembersWithDataCaption &#40;ASSL&#41;](memberswithdatacaption-element-assl.md)|Fournit une chaîne de modèle utilisée pour créer des légendes pour les membres de données générés par le système.|  
|[Élément MimeType &#40;ASSL&#41;](mimetype-element-assl.md)|Contient (le cas échéant) le type MIME (Multipurpose Internet Mail Extensions) des données représentées par l'élément `DataItem` parent.|  
|[Élément MiningModelID &#40;ASSL&#41;](miningmodelid-element-assl.md)|Associe un modèle d'exploration de données à une dimension d'exploration de données.|  
|[Nommez l’élément &#40;ASSL&#41;](name-element-assl.md)|Contient le nom de l'élément parent.|  
|[Élément NamingTemplate &#40;ASSL&#41;](namingtemplate-element-assl.md)|Définit la manière dont les niveaux sont appelés dans une hiérarchie parent-enfant construite à partir de l'élément parent `DimensionAttribute`.|  
|[Élément NonEmptyBehavior &#40;ASSL&#41;](nonemptybehavior-element-assl.md)|Détermine le comportement non vide associé au parent de l'élément `CalculationProperty`.|  
|[Élément NotificationTechnique &#40;ASSL&#41;](notificationtechnique-element-assl.md)|Spécifie si [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou une application cliente externe traite les notifications.|  
|[Élément NullKeyConvertedToUnknown &#40;ASSL&#41;](nullkeyconvertedtounknown-element-assl.md)|Spécifie l'action à entreprendre en cas d'erreur de conversion de type NULL.|  
|[Élément NullKeyNotAllowed &#40;ASSL&#41;](nullkeynotallowed-element-assl.md)|Détermine la manière dont le moteur de traitement [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gère une erreur de clé NULL survenue au cours du traitement.|  
|[Élément NullProcessing &#40;ASSL&#41;](nullprocessing-element-assl.md)|Définit le mode de traitement des valeurs NULL.|  
|[Élément OnlineMode &#40;ASSL&#41;](onlinemode-element-assl.md)|Spécifie si la base de données est remise en ligne immédiatement dès le début de la reconstruction du cache ou seulement lorsque la reconstruction du cache est terminée.|  
|[Élément OptimizedState &#40;ASSL&#41;](state-element-assl.md)|Détermine le niveau d'optimisation appliqué à la hiérarchie.|  
|[Élément optionality &#40;ASSL&#41;](optionality-element-assl.md)|Indique le caractère facultatif des membres pour un élément `AttributeRelationship`.|  
|[Élément OrderBy &#40;ASSL&#41;](orderby-element-assl.md)|Décrit comment classer les membres contenus dans l'attribut.|  
|[Élément OrderByAttributeID &#40;ASSL&#41;](orderbyattributeid-element-assl.md)|Identifie un autre attribut selon lequel trier les membres de la [Dimension](../data-type/dimensionattribute-data-type-assl.md) attribut.|  
|[Élément ordinal &#40;ASSL&#41;](ordinal-element-assl.md)|Indique le nombre ordinal auquel s'associer dans des collections, telles que des clés et des traductions.|  
|[Élément OverrideBehavior &#40;ASSL&#41;](overridebehavior-element-assl.md)|Indique le comportement de substitution de la relation décrite par un élément `AttributeRelationship`.|  
|[Élément PartitionID &#40;ASSL&#41;](partitionid-element-assl.md)|Associe un élément `Partition` à un élément parent, une liaison ou une liaison hors ligne.|  
|[Élément de mot de passe &#40;ASSL&#41;](password-element-assl.md)|Contient le mot de passe du compte d'utilisateur pour l'élément `ImpersonationInfo`.|  
|[Élément de chemin d’accès &#40;ASSL&#41;](path-element-assl.md)|Contient le chemin d’accès, tel que fourni par une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], d’un rapport utilisé par le [ReportAction](../data-type/reportaction-data-type-assl.md) élément.|  
|[Élément PendingValue &#40;ASSL&#41;](pendingvalue-element-assl.md)|Contient la valeur en lecture seule en attente de l'élément `ServerProperty` associé.|  
|[Élément PermissionSet &#40;ASSL&#41;](permissionset-element-assl.md)|Identifie le jeu d’autorisations associé à un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] assembly .NET Framework.|  
|[Élément Persistence &#40;ASSL&#41;](persistence-element-assl.md)|Détermine quelles parties des données sources liées sont dynamiques et sont activés pour les mises à jour à l’aide de la fréquence spécifiée par le [RefreshPolicy](refreshpolicy-element-assl.md) élément.|  
|[Traiter l’élément &#40;ASSL&#41;](process-element-assl.md)|Détermine si un utilisateur peut traiter le propriétaire de l'élément parent.|  
|[Élément ProcessingMode &#40;ASSL&#41;](processingmode-element-assl.md)|Indique si l'instance doit créer les index et effectuer l'agrégation lors du traitement ou après celui-ci.|  
|[Élément ProcessingPriority &#40;ASSL&#41;](processingpriority-element-assl.md)|Détermine la priorité de traitement de l'objet parent lors des opérations en arrière-plan (par exemple, le traitement différé des agrégations, de l'indexation ou du clustering).|  
|[Élément ProcessingQuery &#40;ASSL&#41;](query-element-assl.md)|Contient le texte paramétrable de la requête à exécuter pour la notification d'état de traitement incrémentiel.|  
|[Élément ProductName &#40;ASSL&#41;](productname-element-assl.md)|Contient le nom de produit en lecture seule de l'instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] associée à un élément `Server`.|  
|[Élément de requête &#40;ASSL&#41;](query-element-assl.md)|Contient le texte de la requête à exécuter pour la notification.|  
|[Élément QueryDefinition &#40;ASSL&#41;](querydefinition-element-assl.md)|Contient l’expression opaque d’une requête associée à un `DataSource` élément dans un [QueryBinding](../data-type/querybinding-data-type-assl.md) élément.|  
|[Lire l’élément &#40;ASSL&#41;](read-element-assl.md)|Détermine si les données ou les métadonnées peuvent être lues pour un donné [CubeDimensionPermission](../data-type/permission-data-type-assl.md) ou [autorisation](../data-type/permission-data-type-assl.md) élément.|  
|[Élément ReadDefinition &#40;ASSL&#41;](readdefinition-element-assl.md)|Détermine si les membres peuvent lire la définition de la base de données ou la définition des objets de la base de données.|  
|[Élément ReadSourceData &#40;ASSL&#41;](readsourcedata-element-assl.md)|Détermine la manière dont les noms uniques sont générés pour les hiérarchies contenues dans `CubePermission`.|  
|[Élément RefreshInterval &#40;ASSL&#41;](refreshinterval-element-assl.md)|Spécifie l'intervalle d'actualisation des données liées associées à l'élément parent.|  
|[Élément RefreshPolicy &#40;ASSL&#41;](refreshpolicy-element-assl.md)|Détermine la fréquence à laquelle la partie dynamique de la dimension ou groupe de mesures (comme spécifié par le [persistance](persistence-element-assl.md) élément) est activée pour les modifications.|  
|[Élément RelationshipType &#40;ASSL&#41;](relationshiptype-element-assl.md)|Indique si les relations entre les membres d'un élément `AttributeRelationship` peuvent être modifiées.|  
|[Élément RemoteDatasourceID &#40;ASSL&#41;](remotedatasourceid-element-assl.md)|Spécifie l'ID de la source de données OLAP qui pointe vers l'instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] chargée de stocker la partition distante.|  
|[Élément ReportingFirstMonth &#40;ASSL&#41;](reportingfirstmonth-element-assl.md)|Définit le premier mois de création de rapports pour l'élément `TimeBinding`.|  
|[Élément ReportingFirstWeekOfMonth &#40;ASSL&#41;](reportingfirstweekofmonth-element-assl.md)|Définit la première semaine du mois de création de rapports pour l'élément `TimeBinding`.|  
|[Élément ReportingWeekToMonthPattern &#40;ASSL&#41;](reportingweektomonthpattern-element-assl.md)|Définit la séquence de rapport de semaine en mois de l'élément `TimeBinding`.|  
|[Élément ReportServer &#40;ASSL&#41;](reportserver-element-assl.md)|Contient le nom de l'instance [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] utilisée par l'élément `ReportAction`.|  
|[Élément RequiresRestart &#40;ASSL&#41;](requiresrestart-element-assl.md)|Contient une valeur en lecture seule associée à un élément `ServerProperty` qui détermine si la modification de la valeur de la propriété du serveur nécessite le redémarrage de l'instance pour que la modification soit prise en compte.|  
|[Élément RoleID &#40;ASSL&#41;](roleid-element-assl.md)|Identifie le rôle pour lequel les autorisations sont définies.|  
|[Élément racine &#40;ASSL&#41;](root-element-assl.md)|Contient les données (ensemble de lignes) d'une source de données.|  
|[Élément RootMemberIf &#40;ASSL&#41;](rootmemberif-element-assl.md)|Détermine la manière dont le membre racine ou les membres d'un attribut parent sont identifiés.|  
|[Élément de schéma &#40;ASSL&#41;](schema-element-assl.md)|Contient le schéma de la vue de source de données.|  
|[Élément ScriptCacheProcessingMode &#40;ASSL&#41;](scriptcacheprocessingmode-element-assl.md)|Indique si le serveur doit construire le cache des scripts au cours du traitement ou après celui-ci.|  
|[Élément SilenceInterval &#40;ASSL&#41;](silenceinterval-element-assl.md)|Définit le temps minimal pendant lequel l'instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] s'interrompt avant de démarrer le processus de création d'images MOLAP.|  
|[Élément SilenceOverrideInterval &#40;ASSL&#41;](silenceoverrideinterval-element-assl.md)|Définit le temps qui doit s'écouler après la réception de la première notification et avant le démarrage de manière inconditionnelle du processus de création d'images MOLAP.|  
|[Slice, élément &#40;ASSL&#41;](slice-element-assl.md)|Contient une expression MDX qui définit la tranche contenue dans une partition.|  
|[Élément SolveOrder &#40;ASSL&#41;](solveorder-element-assl.md)|Indique l'ordre de résolution dans lequel l'élément `CalculationProperty` est appliqué à un membre calculé ou une définition de cellule calculée.|  
|[Élément source &#40;liaison&#41; &#40;ASSL&#41;](source-element-binding-assl.md)|Identifie la source de données à laquelle l'élément parent est lié.|  
|[Élément source &#40;ComAssembly&#41; &#40;ASSL&#41;](source-element-comassembly-assl.md)|Contient le nom de fichier ou l'identificateur programmatique (ProgID) d'un composant COM (Component Object Model).|  
|[Élément source &#40;mesure&#41; &#40;ASSL&#41;](source-element-measure-assl.md)|Affiche les détails de la source contenant la valeur de l'élément `Measure`.|  
|[Élément SourceAttributeID &#40;ASSL&#41;](sourceattributeid-element-assl.md)|Contient l’ID de l’attribut source sur lequel le [niveau](../objects/level-element-assl.md) élément repose.|  
|[Élément SourceColumnID &#40;ASSL&#41;](sourcecolumnid-element-assl.md)|Contient l'identificateur (ID) de la colonne de structure d'exploration de données source dans l'élément ancêtre `MiningStructure`.|  
|[Élément d’état &#40;ASSL&#41;](state-element-assl.md)|Contient une valeur en lecture seule qui décrit l'état de traitement actuel de l'élément parent.|  
|[Élément Status &#40;ASSL&#41;](status-element-assl.md)|Contient une expression MDX qui retourne un indicateur d'état pour un élément `Kpi`.|  
|[Élément StatusGraphic &#40;ASSL&#41;](statusgraphic-element-assl.md)|Contient la représentation graphique recommandée de l'état de l'élément `Kpi`.|  
|[Élément StopTime &#40;ASSL&#41;](stoptime-element-assl.md)|Spécifie la date et l'heure auxquelles un élément `Trace` doit s'arrêter.|  
|[Élément StorageLocation &#40;ASSL&#41;](storagelocation-element-assl.md)|Contient l'emplacement de stockage du système de fichiers pour le contenu de l'élément parent.|  
|[Élément StorageMode &#40;ASSL&#41;](storagemode-element-assl.md)|Détermine le mode de stockage de l'élément parent.|  
|[Élément TableID &#40;ASSL&#41;](tableid-element-assl.md)|Contient l'ID de la table (provenant de l'élément `DataSourceView`) associée à l'élément parent.|  
|[Élément Target &#40;ASSL&#41;](target-element-assl.md)|Identifie la cible de l'élément `Action`.|  
|[Élément TargetType &#40;ASSL&#41;](targettype-element-assl.md)|Identifie le type d’élément de l’élément identifié dans le [cible](target-element-assl.md) élément.|  
|[Élément de texte &#40;ASSL&#41;](text-element-assl.md)|Contient le texte d’un [commande](../objects/command-element-assl.md) élément.|  
|[Élément timeout &#40;ASSL&#41;](timeout-element-assl.md)|Spécifie le temps (en secondes) après lequel une tentative de récupération des données signale une expiration de délai d'attente.|  
|[Élément de tendance &#40;ASSL&#41;](trend-element-assl.md)|Contient une expression MDX qui retourne un indicateur de tendance pour un élément `Kpi`.|  
|[Élément TrendGraphic &#40;ASSL&#41;](trendgraphic-element-assl.md)|Contient la représentation graphique recommandée de la tendance de l'élément `Kpi`.|  
|[Élément Trimming &#40;ASSL&#41;](trimming-element-assl.md)|Spécifie comment les données de la source de données sont tronquées.|  
|[Type d’élément &#40;Action&#41; &#40;ASSL&#41;](type-element-action-assl.md)|Contient le type de l'élément `Action`.|  
|[Type d’élément &#40;liaison&#41; &#40;ASSL&#41;](type-element-binding-assl.md)|Contient le type de la liaison d'attribut.|  
|[Type d’élément &#40;ClrAssemblyFile&#41; &#40;ASSL&#41;](type-element-clrassemblyfile-assl.md)|Spécifie le type de fichier d’un des fichiers qui appartiennent à un assembly .NET Framework.|  
|[Type d’élément &#40;Dimension&#41; &#40;ASSL&#41;](type-element-dimension-assl.md)|Fournit des informations sur le contenu de la dimension.|  
|[Type d’élément &#40;DimensionAttribute&#41; &#40;ASSL&#41;](type-element-dimensionattribute-assl.md)|Contient le type de l'attribut.|  
|[Type d’élément &#40;MeasureGroup&#41; &#40;ASSL&#41;](type-element-measuregroup-assl.md)|Spécifie le type de l'élément `MeasureGroup`.|  
|[Type d’élément &#40;MeasureGroupAttribute&#41; &#40;ASSL&#41;](type-element-measuregroupattribute-assl.md)|Contient le type d’un [MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md) élément.|  
|[Type d’élément &#40;MiningStructureColumn&#41; &#40;ASSL&#41;](type-element-miningstructurecolumn-assl.md)|Contient le type de la [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) élément.|  
|[Type d’élément &#40;Partition&#41; &#40;ASSL&#41;](type-element-partition-assl.md)|Contient le type de l'élément `Partition`.|  
|[Type d’élément &#40;PerspectiveCalculation&#41; &#40;ASSL&#41;](type-element-perspectivecalculation-assl.md)|Indique le type de la [PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md) élément.|  
|[Élément UnknownMember &#40;ASSL&#41;](unknownmember-element-assl.md)|Indique si le membre inconnu est visible.|  
|[Élément UnknownMemberName &#40;ASSL&#41;](unknownmembername-element-assl.md)|Contient la légende (dans la langue par défaut de la dimension) du membre inconnu de la dimension.|  
|[Utilisation de l’élément &#40;DimensionAttribute&#41; &#40;ASSL&#41;](usage-element-dimensionattribute-assl.md)|Décrit le mode d'utilisation d'un attribut.|  
|[Utilisation de l’élément &#40;MiningModelColumn&#41; &#40;ASSL&#41;](usage-element-miningmodelcolumn-assl.md)|Décrit le mode d'utilisation de la colonne associée dans l'élément `MiningStructure` parent.|  
|[Valeur d’élément &#40;ASSL&#41;](value-element-assl.md)|Contient la valeur de l'élément parent.|  
|[Élément version &#40;ASSL&#41;](version-element-assl.md)|Contient le numéro de version en lecture seule de l'instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] représentée par l'élément `Server`.|  
|[Élément Visibility &#40;ASSL&#41;](visibility-element-assl.md)|Définit la visibilité d’un [Annotation](../objects/annotation-element-assl.md) élément.|  
|[Élément visible &#40;ASSL&#41;](visible-element-assl.md)|Détermine la visibilité de l'élément parent.|  
|[Élément VisualTotals &#40;ASSL&#41;](visualtotals-element-assl.md)|Contient une expression MDX qui détermine si les valeurs visibles sont affichées pour les membres de cet attribut.|  
|[Écrire l’élément &#40;ASSL&#41;](write-element-assl.md)|Détermine si les données ou les métadonnées peuvent être écrites pour un élément `CubeDimensionPermission` ou `Permission` spécifique.|  
|[Élément WriteEnabled &#40;ASSL&#41;](writeenabled-element-assl.md)|Indique si l'écriture différée de dimension est disponible (soumise à des autorisations de sécurité).|  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchie Analysis Services Scripting Language XML élément &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
