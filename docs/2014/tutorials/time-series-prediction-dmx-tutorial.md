---
title: Didacticiel DMX sur la série prédiction de temps | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38ea7c03-4754-4e71-896a-f68cc2c98ce2
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2a9e3e5db1e0f21bfe3822d73fd0e3c0b456e250
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312194"
---
# <a name="time-series-prediction-dmx-tutorial"></a>Didacticiel DMX sur la prédiction de série chronologique
  Dans ce didacticiel, vous allez apprendre à créer une structure d'exploration de données de série chronologique, à créer trois modèles d'exploration de données de série chronologique personnalisés, puis à élaborer des prédictions à l'aide de ces modèles.  
  
 Les modèles d'exploration de données sont basés sur les données de la société fictive [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] stockées dans l'exemple de base de données [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]. [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] est une importante société de fabrication multinationale.  
  
## <a name="tutorial-scenario"></a>Scénario du didacticiel  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] a décidé d'utiliser l'exploration de données pour générer des projections de ventes. Il ont déjà généré des modèles de prévision régionaux ; Pour plus d’informations, consultez [leçon 2 : génération d’un scénario de prévision &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md). Toutefois, le service commercial doit être en mesure de mettre régulièrement à jour le modèle d'exploration de données à l'aide des nouvelles données de ventes. Ce service souhaite également personnaliser les modèles pour fournir différentes projections.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fournit plusieurs outils qui peuvent être utilisés pour accomplir cette tâche :  
  
-   Langage de requête DMX (Data Mining Extensions)  
  
-   Algorithme MTS (Microsoft Time Series)  
  
-   Éditeur de requête dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]  
  
 L'algorithme MTS ([!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series) crée des modèles qui peuvent être utilisés pour la prédiction de données de type chronologique. Le langage de requête DMX (Data Mining Extensions) fourni par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] permet de créer des modèles d'exploration de données et des requêtes de prédiction.  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Ce didacticiel part du principe que vous connaissez déjà les objets que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise pour créer des modèles d'exploration de données. Si vous n’avez pas précédemment créé une structure ou un modèle d’exploration de données à l’aide de DMX, consultez [didacticiel DMX Bike Buyer](../../2014/tutorials/bike-buyer-dmx-tutorial.md).  
  
 Ce didacticiel contient les leçons suivantes :  
  
 [Leçon 1 : Création d’une série chronologique de modèle d’exploration de données et la Structure d’exploration de données](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)  
 Dans cette leçon, vous allez apprendre à utiliser l'instruction `CREATE MINING MODEL` pour ajouter un nouveau modèle de prévision et un modèle d'exploration de données associé.  
  
 [Leçon 2 : Ajout des modèles d’exploration de données à la Structure d’exploration de données de série chronologique](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
 Dans cette leçon, vous allez apprendre à utiliser l'instruction ALTER MINING STRUCTURE pour ajouter de nouveaux modèles d'exploration de données à la structure de série chronologique. Vous apprendrez également comment personnaliser l'algorithme utilisé pour analyser une série chronologique.  
  
 [Leçon 3 : Traitement de la série chronologique Structure et des modèles](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
 Dans cette leçon, vous allez apprendre à former les modèles en utilisant l'instruction `INSERT INTO` et en renseignant la structure avec des données provenant de la base de données [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].  
  
 [Leçon 4 : Création de prédictions de série chronologique à l’aide de DMX](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
 Dans cette leçon, vous apprendrez à créer des prédictions de séries chronologiques.  
  
 [Leçon 5 : Extension de la série chronologique de modèle](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
 Dans cette leçon, vous apprendrez comment utiliser le paramètre `EXTEND_MODEL_CASES` pour mettre à jour le modèle à l'aide des nouvelles données lorsque vous élaborez des prédictions.  
  
## <a name="requirements"></a>Spécifications  
 Avant d'entamer ce didacticiel, assurez-vous que les éléments suivants sont installés :  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)])  
  
-   Base de données [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]  
  
 Pour des raisons de sécurité, les bases de données exemples ne sont pas installées par défaut. Pour installer les bases de données exemples officiels pour [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], accédez à [ http://www.CodePlex.com/MSFTDBProdSamples ](http://go.microsoft.com/fwlink/?LinkId=88417) ou sur la page d’accueil de Microsoft SQL Server Samples and Community Projects dans la section Microsoft SQL Server Product Samples. Cliquez sur **Databases**, puis cliquez sur l'onglet **Releases** et sélectionnez les bases de données souhaitées.  
  
> [!NOTE]  
>  Lorsque vous parcourez les didacticiels, il est recommandé d'ajouter les boutons **Rubrique suivante** et **Rubrique précédente** dans la barre d'outils de l'afficheur de document.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’exploration de données de base de données](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Les intermédiaires Data Mining Tutorial &#40;Analysis Services - Exploration de données&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  