---
title: Cluster Assistant (Data Mining Add-ins pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clustering [data mining]
ms.assetid: 85b25625-a7ab-4960-9f9c-df22e8ecae37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d93f676aec67b5d791924cbbda8f71a966d5bbc2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66087810"
---
# <a name="cluster-wizard-data-mining-add-ins-for-excel"></a>Assistant Cluster (Compléments d'exploration de données pour Excel)
  ![Assistant de cluster dans le ruban Exploration de données](media/dmc-cluster.gif "Assistant de Cluster dans le ruban Exploration de données")  
  
 L'Assistant Cluster vous aide à créer un modèle de clustering qui détecte les lignes partageant des caractéristiques similaires et les regroupe pour maximiser la distance entre les groupes. Cet Assistant permet de rechercher des séquences dans tous les types de données.  
  
 L'Assistant Cluster utilise l'algorithme de gestion de clusters Microsoft et peut être largement personnalisé. Il fonctionne sur des données existantes à partir d'une table Excel, d'une plage Excel ou d'une requête [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Une fonctionnalité similaire est fournie par le [détecter les catégories](detect-categories-table-analysis-tools-for-excel.md) outil, fourni dans les outils d’analyse de Table pour Excel. Toutefois, l'outil Détecter les catégories ne peut pas être personnalisé et doit utiliser les données de tables Excel.  
  
## <a name="using-the-cluster-wizard"></a>Utilisation de l'Assistant Cluster  
  
1.  Dans le ruban Exploration de données, cliquez sur **Cluster**, puis cliquez sur **suivant**.  
  
2.  Dans le **sélectionner les données Source** , sélectionnez un tableau Excel ou une plage. Ou spécifiez une source de données externe.  
  
     Si vous utilisez une source de données externe, vous pouvez créer des vues personnalisées ou coller un texte de requête personnalisée, et enregistrer le jeu de données en tant que source de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
3.  Sur le **Clustering** page, vous pouvez personnaliser la façon dont le modèle est créé.  
  
    -   Pour **nombre de segments**, vous pouvez indiquer à l’Assistant pour créer un nombre fixe de catégories ou laisser ce dernier détecter automatiquement le nombre optimal de regroupements.  
  
    -   Passez en revue la liste des colonnes dans le **colonnes d’entrée** et désactivez toutes les colonnes qui ne sont pas utiles pour créer des modèles. Les colonnes à exclure comprennent les numéros d'ID, les noms des clients, etc.  
  
4.  Si vous le souhaitez, cliquez sur **paramètres** pour modifier les paramètres d’algorithme et personnaliser le comportement du modèle de clustering.  
  
5.  Dans le **fractionner les données d’apprentissage et jeux de test** , spécifiez la quantité de données à exclure pour le test. Le reste est toujours utilisé pour l'apprentissage du modèle.  
  
     Le paramètre par défaut est 30 % de données de test et 70 % de données de formation.  
  
6.  Sur le **Terminer** page, fournissez un nom descriptif pour votre jeu de données et le modèle et définir les options suivantes qui contrôlent la façon dont vous travaillez avec le modèle fini :  
  
    -   **Parcourir le modèle**. Lorsque cette option est sélectionnée, dès que l’Assistant termine de traiter le modèle, il ouvre une **Parcourir** fenêtre pour vous aider à Explorer les résultats. Le contenu de la visionneuse dépend du type de modèle que vous créez. Pour plus d’informations, consultez [exploration d’un modèle de Clustering](browsing-a-clustering-model.md).  
  
    -   **Activer l’extraction**. Sélectionnez cette option pour examiner les données sous-jacentes du modèle terminé. Cette option est disponible uniquement si vous créez un modèle d'arbre de décision.  
  
    -   **Utiliser le modèle temporaire**. Si cette option est sélectionnée, le modèle ne sera pas enregistré sur le serveur. Lorsque vous fermez Excel, les modèles temporaires sont supprimés.  
  
## <a name="more-about-clustering-models"></a>Pour plus d'informations sur les modèles de clustering  
 Vous pouvez modifier l’algorithme de clustering utilisée par cet Assistant en cliquant sur **avancé** et à l’aide de la **paramètres d’algorithme** boîte de dialogue.  
  
 L'algorithme de gestion de clusters Microsoft fournit les méthodes de clustering suivantes :  
  
-   K-means - évolutif ou non évolutif.  
  
-   EM (Expectation Maximization) - évolutif ou non évolutif.  
  
 Vous pouvez également utiliser le paramètre CLUSTER_SEED pour contrôler la valeur de départ et vous assurer que les modèles répétés utilisant le même jeu de données ont les mêmes résultats.  
  
### <a name="requirements"></a>Configuration requise  
 Pour utiliser l'Assistant Cluster, vous devez être connecté à une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Pour plus d’informations, consultez [se connecter à la Source de données &#40;Client d’exploration de données pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un modèle d’exploration de données](creating-a-data-mining-model.md)   
 [Détecter les catégories &#40;outils d’analyse de Table pour Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
  
  
