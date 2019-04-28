---
title: Modifier les propriétés d’un modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- properties [data mining]
ms.assetid: aefaeb7f-d174-48d1-a188-0987a3b1196b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2533de57dd2baee8297cd0f277c4538d16fbc16a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62689044"
---
# <a name="change-the-properties-of-a-mining-model"></a>Modifier les propriétés d'un modèle d'exploration de données
  Certaines propriétés du modèle d'exploration de données s'appliquent au modèle dans son ensemble, et d'autres propriétés de modèle s'appliquent à des colonnes individuelles. La propriété `Drillthrough`, qui spécifie si les données de cas doivent être disponibles pour l'interrogation, et la propriété `Description` sont des exemples de propriétés qui s'appliquent à l'ensemble du modèle. Les propriétés qui s'appliquent à la colonne incluent `Usage` et `ModelingFlags`, qui contrôlent l'utilisation des données de la colonne dans le modèle.  
  
 Les propriétés de modèle suivantes ont des éditeurs avancés que vous pouvez utiliser pour créer des expressions ou pour configurer les propriétés de modèle complexes. Les propriétés suivantes fournissent :  
  
-   `Filter` Propriété : Ouvre le [Data Set filtre or Model filtre Dialog Box](../data-set-filter-or-model-filter-dialog-box.md).  
  
-   `AlgorithmParameters` Propriété : Ouvre le [boîte dialogue Paramètres d’algorithme &#40;affichage des modèles d’exploration de&#41;](../algorithm-parameters-dialog-box-mining-models-view.md).  
  
 Pour plus d’informations sur la définition des propriétés dans un modèle d’exploration, consultez [Colonnes de modèle d’exploration de données](mining-model-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-model"></a>Pour modifier les propriétés d'un modèle d'exploration de données  
  
1.  Sous l’onglet **Modèles d’exploration de données** du Concepteur d’exploration de données, cliquez avec le bouton droit sur l’en-tête de colonne contenant le nom du modèle d’exploration de données ou sur la ligne de la grille qui contient le nom de l’algorithme d’exploration de données, puis sélectionnez **Propriétés**.  
  
2.  Dans la fenêtre **Propriétés** à droite de l’écran, mettez en surbrillance la valeur qui correspond à la propriété à modifier, puis entrez la nouvelle valeur.  
  
     La nouvelle valeur est appliquée lorsque vous sélectionnez un élément différent dans le concepteur.  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a>Pour modifier les propriétés d'une colonne de modèle d'exploration de données  
  
1.  Sous l’onglet **Modèles d’exploration de données** du Concepteur d’exploration de données, cliquez avec le bouton droit sur la cellule de la grille à l’intersection de la colonne de la structure d’exploration de données et du modèle d’exploration de données, puis sélectionnez **Propriétés**.  
  
2.  Dans la fenêtre **Propriétés** à droite de l’écran, mettez en surbrillance la valeur qui correspond à la propriété à modifier, puis entrez la nouvelle valeur.  
  
    > [!NOTE]  
    >  Si l’utilisation des colonnes est définie sur `Ignore`, le **propriétés** fenêtre pour la colonne est vide.  
  
     La nouvelle valeur est appliquée lorsque vous sélectionnez un élément différent dans le concepteur.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et procédures des modèles d’exploration de données](mining-model-tasks-and-how-tos.md)  
  
  
