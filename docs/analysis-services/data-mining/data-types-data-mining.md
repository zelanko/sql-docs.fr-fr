---
title: "Types de données (exploration de données) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [data mining]
- columns [data mining], data types
- data mining [Analysis Services], data types
ms.assetid: 4af5b7db-790b-459c-b2b4-00f0cf6b5ce4
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7e5d09435546cf0605bb7b70a685021612fd2f9b
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="data-types-data-mining"></a>Types de données (Exploration de données)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Quand vous créez un modèle d’exploration de données ou une structure d’exploration de données dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous devez définir les types de données pour chacune des colonnes dans la structure d’exploration de données. Le type de données indique au moteur d’analyse si les données dans la source de données sont numériques ou de texte, et comment elles doivent être traitées. Par exemple, si vos données sources contiennent des données numériques, vous pouvez spécifier si les nombres doivent être traités en tant qu'entiers ou en utilisant des décimales.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les types de données suivants pour les colonnes de structure d’exploration de données :  
  
|Type de données|Types de contenu pris en charge|  
|---------------|-----------------------------|  
|**Texte**|Cyclique, Discret, Discrétisé, Séquence clé, Ordonné, Séquence|  
|**Long**|Continu, Cyclique, Discret, Discrétisé, Clé, Séquence clé, Temps clé, Ordonné, Séquence, Temps<br /><br /> Classifié|  
|**Booléen**|Cyclique, Discret, Ordonné|  
|**Double**|Continu, Cyclique, Discret, Discrétisé, Clé, Séquence clé, Temps clé, Ordonné, Séquence, Temps<br /><br /> Classifié|  
|**Date**|Continu, Cyclique, Discret, Discrétisé, Clé, Séquence clé, Temps clé, Ordonné|  
  
> [!NOTE]  
>  Les types de contenu Temps et Séquence sont uniquement pris en charge par les algorithmes de tiers. Les types de contenu Cyclique et Ordonné sont pris en charge, mais la plupart des algorithmes les considèrent comme des valeurs discrètes et n'effectuent pas de traitement spécial.  
  
 Le tableau indique également les *types de contenu* pris en charge pour chaque type de données.  
  
 Le type de contenu est spécifique à l’exploration de données et vous permet de personnaliser la façon dont ces données sont traitées ou calculées dans le modèle d’exploration de données. Par exemple, même si votre colonne contient des nombres, vous devrez peut-être les modéliser comme des valeurs discrètes. Si la colonne contient des nombres, vous pouvez également spécifier qu’ils doivent être placés dans un conteneur, ou discrétisés, ou indiquer que le modèle doit les gérer en tant que valeurs continues. Par conséquent, le type de contenu peut avoir un effet considérable sur le modèle. Pour obtenir la liste de tous les types de contenu, consultez [Types de contenu &#40;exploration de données&#41;](../../analysis-services/data-mining/content-types-data-mining.md).  
  
> [!NOTE]  
>  Dans les autres systèmes d’apprentissage automatique, vous pouvez rencontrer les termes *données nominales*, *facteurs* ou *catégories*, *données ordinales*, ou *données séquence*. En général, ils correspondent aux types de contenu. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le type de données ne spécifie que le type de valeur pour le stockage, et non son utilisation dans le modèle.  
  
## <a name="specifying-a-data-type"></a>Spécification d'un type de données  
 Si vous créez le modèle d'exploration de données directement à l'aide d'extensions DMX (Data Mining Extensions), vous pouvez définir le type de données pour chaque colonne lors de la définition du modèle, et Analysis Services crée en même temps la structure d'exploration de données correspondante avec les types de données spécifiés. Si vous créez le modèle d'exploration de données ou la structure d'exploration de données à l'aide d'un Assistant, Analysis Services suggère un type de données ; vous pouvez également sélectionner un type de données dans une liste.  
  
## <a name="changing-a-data-type"></a>Modification d'un type de données  
 Si vous modifiez le type de données d'une colonne, vous devez toujours retraiter la structure d'exploration de données et tous modèles d'exploration de données basés sur cette structure. Si vous modifiez le type de données, il est possible que cette colonne ne puisse plus être utilisée dans un modèle particulier. Dans ce cas, Analysis Services génère une erreur lorsque vous retraitez le modèle, ou traite le modèle mais en ignorant cette colonne particulière.  
  
## <a name="see-also"></a>Voir aussi  
 [Contenu des Types de &#40; exploration de données &#41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [Contenu des Types de &#40; DMX &#41;](../../dmx/content-types-dmx.md)   
 [Algorithmes d’exploration de données &#40; Analysis Services - Exploration de données &#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Les Structures d’exploration de données &#40; Analysis Services - Exploration de données &#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Types de données &#40; DMX &#41;](../../dmx/data-types-dmx.md)   
 [Colonnes du modèle d’exploration de données](../../analysis-services/data-mining/mining-model-columns.md)   
 [Colonnes de structure d'exploration de données](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
