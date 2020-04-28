---
title: Création d’une vue de source de données (didacticiel sur l’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c1e68a88-0f82-415d-becc-78d180d4f845
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ac7730e8437eaed304ed69c40e45fc93ee9b5531
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68888651"
---
# <a name="creating-a-data-source-view-basic-data-mining-tutorial"></a>Création d'une vue de source de données (Didacticiel sur l'exploration de données de base)
  Une vue de source de données est créée à partir d'une source de données et définit un sous-ensemble des données, que vous pouvez ensuite utiliser dans vos structures d'exploration de données. Vous pouvez également utiliser la vue de source de données pour ajouter des colonnes, créer des colonnes calculées et des agrégats, et ajouter des vues nommées. En utilisant des vues de source de données, vous pouvez sélectionner les données qui se rapportent à un projet en particulier, établir des relations entre les tables et modifier la structure des données, sans modifier la source de données d'origine. Pour plus d’informations, consultez [Vues de sources de données dans les modèles multidimensionnels](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models).  
  
### <a name="to-create-a-data-source-view"></a>Pour créer une vue de source de données  
  
1.  Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **vues de source de données**, puis sélectionnez **nouvelle vue de source de données**.  
  
2.  Sur la page **Bienvenue dans l'Assistant Sources de données**, cliquez sur **Suivant**.  
  
3.  Dans la page **Sélectionner une source de données** , sous **sources de données relationnelles**, sélectionnez la source de données Adventure Works DW 2012 que vous avez créée dans la dernière tâche. Cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  Si vous souhaitez créer une source de données, cliquez avec le bouton droit sur **sources de données** , puis cliquez sur **nouvelle source de données** pour démarrer l’Assistant source de données.  
  
4.  Sur la page **Sélectionner des tables et des vues** , sélectionnez les objets suivants, puis cliquez sur la flèche droite pour les inclure dans la nouvelle vue de source de données :  
  
    -   **ProspectiveBuyer (DBO)** -table des acheteurs de bicyclettes potentiels  
  
    -   **vTargetMail (DBO)** : vue des données historiques sur les derniers acheteurs de bicyclettes  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans la page **fin de l’Assistant** , par défaut, la vue de source de données est nommée Adventure Works DW 2012. Remplacez le nom par `Targeted Mailing`, puis cliquez sur **Terminer**.  
  
     La nouvelle vue de source de données s’ouvre dans l’onglet **Publipostage ciblé. DSV [conception]** .  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Création d’une source de données &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : création d’une structure de publipostage ciblée &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Définition d’une vue de source de données &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/defining-a-data-source-view-analysis-services)  
  
  
