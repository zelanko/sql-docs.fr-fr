---
title: Mesures dans le rapport de validation croisée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- root mean square error [data mining]
- cross-validation [data mining]
- mean absolute error [data mining]
- log score [data mining]
- likelihood [data mining]
ms.assetid: a07b1665-7f72-4266-82a4-43a91ae2571d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 30f8daab91172863ba18c6b75529063555b61afc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66084157"
---
# <a name="measures-in-the-cross-validation-report"></a>Mesures dans le rapport de validation croisée
  Pendant la validation croisée, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] divise les données d'une structure d'exploration de données en plusieurs sections croisées, puis teste de manière itérative la structure et tous les modèles d'exploration de données associés. D'après cette analyse, il produit un jeu de mesures de précision standard pour la structure et chaque modèle.  
  
 Le rapport contient certaines informations de base sur le nombre de replis dans les données et le volume de données dans chaque repli, ainsi qu'un ensemble de mesures générales qui décrivent la distribution des données. En comparant les mesures générales de chaque section croisée, vous pouvez évaluer la fiabilité de la structure ou du modèle.  
  
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] affiche également un ensemble de mesures détaillées pour les modèles d'exploration de données. Ces mesures dépendent du type de modèle et du type d'attribut qui est analysé (discret ou continu, par exemple).  
  
 Cette section fournit une liste des mesures contenues dans le rapport de **validation croisée** , ainsi que leur signification. Pour plus d’informations sur la façon dont chaque mesure est calculée, consultez [Formules de validation croisée](cross-validation-formulas.md).  
  
## <a name="list-of-measures-in-the-cross-validation-report"></a>Liste de mesures dans le rapport de validation croisée  
 Le tableau suivant répertorie les mesures qui apparaissent dans le rapport de validation croisée. Les mesures sont regroupées par *type de test*, fourni dans la colonne gauche du tableau suivant. La colonne de droite répertorie le nom de la mesure tel qu'il apparaît dans le rapport, et fournit une brève explication de sa signification.  
  
|type de test|Mesures et descriptions|  
|---------------|-------------------------------|  
|Clustering|Mesures qui s’appliquent aux modèles de clustering :<br /><br /> **Probabilité**de la casse : cette mesure indique habituellement la probabilité qu’un cas appartienne à un cluster particulier. <br />                      Pour la validation croisée, les scores sont additionnés, puis divisés par le nombre de cas ; ici, le score est une vraisemblance moyenne de cas.|  
|classification ;|Mesures qui s’appliquent aux modèles de classification :<br /><br /> **Vrai positif**/<br />                      **Vrai**/ ****/ **positif**faux positif faux négatif : nombre de lignes ou de valeurs dans la partition où l’État prédit correspond à l’État cible, et la probabilité de prédiction est supérieure au seuil spécifié. Les cas qui ont des valeurs manquantes pour l’attribut cible sont exclus, ce qui signifie que le nombre de toutes les valeurs peut ne pas être ajouté|  
||**Réussite/échec**: nombre de lignes ou de valeurs dans la partition où l’État prédit correspond à l’État cible, et où la valeur de probabilité de prédiction est supérieure à 0.|  
|Vraisemblance|Les mesures de vraisemblance s’appliquent à plusieurs types de modèles :<br /><br /> **Élévation**: rapport entre la probabilité de prédiction réelle et la probabilité marginale dans les cas de test. Les lignes qui ont des valeurs manquantes pour l'attribut cible sont exclues. Cette mesure affiche généralement le degré d'amélioration de la probabilité des résultats cibles lorsque le modèle est utilisé.<br /><br /> **Erreur quadratique moyenne**: racine carrée de l’erreur moyenne pour tous les cas de partition, divisée par le nombre de cas dans la partition, en excluant les lignes qui ont des valeurs manquantes pour l’attribut cible. RMSE est un estimateur souvent utilisé pour les modèles prévisionnels. Le score calcule la moyenne des résiduels pour chaque cas et génère un seul indicateur de l'erreur modèle.<br /><br /> **Score du journal**: logarithme de la probabilité réelle pour chaque cas, additionnées, puis divisée par le nombre de lignes dans le jeu de données d’entrée, en excluant les lignes qui ont des valeurs manquantes pour l’attribut cible. Étant donné que la probabilité est représentée comme une fraction décimale, les scores du journal sont toujours un nombre négatif. Un nombre plus proche de 0 représente un meilleur score. Alors que les scores bruts peuvent avoir des distributions très irrégulières ou asymétriques, un score de journal est semblable à un pourcentage.|  
|Estimation|Mesures qui s’appliquent uniquement aux modèles d’estimation, qui prédisent un attribut numérique continu :<br /><br /> **Erreur quadratique moyenne**: erreur moyenne lorsque la valeur prédite est comparée à la valeur réelle. RMSE est un estimateur souvent utilisé pour les modèles prévisionnels. Le score calcule la moyenne des résiduels pour chaque cas et génère un seul indicateur de l'erreur modèle.<br /><br /> **Erreur d’absolue moyenne**: erreur moyenne lorsque les valeurs prédites sont comparées aux valeurs réelles, calculées comme moyenne de la somme absolue des erreurs. L'erreur absolue moyenne est utile pour comprendre la justesse des prédictions par rapport aux valeurs réelles. Un faible score signifie que les prédictions étaient plus précises.<br /><br /> **Score du journal**: logarithme de la probabilité réelle pour chaque cas, additionnées, puis divisée par le nombre de lignes dans le jeu de données d’entrée, en excluant les lignes qui ont des valeurs manquantes pour l’attribut cible. Étant donné que la probabilité est représentée comme une fraction décimale, les scores du journal sont toujours un nombre négatif. Un nombre plus proche de 0 représente un meilleur score. Alors que les scores bruts peuvent avoir des distributions très irrégulières ou asymétriques, un score de journal est semblable à un pourcentage.|  
|Agrégats|Les mesures d’agrégat fournissent une indication de la variance dans les résultats pour chaque partition :<br /><br /> **Moyenne : moyenne**des valeurs de partition pour une mesure particulière.<br /><br /> **Écart type**: moyenne de l’écart par rapport à la moyenne d’une mesure spécifique, sur toutes les partitions d’un modèle. Pour la validation croisée, une valeur plus élevée pour ce score implique une variation substantielle entre les replis.|  
  
## <a name="see-also"></a>Voir aussi  
 [Test et validation &#40;l’exploration de données&#41;](testing-and-validation-data-mining.md)  
  
  
