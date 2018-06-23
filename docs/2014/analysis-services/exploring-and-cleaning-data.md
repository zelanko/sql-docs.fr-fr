---
title: Exploration et nettoyage des données | Documents Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c888c95-8986-461e-9f11-2395044b9d97
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0c39eaa58152fd1a75eeaefdc79bae93ccd36b98
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039429"
---
# <a name="exploring-and-cleaning-data"></a>Exploration et nettoyage des données
  La préparation des données est bien plus que le nettoyage des données. N'oubliez pas que la façon dont les données sont préparées affecte également la façon dont les résultats sont interprétés. La préparation des données implique les tâches suivantes :  
  
-   Exploration et vérification de la distribution des données.  
  
-   Nettoyage des enregistrements incorrects et sélection des colonnes pour l'exploration de données.  
  
-   Gestion des valeurs Null.  
  
-   Placement des valeurs dans un conteneur ou agrégation des valeurs selon différents segments de temps.  
  
-   Ajout d'étiquettes pour améliorer la simplicité d'utilisation des résultats.  
  
-   Conversion des types de données ou classement des valeurs, le cas échéant, pour analyse.  
  
 Si vous ne connaissez pas la modélisation des données, nous vous recommandons de lire la rubrique connexe, [liste de vérification de la préparation pour l’exploration de données de](checklist-of-preparation-for-data-mining.md).  
  
## <a name="data-preparation-tools"></a>Outils de préparation des données  
 Les compléments d’exploration de données pour Office inclut les outils suivants pour le nettoyage des données et de préparation :  
  
### <a name="explore-data"></a>Explorer les données  
 Utilisez le **Explorer les données** Assistant pour ces tâches de préparation des données :  
  
-   Afficher un aperçu de vos données et identifier les erreurs qui doivent être résolues avant l'analyse.  
  
-   Collecter les statistiques utiles pour comprendre l'équilibre de la distribution des données et les tâches de nettoyage nécessaires.  
  
-   Identifier les colonnes qui sont utiles pour l'analyse, et planifier la phase de modélisation des données.  
  
 [Explorer les données &#40;compléments d’exploration de données SQL Server&#41;](explore-data-sql-server-data-mining-add-ins.md).  
  
### <a name="detect-and-handle-outliers"></a>Détecter et gérer les valeurs hors norme  
 Le **observations aberrantes** Assistant représente sous forme graphique la distribution des valeurs dans vos données et vous permet de supprimer les valeurs extrêmes. Utilisez le **observations aberrantes** outil pour les tâches de préparation de données suivantes :  
  
-   Déterminer si les valeurs individuelles sont fiables, basées sur les modèles trouvés dans les données.  
  
-   Examiner les valeurs inhabituelles, les supprimez ou les remplacer.  
  
-   Définir l'étendue d'un modèle à une plage de valeurs spécifique. Par exemple, si vous savez que vous avez des valeurs hors norme dans un magasin spécifique, supprimez cette valeur et obtenez un modèle qui améliore les prédictions d'autres magasins.  
  
 [Valeurs hors norme &#40;compléments d’exploration de données SQL Server&#41;](outliers-sql-server-data-mining-add-ins.md).  
  
### <a name="relabel-and-bin-data"></a>Réétiqueter et placer les données dans un conteneur  
 Le **Réétiqueter** Assistant regroupe les données par valeurs afin que vous pouvez modifier les étiquettes des données. Utilisez l'outil Réétiqueter pour les tâches de préparation des données suivantes :  
  
-   Modifier les codes numériques utilisés dans les résultats d'enquête en une description textuelle de la signification du code numérique.  
  
     Par exemple, vous pouvez remplacer des entrées de données telles que Sexe = 1 par Sexe = Féminin.  
  
-   Placez les données dans un conteneur, en créant des groupes pour représenter des plages de nombres.  
  
     Par exemple, vous souhaiterez peut-être remplacer une colonne de revenus de nombres avec des étiquettes telles que **Income – modéré** et **revenus élevés**.  
  
-   Réduisez les valeurs discrètes dans des catégories.  
  
     Par exemple, si vous disposez de trop de produits individuels pour détecter un schéma parmi les achats, vous pouvez essayer d'affecter des produits dans des catégories plus vastes.  
  
 [Réétiqueter &#40;compléments d’exploration de données SQL Server&#41;](relabel-sql-server-data-mining-add-ins.md)  
  
### <a name="cleanse-data"></a>Nettoyer les données  
 Le nettoyage de données comprend une grande variété d'activités, la plupart étant prises en charge par les compléments  
  
-   Identifiez les valeurs nulles et déterminez si elles doivent être remplacées par une valeur réelle ou être gérées en tant que valeurs `Missing`.  
  
-   Détectez les valeurs manquantes, puis supprimez-les ou imputez une valeur appropriée, comme une moyenne, une valeur NULL ou une autre valeur.  
  
 [Explorer les données &#40;compléments d’exploration de données SQL Server&#41;](explore-data-sql-server-data-mining-add-ins.md)  
  
 [Réétiqueter &#40;compléments d’exploration de données SQL Server&#41;](relabel-sql-server-data-mining-add-ins.md)  
  
 [Remplir à partir de l’exemple](fill-from-example-table-analysis-tools-for-excel.md)  
  
### <a name="sample-data"></a>Exemples de données  
 L'Assistant Exemples de données fournit deux méthodes pour créer des jeux de données équilibrés pour des modèles d'apprentissage et de test.  
  
-   **Échantillonnage aléatoire.** Utilisez cette option pour extraire un jeu de données représentatif d'un plus grand jeu de données, en vue de l'utiliser pour l'apprentissage ou le test. Compléments d’exploration de données utilisent *l’échantillonnage stratifié* pour vous assurer qu’un jeu équilibré de valeurs est obtenu pour chaque variable échantillonnée.  
  
-   **Suréchantillonnage.** Utilisez cette option si vous avez moins de données que vous ne le souhaiteriez pour le résultat, et que vous devez pondérer ces données de manière plus importante. Par exemple, la fraude peut être relativement rare, mais vous pouvez suréchantillonner des cas impliquant de la fraude pour obtenir les données adéquates pour la modélisation.  
  
 [Les exemples de données &#40;compléments d’exploration de données SQL Server&#41;](sample-data-sql-server-data-mining-add-ins.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un modèle d’exploration de données](creating-a-data-mining-model.md)   
 [Validation des modèles et à l’aide de modèles pour la prédiction &#40;les données des compléments d’exploration de données pour Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)   
 [Déploiement et mise à l’échelle des modèles d’exploration de données &#40;les données des compléments d’exploration de données pour Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  