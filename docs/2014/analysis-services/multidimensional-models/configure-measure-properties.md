---
title: Configurer les propriétés de mesure | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- additivity [Analysis Services]
- ID property
- ErrorConfiguration property
- AggregateFunction property
- DisplayFolder property
- IgnoreUnrelatedDimensions property
- FormatString property
- Description property
- semiadditive
- properties [Analysis Services], measure groups
- aggregate functions [Analysis Services]
- DataType property
- ProcessingMode property
- MeasureExpression property
- AggregationPrefix property
- Visible property
- properties [Analysis Services], measures
- StorageLocation property
- StorageMode property
- formats [Analysis Services], measures
- Source property
- aggregations [Analysis Services], measures
- measures [Analysis Services], properties
- nonadditive [Analysis Services]
- Name property
- measures [Analysis Services], display formats
- ProcessingPriority property
- measure groups [Analysis Services], properties
- Type property
- ProactiveCaching property
ms.assetid: e9031078-c4f5-4986-b0c9-4d064b622ab7
caps.latest.revision: 50
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b7be3b5e73134e65cefad48b3d03c4c912a4279a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323179"
---
# <a name="configure-measure-properties"></a>Configurer des propriétés de mesure
  Les propriétés des mesures vous permettent de définir le fonctionnement des mesures et de contrôler l'affichage des mesures pour les utilisateurs.  
  
 Vous pouvez définir les propriétés dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] au moment de la création ou modification d'un cube ou d'une mesure. Vous pouvez également le faire par programmation, en utilisant MDX ou AMO. Pour plus d’informations, consultez [Création de mesures et de groupes de mesures dans les modèles multidimensionnels](create-measures-and-measure-groups-in-multidimensional-models.md), [Instruction CREATE MEMBER &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) ou [Programmation d’objets de base OLAP AMO](analysis-management-objects/programming-amo-olap-basic-objects.md).  
  
## <a name="measure-properties"></a>Propriétés des mesures  
 Les mesures héritent certaines propriétés du groupe de mesures dont elles sont membres, sauf si ces propriétés sont remplacées à l'échelle de la mesure. Les propriétés d'une mesure déterminent la manière dont la mesure est agrégée, son type de données, le nom qui s'affiche pour l'utilisateur, le dossier d'affichage dans lequel elle apparaît, sa chaîne de format, l'expression de mesure (le cas échéant), la colonne source sous-jacente et sa visibilité par rapport aux utilisateurs.  
  
|Propriété|Définition|  
|--------------|----------------|  
|`AggregateFunction`|Obligatoire. Détermine la manière dont les mesures sont agrégées. `Sum` est l’agrégation par défaut. Pour plus d’informations et obtenir une description de chaque fonction, consultez [Utiliser des fonctions d’agrégation](use-aggregate-functions.md) .|  
|`DataType`|Obligatoire. Spécifie le type de données de la colonne dans la table de faits sous-jacente à laquelle est liée la mesure. Par défaut, cette valeur est héritée de la colonne source.|  
|`Description`|Fournit une description de la mesure qui peut être exposée dans les applications clientes.|  
|`DisplayFolder`|Spécifie le dossier dans lequel apparaît la mesure lorsque les utilisateurs se connectent au cube. Si un cube possède plusieurs mesures, vous pouvez utiliser les dossiers d'affichage pour classer les mesures par catégories et faciliter la navigation pour l'utilisateur.|  
|`FormatString`|Vous pouvez sélectionner le format utilisé pour afficher les valeurs de mesure pour les utilisateurs à l’aide de la `FormatString` propriété de la mesure.<br /><br /> Une liste de formats d'affichage est fournie dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], mais vous pouvez spécifier de nombreux autres formats qui ne figurent pas dans cette liste. Vous pouvez spécifier n'importe quel format nommé ou défini par l'utilisateur, à condition qu'il soit valide dans Microsoft Visual Basic.|  
|`ID`|Obligatoire. Affiche l'identificateur (ID) unique de la mesure. Cette propriété est en lecture seule.|  
|`MeasureExpression`|Spécifie une expression MDX contrainte définissant la valeur de la mesure. L'expression est évaluée au niveau feuille avant d'être agrégée et permet d'effectuer la pondération d'une valeur. C'est le cas, par exemple, dans une conversion monétaire où un montant des ventes est pondéré en fonction du taux de change.|  
|`Name`|Obligatoire. Spécifie le nom de la mesure.|  
|`Source`|Obligatoire. Spécifie la colonne de la vue de source de données à laquelle est liée la mesure. Consultez [Sources de données et liaisons &#40;SSAS Multidimensionnel&#41;](data-sources-and-bindings-ssas-multidimensional.md).|  
|`Visible`|Détermine la visibilité de la mesure dans les applications clientes.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés du groupe de mesures](configure-measure-group-properties.md)   
 [Modification des mesures](../lesson-3-1-modifying-measures.md)  
  
  
