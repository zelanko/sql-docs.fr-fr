---
title: '&lt;requête de données source &gt; | Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7117409372fcbcbc6ef3662a2355f063b2a99d98
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970277"
---
# <a name="ltsource-data-querygt"></a>&lt;requête de données sources&gt;
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Pour effectuer l’apprentissage d’un modèle d’exploration de données et créer des prédictions à partir d’un modèle d’exploration de données, vous devez accéder aux données qui sont externes à la [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données. Vous utilisez la \<source data query> clause dans les extensions DMX (Data Mining Extensions) pour définir ces données externes. L' [insertion dans &#40;&#41;DMX ](../dmx/insert-into-dmx.md), [Select from &#60;Model&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md), et [Select from Natural PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md) All use **\<source data query>** .  
  
## <a name="query-types"></a>Types de requêtes  
 Les trois méthodes les plus courantes pour spécifier les données source sont :  
  
 [&#41;&#40;DMX OPENQUERY](../dmx/source-data-query-openquery.md)  
 Cette instruction interroge des données qui sont externes à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], en utilisant une source de données existante.  
  
 Alors que **OPENQUERY** est similaire dans la fonction à **OpenRowset**, **OPENQUERY** présente les avantages suivants :  
  
-   Une requête DMX est beaucoup plus facile à écrire avec **OPENQUERY**. Au lieu de créer une nouvelle chaîne de connexion à chaque fois que vous écrivez une requête, vous pouvez bénéficier de la chaîne de connexion existante dans la source de données. L'objet de source de données peut également contrôler l'accès aux données pour les utilisateurs individuels.  
  
-   L'administrateur a davantage de contrôle sur le mode d'accès aux données sur le serveur. Par exemple, il peut déterminer les fournisseurs à charger dans le serveur et les données externes accessibles.  
  
 [OPENROWSET &#40;&#41;DMX](../dmx/source-data-query-openrowset.md)  
 Cette instruction interroge des données qui sont externes à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], en utilisant une source de données existante.  
  
 [FORME &#40;&#41;DMX](../dmx/source-data-query-shape.md)  
 Cette instruction interroge plusieurs sources de données pour créer une table imbriquée. À l’aide de **Shape**, vous pouvez combiner des données de plusieurs sources en une seule table hiérarchique. Ceci vous permet de bénéficier de la capacité de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] d'imbriquer les tables en incorporant une table dans une autre.  
  
 Pour spécifier les données source, vous pouvez également utiliser les options suivantes :   
  
-   Une instruction DMX valide  
  
-   Une instruction MDX (Multidimensional Expressions) valide  
  
-   Une table qui retourne une procédure stockée  
  
-   Un ensemble de lignes XMLA (XML for Analysis)  
  
-   Un paramètre d'ensemble de lignes  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Tables imbriquées &#40;Analysis Services d’exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/nested-tables-analysis-services-data-mining)  
  
  
