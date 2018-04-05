---
title: Configurer les propriétés du groupe de mesures | Documents Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [Analysis Services], measure groups
ms.assetid: fa66bdb6-60b8-413c-ac2a-00e4d09f60a2
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f7cf2328a6f93ed1c7fe17034af1b42b53baaa39
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="configure-measure-group-properties"></a>Configurer les propriétés d'un groupe de mesures
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Groupes de mesures ont des propriétés qui vous permettent de définir la manière dont des groupes de mesures.  
  
## <a name="measure-group-properties"></a>Propriétés des groupes de mesures  
 Les propriétés d'un groupe de mesures déterminent les comportements de l'ensemble du groupe de mesures et définissent les comportements par défaut des nouveaux objets de certaines propriétés de mesures dans un groupe de mesures.  
  
|Propriété|Définition|  
|--------------|----------------|  
|**AggregationPrefix**|S'applique au stockage ROLAP. Affecte un préfixe commun aux vues indexées dans SQL Server. Ce préfixe est utilisé pour stocker les agrégations des partitions associées au groupe de mesures.|  
|**DataAggregation**|Cette propriété est réservée à un usage ultérieur et n'a aucun effet actuellement. Il est donc recommandé de ne pas modifier ce paramètre.|  
|**Description**|Vous pouvez utiliser cette propriété pour décrire le groupe de mesures.|  
|**ErrorConfiguration**|Paramètres de gestion des erreurs configurables pour gérer les clés dupliquées, les clés inconnues, les clés NULL, les limitations des erreurs, l'action lors de la détection d'erreurs, le fichier journal des erreurs. Consultez [Configuration d’erreur pour le traitement des cubes, des partitions et des dimensions &#40;SSAS – Multidimensionnel&#41;](../../analysis-services/multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md).|  
|**EstimatedRows**|Spécifie le nombre estimé de lignes dans la table de faits.|  
|**EstimatedSize**|Spécifie la taille estimée (en octets) du groupe de mesures.|  
|**ID**|Spécifie l'identificateur de l'objet.|  
|**IgnoreUnrelatedDimensions**|Détermine si les dimensions non liées sont ignorées lorsque des membres de dimensions qui ne sont pas associées au groupe de mesures sont inclus dans une requête. La valeur par défaut est **True**.|  
|**Nom**|Spécifie le nom de la mesure. Cette propriété est en lecture seule.|  
|**ProactiveCaching**|Paramètres de gestion des erreurs configurables pour gérer les clés dupliquées, les clés inconnues, les clés NULL, les limitations des erreurs, l'action lors de la détection d'erreurs, le fichier journal des erreurs.|  
|**ProcessingMode**|Indique si l'indexation et l'agrégation doivent avoir lieu lors du traitement ou après celui-ci. Les options sont Regular et LazyAggregations. L'option LazyAggregations permet d'exécuter l'agrégation en tant que tâche en arrière-plan.|  
|**ProcessingPriority**|Détermine la priorité de traitement du cube pendant les opérations d'arrière-plan, telles que les agrégations et les indexations différées (Lazy). La valeur par défaut est **0**.|  
|**StorageLocation**|Emplacement de stockage du système de fichiers du groupe de mesures. Si aucun emplacement n'est spécifié, l'emplacement est hérité du cube contenant le groupe de mesures.|  
|**StorageMode**|Mode de stockage pour le groupe de mesures. Les valeurs possibles sont MOLAP, ROLAP ou HOLAP.|  
|**Type**|Spécifie le type du groupe de mesures.|  
  
  
