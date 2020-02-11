---
title: Onglet validation croisée (vue graphique d’analyse de précision de l’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.crossvalidation.f1
ms.assetid: bd215a68-1ad7-4046-9c44-ec8e2be13a64
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f5a8508218ed6a2b4407943fe962959e3cd4f97d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66086617"
---
# <a name="cross-validation-tab-mining-accuracy-chart-view"></a>Onglet Validation croisée (vue Graphique d'analyse de précision de l'exploration de données)
  La validation croisée vous permet de partitionner une structure d'exploration de données en sections croisées et d'effectuer l'apprentissage et le test des modèles de manière itérative sur chaque section croisée. Vous spécifiez un nombre de replis pour la division des données. Chaque repli est utilisé à son tour comme données de test, tandis que les autres données sont utilisées pour l'apprentissage d'un nouveau modèle. 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] génère ensuite un jeu de mesures de précision standard pour chaque modèle. En comparant les mesures des modèles générés pour chaque section croisée, vous pouvez vous faire une bonne idée de la fiabilité du modèle d'exploration de données pour le jeu de données complet.  
  
 Pour plus d’informations, consultez [Validation croisée &#40;Analysis Services - Exploration de données&#41;](data-mining/cross-validation-analysis-services-data-mining.md).  
  
> [!NOTE]  
>  La validation croisée ne peut pas être utilisée avec des modèles qui ont été générés à l’aide de l’algorithme MTS ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series) ou de l’algorithme MSC ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering). Si vous exécutez le rapport sur une structure d'exploration de données qui contient ces types de modèles, ils ne seront pas inclus dans le rapport.  
  
## <a name="task-list"></a>Liste des tâches  
  
-   Spécifiez le nombre de replis.  
  
-   Spécifiez le nombre maximal de cas à utiliser pour la validation croisée.  
  
-   Spécifiez la colonne prédictible.  
  
-   Spécifiez, de manière facultative, un état prévisible.  
  
-   Définissez, de manière facultative, les paramètres qui contrôlent la façon dont la précision de prédiction est évaluée.  
  
-   Cliquez sur **Obtenir les résultats** pour afficher les résultats de la validation croisée.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Nombre de replis**  
 Spécifiez le nombre de replis ou de partitions à créer. La valeur minimale est 2, ce qui signifie qu'une moitié du jeu de données est utilisée pour le test et une autre moitié pour l'apprentissage.  
  
 La valeur maximale est 10 pour les structures d'exploration de données de session.  
  
 La valeur maximale est 256 si la structure d'exploration de données est stockée dans une instance d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  Lorsque vous augmentez le nombre de replis, le temps nécessaire pour effectuer la validation croisée augmente de façon similaire à n. Vous pouvez rencontrer des problèmes de performances si le nombre de cas est élevé et la valeur **Nombre de replis** est également importante.  
  
 **Nbre max. de cas**  
 Spécifiez le nombre maximal de cas à utiliser pour la validation croisée. Le nombre de cas dans un repli donné est égal à la valeur **Nombre maximal de cas** divisée par la valeur **Nombre de replis** .  
  
 Si vous utilisez **0**, tous les cas des données sources sont utilisés pour la validation croisée.  
  
 Il n'existe aucune valeur par défaut.  
  
> [!NOTE]  
>  Le temps de traitement augmente également avec l'augmentation du nombre de cas.  
  
 **Attribut cible**  
 Sélectionnez une colonne dans la liste des colonnes prédictibles trouvées dans tous les modèles. Vous ne pouvez sélectionner qu'une colonne prédictible chaque fois que vous effectuez une validation croisée.  
  
 Pour tester des modèles de clustering seulement, sélectionnez **Cluster**.  
  
 **État cible**  
 Tapez une valeur cible ou sélectionnez-en une dans une liste déroulante.  
  
 La valeur par défaut est `null`, ce qui indique que tous les états doivent être testés.  
  
 Ce paramètre est désactivé pour les modèles de clustering.  
  
 ******Seuil** cible    
 Spécifiez une valeur comprise entre 0 et 1 qui indique la probabilité de prédiction au-dessus de laquelle un état prédit est considéré comme correct. La valeur peut être définie par incréments de 0,1.  
  
 La valeur par défaut est `null`, ce qui indique que la prédiction la plus probable est comptabilisée comme correcte.  
  
> [!NOTE]  
>  Bien que vous puissiez définir la valeur 0,0, son utilisation augmentera le temps de traitement et ne produira pas de résultats significatifs.  
  
 **Obtenir les résultats**  
 Cliquez pour commencer la validation croisée du modèle à l'aide des paramètres spécifiés.  
  
 Le modèle est partitionné selon le nombre spécifié de replis et un modèle distinct est testé pour chaque repli. Par conséquent, la validation croisée peut mettre du temps à retourner les résultats.  
  
 Pour plus d’informations sur la façon d’interpréter les résultats du rapport de validation croisée, consultez [Mesures dans le rapport de validation croisée](data-mining/measures-in-the-cross-validation-report.md).  
  
## <a name="setting-the-accuracy-threshold"></a>Définition du seuil de précision  
 Vous pouvez contrôler le standard pour mesurer la précision de prédiction en définissant une valeur pour le paramètre **Seuil** **cible**. Le seuil représente une sorte de barre de précision. À chaque prédiction est assignée une probabilité d'exactitude de la valeur prédite. Par conséquent, si vous affectez à **Seuil** **cible** une valeur plus proche de 1, la probabilité d’une prédiction donnée doit être relativement élevée pour être comptabilisée en tant que prédiction correcte. Inversement, si vous affectez à **Seuil** **cible** une valeur plus proche de 0, même les prédictions ayant des valeurs de probabilité inférieures sont comptabilisées en tant que prédictions correctes.  
  
 Aucune valeur de seuil particulière n'est recommandée, car la probabilité de toute prédiction dépend du volume de données et du type de prédiction que vous faites. Vous devez examiner des prédictions à différents niveaux de probabilité pour déterminer une barre de précision appropriée pour vos données. Il est important de procéder ainsi, car la valeur que vous définissez pour **Seuil** **cible** affecte la précision mesurée du modèle.  
  
 Par exemple, supposons que trois prédictions soient effectuées pour un état cible donné et que les probabilités de chaque prédiction soient égales à 0,05, 0,15 et 0,8. Si vous définissez la valeur 0,5 pour le seuil, une seule prédiction est comptabilisée comme correcte. Si vous affectez à **Seuil** **cible** la valeur 0,10, deux prédictions sont comptabilisées comme correctes.  
  
 Lorsque **** le **seuil** cible est défini `null`sur, qui est la valeur par défaut, la prédiction la plus probable pour chaque cas est comptabilisée comme correcte. Dans l'exemple que nous venons de citer, 0,05, 0,15 et 0,8 sont les probabilités des prédictions de trois cas différents. Bien que les probabilités soient très différentes, chaque prédiction est comptabilisée comme correcte, car chaque cas génère une seule prédiction et il s'agit des meilleures prédictions pour ces cas.  
  
## <a name="see-also"></a>Voir aussi  
 [Test et validation &#40;l’exploration de données&#41;](data-mining/testing-and-validation-data-mining.md)   
 [Validation croisée &#40;Analysis Services d’exploration de données&#41;](data-mining/cross-validation-analysis-services-data-mining.md)   
 [Mesures dans le rapport de validation croisée](data-mining/measures-in-the-cross-validation-report.md)   
 [Procédures stockées d’exploration de données &#40;Analysis Services d’exploration de données&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)  
  
  
