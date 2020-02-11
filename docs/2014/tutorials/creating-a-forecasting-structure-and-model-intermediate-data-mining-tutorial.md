---
title: Création d’une structure et d’un modèle de prévision (Didacticiel intermédiaire sur l’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5f55cbf6-0db4-4cb4-a0f5-e27441873d4f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6e631a8983705d4f58e4b193823c9a255284f346
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63204808"
---
# <a name="creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial"></a>Création d'une structure et d'un modèle de prévision (Didacticiel sur l'exploration de données intermédiaire)
  Ensuite, vous utiliserez l'Assistant Exploration de données pour créer une nouvelle structure d'exploration de données et un nouveau modèle d'exploration de données basés sur la vue de source de données que vous venez de créer. Au cours de cette tâche, vous spécifierez que le modèle d'exploration de données doit utiliser l'algorithme MTS ([!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series).  
  
### <a name="to-create-a-forecasting-mining-structure"></a>Pour créer une structure d'exploration de données de prévision  
  
1.  Dans Explorateur de solutions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], cliquez avec le bouton droit sur **structures d’exploration de données** et sélectionnez **nouvelle structure d’exploration de données**.  
  
2.  Dans la page **Assistant Exploration de données** , cliquez sur **Suivant**.  
  
3.  Sur la page **Sélectionner la méthode de définition** , vérifiez que **à partir de la base de données relationnelle ou de l’entrepôt de données existant** est sélectionné, puis cliquez sur **suivant**.  
  
4.  Dans la page **créer la structure d’exploration de données** , sous **quelle technique d’exploration de données voulez-vous utiliser ?**, sélectionnez **séries chronologiques Microsoft**, puis cliquez sur **suivant**.  
  
5.  Dans la page **Sélectionner une vue de source de données** , sous vues de sources de **données disponibles**, sélectionnez **SalesByRegion**.  
  
6.  Cliquez sur **Suivant**.  
  
7.  Dans la page **spécifier les types des tables** , vérifiez que la case à cocher dans la colonne **cas** de la table vTimeSeries est sélectionnée, puis cliquez sur **suivant**.  
  
8.  Dans la page **spécifier les données d’apprentissage** , activez les cases à cocher dans la colonne **clé** pour les colonnes ModelRegion et ReportingDate.  
  
     La colonne ReportingDate doit être sélectionnée par défaut, parce que vous avez spécifié cette colonne en tant que clé primaire logique lorsque vous avez créé la vue de source de données. En ajoutant ModelRegion comme deuxième clé, vous indiquez à l'algorithme de créer une série chronologique distincte pour chaque combinaison de modèle et région répertoriée dans ce champ.  
  
9. Activez les cases à cocher dans les colonnes **d’entrée** et **prévisibles** pour la quantité, la colonne, puis cliquez sur **suivant**.  
  
     En sélectionnant **prévisible**, vous indiquez que vous souhaitez créer des prévisions sur les données de cette colonne. Toutefois, étant donné que vous souhaitez baser les prévisions sur des données passées, vous devez également ajouter la colonne en tant qu'entrée.  
  
10. Dans la page **spécifier le type de contenu et de données des colonnes**, passez en revue les sélections.  
  
     La colonne ModelRegion est désignée en tant que colonne **clé** et la colonne ReportingDate est automatiquement désignée comme colonne **Key Time** . Il ne peut y avoir qu'une seule occurrence de chaque type de clé.  
  
11. Cliquez sur **Suivant**.  
  
12. Dans la page **fin de l’Assistant** , pour nom de la structure `Forecasting`d’exploration de **données**, tapez.  
  
    > [!NOTE]  
    >  L'option permettant d'activer l'extraction n'est pas disponible pour les modèles de série chronologique.  
  
13. Dans **nom du modèle**d’exploration `Forecasting`de données, tapez, puis cliquez sur **Terminer**.  
  
     Le concepteur d’exploration de données s' `Forecasting` ouvre pour afficher la structure d’exploration de données que vous venez de créer.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Modification de la structure de prévision &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur d’exploration de données](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Algorithme MTS (Microsoft Time Series)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
