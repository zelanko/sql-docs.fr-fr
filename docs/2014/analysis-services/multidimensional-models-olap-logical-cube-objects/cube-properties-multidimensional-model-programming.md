---
title: Propriétés du cube | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
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
author: minewiskan
ms.author: owend
ms.openlocfilehash: 27d4202774107795eaddf76c27e21010d534d977
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545251"
---
# <a name="cube-properties"></a>Propriétés de cube
  Les cubes ont un grand nombre de propriétés que vous pouvez définir pour affecter le comportement à l'échelle du cube. Ces propriétés sont présentées dans le tableau suivant.  
  
> [!NOTE]  
>  Certaines propriétés sont définies automatiquement lors de la création du cube et ne peuvent pas être modifiées.  
  
 Pour plus d’informations sur la définition des propriétés d’un cube, consultez [Concepteur de cube &#40;Analysis Services-données multidimensionnelles&#41;](../cube-designer-analysis-services-multidimensional-data.md).  
  
|Propriété|Description|  
|--------------|-----------------|  
|`AggregationPrefix`|Spécifie le préfixe commun qui est utilisé pour les noms d'agrégation.|  
|`Collation`|Spécifie l'identificateur de paramètres régionaux (LCID) et l'indicateur de comparaison, séparés par un trait de soulignement, comme dans Latin1_General_C1_AS.|  
|`DefaultMeasure`|Contient une expression MDX (Multidimensional Expressions) qui définit la mesure par défaut pour le cube.|  
|`Description`|Fournit une description du cube, qui peut être exposée dans les applications clientes.|  
|`ErrorConfiguration`|Contient des paramètres configurables de gestion d'erreur pour la gestion des clés dupliquées, des clés inconnues, des limites d'erreur, des actions en cas de détection d'erreur, du fichier journal des erreurs et pour la gestion des clés NULL.|  
|`EstimatedRows`|Spécifie le nombre de lignes estimées dans le cube.|  
|`ID`|Contient l'identificateur (ID) unique du cube.|  
|`Language`|Spécifie l'identificateur de langue par défaut du cube.|  
|`Name`|Spécifie le nom convivial du cube.|  
|`ProactiveCaching`|Définit les paramètres de mise en cache proactive pour le cube.|  
|`ProcessingMode`|Indique si l'indexation et l'agrégation doivent avoir lieu lors du traitement ou après celui-ci. Les options sont **Regular** ou `lazy` .|  
|`ProcessingPriority`|Détermine la priorité de traitement du cube pendant les opérations d'arrière-plan, telles que les agrégations et les indexations différées (Lazy). La valeur par défaut est **0**.|  
|`ScriptCacheProcessingMode`|Indique si le cache des scripts doit être généré durant le traitement ou après celui-ci. Les options sont **Regular** et `lazy` .|  
|`ScriptErrorHandlingMode`|Détermine la gestion des erreurs. Les options sont `IgnoreNone` ou`IgnoreAll`|  
|`Source`|Affiche la vue de source de données utilisée pour le cube.|  
|`StorageLocation`|Spécifie l'emplacement de stockage du système de fichiers pour le cube. Si aucun n'est spécifié, l'emplacement est hérité de la base de données qui contient l'objet du cube.|  
|`StorageMode`|Spécifie le mode de stockage pour le cube. Les valeurs sont `MOLAP` , `ROLAP` ou`HOLAP``.`|  
|`Visible`|Détermine la visibilité du cube.|  
  
> [!NOTE]  
>  Pour plus d’informations sur la définition des valeurs de la propriété ErrorConfiguration lors de l’utilisation de valeurs NULL et d’autres problèmes d’intégrité des données, consultez [gestion des problèmes d’intégrité des données dans Analysis Services 2005](https://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en cache proactive &#40;les partitions&#41;](partitions-proactive-caching.md)  
  
  
