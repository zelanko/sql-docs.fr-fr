---
title: '&lt;requête de source de données&gt; | Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fdd0a3091440295e393d969f1b8161b83fb58d95
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38063959"
---
# <a name="ltsource-data-querygt"></a>&lt;requête de source de données&gt;
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Pour former un modèle d’exploration de données et créer des prédictions à partir d’un modèle d’exploration de données, vous devez accéder aux données qui sont externes à la [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données. Vous utilisez le \<requête de source de données > clause dans Extensions DMX (Data Mining) pour définir ces données externes. Le [INSERT INTO &#40;DMX&#41;](../dmx/insert-into-dmx.md), [SELECT FROM &#60;modèle&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md), et [SELECT FROM NATURAL PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md) toutes les instructions utilisent  **\<requête de source de données >**.  
  
## <a name="query-types"></a>Types de requêtes  
 Les trois méthodes les plus courantes pour spécifier les données source sont :  
  
 [OPENQUERY &AMP;#40;DMX&AMP;#41;](../dmx/source-data-query-openquery.md)  
 Cette instruction interroge des données qui sont externes à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], en utilisant une source de données existante.  
  
 Bien que **OPENQUERY** est similaire à celui à **OPENROWSET**, **OPENQUERY** présente les avantages suivants :  
  
-   Une requête DMX est beaucoup plus facile à écrire avec **OPENQUERY**. Au lieu de créer une nouvelle chaîne de connexion à chaque fois que vous écrivez une requête, vous pouvez bénéficier de la chaîne de connexion existante dans la source de données. L'objet de source de données peut également contrôler l'accès aux données pour les utilisateurs individuels.  
  
-   L'administrateur a davantage de contrôle sur le mode d'accès aux données sur le serveur. Par exemple, il peut déterminer les fournisseurs à charger dans le serveur et les données externes accessibles.  
  
 [OPENROWSET &AMP;#40;DMX&AMP;#41;](../dmx/source-data-query-openrowset.md)  
 Cette instruction interroge des données qui sont externes à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], en utilisant une source de données existante.  
  
 [FORME &AMP;#40;DMX&AMP;#41;](../dmx/source-data-query-shape.md)  
 Cette instruction interroge plusieurs sources de données pour créer une table imbriquée. À l’aide de **forme**, vous pouvez combiner des données provenant de plusieurs sources dans une table hiérarchique unique. Ceci vous permet de bénéficier de la capacité de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] d'imbriquer les tables en incorporant une table dans une autre.  
  
 Pour spécifier les données source, vous pouvez également utiliser les options suivantes :   
  
-   Une instruction DMX valide  
  
-   Une instruction MDX (Multidimensional Expressions) valide  
  
-   Une table qui retourne une procédure stockée  
  
-   Un ensemble de lignes XMLA (XML for Analysis)  
  
-   Un paramètre d'ensemble de lignes  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; les instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Tables imbriquées &#40;Analysis Services - Exploration de données&#41;](../analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)  
  
  
