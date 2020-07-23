---
title: Référence des instructions DMX (Data Mining Extensions) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1b8fe4c8a83eaf56aea70abc810e7dc45f35eebb
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971769"
---
# <a name="data-mining-extensions-dmx-statements"></a>Instructions DMX (Data Mining Extensions)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  L’utilisation des modèles d’exploration de données dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] implique les tâches principales suivantes :  
  
-   Création de structures et de modèles d'exploration de données  
  
-   Traitement des structures et des modèles d'exploration de données  
  
-   Suppression de structures ou de modèles d'exploration de données  
  
-   Copie de modèles d'exploration de données  
  
-   Exploration des modèles d’exploration de données  
  
-   Prévision dans des modèles d'exploration de données  
  
 Vous pouvez utiliser les instructions DMX (Data Mining Extensions) pour exécuter chacune de ces tâches par programme.  
  
 Création de structures et de modèles d'exploration de données  
 Utilisez l’instruction [Create Mining structure &#40;DMX&#41;](../dmx/create-mining-structure-dmx.md) pour ajouter une nouvelle structure d’exploration de données à une base de données. Vous pouvez ensuite utiliser l’instruction [ALTER Mining STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md) pour ajouter des modèles d’exploration de données à la structure d’exploration de données.  
  
 Utilisez l’instruction [Create MINING MODEL &#40;DMX&#41;](../dmx/create-mining-model-dmx.md) pour créer un nouveau modèle d’exploration de données et une structure d’exploration de données associée.  
  
 Traitement des structures et des modèles d'exploration de données  
 Utilisez l’instruction [INSERT INTO &#40;DMX&#41;](../dmx/insert-into-dmx.md) pour traiter une structure d’exploration de données et un modèle d’exploration de données.  
  
 Suppression de structures ou de modèles d'exploration de données  
 Utilisez l’instruction [DELETE &#40;DMX&#41;](../dmx/delete-dmx.md) pour supprimer toutes les données formées d’un modèle ou d’une structure d’exploration de données. Utilisez les instructions [Drop Mining STRUCTURE &#40;dmx&#41;](../dmx/drop-mining-structure-dmx.md) ou [drop MINING MODEL &#40;DMX&#41;](../dmx/drop-mining-model-dmx.md) pour supprimer complètement une structure ou un modèle d’exploration de données d’une base de données.  
  
 Copie de modèles d'exploration de données  
 Utilisez l’instruction [SELECT INTO &#40;DMX&#41;](../dmx/select-into-dmx.md) pour copier la structure d’un modèle d’exploration de données existant dans un nouveau modèle d’exploration de données et pour effectuer l’apprentissage du nouveau modèle avec les mêmes données.  
  
 Exploration des modèles d’exploration de données  
 Utilisez l’instruction [SELECT &#40;DMX&#41;](../dmx/select-dmx.md) pour parcourir les informations que l’algorithme d’exploration de données calcule et stocke dans le modèle d’exploration de données lors de l’apprentissage du modèle. À l’instar de [!INCLUDE[tsql](../includes/tsql-md.md)] , vous pouvez utiliser plusieurs clauses avec l’instruction SELECT pour étendre sa puissance. Ces clauses incluent [distinct de \<model> ](../dmx/select-distinct-from-model-dmx.md), [from \<model> . CAS](../dmx/select-from-model-cases-dmx.md), [de \<model> . SAMPLE_CASES](../dmx/select-from-model-sample-cases-dmx.md), [à partir de \<model> . CONTENU](../dmx/select-from-model-content-dmx.md) et [à partir de \<model> . DIMENSION_CONTENT](../dmx/select-from-model-dimension-content-dmx.md).  
  
 Prévision dans des modèles d'exploration de données  
 Utilisez la clause [PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md) de l’instruction SELECT pour créer des prédictions basées sur un modèle d’exploration de données existant.  
  
 Vous pouvez également importer et exporter des modèles à l’aide des instructions [import &#40;dmx&#41;](../dmx/import-dmx.md) et [export &#40;DMX&#41;](../dmx/export-dmx.md) .  
  
 Ces tâches sont classées en deux catégories, les instructions de définition de données et les instructions de manipulation de données, décrites dans les tableaux ci-dessous.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Instructions de définition de données DMX &#40;Data Mining Extensions&#41;](../dmx/dmx-statements-data-definition.md)|Fait partie du langage de définition de données (DDL). utilisé pour définir un nouveau modèle d'exploration de données (y compris l'apprentissage) ou pour supprimer un modèle d'exploration de données existant d'une base de données.|  
|[Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)|Fait partie du langage de manipulation de données (DML). Est utilisé pour utiliser les modèles d'exploration de données existants, notamment pour explorer un modèle ou pour créer des prévisions.|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Conventions de syntaxe du&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;les éléments de la syntaxe DMX&#41;](../dmx/data-mining-extensions-dmx-syntax-elements.md)  
  
  
