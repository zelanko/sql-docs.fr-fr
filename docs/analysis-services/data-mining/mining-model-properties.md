---
title: Propriétés du modèle d’exploration de données | Documents Microsoft
ms.custom: ''
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- data mining [Analysis Services], properties
- columns [data mining], properties
- Data Mining Designer
- properties [data mining]
ms.assetid: c5194619-8b31-42be-a95f-585711462945
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b29794e3c41f218f1bd117fd68ad5a978066b150
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="mining-model-properties"></a>Propriétés du modèle d'exploration de données
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
|**Filtre**|Définit un filtre qui s'applique aux données utilisées pour former et tester le modèle d'exploration de données. La définition de filtre est stockée avec le modèle et peut être utilisée facultativement lorsque vous créez des requêtes de prédiction ou lorsque vous testez la précision du modèle.<br /><br /> Le filtre de modèle n'est pas facultatif lors de la formation du modèle.|  
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
|**Utilisation**|Définit comment la colonne sera utilisée par le modèle d'exploration de données.|  
  
## <a name="see-also"></a>Voir aussi  
 [Colonnes du modèle d’exploration de données](../../analysis-services/data-mining/mining-model-columns.md)   
 [Les Structures d’exploration de données & #40 ; Analysis Services - Exploration de données & #41 ;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Tâches liées aux modèles d’exploration de données et procédures](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Modifier les propriétés d’un modèle d’exploration de données](../../analysis-services/data-mining/change-the-properties-of-a-mining-model.md)   
 [Outils d’exploration de données](../../analysis-services/data-mining/data-mining-tools.md)   
 [Créer une Structure d’exploration de données relationnelles](../../analysis-services/data-mining/create-a-relational-mining-structure.md)   
 [Créer un Alias pour une colonne de modèle](../../analysis-services/data-mining/create-an-alias-for-a-model-column.md)  
  
  
