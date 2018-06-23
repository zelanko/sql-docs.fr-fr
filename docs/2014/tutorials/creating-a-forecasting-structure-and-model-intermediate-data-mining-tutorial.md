---
title: Création d’une Structure de prévision et un modèle (didacticiel sur l’exploration des données intermédiaires) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5f55cbf6-0db4-4cb4-a0f5-e27441873d4f
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 47d6e75a691c53fe1658fb5f79ee2bde8e9c2d01
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312267"
---
# <a name="creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial"></a>Création d'une structure et d'un modèle de prévision (Didacticiel sur l'exploration de données intermédiaire)
  Ensuite, vous utiliserez l'Assistant Exploration de données pour créer une nouvelle structure d'exploration de données et un nouveau modèle d'exploration de données basés sur la vue de source de données que vous venez de créer. Au cours de cette tâche, vous spécifierez que le modèle d'exploration de données doit utiliser l'algorithme MTS ([!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series).  
  
### <a name="to-create-a-forecasting-mining-structure"></a>Pour créer une structure d'exploration de données de prévision  
  
1.  Dans l’Explorateur de solutions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], avec le bouton droit **des Structures d’exploration de données** et sélectionnez **nouvelle Structure d’exploration de données**.  
  
2.  Dans la page **Assistant Exploration de données** , cliquez sur **Suivant**.  
  
3.  Sur le **sélectionner la méthode de définition** page, vérifiez que **à partir de l’entrepôt de données ou de la base de données relationnelle existant** est sélectionné, puis cliquez sur **suivant**.  
  
4.  Sur le **créer la Structure d’exploration de données** sous **quelle technique d’exploration de données voulez-vous utiliser ?**, sélectionnez **Microsoft Time Series**, puis cliquez sur  **Suivant**.  
  
5.  Sur le **sélectionner une vue de Source de données** sous **vues de sources de données disponibles**, sélectionnez **SalesByRegion**.  
  
6.  Cliquez sur **Suivant**.  
  
7.  Sur le **spécifier les Types de Table** page, vérifiez que la case à cocher dans la **cas** colonne pour la table vTimeSeries est sélectionné, puis cliquez sur **suivant**.  
  
8.  Sur le **spécifier les données d’apprentissage** , sélectionnez les cases à cocher dans la **clé** colonne pour les colonnes ModelRegion et ReportingDate.  
  
     La colonne ReportingDate doit être sélectionnée par défaut, parce que vous avez spécifié cette colonne en tant que clé primaire logique lorsque vous avez créé la vue de source de données. En ajoutant ModelRegion comme deuxième clé, vous indiquez à l'algorithme de créer une série chronologique distincte pour chaque combinaison de modèle et région répertoriée dans ce champ.  
  
9. Activez les cases à cocher dans la **entrée** et **prédictible** colonnes pour la quantité, colonne, puis cliquez sur **suivant**.  
  
     En sélectionnant **prédictible**, vous indiquez que vous souhaitez créer des prévisions sur les données de cette colonne. Toutefois, étant donné que vous souhaitez baser les prévisions sur des données passées, vous devez également ajouter la colonne en tant qu'entrée.  
  
10. Dans la page **Type de données et de contenu des colonnes spécifier**, passez en revue les sélections.  
  
     La colonne ModelRegion est désignée comme un **clé** colonne et la colonne ReportingDate est automatiquement désigné comme un **Key Time** colonne. Il ne peut y avoir qu'une seule occurrence de chaque type de clé.  
  
11. Cliquez sur **Suivant**.  
  
12. Sur le **fin de l’Assistant** page, pour **nom de la structure d’exploration de données**, type `Forecasting`.  
  
    > [!NOTE]  
    >  L'option permettant d'activer l'extraction n'est pas disponible pour les modèles de série chronologique.  
  
13. Dans **nom du modèle d’exploration de données**, type `Forecasting`, puis cliquez sur **Terminer**.  
  
     Concepteur d’exploration de données s’ouvre et affiche le `Forecasting` structure d’exploration de données que vous venez de créer.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Modification de la Structure de prévision &#40;intermédiaire Didacticiel d’exploration de données&#41;](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur d’exploration de données](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Algorithme de série chronologique de Microsoft](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  