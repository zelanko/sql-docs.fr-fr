---
title: "Programmation du modèle multidimensionnel - propriétés de cube | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Collation property
- ID property
- ErrorConfiguration property
- cubes [Analysis Services], properties
- Description property
- DefaultMeasure property
- ProcessingMode property
- AggregationPrefix property
- EstimatedRows property
- Visible property
- StorageLocation property
- StorageMode property
- ScriptErrorHandlingMode property
- Source property
- ScriptCacheProcessingMode property
- Language property
- Name property
- properties [Analysis Services], cubes
- ProcessingPriority property
- ProactiveCaching property
ms.assetid: 72ca3387-620d-4473-8e23-7fe1f2b3d5bf
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3b86278422fc1e3ec91845c223adc56640602739
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="cube-properties---multidimensional-model-programming"></a>Programmation du modèle multidimensionnel - propriétés de cube
  Les cubes ont un grand nombre de propriétés que vous pouvez définir pour affecter le comportement à l'échelle du cube. Ces propriétés sont présentées dans le tableau suivant.  
  
> [!NOTE]  
>  Certaines propriétés sont définies automatiquement lors de la création du cube et ne peuvent pas être modifiées.  
  
 Pour plus d’informations sur la définition des propriétés de cube, consultez [Concepteur de Cube &#40; Analysis Services - données multidimensionnelles &#41; ](http://msdn.microsoft.com/library/a6692467-da88-4312-8b03-d812f2ae5a96).  
  
|Propriété| Description|  
|--------------|-----------------|  
|**AggregationPrefix**|Spécifie le préfixe commun qui est utilisé pour les noms d'agrégation.|  
|**Classement**|Spécifie l'identificateur de paramètres régionaux (LCID) et l'indicateur de comparaison, séparés par un trait de soulignement, comme dans Latin1_General_C1_AS.|  
|**DefaultMeasure**|Contient une expression MDX (Multidimensional Expressions) qui définit la mesure par défaut pour le cube.|  
|**Description**|Fournit une description du cube, qui peut être exposée dans les applications clientes.|  
|**ErrorConfiguration**|Contient des paramètres configurables de gestion d'erreur pour la gestion des clés dupliquées, des clés inconnues, des limites d'erreur, des actions en cas de détection d'erreur, du fichier journal des erreurs et pour la gestion des clés NULL.|  
|**EstimatedRows**|Spécifie le nombre de lignes estimées dans le cube.|  
|**ID**|Contient l'identificateur (ID) unique du cube.|  
|**Langage**|Spécifie l'identificateur de langue par défaut du cube.|  
|**Nom**|Spécifie le nom convivial du cube.|  
|**ProactiveCaching**|Définit les paramètres de mise en cache proactive pour le cube.|  
|**ProcessingMode**|Indique si l'indexation et l'agrégation doivent avoir lieu lors du traitement ou après celui-ci. Les options sont **régulière** ou **différée**.|  
|**ProcessingPriority**|Détermine la priorité de traitement du cube pendant les opérations d'arrière-plan, telles que les agrégations et les indexations différées (Lazy). La valeur par défaut est **0**.|  
|**ScriptCacheProcessingMode**|Indique si le cache des scripts doit être généré durant le traitement ou après celui-ci. Les options sont **régulière** et **différée**.|  
|**ScriptErrorHandlingMode**|Détermine la gestion des erreurs. Les options sont **IgnoreNone** ou **IgnoreAll**|  
|**Source**|Affiche la vue de source de données utilisée pour le cube.|  
|**StorageLocation**|Spécifie l'emplacement de stockage du système de fichiers pour le cube. Si aucun n'est spécifié, l'emplacement est hérité de la base de données qui contient l'objet du cube.|  
|**StorageMode**|Spécifie le mode de stockage pour le cube. Les valeurs sont **MOLAP**, **ROLAP**, ou **HOLAP ***.**|  
|**Visible**|Détermine la visibilité du cube.|  
  
> [!NOTE]  
>  Pour plus d’informations sur la définition des valeurs pour la propriété ErrorConfiguration lorsque vous travaillez avec des valeurs null et d’autres problèmes d’intégrité des données, consultez [la gestion des problèmes d’intégrité des données dans Analysis Services 2005](http://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en cache proactive &#40; Partitions &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)  
  
  

