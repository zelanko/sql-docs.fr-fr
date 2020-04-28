---
title: Spécification d’un jeu de données de test pour la structure (didacticiel sur l’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 75cd508f-b126-418b-848d-3c4c3e6c303f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 21eaa86fb1ff594e8b9d2b779b787276ee13ab4b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62720099"
---
# <a name="specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial"></a>Spécification d'un jeu de données de test pour la structure (Didacticiel sur l'exploration de données de base)
  Dans les écrans finals de l'Assistant Exploration de données, vous allez diviser vos données en un jeu de test et un jeu d'apprentissage. Vous nommerez ensuite votre structure et activerez l'extraction sur le modèle.  
  
## <a name="specifying-a-testing-set"></a>Spécification d'un jeu de test  
 La séparation des données en jeux d'apprentissage et de test lorsque vous créez une structure d'exploration de données permet d'évaluer facilement l'exactitude des modèles d'exploration de données que vous créerez ultérieurement. Pour plus d’informations sur les jeux de test, consultez [jeux de données d’apprentissage et de test](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md).  
  
#### <a name="to-specify-the-testing-set"></a>Pour spécifier le jeu de test  
  
1.  Sur la page **créer un jeu de test** , pour **pourcentage de données à tester**, laissez la valeur `30`par défaut.  
  
2.  Pour le **nombre maximal de cas dans le jeu de données de test**, tapez. `1000`  
  
3.  Cliquez sur **Suivant**.  
  
## <a name="specifying-drillthrough"></a>Spécification de l'extraction  
 L'extraction peut être activée sur les modèles et sur les structures. La case à cocher dans cette boîte de dialogue active l'extraction sur le modèle nommé. Une fois le modèle traité, vous serez en mesure d'extraire des informations détaillées des données d'apprentissage qui ont été utilisées pour créer le modèle.  
  
 Si la structure sous-jacente d'exploration de données a été également configurée pour autoriser l'extraction, vous pouvez récupérer des informations détaillées des cas du modèle et de la structure d'exploration de données, y compris des colonnes non incluses dans le modèle d'exploration de données. Pour plus d’informations, consultez [Requêtes d’extraction &#40;exploration de données&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
#### <a name="to-name-the-model-and-structure-and-specify-drillthrough"></a>Pour nommer le modèle et la structure et spécifier l'extraction  
  
1.  Dans la page **fin de l’Assistant** , dans nom de la structure `Targeted Mailing`d’exploration de **données**, tapez.  
  
2.  Dans **nom du modèle**d’exploration `TM_Decision_Tree`de données, tapez.  
  
3.  Activez la case à cocher **autoriser l’extraction** .  
  
4.  Passez en revue le volet de **visualisation** . Notez que seules les colonnes sélectionnées en tant que **clé**, **entrée** ou **prédiction** sont affichées. Les autres colonnes que vous avez sélectionnées (par exemple, AddressLine1) ne sont pas utilisées pour générer le modèle mais seront disponibles dans la structure sous-jacente et pourront être interrogées à l'issue du traitement et du déploiement du modèle.  
  
5.  Cliquez sur **Terminer**.  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Spécification du type de données et du type de contenu &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 3 : Ajout et traitement des modèles](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Activer l’extraction pour un modèle d’exploration de données](../../2014/analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)   
 [Requêtes d’extraction &#40;l’exploration de données&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)   
 [Spécifiez les données d’apprentissage &#40;l’Assistant Exploration de données&#41;](../../2014/analysis-services/specify-the-training-data-data-mining-wizard.md)  
  
  
