---
title: Configurer les propriétés du groupe de mesures | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- properties [Analysis Services], measure groups
ms.assetid: fa66bdb6-60b8-413c-ac2a-00e4d09f60a2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c7571457847d8ffb0388608b7d634cc19261a609
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66076668"
---
# <a name="configure-measure-group-properties"></a>Configurer les propriétés d'un groupe de mesures
  Les propriétés des groupes de mesures vous permettent de définir le fonctionnement des groupes de mesures.  
  
## <a name="measure-group-properties"></a>Propriétés des groupes de mesures  
 Les propriétés d'un groupe de mesures déterminent les comportements de l'ensemble du groupe de mesures et définissent les comportements par défaut des nouveaux objets de certaines propriétés de mesures dans un groupe de mesures.  
  
|Propriété|Définition|  
|--------------|----------------|  
|`AggregationPrefix`|S'applique au stockage ROLAP. Affecte un préfixe commun aux vues indexées dans SQL Server. Ce préfixe est utilisé pour stocker les agrégations des partitions associées au groupe de mesures.|  
|`DataAggregation`|Cette propriété est réservée à un usage ultérieur et n'a aucun effet actuellement. Il est donc recommandé de ne pas modifier ce paramètre.|  
|`Description`|Vous pouvez utiliser cette propriété pour décrire le groupe de mesures.|  
|`ErrorConfiguration`|Paramètres de gestion des erreurs configurables pour gérer les clés dupliquées, les clés inconnues, les clés NULL, les limitations des erreurs, l'action lors de la détection d'erreurs, le fichier journal des erreurs. Consultez [Configuration d’erreur pour le traitement des cubes, des partitions et des dimensions &#40;SSAS – Multidimensionnel&#41;](error-configuration-for-cube-partition-and-dimension-processing.md).|  
|`EstimatedRows`|Spécifie le nombre estimé de lignes dans la table de faits.|  
|`EstimatedSize`|Spécifie la taille estimée (en octets) du groupe de mesures.|  
|`ID`|Spécifie l'identificateur de l'objet.|  
|`IgnoreUnrelatedDimensions`|Détermine si les dimensions non liées sont ignorées lorsque des membres de dimensions qui ne sont pas associées au groupe de mesures sont inclus dans une requête. Le paramètre par défaut est `True`.|  
|`Name`|Spécifie le nom de la mesure. Cette propriété est en lecture seule.|  
|`ProactiveCaching`|Paramètres de gestion des erreurs configurables pour gérer les clés dupliquées, les clés inconnues, les clés NULL, les limitations des erreurs, l'action lors de la détection d'erreurs, le fichier journal des erreurs.|  
|`ProcessingMode`|Indique si l'indexation et l'agrégation doivent avoir lieu lors du traitement ou après celui-ci. Les options sont Regular et LazyAggregations. L'option LazyAggregations permet d'exécuter l'agrégation en tant que tâche en arrière-plan.|  
|`ProcessingPriority`|Détermine la priorité de traitement du cube pendant les opérations d'arrière-plan, telles que les agrégations et les indexations différées (Lazy). La valeur par défaut est **0**.|  
|`StorageLocation`|Emplacement de stockage du système de fichiers du groupe de mesures. Si aucun emplacement n'est spécifié, l'emplacement est hérité du cube contenant le groupe de mesures.|  
|`StorageMode`|Mode de stockage pour le groupe de mesures. Les valeurs possibles sont MOLAP, ROLAP ou HOLAP.|  
|`Type`|Spécifie le type du groupe de mesures.|  
  
  
