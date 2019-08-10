---
title: '&lt;requête&gt; de données source | Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e523d33da502a971b950e33ec0bd935149ed26f7
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892342"
---
# <a name="ltsource-data-querygt"></a>&lt;requête de données sources&gt;
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Pour effectuer l’apprentissage d’un modèle d’exploration de données et créer des prédictions à partir d’un modèle d’exploration de [!INCLUDE[msCoName](../includes/msconame-md.md)] données, vous devez accéder aux données qui sont externes à la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données. Vous utilisez la \<clause de > de requête de données source dans les extensions DMX (Data Mining Extensions) pour définir ces données externes. Le modèle d' [insertion dans &#40;&#41;DMX](../dmx/insert-into-dmx.md), [Select from &#60;Model&#62; Prediction &#40;Join&#41;DMX](../dmx/select-from-model-prediction-join-dmx.md)et [Select from Natural PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md) States use **\<source Data Query >** .  
  
## <a name="query-types"></a>Types de requêtes  
 Les trois méthodes les plus courantes pour spécifier les données source sont :  
  
 [OPENQUERY &#40;DMX&#41;](../dmx/source-data-query-openquery.md)  
 Cette instruction interroge des données qui sont externes à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], en utilisant une source de données existante.  
  
 Alors que **OPENQUERY** est similaire dans la fonction à **OpenRowset**, **OPENQUERY** présente les avantages suivants:  
  
-   Une requête DMX est beaucoup plus facile à écrire avec **OPENQUERY**. Au lieu de créer une nouvelle chaîne de connexion à chaque fois que vous écrivez une requête, vous pouvez bénéficier de la chaîne de connexion existante dans la source de données. L'objet de source de données peut également contrôler l'accès aux données pour les utilisateurs individuels.  
  
-   L'administrateur a davantage de contrôle sur le mode d'accès aux données sur le serveur. Par exemple, il peut déterminer les fournisseurs à charger dans le serveur et les données externes accessibles.  
  
 [À &#40;OPENROWSET DMX&#41;](../dmx/source-data-query-openrowset.md)  
 Cette instruction interroge des données qui sont externes à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], en utilisant une source de données existante.  
  
 [FORME &#40;DMX&#41;](../dmx/source-data-query-shape.md)  
 Cette instruction interroge plusieurs sources de données pour créer une table imbriquée. À l’aide de **Shape**, vous pouvez combiner des données de plusieurs sources en une seule table hiérarchique. Ceci vous permet de bénéficier de la capacité de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] d'imbriquer les tables en incorporant une table dans une autre.  
  
 Pour spécifier les données source, vous pouvez également utiliser les options suivantes :  
  
-   Une instruction DMX valide  
  
-   Une instruction MDX (Multidimensional Expressions) valide  
  
-   Une table qui retourne une procédure stockée  
  
-   Un ensemble de lignes XMLA (XML for Analysis)  
  
-   Un paramètre d'ensemble de lignes  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de manipulation &#40;de&#41; données DMX des extensions d’exploration de données](../dmx/dmx-statements-data-manipulation.md)   
 [Référence des instructions &#40;DMX&#41; Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Tables &#40;imbriquées Analysis Services-exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/nested-tables-analysis-services-data-mining)  
  
  
