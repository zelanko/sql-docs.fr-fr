---
title: Types de données (exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data types [data mining]
- columns [data mining], data types
- data mining [Analysis Services], data types
ms.assetid: 4af5b7db-790b-459c-b2b4-00f0cf6b5ce4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 77a0c6f2f0100e7e0c0e73ee70bc8705135d259f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62722811"
---
# <a name="data-types-data-mining"></a>Types de données (Exploration de données)
  Quand vous créez un modèle d’exploration de données ou une structure d’exploration de données dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous devez définir les types de données pour chacune des colonnes dans la structure d’exploration de données. Le type de données indique au moteur d'exploration de données si les données dans la source de données sont numériques ou de texte, et comment elles doivent être traitées. Par exemple, si vos données sources contiennent des données numériques, vous pouvez spécifier si les nombres doivent être traités en tant qu'entiers ou en utilisant des décimales.  
  
 Chaque type de données prend en charge un ou plusieurs types de contenu. En définissant le type de contenu, vous pouvez personnaliser la façon dont les données de la colonne sont traitées ou calculées dans le modèle d'exploration de données.  
  
 Par exemple, si une colonne contient des données numériques, vous pouvez choisir de les gérer en tant que type de données numérique ou en tant que type de données texte. Si vous choisissez le type de données numérique, vous pouvez définir plusieurs types de contenu différents : vous pouvez discrétiser les nombres ou les gérer en tant que valeurs continues. Pour obtenir la liste de tous les types de contenu, consultez [Types de contenu &#40;exploration de données&#41;](content-types-data-mining.md).  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les types de données suivants pour les colonnes de structure d’exploration de données :  
  
|Type de données|Types de contenu pris en charge|  
|---------------|-----------------------------|  
|`Text`|Cyclique, Discret, Discrétisé, Séquence clé, Ordonné, Séquence|  
|`Long`|Continu, Cyclique, Discret, Discrétisé, Clé, Séquence clé, Temps clé, Ordonné, Séquence, Temps<br /><br /> Classifié|  
|`Boolean`|Cyclique, Discret, Ordonné|  
|`Double`|Continu, Cyclique, Discret, Discrétisé, Clé, Séquence clé, Temps clé, Ordonné, Séquence, Temps<br /><br /> Classifié|  
|`Date`|Continu, Cyclique, Discret, Discrétisé, Clé, Séquence clé, Temps clé, Ordonné|  
  
> [!NOTE]  
>  Les types de contenu Temps et Séquence sont uniquement pris en charge par les algorithmes de tiers. Les types de contenu Cyclique et Ordonné sont pris en charge, mais la plupart des algorithmes les considèrent comme des valeurs discrètes et n'effectuent pas de traitement spécial.  
  
## <a name="specifying-a-data-type"></a>Spécification d'un type de données  
 Si vous créez le modèle d'exploration de données directement à l'aide d'extensions DMX (Data Mining Extensions), vous pouvez définir le type de données pour chaque colonne lors de la définition du modèle, et Analysis Services crée en même temps la structure d'exploration de données correspondante avec les types de données spécifiés. Si vous créez le modèle d'exploration de données ou la structure d'exploration de données à l'aide d'un Assistant, Analysis Services suggère un type de données ; vous pouvez également sélectionner un type de données dans une liste.  
  
## <a name="changing-a-data-type"></a>Modification d'un type de données  
 Si vous modifiez le type de données d'une colonne, vous devez toujours retraiter la structure d'exploration de données et tous modèles d'exploration de données basés sur cette structure. Si vous modifiez le type de données, il est possible que cette colonne ne puisse plus être utilisée dans un modèle particulier. Dans ce cas, Analysis Services génère une erreur lorsque vous retraitez le modèle, ou traite le modèle mais en ignorant cette colonne particulière.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de contenu &#40;Exploration de données&#41;](content-types-data-mining.md)   
 [Types de contenu &#40;DMX&#41;](/sql/dmx/content-types-dmx)   
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Structures d’exploration de données &#40;Analysis Services – Exploration de données&#41;](mining-structures-analysis-services-data-mining.md)   
 [Types de données &#40;DMX&#41;](/sql/dmx/data-types-dmx)   
 [Colonnes d'un modèle d'exploration de données](mining-model-columns.md)   
 [Colonnes de structure d'exploration de données](mining-structure-columns.md)  
  
  
