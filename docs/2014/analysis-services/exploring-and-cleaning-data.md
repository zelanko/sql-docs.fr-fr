---
title: Exploration et nettoyage des données | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7c888c95-8986-461e-9f11-2395044b9d97
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 79d356aa1b14ac30ba5bc9a8f579fc66ddebea92
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66081270"
---
# <a name="exploring-and-cleaning-data"></a>Exploration et nettoyage des données
  La préparation des données est bien plus que le nettoyage des données. N'oubliez pas que la façon dont les données sont préparées affecte également la façon dont les résultats sont interprétés. La préparation des données implique les tâches suivantes :  
  
-   Exploration et vérification de la distribution des données.  
  
-   Nettoyage des enregistrements incorrects et sélection des colonnes pour l'exploration de données.  
  
-   Gestion des valeurs Null.  
  
-   Placement des valeurs dans un conteneur ou agrégation des valeurs selon différents segments de temps.  
  
-   Ajout d'étiquettes pour améliorer la simplicité d'utilisation des résultats.  
  
-   Conversion des types de données ou classement des valeurs, le cas échéant, pour analyse.  
  
 Si vous débutez avec la modélisation des données, nous vous recommandons de lire la rubrique correspondante, [liste de contrôle de préparation pour l’exploration de données](checklist-of-preparation-for-data-mining.md).  
  
## <a name="data-preparation-tools"></a>Outils de préparation des données  
 Les compléments d’exploration de données pour Office incluent les outils suivants pour le nettoyage et la préparation des données :  
  
### <a name="explore-data"></a>Explorer les données  
 Utilisez l’Assistant **exploration des données** pour ces tâches de préparation des données :  
  
-   Afficher un aperçu de vos données et identifier les erreurs qui doivent être résolues avant l'analyse.  
  
-   Collecter les statistiques utiles pour comprendre l'équilibre de la distribution des données et les tâches de nettoyage nécessaires.  
  
-   Identifier les colonnes qui sont utiles pour l'analyse, et planifier la phase de modélisation des données.  
  
 [Explorez les&#41;de données &#40;SQL Server des compléments d’exploration de données ](explore-data-sql-server-data-mining-add-ins.md).  
  
### <a name="detect-and-handle-outliers"></a>Détecter et gérer les valeurs hors norme  
 L' **Assistant valeurs** hors norme graphe la distribution des valeurs dans vos données et vous permet de supprimer les valeurs extrêmes. Utilisez l' **outil valeurs** hors norme pour les tâches de préparation des données suivantes :  
  
-   Déterminer si les valeurs individuelles sont fiables, basées sur les modèles trouvés dans les données.  
  
-   Examiner les valeurs inhabituelles, les supprimez ou les remplacer.  
  
-   Définir l'étendue d'un modèle à une plage de valeurs spécifique. Par exemple, si vous savez que vous avez des valeurs hors norme dans un magasin spécifique, supprimez cette valeur et obtenez un modèle qui améliore les prédictions d'autres magasins.  
  
 Valeurs hors norme [&#40;SQL Server les compléments d’exploration de données&#41;](outliers-sql-server-data-mining-add-ins.md).  
  
### <a name="relabel-and-bin-data"></a>Réétiqueter et placer les données dans un conteneur  
 L’Assistant **réétiqueter** regroupe les données par valeurs afin que vous puissiez modifier les étiquettes des données. Utilisez l'outil Réétiqueter pour les tâches de préparation des données suivantes :  
  
-   Modifier les codes numériques utilisés dans les résultats d'enquête en une description textuelle de la signification du code numérique.  
  
     Par exemple, vous pouvez remplacer des entrées de données telles que Sexe = 1 par Sexe = Féminin.  
  
-   Placez les données dans un conteneur, en créant des groupes pour représenter des plages de nombres.  
  
     Par exemple, vous souhaiterez peut-être remplacer une colonne revenu des nombres par des étiquettes telles que **revenu-modéré** et **revenu-High**.  
  
-   Réduisez les valeurs discrètes dans des catégories.  
  
     Par exemple, si vous disposez de trop de produits individuels pour détecter un schéma parmi les achats, vous pouvez essayer d'affecter des produits dans des catégories plus vastes.  
  
 [Réétiqueter les compléments d’exploration de données &#40;SQL Server&#41;](relabel-sql-server-data-mining-add-ins.md)  
  
### <a name="cleanse-data"></a>Nettoyer les données  
 Le nettoyage de données comprend une grande variété d'activités, la plupart étant prises en charge par les compléments  
  
-   Identifiez les valeurs nulles et déterminez si elles doivent être remplacées par une valeur réelle ou être gérées en tant que valeurs `Missing`.  
  
-   Détectez les valeurs manquantes, puis supprimez-les ou imputez une valeur appropriée, comme une moyenne, une valeur NULL ou une autre valeur.  
  
 [Explorez les &#40;de données SQL Server les compléments d’exploration de données&#41;](explore-data-sql-server-data-mining-add-ins.md)  
  
 [Réétiqueter les compléments d’exploration de données &#40;SQL Server&#41;](relabel-sql-server-data-mining-add-ins.md)  
  
 [Remplir à partir de l'exemple](fill-from-example-table-analysis-tools-for-excel.md)  
  
### <a name="sample-data"></a>Exemples de données  
 L'Assistant Exemples de données fournit deux méthodes pour créer des jeux de données équilibrés pour des modèles d'apprentissage et de test.  
  
-   **Échantillonnage aléatoire.** Utilisez cette option pour extraire un jeu de données représentatif d'un plus grand jeu de données, en vue de l'utiliser pour l'apprentissage ou le test. Les compléments d’exploration de données utilisent l' *échantillonnage stratifié* pour s’assurer qu’un ensemble équilibré de valeurs est obtenu pour chaque variable échantillonnée.  
  
-   **Suréchantillonnage.** Utilisez cette option si vous avez moins de données que vous ne le souhaiteriez pour le résultat, et que vous devez pondérer ces données de manière plus importante. Par exemple, la fraude peut être relativement rare, mais vous pouvez suréchantillonner des cas impliquant de la fraude pour obtenir les données adéquates pour la modélisation.  
  
 [Exemples de données &#40;SQL Server&#41;des compléments d’exploration de données ](sample-data-sql-server-data-mining-add-ins.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un modèle d’exploration de données](creating-a-data-mining-model.md)   
 [Validation des modèles et utilisation de modèles pour la prédiction &#40;compléments d’exploration de données pour Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)   
 [Déploiement et mise à l’échelle des modèles d’exploration de données &#40;les compléments d’exploration de données pour Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
