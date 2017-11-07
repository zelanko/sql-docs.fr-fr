---
title: "Colonnes de Structure d’exploration de données | Documents Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], structure
- mining structures [Analysis Services], columns
- data sources [Analysis Services], mining structure columns
- columns [data mining], mining structure columns
ms.assetid: 20cbf433-70d1-4b61-a462-41a8435b27b4
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0bf7ffc6f8531385ef9100b3c104db887c2fb565
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="mining-structure-columns"></a>Colonnes de structure d'exploration de données
  Vous définissez les colonnes d'une structure d'exploration de données lorsque vous créez la structure d'exploration de données, en choisissant des colonnes de données externes, puis en spécifiant comment les données doivent être utilisées pour la modélisation. Par conséquent, les colonnes de structure d'exploration de données sont plus que des copies des données d'une source de données : elles définissent comment les données de la source doivent être utilisées par le modèle d'exploration de données. Vous pouvez affecter des propriétés qui déterminent comment les données sont discrétisées, propriétés qui décrivent comment les valeurs de données sont distribuées  
  
 Les colonnes de structure d'exploration de données sont conçues pour être flexibles et extensibles, étant donné que chacun des algorithmes que vous utilisez pour générer un modèle d'exploration de données peut utiliser différentes colonnes de la structure pour interpréter les données. Plutôt que d'avoir un jeu de données pour chaque modèle, vous pouvez utiliser une structure d'exploration de données unique et ses colonnes pour personnaliser les données de chaque modèle.  
  
## <a name="defining-mining-structure-columns"></a>Définition des colonnes de structure d'exploration de données  
 Les types de données et les types de contenu de base définissant les colonnes de la structure sont issus de la source de données que vous utilisez pour créer la structure. Vous pouvez modifier ces paramètres au sein de la structure d'exploration de données et vous pouvez également définir des indicateurs de modélisation et configurer la distribution pour les colonnes continues.  
  
 La définition d'une colonne de structure d'exploration de données doit contenir les informations suivantes :  
  
-   **ID**: nom unique de la colonne, souvent identique au nom. Vous ne pouvez pas le modifier après avoir créé la structure d'exploration de données, tandis que le nom peut être modifié.  
  
-   **Nom**: nom ou alias de la colonne.  
  
-   **Contenu**: énumération qui décrit si les données sont discrètes ou continues.  
  
-   **Type**: énumération qui indique le type de données général.  
  
-   **Distribution**: énumération qui décrit la distribution attendue des valeurs. Une distribution est incluse si la colonne est continue.  
  
-   **Indicateurs de modélisation**: énumération qui indique comment gérer des valeurs manquantes, etc. Les indicateurs de modélisation peuvent également être définis sur le modèle d'exploration de données, mais les indicateurs de modèle sont différents des indicateurs utilisés sur les colonnes de structure.  
  
-   **Liaisons**: propriétés qui spécifient les données sources.  
  
 Les algorithmes de tiers peuvent également inclure des propriétés personnalisées qui peuvent être définies sur la colonne de structure d'exploration de données.  
  
 Pour plus d’informations sur la structure et le modèle d’exploration de données, consultez [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).  
  
## <a name="related-content"></a>Contenu connexe  
 Consultez les rubriques suivantes pour plus d'informations sur la définition et l'utilisation des colonnes de structure d'exploration de données.  
  
|Rubrique|Liens|  
|-----------|-----------|  
|Décrit les types de données que vous pouvez utiliser pour définir une colonne de structure d'exploration de données.|[Types de données &#40;exploration de données&#41;](../../analysis-services/data-mining/data-types-data-mining.md)|  
|Décrit les types de contenu qui sont disponibles pour chaque type de données contenu dans une colonne de structure d'exploration de données. Les types de contenu dépendent du type de données. Le type de contenu est affecté au niveau du modèle et détermine comment les données de la colonne sont utilisées par le modèle.|[Types de contenu &#40;exploration de données&#41;](../../analysis-services/data-mining/content-types-data-mining.md)|  
|Présente le concept de tables imbriquées, et explique comment les tables imbriquées peuvent être ajoutées à la source de données comme colonnes de structure d'exploration de données.|[Colonnes classifiées &#40;exploration de données&#41;](../../analysis-services/data-mining/classified-columns-data-mining.md)|  
|Répertorie et décrit les propriétés de distribution que vous pouvez définir sur une colonne de structure d'exploration de données pour spécifier la distribution attendue des valeurs dans la colonne.|[Distributions de colonnes &#40;exploration de données&#41;](../../analysis-services/data-mining/column-distributions-data-mining.md)|  
|Décrit le concept de discrétisation (parfois appelée *placement dans un conteneur*) et décrit les méthodes qu’Analysis Services fournit pour la discrétisation des données numériques continues.|[Méthodes de discrétisation &#40;exploration de données&#41;](../../analysis-services/data-mining/discretization-methods-data-mining.md)|  
|Décrit les indicateurs de modélisation que vous pouvez définir sur une colonne de structure d'exploration de données.|[Indicateurs de modélisation &#40;exploration de données&#41;](../../analysis-services/data-mining/modeling-flags-data-mining.md)|  
|Décrit les colonnes classifiées, qui sont un type spécial de colonne que vous pouvez utiliser pour associer une colonne de structure d'exploration de données à une autre.|[Colonnes classifiées &#40;exploration de données&#41;](../../analysis-services/data-mining/classified-columns-data-mining.md)|  
|Apprenez à ajouter et modifier des colonnes de structure d'exploration de données.|[Tâches de la structure d'exploration de données et procédures](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Colonnes d'un modèle d'exploration de données](../../analysis-services/data-mining/mining-model-columns.md)  
  
  

