---
title: Définir les propriétés d’attribut de Cube | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], defining
ms.assetid: 579ca818-f33d-4060-906d-c8bfee93bf99
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6a6c5cb8c8ca0492edf9798f972b458054ae5b58
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66075737"
---
# <a name="define-cube-attribute-properties"></a>Définir des propriétés d'attributs de cube
  Les propriétés des attributs de cube vous permettent de spécifier des paramètres uniques pour les attributs de dimension des dimensions de cube à partir de la même dimension de base de données. Le tableau suivant décrit les propriétés d'un attribut de cube.  
  
|Propriété|Description|  
|--------------|-----------------|  
|`AggregationUsage`|Indique le mode de création des agrégations d'attribut par l'Assistant Conception d'agrégation. Cette propriété peut avoir les valeurs suivantes :<br /><br /> `Default`: Valeur par défaut. L'Assistant Conception d'agrégation applique une règle par défaut en fonction du type d'attribut (Full pour les clés, Unrestricted pour les autres types).<br /><br /> `None`: Aucune agrégation du cube ne doit inclure cet attribut.<br /><br /> `Unrestricted`: Aucune restriction sur l’Assistant conception d’agrégation.<br /><br /> `Full`: Toutes les agrégations de cube doivent inclure cet attribut.|  
|`AttributeHierarchyEnabled`|Indique si la hiérarchie d'attributs est activée sur cette dimension de cube. Cet attribut permet de désactiver les hiérarchies d'attributs sur des cubes ou des rôles de dimension spécifiques. Ce paramètre est sans effet si la hiérarchie d'attributs sous-jacente est désactivée. La valeur par défaut est `True`.|  
|`OptimizedState`|Indique si la hiérarchie d'attributs est optimisée sur cette dimension de cube. Cet attribut permet d'optimiser les hiérarchies d'attributs sur des cubes ou des rôles de dimension spécifiques. Ce paramètre est sans effet si la hiérarchie d'attributs sous-jacente n'est pas optimisée. Cette propriété peut avoir les valeurs suivantes :<br /><br /> `FullyOptimized`: Valeur par défaut. L'instance construit des index pour la hiérarchie afin d'augmenter les performances en matière de requêtes. Valeur par défaut.<br /><br /> `NotOptimized`: L'instance ne construit pas d'index supplémentaire.|  
|`AttributeHierarchyVisible`|Indique si la hiérarchie d'attributs est visible sur cette dimension de cube. Cet attribut permet de rendre visible les hiérarchies d'attributs sur des cubes ou des rôles de dimension spécifiques. Ce paramètre est sans effet si la hiérarchie d'attributs sous-jacente n'est pas visible. La valeur par défaut est `True`.|  
|`AttributeID`|Contient l'identificateur unique (ID) de l'attribut.|  
  
## <a name="see-also"></a>Voir aussi  
 [Définir des propriétés d'une dimension de cube](define-cube-dimension-properties.md)   
 [Définir les propriétés des hiérarchies de cube](define-cube-hierarchy-properties.md)  
  
  
