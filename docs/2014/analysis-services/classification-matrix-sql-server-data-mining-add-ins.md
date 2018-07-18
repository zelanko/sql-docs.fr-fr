---
title: Matrice de classification (SQL Server Data Mining Add-ins) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- classification matrix
- confusion table
- mining models, testing
ms.assetid: d6f620f4-39af-4714-9628-28ce3c361fca
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3d87c2d37ed69e2cc3f3e224ddf1a489b34425b8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249639"
---
# <a name="classification-matrix-sql-server-data-mining-add-ins"></a>Matrice de classification (Compléments d'exploration de données SQL Server)
  ![Bouton matrice de classification, ruban Exploration de données](media/dmc-cmatrix.gif "bouton matrice de Classification, ruban Exploration de données")  
  
 Utilisez la matrice de classification pour évaluer la précision d'un modèle de prédiction. Pour créer une matrice de classification, vous exécutez un jeu de données de test dans le modèle, et l'outil matrice de classification compare les valeurs réelles du jeu de test par rapport aux prédictions effectuées par le modèle. Consultez la matrice pour indiquer, d'un seul coup d'œil, la fréquence à laquelle le modèle est correct, et la fréquence à laquelle les prédictions sont incorrectes.  
  
 Dans ces compléments, utilisez le **matrice de Classification** Assistant pour sélectionner un modèle, spécifiez les données de test et puis générer une matrice de résultats.  
  
## <a name="how-to-read-a-classification-matrix"></a>Procédure : lire une matrice de classification  
 Supposons que votre objectif est de créer un programme de fidélisation des clients et d'affecter les clients aux catégories appropriées, afin que vous puissiez leur fournir un niveau approprié d'incitation. Vous avez implémenté trois niveaux pour le programme de récompense (bronze, argent et or) et les avez divulgué aux clients dans une phase de test. Vous avez également conçu un modèle qui analyse les clients et prédit les catégories correctes. Maintenant vous allez utiliser la matrice de classification sur les données de test pour déterminer la qualité du modèle est prédire l'offre correcte pour tous les clients.  
  
 La table de la matrice de classification vous indique combien de clients sont affectés à chaque catégorie selon le modèle, puis compare le résultat au nombre de clients qui se sont réellement inscrits pour chaque niveau de récompense.  
  
||Bronze (réel)|Or (réel)|Argent (réel)|  
|-|-----------------------|---------------------|-----------------------|  
|Bronze|**94.45 %**|15.18 %|1.70 %|  
|Or|2.72 %|**84.82 %**|0.00%|  
|Argent|1.84 %|0.00%|**93.80 %**|  
|*Corriger*|*95.45 %*|*84.82 %*|*98.30 %*|  
|*Mal classées*|*4.55 %*|*15.18 %*|*1.70 %*|  
  
-   Chaque colonne indique les valeurs réelles dans le jeu de données de test.  
  
-   Chaque ligne affiche les valeurs prédites.  
  
-   Les valeurs en gras, disposées en diagonale entre le coin supérieur gauche et le coin inférieur droit de la matrice, correspondent au nombre correct dans le modèle.  
  
-   Toutes les autres valeurs en dehors de la diagonale représentent des erreurs. Certaines erreurs sont des faux positifs, c'est-à-dire que le modèle a prédit que le client va rejoindre le programme au niveau Or, ce qui est incorrect.  Selon votre domaine, les faux positifs s'avèrent très coûteux.  
  
     D'autres sont des faux négatifs, ce qui signifie que le modèle a prédit que le client ne serait pas intéressé bien qu'il ait rejoint le programme. Là encore, selon le domaine à problème, le coût de l'occasion perdue peut être significatif.  
  
## <a name="using-the-classification-matrix-wizard"></a>Utilisation de l'Assistant Matrice de classification  
  
1.  Sélectionnez le modèle d'exploration de données sur lequel vous voulez baser les prédictions.  
  
2.  Sélectionnez une source de nouvelles données de test, ou utilisez les données de test enregistrées avec la structure.  
  
3.  Sélectionnez la colonne pour laquelle vous souhaitez évaluer la précision. Vous pouvez choisir une seule colonne lorsque vous créez une matrice, mais la colonne peut avoir plusieurs valeurs.  
  
     Conseil : Il peut être difficile d'interpréter une matrice de classification si votre colonne prédictible possède plusieurs colonnes à comparer.  
  
     Dans le **sélectionner des colonnes à prédire** page, vous pouvez également spécifier si vous souhaitez afficher le nombre de valeurs correctes et incorrectes, ou afficher un pourcentage.  
  
4.  Sur la page Sélectionner les données source, indiquez si vous utilisez des données de test externes, ou les données de test enregistrées avec le modèle.  
  
5.  Si vous utilisez des données de test externes, vous devez mapper le modèle aux colonnes d’entrée sur le **spécifier une relation** page de l’Assistant.  
  
     Si vous utilisez le jeu de données de test incorporé, le mappage est effectué automatiquement  
  
6.  Cliquez sur **Terminer** pour exécuter des prédictions sur le modèle et de générer la matrice de classification.  
  
     L'Assistant crée un rapport contenant la matrice de classification ainsi que d'autres détails à propos de l'analyse. Ce rapport est enregistré en tant que table dans Excel, avec un résumé au-dessus du rapport qui indique combien de cas ont été prédits correctement et le nombre de prédictions incorrectes.  
  
### <a name="requirements"></a>Spécifications  
  
-   Pour créer une matrice de classification, vous devez avoir accès à un modèle existant qui prend en charge les mesures de précision. Les modèles de prévision et les modèles d'association ne peuvent pas être mesurés à l'aide de cet outil.  
  
-   Le modèle que vous mesurez doit prédire une valeur discrète ou qui a déjà été discrétisée.  
  
-   Si vous n'utilisez pas l'option permettant d'enregistrer un jeu de test avec votre structure ou modèle, vous devez obtenir un jeu de données d'entrée qui a le même nombre de colonnes, avec les types de données correspondants, comme ceux utilisés dans le modèle.  
  
-   Le modèle d'exploration de données et les nouvelles données que vous utilisez à des fins de test doivent contenir au moins une colonne qui peut être prédite, et les colonnes doivent contenir le même type de données.  
  
### <a name="known-issues"></a>Problèmes connus  
 Dans SQL Server 2012 et SQL Server 2014, la possibilité de mapper le jeu de données de test interne au modèle ne fonctionne pas le **matrice de Classification** outil. Toutefois, vous pouvez spécifier un jeu de données externe, puis sélectionner le jeu d'apprentissage comme entrée pour déterminer l'erreur dans le jeu de données d'origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Validation des modèles et à l’aide de modèles pour la prédiction &#40;les données des compléments d’exploration de données pour Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)   
 [Explorer les données &#40;compléments d’exploration de données SQL Server&#41;](explore-data-sql-server-data-mining-add-ins.md)   
 [Détecter les catégories &#40;outils d’analyse de Table pour Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
  
  
