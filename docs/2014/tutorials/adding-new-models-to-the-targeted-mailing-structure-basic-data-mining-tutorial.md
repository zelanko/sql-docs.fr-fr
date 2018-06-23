---
title: Ajout de nouveaux modèles à la Structure de publipostage ciblé (didacticiel d’exploration de données de base de données) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 512c6888-60f1-46e4-9639-bc448395b8d7
caps.latest.revision: 45
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c5e31e06a489b1807335f63dd1675fc9e77c45b4
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312377"
---
# <a name="adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial"></a>Ajout de nouveaux modèles à la structure de publipostage ciblé (Didacticiel sur l'exploration de données de base)
  Dans cette tâche, vous allez définir deux modèles supplémentaires à l’aide de la **des modèles d’exploration de données** onglet du Concepteur d’exploration de données. Vous allez utiliser l'algorithme MNB (Microsoft Naive Bayes) et l'algorithme de gestion de clusters Microsoft pour créer les modèles. Ces deux algorithmes sont sélectionnés en raison de leur capacité à prédire une valeur discrète (c.-à-d., un achat de vélo). Pour plus d’informations sur ces algorithmes, consultez [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md) et [l’algorithme Microsoft Naive Bayes](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)  
  
### <a name="to-create-a-clustering-mining-model"></a>Pour créer un modèle d'exploration de données Microsoft Clustering  
  
1.  Basculez vers le **des modèles d’exploration de données** onglet dans le Concepteur d’exploration de données dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
     Notez que le concepteur affiche deux colonnes, une pour la structure d’exploration de données et une pour la `TM_Decision_Tree` modèle d’exploration de données, que vous avez créé dans la leçon précédente.  
  
2.  Cliquez sur le **Structure** colonne et sélectionnez **nouveau modèle d’exploration de données**.  
  
3.  Dans le **nouveau modèle d’exploration de données** boîte de dialogue **nom_modèle**, type `TM_Clustering`.  
  
4.  Dans **nom de l’algorithme**, sélectionnez **Microsoft Clustering**.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 Le nouveau modèle apparaît désormais dans le **des modèles d’exploration de données** onglet du Concepteur d’exploration de données. Ce modèle, créé avec le [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme, le Clustering regroupe les clients présentant des caractéristiques similaires dans des clusters et prédit l’achat de vélo pour chaque cluster. Bien que vous pouvez modifier l’utilisation des colonnes et les propriétés pour le nouveau modèle, aucune modification à la `TM_Clustering` modèle sont nécessaires pour ce didacticiel.  
  
### <a name="to-create-a-naive-bayes-mining-model"></a>Pour créer un modèle d'exploration de données Naive Bayes  
  
1.  Dans le **des modèles d’exploration de données** onglet du Concepteur d’exploration de données, à droite-clickthe **Structure** colonne, puis sélectionnez **nouveau modèle d’exploration de données**.  
  
2.  Dans le **nouveau modèle d’exploration de données** boîte de dialogue **nom_modèle**, type `TM_NaiveBayes`.  
  
3.  Dans **nom de l’algorithme**, sélectionnez **Microsoft Naive Bayes**, puis cliquez sur **OK**.  
  
     Un message s’affiche indiquant que la [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme Naive Bayes ne prend pas en charge la **âge** et **Yearly Income** les colonnes continues.  
  
4.  Cliquez sur **Oui** pour accuser réception du message et continuer.  
  
 Un nouveau modèle apparaît dans le **des modèles d’exploration de données** onglet du Concepteur d’exploration de données. Bien que vous pouvez modifier l’utilisation des colonnes et les propriétés pour tous les modèles dans cet onglet, aucune modification à la `TM_NaiveBayes` modèle sont nécessaires pour ce didacticiel.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Traitement de modèles dans la Structure de publipostage ciblé &#40;didacticiel d’exploration de données de base de données&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des modèles d’exploration de données à une Structure &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)   
 [Concepteur d’exploration de données](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Déplacement d’objets d’exploration de données](../../2014/analysis-services/data-mining/moving-data-mining-objects.md)  
  
  