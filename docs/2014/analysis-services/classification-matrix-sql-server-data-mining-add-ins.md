---
title: Matrice de classification (compléments d’exploration de données SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- classification matrix
- confusion table
- mining models, testing
ms.assetid: d6f620f4-39af-4714-9628-28ce3c361fca
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 78f8581839b6b4bdd761c25a1a207e942ae37f62
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66087968"
---
# <a name="classification-matrix-sql-server-data-mining-add-ins"></a>Matrice de classification (Compléments d'exploration de données SQL Server)
  ![Bouton Matrice de classification, ruban Exploration de données](media/dmc-cmatrix.gif "Bouton Matrice de classification, ruban Exploration de données")  
  
 Utilisez la matrice de classification pour évaluer la précision d'un modèle de prédiction. Pour créer une matrice de classification, vous exécutez un jeu de données de test dans le modèle, et l'outil matrice de classification compare les valeurs réelles du jeu de test par rapport aux prédictions effectuées par le modèle. Consultez la matrice pour indiquer, d'un seul coup d'œil, la fréquence à laquelle le modèle est correct, et la fréquence à laquelle les prédictions sont incorrectes.  
  
 Dans ces compléments, utilisez l’Assistant **matrice de classification** pour sélectionner un modèle, spécifier les données de test, puis générer une matrice de résultats.  
  
## <a name="how-to-read-a-classification-matrix"></a>Procédure : lire une matrice de classification  
 Supposons que votre objectif est de concevoir un programme de fidélisation des clients, puis d’affecter des clients aux catégories appropriées, afin que vous puissiez leur fournir le niveau d’incentives approprié. Vous avez mis en œuvre trois niveaux pour le programme de récompense (bronze, Silver et Gold) et nous l’avons donné aux clients dans le cas d’une phase d’essai. Vous avez également conçu un modèle qui analyse les clients et prédit les catégories correctes. Maintenant vous allez utiliser la matrice de classification sur les données de test pour déterminer la qualité du modèle est prédire l'offre correcte pour tous les clients.  
  
 La table de la matrice de classification vous indique combien de clients sont affectés à chaque catégorie selon le modèle, puis compare le résultat au nombre de clients qui se sont réellement inscrits pour chaque niveau de récompense.  
  
||Bronze (réel)|Or (réel)|Argent (réel)|  
|-|-----------------------|---------------------|-----------------------|  
|Bronze|**94,45%**|15,18%|1,70 %|  
|Or|2,72 %|**84,82%**|0.00%|  
|Argent|1,84%|0.00%|**93,80%**|  
|*Correct*|*95,45%*|*84,82%*|*98,30%*|  
|*Mal classés*|*4,55%*|*15,18%*|*1,70%*|  
  
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
  
     Dans la page **Sélectionner les colonnes à prédire** , vous pouvez également spécifier si vous souhaitez afficher le nombre de valeurs incorrectes et incorrectes, ou afficher un pourcentage.  
  
4.  Sur la page Sélectionner les données source, indiquez si vous utilisez des données de test externes, ou les données de test enregistrées avec le modèle.  
  
5.  Si vous utilisez des données de test externes, vous devez mapper le modèle aux colonnes d’entrée dans la page **spécifier la relation** de l’Assistant.  
  
     Si vous utilisez le jeu de données de test incorporé, le mappage est effectué automatiquement  
  
6.  Cliquez sur **Terminer** pour exécuter des prédictions sur le modèle et générer la matrice de classification.  
  
     L'Assistant crée un rapport contenant la matrice de classification ainsi que d'autres détails à propos de l'analyse. Ce rapport est enregistré en tant que table dans Excel, avec un résumé au-dessus du rapport qui indique combien de cas ont été prédits correctement et le nombre de prédictions incorrectes.  
  
### <a name="requirements"></a>Conditions requises  
  
-   Pour créer une matrice de classification, vous devez avoir accès à un modèle existant qui prend en charge les mesures de précision. Les modèles de prévision et les modèles d'association ne peuvent pas être mesurés à l'aide de cet outil.  
  
-   Le modèle que vous mesurez doit prédire une valeur discrète ou qui a déjà été discrétisée.  
  
-   Si vous n’avez pas utilisé l’option pour enregistrer un jeu de test avec votre structure ou modèle, vous devez obtenir un jeu de données d’entrée qui a essentiellement le même nombre de colonnes, avec des types de données correspondants, comme ceux utilisés dans le modèle.  
  
-   Le modèle d'exploration de données et les nouvelles données que vous utilisez à des fins de test doivent contenir au moins une colonne qui peut être prédite, et les colonnes doivent contenir le même type de données.  
  
### <a name="known-issues"></a>Problèmes connus  
 Dans SQL Server 2012 et SQL Server 2014, la possibilité de mapper le jeu de données de test interne au modèle ne fonctionne pas dans l’outil **matrice de classification** . Toutefois, vous pouvez spécifier un jeu de données externe, puis sélectionner le jeu d'apprentissage comme entrée pour déterminer l'erreur dans le jeu de données d'origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Validation des modèles et utilisation de modèles pour la prédiction &#40;compléments d’exploration de données pour Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)   
 [Explorez les &#40;de données SQL Server les compléments d’exploration de données&#41;](explore-data-sql-server-data-mining-add-ins.md)   
 [Détecter les catégories &#40;les outils d’analyse de table pour Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
  
  
