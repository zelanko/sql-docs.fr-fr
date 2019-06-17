---
title: Colonnes du modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], mining model columns
- columns [data mining]
- REGRESSOR column
- columns [data mining], modeling flags
- modeling flags [data mining]
- MODEL_EXISTENCE_ONLY column
- usage property [data mining]
ms.assetid: fab47643-5bfd-424e-a0f7-69e665db6bab
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f99a2dc218543faa4d862fa7520c1618ec307ba7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66083705"
---
# <a name="mining-model-columns"></a>Colonnes d'un modèle d'exploration de données
  Un modèle d'exploration de données applique un algorithme de modèle d'exploration de données aux données qui sont représentées par une structure d'exploration de données. Comme la structure d'exploration de données, le modèle d'exploration de données contient des colonnes. Un modèle d'exploration de données est inclus dans la structure d'exploration de données et hérite de toutes les valeurs des propriétés définies par la structure d'exploration de données. Le modèle peut utiliser toutes les colonnes que contient la structure d'exploration de données ou un sous-ensemble de ces colonnes.  
  
 Vous pouvez définir deux éléments d'informations supplémentaires sur une colonne de modèle d'exploration de données : l'utilisation et les indicateurs de modélisation.  
  
-   **Utilisation** est une propriété qui définit la façon dont le modèle utilise la colonne. Les colonnes peuvent être utilisées en tant que colonnes d'entrée, que colonnes clés ou que colonnes prédictibles.  
  
-   Les**indicateurs de modélisation** fournissent à l’algorithme des informations supplémentaires sur les données définies dans la table de cas, de sorte que l’algorithme puisse générer un modèle plus précis. Vous pouvez définir des indicateurs de modélisation par programmation en utilisant le langage DMX (Data Mining Extensions) ou le **Concepteur d’exploration de données** dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 La liste ci-dessous décrit les indicateurs de modélisation que vous pouvez définir sur une colonne de modèle d'exploration de données.  
  
 `MODEL_EXISTENCE_ONLY`  
 Indique que la présence de l'attribut est plus importante que les valeurs incluses dans la colonne de l'attribut. Par exemple, considérez une table de cas qui contient une liste d'articles associés à un client particulier. Les données de la table incluent le type de produit, l'ID et le coût de chaque élément. Pour la modélisation, le fait que le client ait acheté un article particulier peut être plus important que le coût de l'article. Dans ce cas, la colonne de coût doit recevoir l'indicateur `MODEL_EXISTENCE_ONLY`.  
  
 `REGRESSOR`  
 Indique que l'algorithme peut utiliser la colonne spécifiée dans la formule de régression des algorithmes de régression. Cet indicateur est pris en charge par les algorithmes MDT ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees) et MTS ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series).  
  
 Pour plus d’informations sur la définition de la propriété Utilisation et la définition des indicateurs de modélisation par programmation à l’aide du langage DMX, consultez [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx). Pour plus d’informations sur la définition de la propriété Utilisation et la définition des indicateurs de modélisation dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], consultez [Déplacement d’objets d’exploration de données](moving-data-mining-objects.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Structures d’exploration de données &#40;Analysis Services – Exploration de données&#41;](mining-structures-analysis-services-data-mining.md)   
 [Modifier les propriétés d'un modèle d'exploration de données](change-the-properties-of-a-mining-model.md)   
 [Exclure une colonne d'un modèle d'exploration de données](exclude-a-column-from-a-mining-model.md)   
 [Colonnes de structure d’exploration de données](mining-structure-columns.md)  
  
  
