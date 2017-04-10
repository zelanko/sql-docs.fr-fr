---
title: "Colonnes d&#39;un mod&#232;le d&#39;exploration de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "colonnes [exploration de données], colonnes du modèle d’exploration de données"
  - "colonnes [exploration de données]"
  - "REGRESSOR (colonne)"
  - "colonnes [exploration de données], indicateurs de modélisation"
  - "indicateurs de modélisation [exploration de données]"
  - "MODEL_EXISTENCE_ONLY (colonne)"
  - "propriété d'utilisation [exploration de données]"
ms.assetid: fab47643-5bfd-424e-a0f7-69e665db6bab
caps.latest.revision: 38
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 38
---
# Colonnes d&#39;un mod&#232;le d&#39;exploration de donn&#233;es
  Un modèle d'exploration de données applique un algorithme de modèle d'exploration de données aux données qui sont représentées par une structure d'exploration de données. Comme la structure d'exploration de données, le modèle d'exploration de données contient des colonnes. Un modèle d'exploration de données est inclus dans la structure d'exploration de données et hérite de toutes les valeurs des propriétés définies par la structure d'exploration de données. Le modèle peut utiliser toutes les colonnes que contient la structure d'exploration de données ou un sous-ensemble de ces colonnes.  
  
 Vous pouvez définir deux éléments d'informations supplémentaires sur une colonne de modèle d'exploration de données : l'utilisation et les indicateurs de modélisation.  
  
-   **Utilisation** est une propriété qui définit la façon dont le modèle utilise la colonne. Les colonnes peuvent être utilisées en tant que colonnes d'entrée, que colonnes clés ou que colonnes prédictibles.  
  
-   Les **indicateurs de modélisation** fournissent à l’algorithme des informations supplémentaires sur les données définies dans la table de cas, de sorte que l’algorithme puisse générer un modèle plus précis. Vous pouvez définir des indicateurs de modélisation par programmation en utilisant le langage DMX (Data Mining Extensions) ou le **Concepteur d’exploration de données** dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 La liste ci-dessous décrit les indicateurs de modélisation que vous pouvez définir sur une colonne de modèle d'exploration de données.  
  
 **MODEL_EXISTENCE_ONLY**  
 Indique que la présence de l'attribut est plus importante que les valeurs incluses dans la colonne de l'attribut. Par exemple, considérez une table de cas qui contient une liste d'articles associés à un client particulier. Les données de la table incluent le type de produit, l'ID et le coût de chaque élément. Pour la modélisation, le fait que le client ait acheté un article particulier peut être plus important que le coût de l'article. Dans ce cas, la colonne des coûts doit être marquée comme **MODEL_EXISTENCE_ONLY**.  
  
 **REGRESSOR**  
 Indique que l'algorithme peut utiliser la colonne spécifiée dans la formule de régression des algorithmes de régression. Cet indicateur est pris en charge par les algorithmes MDT ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees) et MTS ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series).  
  
 Pour plus d’informations sur la définition de la propriété Utilisation et la définition des indicateurs de modélisation par programmation à l’aide du langage DMX, consultez [CREATE MINING MODEL &#40;DMX&#41;](../../dmx/create-mining-model-dmx.md). Pour plus d’informations sur la définition de la propriété Utilisation et la définition des indicateurs de modélisation dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], consultez [Déplacement d’objets d’exploration de données](../../analysis-services/data-mining/moving-data-mining-objects.md).  
  
## Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services – Exploration de données&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Structures d’exploration de données &#40;Analysis Services – Exploration de données&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Modifier les propriétés d'un modèle d'exploration de données](../../analysis-services/data-mining/change-the-properties-of-a-mining-model.md)   
 [Exclure une colonne d'un modèle d'exploration de données](../../analysis-services/data-mining/exclude-a-column-from-a-mining-model.md)   
 [Colonnes de structure d'exploration de données](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  