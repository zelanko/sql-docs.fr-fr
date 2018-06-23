---
title: Type de données DimensionAttribute (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DimensionAttribute Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DimensionAttribute
helpviewer_keywords:
- DimensionAttribute data type
ms.assetid: 94349a87-b284-49d1-ac72-888f0375ceb8
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2d022a0bfb5c11efe38694b614bd65676fb3ee28
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038912"
---
# <a name="dimensionattribute-data-type-assl"></a>Type de données DimensionAttribute (ASSL)
  Définit un type de données primitif représentant un attribut dans une dimension.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Description>...</Description>  
   <Type>...</Type>  
   <Usage>...</Usage>  
   <Source>...</Source>  
   <EstimatedCount>...</EstimatedCount>  
   <KeyColumns>...</KeyColumns>  
   <NameColumn>...</NameColumn>  
   <ValueColumn>...</ValueColumn>  
   <Translations>...</Translations>  
   <AttributeRelationships>...</AttributeRelationships>  
   <DiscretizationMethod>...</DiscretizationMethod>  
   <DiscretizationBucketCount>...</DiscretizationBucketCount>  
   <RootMemberIf>...</RootMemberIf>  
   <OrderBy>...</OrderBy>  
   <DefaultMember>...</DefaultMember>  
   <OrderByAttributeID>...</OrderByAttributeID>  
   <SkippedLevelsColumn>...</SkippedLevelsColumn>  
   <NamingTemplate>...</NamingTemplate>  
   <MembersWithData>...</MembersWithData>  
   <MembersWithDataCaption>...</MembersWithDataCaption>  
   <NamingTemplateTranslations>...</NamingTemplateTranslations>  
   <CustomRollupColumn>...</CustomRollupColumn>  
   <CustomRollupPropertiesColumn>...</CustomRollupPropertiesColumn>  
   <UnaryOperatorColumn>...</UnaryOperatorColumn>  
   <AttributeHierarchyOrdered>...</AttributeHierarchyOrdered>  
   <MemberNamesUnique>...</MemberNamesUnique>  
   <IsAggregatable>...</IsAggregatable>  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
   <AttributeHierarchyOptimizedState>...</AttributeHierarchyOptimizedState>  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
   <AttributeHierarchyDisplayFolder>...</AttributeHierarchyDisplayFolder>  
   <KeyUniquenessGuarantee>...<KeyUniquenessGuarantee>  
   <InstanceSelection>...</InstanceSelection>  
   <Annotations>...</Annotations>  
</DimensionAttribute>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Annotations](../collections/annotations-element-assl.md), [AttributeHierarchyDisplayFolder](../properties/displayfolder-element-assl.md), [AttributeHierarchyEnabled](../properties/enabled-element-assl.md), [AttributeHierarchyOptimizedState](../properties/state-element-assl.md), [AttributeHierarchyOrdered](../properties/attributehierarchyordered-element-assl.md), [AttributeHierarchyVisible](../properties/visible-element-assl.md), [AttributeRelationships](../collections/relationships-element-assl.md), [CustomRollupColumn](../objects/column-element-assl.md), [CustomRollupPropertiesColumn](../objects/customrolluppropertiescolumn-element-assl.md), [DefaultMember](../objects/member-element-assl.md), [Description](../properties/description-element-assl.md), [DiscretizationBucketCount](../properties/discretizationbucketcount-element-assl.md), [DiscretizationMethod](../properties/discretizationmethod-element-assl.md), [EstimatedCount](../properties/estimatedcount-element-assl.md), [ID](../properties/id-element-assl.md), [InstanceSelection](../properties/instanceselection-element-assl.md), [IsAggregatable](../properties/isaggregatable-element-assl.md), [KeyColumns](../collections/columns-element-assl.md), [KeyUniquenessGuarantee](../properties/keyuniquenessguarantee-element-assl.md), [MemberNamesUnique](../properties/membernamesunique-element-assl.md), [MembersWithData](../objects/data-element-assl.md), [MembersWithDataCaption](../properties/caption-element-assl.md), [Name](../properties/name-element-assl.md), [NameColumn](../objects/namecolumn-element-assl.md), [NamingTemplate](../properties/namingtemplate-element-assl.md), [NamingTemplateTranslations](../collections/translations-element-assl.md), [OrderBy](../properties/orderby-element-assl.md), [OrderByAttributeID](../properties/attributeid-element-assl.md), [RootMemberIf](../properties/rootmemberif-element-assl.md), [SkippedLevelsColumn](../objects/skippedlevelscolumn-element-assl.md), [Source](../properties/source-element-binding-assl.md), [Translations](../collections/translations-element-assl.md), [Type](../properties/type-element-dimensionattribute-assl.md), [UnaryOperatorColumn](../objects/unaryoperatorcolumn-element-assl.md), [Usage](../properties/usage-element-dimensionattribute-assl.md), [ValueColumn](../objects/valuecolumn-element-assl.md)|  
|Éléments dérivés|[Attribute](../objects/attribute-element-assl.md) (collection[Attributes](../collections/attributes-element-assl.md) de [Dimension](../objects/dimension-element-assl.md))|  
  
## <a name="remarks"></a>Notes  
 Les restrictions suivantes s'appliquent lors de l'exécution du service selon les valeurs de propriété de configuration DeploymentMode 1 et 2 (modes SharePoint et tabulaire, utilisés pour exécuter PowerPivot et les bases de données model tabulaires) :  
  
-   L'élément utilisé accepte seulement des valeurs KEY ou REGULAR.  
  
-   L'élément IsAggregatable ne peut pas être FALSE.  
  
-   L'élément OrderBy accepte seulement des valeurs KEY ou PROPERTYKEY.  
  
-   Une colonne calculée ne peut pas être une clé primaire dans la table.  
  
-   Une colonne calculée ne peut pas contenir DataSize dans la liaison.  
  
-   Pour chaque colonne calculée, une validation de syntaxe est effectuée avant d'enregistrer la définition d'attribut.  
  
-   Pour AttributeRelationships, RelationshipType doit être défini sur la valeur Flexible.  
  
-   L'attribut « RowNumber », identifié par « RowNumber », doit avoir le type entier.  
  
-   Seul l'attribut « RowNumber » peut avoir le KeyBinding de type RowNumberBinding.  
  
-   Tous les attributs autres que « RowNumber » doivent avoir une cardinalité de 1 par rapport à la clé, à moins que l'attribut lui-même soit la clé.  
  
-   Lorsque la colonne spécifié par OrderBy est également le PropertyKey, OrderByAttributeId ne peut pas pointer sur la colonne de numéro de ligne.  
  
-   Les attributs utilisés comme clés doivent être mis en rapport avec tous les autres attributs ; les autres types de relations ne sont pas prises en charge.  
  
-   L'élément NullProcessing ne peut pas être défini sur « UnknownMember ».  
  
-   Les liaisons ne peuvent pas être définies sur « Value ».  
  
 Les éléments suivants ne sont pas pris en charge lors de l'exécution du service selon les valeurs de propriété de configuration DeploymentMode 1 et 2 (modes SharePoint et tabulaire, utilisés pour exécuter PowerPivot et les bases de données model tabulaires) :  
  
-   AttributeHierarchyOptimizedState  
  
-   CustomRollupColumn  
  
-   CustomRollupPropertiesColumn  
  
-   DefaultMember  
  
-   DiscretizationBucketCount  
  
-   DiscretizationMethod  
  
-   SkippedLevelsColumn  
  
-   Source  
  
-   UnaryOperatorColumn  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  