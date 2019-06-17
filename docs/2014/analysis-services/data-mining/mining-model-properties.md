---
title: Propriétés du modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- data mining [Analysis Services], properties
- columns [data mining], properties
- Data Mining Designer
- properties [data mining]
ms.assetid: c5194619-8b31-42be-a95f-585711462945
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 030ebd318b310b2c7ca4f85d1f736d168a7adda8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66083511"
---
# <a name="mining-model-properties"></a>Propriétés du modèle d'exploration de données
  Les modèles d'exploration de données ont les types de propriétés suivantes :  
  
-   les propriétés qui sont héritées de la structure d'exploration de données et qui définissent le type de données et le type de contenu des données utilisées par le modèle ;  
  
-   les propriétés qui sont liées à l'algorithme utilisé pour créer le modèle d'exploration de données, y compris tout paramètre client ;  
  
-   les propriétés qui définissent un filtre sur le modèle utilisé pour l'apprentissage du modèle.  
  
 Les propriétés d'un modèle d'exploration de données sont initialement définies lors de la création du modèle ; toutefois, vous pouvez modifier la plupart des propriétés ultérieurement, notamment les paramètres d'algorithme, les filtres et les propriétés d'utilisation des colonnes. Vous modifiez ces propriétés à l’aide de l’onglet **Modèles d’exploration de données** du Concepteur d’exploration de données, ou en utilisant AMO ou XMLA.  
  
 Chaque fois que vous modifiez une propriété d'un modèle, vous devez traiter de nouveau le modèle pour que les modifications soient visibles dans le modèle. Un retraitement est requis même si la modification implique seulement des métadonnées, telles que l'ajout d'un alias ou d'une description de colonne.  
  
## <a name="properties-of-models"></a>Propriétés des modèles  
 Le tableau suivant décrit les propriétés spécifiques aux modèles d'exploration de données. De plus, il existe des propriétés que vous pouvez définir sur des colonnes individuelles dans l'exploration de données  
  
|Propriété|Description|  
|--------------|-----------------|  
|**Algorithm**|Définit le type d'algorithme pour le modèle d'exploration de données.|  
|**AlgorithmParameters**|Définit les valeurs pour les paramètres d'algorithme disponibles pour chaque type d'algorithme.|  
|**Filter**|Définit un filtre qui s'applique aux données utilisées pour former et tester le modèle d'exploration de données. La définition de filtre est stockée avec le modèle et peut être utilisée facultativement lorsque vous créez des requêtes de prédiction ou lorsque vous testez la précision du modèle.<br /><br /> Le filtre de modèle n'est pas facultatif lors de la formation du modèle.|  
|**Nom**|Définit le nom du modèle d'exploration de données.|  
|**AllowDrillThrough**|Spécifie si l'extraction est activée sur le modèle d'exploration de données.|  
  
## <a name="properties-of-model-columns"></a>Propriétés des colonnes d'un modèle  
 Vous pouvez définir les propriétés ci-dessous, spécifiques à l'exploration de données, pour chaque colonne dans un modèle d'exploration de données. Vous pouvez affecter à ces propriétés une valeur différente pour chaque modèle d'exploration de données d'une structure d'exploration de données.  
  
|Propriété|Description|  
|--------------|-----------------|  
|**Description**|Décrit la fonction de la colonne d'exploration des données.|  
|**Nom**|Définit le nom de la colonne du modèle d'exploration de données. Vous pouvez taper un nouveau nom, pour fournir un alias pour la colonne du modèle d'exploration de données.|  
|**ModelingFlags**|Définit tous les indicateurs spécifiques des algorithmes pour la colonne.|  
|**SourceColumnID**|Indique le nom de la colonne de structure d'exploration de données sur laquelle la colonne du modèle est basée.<br /><br /> Cette propriété est en lecture seule.|  
|**Usage**|Définit comment la colonne sera utilisée par le modèle d'exploration de données.|  
  
## <a name="see-also"></a>Voir aussi  
 [Colonnes d'un modèle d'exploration de données](mining-model-columns.md)   
 [Structures d’exploration &#40;Analysis Services – Exploration de données&#41;](mining-structures-analysis-services-data-mining.md)   
 [Tâches du modèle d'exploration de données et procédures](mining-model-tasks-and-how-tos.md)   
 [Modifier les propriétés d'un modèle d'exploration de données](change-the-properties-of-a-mining-model.md)   
 [Outils d'exploration de données](data-mining-tools.md)   
 [Créer une structure d'exploration de données relationnelle](create-a-relational-mining-structure.md)   
 [Créer un alias pour une colonne du modèle](create-an-alias-for-a-model-column.md)  
  
  
