---
title: Concepteur d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], structure
- mining structures [Analysis Services], modifying
- data mining editor [Analysis Services]
- Data Mining Designer
- data mining [Analysis Services], modifying
ms.assetid: 2540db5b-2bf3-4b6c-87c8-79c48d71acce
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 010b9b18be2264add14bc5242ced6a57ed8fdcca
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62722861"
---
# <a name="data-mining-designer"></a>Concepteur d’exploration de données
  Le Concepteur d’exploration de données est l’environnement principal dans lequel vous utilisez des modèles d’exploration de données dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour accéder au concepteur, vous pouvez sélectionner une structure d'exploration de données existante ou utiliser l'Assistant Exploration de données pour créer une structure d'exploration de données et un modèle d'exploration de données. Vous pouvez utiliser le Concepteur d'exploration de données pour effectuer les tâches suivantes :  
  
-   modifier la structure d'exploration de données et le modèle d'exploration de données initialement créés par l'Assistant Exploration de données ;  
  
-   créer de nouveaux modèles d'après une structure d'exploration de données existante ;  
  
-   instruire et parcourir des modèles d'exploration de données ;  
  
-   comparer des modèles à l'aide de graphiques d'analyse de précision ;  
  
-   créer des requêtes de prédictions basées sur des modèles d'exploration de données.  
  
## <a name="mining-structure-tab"></a>Onglet Structure d'exploration de données  
 Utilisez l’onglet **Structure d’exploration de données** pour ajouter des colonnes et modifier les propriétés d’une structure d’exploration de données existante. Les tâches et les rubriques suivantes fournissent d'autres informations sur l'utilisation des structures d'exploration de données :  
  
 [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](mining-structures-analysis-services-data-mining.md)  
  
 [Tâches et procédures relatives aux structures d’exploration de données](mining-structure-tasks-and-how-tos.md)  
  
## <a name="mining-models-tab"></a>Onglet Modèles d'exploration de données  
 Utilisez l’onglet **Modèles d’exploration de données** pour gérer les modèles d’exploration de données existants et pour créer des modèles. Les modèles d’exploration de données sont toujours basés sur une structure d’exploration de données existante.  
  
 Sous l’onglet **Modèles d’exploration de données** , vous pouvez modifier le type d’algorithme, ajouter ou supprimer des colonnes associées à la structure du modèle, ajuster des propriétés de colonne propres aux algorithmes, spécifier l’utilisation des colonnes de modèle d’exploration de données et ajuster les paramètres d’algorithme associés au modèle d’exploration de données. Vous pouvez également traiter la structure d'exploration de données avec les modèles sélectionnés ou tous les modèles associés.  
  
 Consultez les rubriques suivantes pour plus d'informations sur l'utilisation des modèles d'exploration de données :  
  
 [Modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](mining-models-analysis-services-data-mining.md)  
  
 [Tâches du modèle d'exploration de données et procédures](mining-model-tasks-and-how-tos.md)  
  
## <a name="mining-model-viewer-tab"></a>Onglet Visionneuse de modèle d'exploration de données  
 Utilisez l’onglet **Visionneuse de modèle d’exploration de données** pour explorer visuellement vos modèles d’exploration de données. Chaque modèle d'exploration de données est associé à une visionneuse personnalisée qui affiche le contenu spécifique à ce modèle. Vous pouvez également afficher le contenu du modèle d'exploration de données à l'aide de l'utilitaire Microsoft Mining Content Viewer.  
  
 Consultez les rubriques suivantes pour plus d'informations sur l'exploration des modèles d'exploration de données avec les visionneuses d'exploration de données :  
  
 [Visionneuses de modèle d’exploration de données](data-mining-model-viewers.md)  
  
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](mining-model-viewer-tasks-and-how-tos.md)  
  
## <a name="mining-accuracy-chart-tab"></a>Onglet Graphique d'analyse de précision de l'exploration de données  
 Utilisez l’onglet **Graphique d’analyse de précision de l’exploration de données** pour tester la précision prédictive d’un modèle d’exploration de données unique ou pour comparer l’efficacité de plusieurs modèles d’exploration de données appartenant à la même structure d’exploration de données. Cet onglet contient des outils pour filtrer les données, sélectionner des modèles d'exploration de données et afficher les résultats dans un graphique de courbes d'élévation, dans un graphique des bénéfices ou dans une matrice de classification.  
  
 Consultez les rubriques suivantes pour plus d'informations sur le test et la validation des modèles d'exploration de données :  
  
 [Test et validation &#40;exploration de données&#41;](testing-and-validation-data-mining.md)  
  
 [Tâches de test et validation et procédures &#40;exploration des données&#41;](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
## <a name="mining-model-prediction-tab"></a>Onglet Prévision de modèle d'exploration de données  
 L’onglet **Prévision de modèle d’exploration de données** contient le Générateur de requêtes de prédictions, que vous pouvez utiliser pour créer une requête de prédiction DMX (Data Mining Extensions). Cet onglet contient également des outils pour spécifier des modèles d'exploration de données et des tables d'entrée, mapper les colonnes du modèle d'exploration de données vers les colonnes de la table d'entrée, ajouter des fonctions à une requête et pour spécifier des critères pour chaque colonne.  
  
 Une fois que vous avez conçu une requête, cet onglet vous propose différents affichages pour afficher les résultats de la requête et pour modifier manuellement la requête. Vous pouvez également enregistrer les résultats de la requête dans une table de base de données.  
  
 Consultez les rubriques suivantes pour plus d'informations sur la création de requêtes d'exploration de données :  
  
 [Requêtes d'exploration de données](data-mining-queries.md)  
  
 [Tâches de requête d'exploration de données et procédures](data-mining-query-tasks-and-how-tos.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions d’exploration de données](data-mining-solutions.md)  
  
  
