---
title: "D&#233;finir des propri&#233;t&#233;s d&#39;attributs de cube | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cubes [Analysis Services], définition"
ms.assetid: 579ca818-f33d-4060-906d-c8bfee93bf99
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 13
---
# D&#233;finir des propri&#233;t&#233;s d&#39;attributs de cube
  Les propriétés des attributs de cube vous permettent de spécifier des paramètres uniques pour les attributs de dimension des dimensions de cube à partir de la même dimension de base de données. Le tableau suivant décrit les propriétés d'un attribut de cube.  
  
|Propriété|Description|  
|--------------|-----------------|  
|**AggregationUsage**|Indique le mode de création des agrégations d'attribut par l'Assistant Conception d'agrégation. La valeur par défaut est **Default**. Cette propriété peut avoir les valeurs suivantes :<br /><br /> **Par défaut** :<br />                    L'Assistant Conception d'agrégation applique une règle par défaut en fonction du type d'attribut (Full pour les clés, Unrestricted pour les autres types).<br /><br /> **Aucun** :<br />                    Aucune agrégation du cube ne doit inclure cet attribut.<br /><br /> **Illimité** :<br />                    L’Assistant Conception d’agrégation ne fait l’objet d’aucune restriction.<br /><br /> **Complet** :<br />                    Toutes les agrégations de cube doivent inclure cet attribut.|  
|**AttributeHierarchyEnabled**|Indique si la hiérarchie d'attributs est activée sur cette dimension de cube. Cet attribut permet de désactiver les hiérarchies d'attributs sur des cubes ou des rôles de dimension spécifiques. Ce paramètre est sans effet si la hiérarchie d'attributs sous-jacente est désactivée. La valeur par défaut est **True**.|  
|**OptimizedState**|Indique si la hiérarchie d'attributs est optimisée sur cette dimension de cube. Cet attribut permet d'optimiser les hiérarchies d'attributs sur des cubes ou des rôles de dimension spécifiques. Ce paramètre est sans effet si la hiérarchie d'attributs sous-jacente n'est pas optimisée. La valeur par défaut est **FullyOptimized**. Cette propriété peut avoir les valeurs suivantes :<br /><br /> **FullyOptimized**: L’instance construit des index pour la hiérarchie pour augmenter les performances des requêtes. Ceci est la valeur par défaut.<br /><br /> **NotOptimized** :<br />                    L'instance ne construit pas d'index supplémentaire.|  
|**AttributeHierarchyVisible**|Indique si la hiérarchie d'attributs est visible sur cette dimension de cube. Cet attribut permet de rendre visible les hiérarchies d'attributs sur des cubes ou des rôles de dimension spécifiques. Ce paramètre est sans effet si la hiérarchie d'attributs sous-jacente n'est pas visible. La valeur par défaut est **True**.|  
|**AttributeID**|Contient l'identificateur unique (ID) de l'attribut.|  
  
## Voir aussi  
 [Définir des propriétés d'une dimension de cube](../../analysis-services/multidimensional-models/define-cube-dimension-properties.md)   
 [Définir les propriétés des hiérarchies de cube](../../analysis-services/multidimensional-models/define-cube-hierarchy-properties.md)  
  
  