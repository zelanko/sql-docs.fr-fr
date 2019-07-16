---
title: Data Mining Extensions (DMX) de référence des instructions | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7a7a9c18599d13c4db510793a1d75c85bbb7a829
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070861"
---
# <a name="data-mining-extensions-dmx-statements"></a>Instructions DMX (Data Mining Extensions)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Utilisation de données des modèles d’exploration de données [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] implique les principales tâches suivantes :  
  
-   Création de structures et de modèles d'exploration de données  
  
-   Traitement des structures et des modèles d'exploration de données  
  
-   Suppression de structures ou de modèles d'exploration de données  
  
-   Copie de modèles d'exploration de données  
  
-   Exploration des modèles d’exploration de données  
  
-   Prévision dans des modèles d'exploration de données  
  
 Vous pouvez utiliser les instructions DMX (Data Mining Extensions) pour exécuter chacune de ces tâches par programme.  
  
 Création de structures et de modèles d'exploration de données  
 Utilisez le [CREATE MINING STRUCTURE &#40;DMX&#41; ](../dmx/create-mining-structure-dmx.md) instruction pour ajouter une nouvelle structure d’exploration de données à une base de données. Vous pouvez ensuite utiliser le [ALTER MINING STRUCTURE &#40;DMX&#41; ](../dmx/alter-mining-structure-dmx.md) instruction pour ajouter des modèles d’exploration de données à la structure d’exploration de données.  
  
 Utilisez le [CREATE MINING MODEL &#40;DMX&#41; ](../dmx/create-mining-model-dmx.md) instruction pour créer la structure d’exploration de données associé et de modèle d’exploration de données.  
  
 Traitement des structures et des modèles d'exploration de données  
 Utilisez le [INSERT INTO &#40;DMX&#41; ](../dmx/insert-into-dmx.md) instruction pour traiter une structure d’exploration de données et le modèle d’exploration.  
  
 Suppression de structures ou de modèles d'exploration de données  
 Utilisez le [supprimer &#40;DMX&#41; ](../dmx/delete-dmx.md) instruction pour supprimer toutes les données d’apprentissage à partir d’un modèle d’exploration de données ou la structure d’exploration. Utilisez le [DROP MINING STRUCTURE &#40;DMX&#41; ](../dmx/drop-mining-structure-dmx.md) ou [DROP MINING MODEL &#40;DMX&#41; ](../dmx/drop-mining-model-dmx.md) instructions pour supprimer complètement un modèle ou une structure d’exploration de données à partir d’une base de données.  
  
 Copie de modèles d'exploration de données  
 Utilisez le [SELECT INTO &#40;DMX&#41; ](../dmx/select-into-dmx.md) instruction pour copier la structure d’un modèle d’exploration de données existant dans un nouveau modèle d’exploration de données et pour former le modèle de nouveau avec les mêmes données.  
  
 Exploration des modèles d’exploration de données  
 Utilisez le [sélectionnez &#40;DMX&#41; ](../dmx/select-dmx.md) instruction pour parcourir les informations que l’algorithme d’exploration de données calcule et stocke dans le modèle d’exploration de données au cours de l’apprentissage du modèle. Comme avec [!INCLUDE[tsql](../includes/tsql-md.md)], vous pouvez utiliser plusieurs clauses avec l’instruction SELECT, d’étendre sa puissance. Ces clauses incluent [DISTINCT FROM \<modèle >](../dmx/select-distinct-from-model-dmx.md), [FROM \<modèle >. CAS](../dmx/select-from-model-cases-dmx.md), [FROM \<modèle >. SAMPLE_CASES](../dmx/select-from-model-sample-cases-dmx.md), [FROM \<modèle >. CONTENU](../dmx/select-from-model-content-dmx.md) et [FROM \<modèle >. DIMENSION_CONTENT](../dmx/select-from-model-dimension-content-dmx.md).  
  
 Prévision dans des modèles d'exploration de données  
 Utilisez le [PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md) clause de l’instruction SELECT pour créer des prédictions basées sur un modèle d’exploration de données existant.  
  
 Vous pouvez également importer et exporter des modèles à l’aide de la [importer &#40;DMX&#41; ](../dmx/import-dmx.md) et [exporter &#40;DMX&#41; ](../dmx/export-dmx.md) instructions.  
  
 Ces tâches sont classées en deux catégories, les instructions de définition de données et les instructions de manipulation de données, décrites dans les tableaux ci-dessous.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Instructions de définition de données DMX &#40;Data Mining Extensions&#41;](../dmx/dmx-statements-data-definition.md)|Fait partie du langage de définition de données (DDL). utilisé pour définir un nouveau modèle d'exploration de données (y compris l'apprentissage) ou pour supprimer un modèle d'exploration de données existant d'une base de données.|  
|[Data Mining Extensions &#40;DMX&#41; les instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)|Fait partie du langage de manipulation de données (DML). Est utilisé pour utiliser les modèles d'exploration de données existants, notamment pour explorer un modèle ou pour créer des prévisions.|  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; Conventions de syntaxe](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;DMX&#41; éléments de syntaxe](../dmx/data-mining-extensions-dmx-syntax-elements.md)  
  
  
