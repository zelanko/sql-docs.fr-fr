---
title: Traitement des modèles dans la structure de publipostage ciblée (didacticiel sur l’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9d8233bb-117e-4563-9302-8a5a8ad1fae2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 605088d405cbd2dcfba92a2da5fa4e07c38d8f0b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63188225"
---
# <a name="processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial"></a>Traitement de modèles dans la structure de publipostage ciblé (Didacticiel sur l'exploration de données de base)
  Avant de pouvoir consulter ou utiliser les modèles d'exploration de données que vous avez créés, vous devez déployer le projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et traiter la structure d'exploration de données et les modèles d'exploration de données.  
  
-   Le *déploiement* envoie le projet à un serveur et crée tous les objets de ce projet sur le serveur.  
  
-   Le *traitement* remplit [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] des objets avec des données provenant de sources de données relationnelles.  
  
 Les modèles ne peuvent pas être utilisés tant qu'ils n'ont pas été déployés et traités. En outre, lorsque vous apportez des modifications au modèle, notamment lorsque vous ajoutez de nouvelles données, vous devez redéployer et retraiter les modèles.  
  
## <a name="ensuring-consistency-with-holdoutseed"></a>Garantir la cohérence avec HoldoutSeed  
 Lorsque vous déployez un projet et traitez la structure et les modèles, les lignes individuelles dans votre structure de données sont assignées au jeu d'apprentissage ou au jeu de test selon une valeur de départ numérique. Par défaut, la valeur de départ numérique est calculée selon des attributs de la structure de données. Cependant, si vous modifiez certains aspects de votre modèle, la valeur de départ change, ce qui génère des résultats légèrement différents. Par conséquent, pour garantir que vos résultats sont les mêmes que ceux décrits ici, nous attribuons arbitrairement une *valeur de départ exclusion* fixe de `12`. La valeur de départ d'exclusion est utilisée pour initialiser l'algorithme d'échantillonnage et garantit que les données sont partitionnées à peu près de la même manière pour toutes les structures d'exploration de données et leurs modèles.  
  
 Cette valeur n'affecte pas le nombre de cas dans le jeu d'apprentissage ; elle garantit simplement que la même méthode de partitionnement est utilisée à chaque création du modèle.  
  
 Pour plus d’informations sur la valeur initiale de exclusion, consultez [jeux de données d’apprentissage et de test](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md).  
  
#### <a name="to-set-the-holdout-seed"></a>Pour définir la valeur initiale d'exclusion  
  
1.  Cliquez sur l’onglet **structure d’exploration** de données ou l’onglet modèles d' **exploration** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]données du concepteur d’exploration de données dans.  
  
     Le **MiningStructure de publipostage ciblé** s’affiche dans le volet **Propriétés** .  
  
2.  Assurez-vous que le volet **Propriétés** est ouvert en appuyant sur **F4**.  
  
3.  Vérifiez que **CacheMode** est défini sur **KeepTrainingCases**.  
  
4.  Entrez `12` pour **HoldoutSeed**.  
  
## <a name="deploying-and-processing-the-models"></a>Déploiement et traitement des modèles  
 Dans le concepteur d’exploration de données, vous pouvez décider quels objets traiter, en fonction de l’étendue des modifications apportées à votre modèle ou aux données sous-jacentes :  
  
 Pour cette tâche, étant donné que les données et les modèles sont nouveaux, vous allez traiter la structure et tous les modèles en même temps.  
  
#### <a name="to-deploy-the-project-and-process-all-the-mining-models"></a>Pour déployer le projet et traiter tous les modèles d'exploration de données  
  
1.  Dans le menu **modèle d’exploration de données** , sélectionnez traiter l' **exploration de données et tous les modèles**.  
  
     Si vous avez modifié la structure, un message vous demande de créer et de déployer le projet avant de traiter les modèles. Cliquez sur **Oui**.  
  
2.  Cliquez sur **exécuter** dans la boîte de dialogue **traitement de la structure d’exploration de données-Publipostage ciblé** .  
  
     La boîte de dialogue **État d’avancement du traitement** s’ouvre avec les informations sur le traitement des modèles. Le temps nécessaire au traitement des modèles varie en fonction de votre ordinateur.  
  
3.  Cliquez sur **Fermer** dans la boîte de dialogue **État d’avancement du traitement** une fois que les modèles ont été traités.  
  
4.  Cliquez sur **Fermer** dans la boîte de dialogue traitement de la structure d' **exploration de données \<-structure>** .  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Ajout de nouveaux modèles à la structure de publipostage ciblée &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 4 : exploration des modèles de publipostage ciblés &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exigences et considérations relatives au traitement &#40;l’exploration de données&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
