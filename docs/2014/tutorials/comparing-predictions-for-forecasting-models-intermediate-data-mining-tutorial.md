---
title: Comparaison de prédictions pour prévoir des modèles (didacticiel d’exploration de données intermédiaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ead8a1fe-60d8-4017-8fb8-6fe32168e46d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 26cc445d3bad5c628628353d5c0c84ffa4755e97
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63066332"
---
# <a name="comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial"></a>Comparaison de prédictions pour les modèles de prévision (Didacticiel intermédiaire sur l'exploration de données) 
  Dans les étapes précédentes de ce didacticiel, vous avez créé plusieurs modèles de série chronologique :  
  
-   Les prédictions de chaque combinaison de région et modèle basées uniquement sur les données pour chaque modèle et région.  
  
-   Les prédictions de chaque région, basées sur les données mises à jour.  
  
-   Les prédictions de tous les modèles sur une base internationale, à partir des données cumulées.  
  
-   Les prédictions du modèle M200 dans la région North America, basées sur le modèle cumulé.  
  
 Pour résumer les fonctionnalités des prédictions de série chronologique, vous allez examiner les modifications pour voir comment l'utilisation des options d'extension ou de remplacement des données ont affecté les résultats de prédiction.  
  
 [EXTEND_MODEL_CASES](#bkmk_EXTEND)  
  
 [REPLACE_MODEL_CASES](#bkmk_REPLACE)  
  
##  <a name="bkmk_EXTEND"></a> Comparaison des résultats d’origine avec les résultats après l’ajout de données  
 Examinons les données pour juste la gamme de produits M200 dans la région Pacific, pour voir comment la mise à jour le modèle avec de nouvelles données affecte les résultats. Souvenez-vous que la série de données d'origine s'est terminée en juin 2004 et nous avons obtenu de nouvelles données pour juillet, août et septembre.  
  
-   La première colonne affiche les nouvelles données ajoutées.  
  
-   La deuxième colonne affiche la prédiction pour juillet et les mois suivants en fonction des séries de données d'origine.  
  
-   La troisième colonne affiche la prédiction en fonction des données étendues.  
  
|**M200 Pacific**|Données réelles de ventes mises à jour|Prédiction préalable à l'ajout des données|Prédiction étendue|  
|----------------------|-----------------------------|------------------------------------|-------------------------|  
|7-25-2008|**65**|32|**65**|  
|8-25-2008|**54**|37|**54**|  
|9-25-2008|**61**|32|**61**|  
|10-25-2008|Pas de données|36|32|  
|11-25-2008|Pas de données|31|41|  
|12-25-2008|Pas de données|34|32|  
  
 Vous noterez que les prévisions qui utilisent les données étendues (en gras) répètent exactement les points de données réels. Cette répétition est la procédure normale. Tant qu'il existe des points de données réels à utiliser, la requête de prédiction renvoie les valeurs réelles et sort de nouvelles valeurs de prédiction uniquement après que les nouveaux points de données réels ont tous été utilisés.  
  
 En général, l'algorithme pondère les modifications apportées aux nouvelles données de manière plus importante que la pondération des données issues du début des données de modèle. Toutefois, dans ce cas, les nouveaux chiffres de vente représentent une augmentation de uniquement 20-30 pour cent par rapport à la période précédente, il y a donc une augmentation minimale des projections de ventes, après quoi les prévisions de vente baissent à nouveau, plus fidèles à la tendance des mois précédant les nouvelles données.  
  
##  <a name="bkmk_REPLACE"></a> Comparaison des résultats d’origine et la prédiction croisée  
 Souvenez-vous que le modèle d'exploration de données d'origine révélait des différences importantes entres les régions et entre les gammes de produits. Par exemple, les ventes pour le modèle M200 étaient très élevées, tandis que les ventes pour le modèle T1000 étaient relativement basses dans toutes les régions. En outre, certaines séries ne contenaient pas beaucoup de données. La série est déséquilibrée, ce qui signifie qu’ils n’avaient pas le même point de départ.  
  
 ![Série de prédire la quantité M200 et T1000](../../2014/tutorials/media/6series-defaultforecasting.gif "M200 et T1000 la quantité de prédiction de série")  
  
 Ainsi, comment les prédictions ont-elles changé lorsque vous avez effectué vos projections en fonction du modèle général, qui était basé sur les ventes internationales, plutôt que sur les jeux de données d'origine ? Pour vérifier que vous n'avez perdu aucune information ou biaisé les prédictions, vous pouvez enregistrer les résultats dans une table, joindre la table des prédictions à la table des données historiques, puis représenter graphiquement les deux jeux de données historiques et de prédictions.  
  
 Le diagramme suivant est basé sur une seule gamme de produit, le M200. Le graphique compare les prédictions du modèle d'exploration de données initial aux prédictions utilisant le modèle d'exploration de données cumulées.  
  
 ![Graphique Excel comparant des prédictions](../../2014/tutorials/media/m200-predictions-compared.gif "graphique Excel comparant des prédictions")  
  
 D'après ce diagramme, vous pouvez constater que le modèle d'exploration de données cumulées conserve les tendances et la gamme générales des valeurs tout en réduisant les fluctuations dans les séries de données.  
  
## <a name="conclusion"></a>Conclusion  
 Vous avez appris à créer et personnaliser un modèle de série chronologique qui peut être utilisé pour les prévisions.  
  
 Vous avez appris à mettre à jour vos modèles de série chronologique sans avoir à les retraiter, en ajoutant de nouvelles données et en créant des prédictions à l'aide du paramètre, EXTEND_MODEL_CASES.  
  
 Vous avez appris à créer des modèles qui peuvent être utilisés pour la prédiction croisée, à l'aide du paramètre REPLACE_MODEL_CASES et en appliquant le modèle à une autre série de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’exploration de données intermédiaire &#40;Analysis Services - Exploration de données&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Exemples de requêtes de modèle de séries chronologiques](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)  
  
  
